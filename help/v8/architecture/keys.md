---
title: Nyckelhantering i Campaign
description: Kom igång med nyckelhantering
feature: Configuration, FFDA
role: Developer
level: Intermediate
exl-id: ef06cb6b-1b25-4dbe-8fd0-f880ec9d645b
source-git-commit: f577ee6d303bab9bb07350b60cf0fa6fc9d3a163
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Nyckelhantering och unicitet {#key-management}

När det gäller en [Företagsdistribution (FFDA)](enterprise-deployment.md)primärnyckeln är en UUID (Universally Unique IDentifier) som är en teckensträng. För att skapa detta UUID måste schemats huvudelement innehålla **autouuid** och **autopk** attribut inställda på **true**.

Adobe Campaign v8 använder [!DNL Snowflake] som kärndatabas. Den distribuerade arkitekturen för [!DNL Snowflake] databasen har ingen mekanism som säkerställer att en nyckel i en tabell är unik: slutanvändarna ansvarar för nyckelkonsekvens i Adobe Campaign-databasen.

För att relationsdatabasens enhetlighet ska bevaras är det obligatoriskt att undvika dubbletter av nycklar, särskilt på primärnycklar. Dubbletter av primärnycklar leder till problem med arbetsflödesaktiviteter för datahantering, som **Fråga**, **Avstämning**, **Uppdatera data**, med mera. Detta är viktigt för att definiera korrekta avstämningskriterier vid uppdatering [!DNL Snowflake] tabeller.


>[!CAUTION]
>
>Duplicerade nycklar är inte begränsade till UUID. Det kan hända med ID:n, inklusive anpassade nycklar som skapats i anpassade tabeller.


## Universitetstjänst{#unicity-service}

Unicity Service är en komponent i Cloud Database Manager som hjälper användare att bevara och övervaka integriteten för unika nyckelbegränsningar i molndatabastabeller. På så sätt kan du minska risken att infoga dubblettnycklar.

Eftersom molndatabasen inte tillämpar begränsningar för användargrupper minskar Unicity Service risken att infoga dubbletter när data hanteras med Adobe Campaign.

### Universitetsarbetsflöde{#unicity-wf}

Universitetstjänsten har en dedikerad **[!UICONTROL Unicity alerting]** inbyggt arbetsflöde för att övervaka begränsningar för användargrupper och varningar när dubbletter upptäcks.

Det här tekniska arbetsflödet är tillgängligt från **[!UICONTROL Administration > Production > Technical workflows > Full FFDA Unicity]** nod i Campaign Explorer. **Den får inte ändras**.

Det här arbetsflödet kontrollerar alla anpassade och inbyggda scheman för att upptäcka dubblerade rader.

![](assets/unicity-alerting-wf.png)

Om **[!UICONTROL Unicity alerting]** (ffdaUnicity) arbetsflödet identifierar vissa dubblettnycklar, de läggs till i en viss **Granskningsenhet** tabellen, som innehåller schemats namn, typ av nyckel, antalet påverkade rader och datumet. Du kan komma åt duplicerade nycklar från **[!UICONTROL Administration > Audit > Key Unicity]** nod.

![](assets/unicity-table.png)

Som databasadministratör kan du använda en SQL-aktivitet för att ta bort dubbletter eller kontakta Adobe kundtjänst för mer vägledning.

### Varningar{#unicity-wf-alerting}

Ett specifikt meddelande skickas till **[!UICONTROL Workflow Supervisors]** när dubblettnycklar identifieras. Innehållet och målgruppen för den här aviseringen kan ändras i **Varning** verksamhet som **[!UICONTROL Unicity alerting]** arbetsflöde.

![](assets/wf-alert-activity.png)


## Ytterligare skyddsräcken{#duplicates-guardrails}

Campaign innehåller en uppsättning nya skyddsritningar för att förhindra att duplicerad nyckel infogas i [!DNL Snowflake] databas.

>[!NOTE]
>
>Dessa skyddsförslag är tillgängliga från och med Campaign v8.3. Om du vill kontrollera versionen läser du [det här avsnittet](../start/compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)

### Förberedelse av leverans{#remove-duplicates-delivery-preparation}

Adobe Campaign tar automatiskt bort alla dubbletter av UUID från en målgrupp när leveransen förbereds. Den här mekanismen förhindrar att fel inträffar när en leverans förbereds. Som slutanvändare kan du kontrollera den här informationen i leveransloggarna: vissa mottagare kan uteslutas från huvudmålet på grund av dubblettnyckeln. I så fall visas följande varning: `Exclusion of duplicates (based on the primary key or targeted records)`.

![](assets/exclusion-duplicates-log.png)

### Uppdatera data i ett arbetsflöde{#duplicates-update-data}

När det gäller en [Företagsdistribution (FFDA)](enterprise-deployment.md)kan du inte välja en intern nyckel (UUID) som fält för att uppdatera data i ett arbetsflöde.

![](assets/update-data-no-internal-key.png)

### Fråga ett schema med dubbletter{#query-with-duplicates}

När ett arbetsflöde börjar köra en fråga i ett schema, kontrollerar Adobe Campaign om det finns dubblerade poster i [Granska Unicity-register](#unicity-wf). I så fall loggar arbetsflödet en varning eftersom den efterföljande åtgärden på de duplicerade data kan påverka arbetsflödesresultatet.

![](assets/query-with-duplicates.png)

Den här kontrollen utförs i följande arbetsflödesaktiviteter:

* Fråga
* Inkrementell fråga
* Läslista