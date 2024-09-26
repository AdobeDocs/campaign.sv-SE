---
title: Nyckelhantering i Campaign
description: Kom igång med nyckelhantering
feature: Configuration, FFDA
role: Developer
level: Intermediate
exl-id: ef06cb6b-1b25-4dbe-8fd0-f880ec9d645b
source-git-commit: 9d500f185a9e706b6558135978c4f8c79d92d0d4
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Nyckelhantering och unicitet {#key-management}

I kontexten för en [Enterprise (FFDA)-distribution](enterprise-deployment.md) är primärnyckeln en UUID (Universally Unique IDentifier), som är en teckensträng. Om du vill skapa det här UUID:t måste huvudelementet i schemat innehålla attributen **autouid** och **autopk** inställda på **true**.

Adobe Campaign v8 använder [!DNL Snowflake] som kärndatabas. Den distribuerade arkitekturen för databasen [!DNL Snowflake] tillhandahåller ingen mekanism som garanterar att en nyckel i en tabell är unik: slutanvändarna ansvarar för nyckelkonsekvens i Adobe Campaign-databasen.

För att relationsdatabasens enhetlighet ska bevaras är det obligatoriskt att undvika dubbletter av nycklar, särskilt på primärnycklar. Dubbletter av primärnycklar leder till problem med datahanteringsarbetsflödesaktiviteter som **Fråga**, **Avstämning**, **Uppdatera data** och mycket annat. Detta är viktigt för att definiera korrekta avstämningsvillkor när [!DNL Snowflake]-tabeller uppdateras.


>[!CAUTION]
>
>Duplicerade nycklar är inte begränsade till UUID. Det kan hända med ID:n, inklusive anpassade nycklar som skapats i anpassade tabeller.


## Universitetstjänst{#unicity-service}

Unicity Service är en komponent i Cloud Database Manager som hjälper användare att bevara och övervaka integriteten för unika nyckelbegränsningar i molndatabastabeller. På så sätt kan du minska risken att infoga dubblettnycklar.

Eftersom molndatabasen inte tillämpar begränsningar för användargrupper minskar Unicity Service risken att infoga dubbletter när data hanteras med Adobe Campaign.

### Universitetsarbetsflöde{#unicity-wf}

Unicity Service levereras med ett dedikerat **[!UICONTROL Unicity alerting]** inbyggt arbetsflöde, som övervakar begränsningar för unicitet och varningar när dubbletter identifieras.

Det här tekniska arbetsflödet är tillgängligt från noden **[!UICONTROL Administration > Production > Technical workflows > Full FFDA Unicity]** i Campaign Explorer. **Den får inte ändras**.

Det här arbetsflödet kontrollerar alla anpassade och inbyggda scheman för att upptäcka dubblerade rader.

![](assets/unicity-alerting-wf.png)

Om arbetsflödet **[!UICONTROL Unicity alerting]** (ffdaUnicity) upptäcker några dubblettnycklar läggs de till i en specifik **Audit Unicity**-tabell, som innehåller schemats namn, typ av nyckel, antalet påverkade rader och datumet. Du kan komma åt duplicerade nycklar från noden **[!UICONTROL Administration > Audit > Key Unicity]**.

![](assets/unicity-table.png)

Som databasadministratör kan du använda en SQL-aktivitet för att ta bort dubbletter eller kontakta Adobe kundtjänst för mer vägledning.

### Varningar{#unicity-wf-alerting}

Ett specifikt meddelande skickas till operatörsgruppen **[!UICONTROL Workflow Supervisors]** när dubblettnycklar identifieras. Innehållet och målgruppen för den här aviseringen kan ändras i **aviseringsaktiviteten** i arbetsflödet **[!UICONTROL Unicity alerting]**.

![](assets/wf-alert-activity.png)


## Ytterligare skyddsräcken {#duplicates-guardrails}

Campaign innehåller en uppsättning nya skyddsritningar för att förhindra att dubblettnyckeln infogas i [!DNL Snowflake]-databasen.

>[!NOTE]
>
>Dessa skyddsförslag är tillgängliga från och med Campaign v8.3. Mer information om hur du kontrollerar versionen finns i [det här avsnittet](../start/compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)

### Förberedelse av leverans {#remove-duplicates-delivery-preparation}

Adobe Campaign tar automatiskt bort alla dubbletter av UUID från en målgrupp när leveransen förbereds. Den här mekanismen förhindrar att fel inträffar när en leverans förbereds. Som slutanvändare kan du kontrollera den här informationen i leveransloggarna: vissa mottagare kan uteslutas från huvudmålet på grund av dubblettnyckeln. I så fall visas följande varning: `Exclusion of duplicates (based on the primary key or targeted records)`.

![](assets/exclusion-duplicates-log.png)

### Uppdatera data i ett arbetsflöde {#duplicates-update-data}

I kontexten för en [Enterprise (FFDA)-distribution](enterprise-deployment.md) kan du inte välja en intern nyckel (UUID) som fält för att uppdatera data i ett arbetsflöde.

![](assets/update-data-no-internal-key.png)

### Fråga ett schema med dubbletter {#query-with-duplicates}

När ett arbetsflöde börjar köra en fråga i ett schema, kontrollerar Adobe Campaign om någon dubblerad post har rapporterats i tabellen [Audit Unicity](#unicity-wf). I så fall loggar arbetsflödet en varning eftersom den efterföljande åtgärden på de duplicerade data kan påverka arbetsflödesresultatet.

![](assets/query-with-duplicates.png)

Den här kontrollen utförs i följande arbetsflödesaktiviteter:

* Fråga
* Inkrementell fråga
* Läslista


>[!NOTE]
>
>Om ni övergår från en annan Campaign-version är det av största vikt att ni tar bort dubbletter, felsöker och sanerar data så att övergången inte påverkas.
