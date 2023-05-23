---
title: Genomförande av riktlinjer
description: Lär dig implementera Campaign v8
feature: Overview
role: User, Admin, Developer
level: Beginner, Intermediate
exl-id: 09562b6c-3d3d-4808-a70b-202172867f46
source-git-commit: 65f4da979f0c5884797af0c3a835d948672b4a7c
workflow-type: tm+mt
source-wordcount: '1187'
ht-degree: 4%

---

# Riktlinjer för kampanjgenomförande{#gs-implementation}

I det här avsnittet får du lära dig hur du anpassar Adobe Campaign efter företagets behov. Använd följande riktlinjer för att strukturera och organisera implementeringen.

1. **Definiera inställningar**: ge åtkomst, dela klientkonsolen, konfigurera kanaler (e-post, push, sms). [Läs mer](#implementation-ac-settings)
1. **Förbered din miljö**: importera profiler, skapa målgrupper, utforma arbetsflöden och kampanjmallar, skapa typologiregler. [Läs mer](#implementation-prepare-your-env)
1. **Anpassa instansen**: skapa nya datafält, lägga till tabeller/scheman. [Läs mer](#implementation-custom-your-instance)
1. **Automatisera era processer**: konfigurera Adobe Campaign automatiseringsfunktioner. [Läs mer](#implementation-automation)
1. **Utöka er driftsättning**: ansluta till Adobe-lösningar, andra produkter och system - anslutningar, inställningar för flera lösningar. [Läs mer](#implementation-extend)

>[!CAUTION]
>
>Med **Kampanjhanterade Cloud Services**, din miljö och den ursprungliga konfigurationen anges av Adobe, enligt villkoren i licensavtalet. Du får inte ändra installerade inbyggda paket, inbyggda scheman eller rapporter.
>
>Om du behöver använda ett Campaign-tillägg eller en specifik funktion som inte har etablerats för dig måste du kontakta **Adobe kundtjänst**.

## Före start{#before-starting}

Det här avsnittet innehåller viktig information om sekretess och säkerhet som måste granskas och beaktas innan den faktiska implementeringen kan påbörjas.

### Sekretess{#implementation-privacy}

Adobe Campaign innehåller processer och inställningar som gör att ni kan använda Campaign i enlighet med gällande datasekretesslagstiftning och mottagarens önskemål. Du kan hantera:

* **Datainsamling**: Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du får och hanterar samtycke från dina mottagare.

   Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html#data-acquisition){target="_blank"}

* **Användarens samtycke och datalagring**: måste du få användarens samtycke, skapa prenumerationsmekanismer för dubbel anmälan, underlätta avanmälan och konfigurera datalagring.

   Läs mer i [Sekretessdokumentation för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html#consent){target="_blank"}

* **Sekretess- och dataskyddsbestämmelser**: referera till [det här avsnittet](privacy.md) om du vill ha information om sekretesskrav och hur dessa bestämmelser påverkar din organisation och Adobe Campaign.

### Säkerhet

Läs säkerhetsriktlinjer och principer med Adobe Campaign i [Checklista för kampanjsäkerhet](../config/security.md).

## Definiera kampanjinställningar{#implementation-ac-settings}

### Lägga till användare och bevilja behörigheter{#implementation-add-users}

Du kan lägga till användare manuellt i Campaign och associera dem med grupper, justerade mot din rollhierarki. Användarna kan sedan logga in och komma åt de data och behörigheter som passar dem.

![](../assets/do-not-localize/glass.png) Lär dig hur du lägger till användare i Adobe Campaign i [det här avsnittet](../start/gs-permissions.md).

### Installera Campaign Client Console{#implementation-install-console}

Programmets huvudanvändargränssnitt är en avancerad klient, d.v.s. ett inbyggt program (Windows) som kommunicerar med Adobe Campaign programserver enbart med standardInternetprotokoll (SOAP, HTTP osv.). Adobe Campaign Client Console är mycket användarvänligt för ökad produktivitet och använder mycket liten bandbredd (genom att använda ett lokalt cacheminne) och är utformat för enkel driftsättning. Konsolen kan distribueras från en webbläsare, kan uppdateras automatiskt och kräver ingen specifik nätverkskonfiguration eftersom den bara genererar HTTP(S)-trafik.

![](../assets/do-not-localize/glass.png) [Läs mer om Campaign Client Console](connect.md).

## Förbered din miljö{#implementation-prepare-your-env}

Innan du börjar skicka meddelanden och skapa marknadsföringskampanjer måste du:

1. **Importera profiler och skapa målgrupper**

   Med Campaign kan du lägga till kontakter i molndatabasen. Du kan läsa in en fil, schemalägga och automatisera flera kontaktuppdateringar, samla in data på webben eller ange profilinformation direkt i mottagartabellen.

   ![](../assets/do-not-localize/glass.png) [Så här importerar du profiler](import.md).

   Målgrupper grupperas i listor och kan skapas med arbetsflöden. De kan sedan användas för flerkanalsleveranser.

   ![](../assets/do-not-localize/glass.png) [Lär dig definiera målgrupper](audiences.md).

1. **Använda mallar**

   Kampanjer, leveranser, jobb eller arbetsflöden är alla baserade på en mall som lagrar viktiga inställningar och funktioner. En inbyggd mall tillhandahålls för varje komponent som ingen specifik konfiguration har definierats för. Du måste konfigurera och anpassa mallar efter dina behov och göra dem tillgängliga för slutanvändarna.


   ![](../assets/do-not-localize/glass.png) Lär dig hur du arbetar med kampanjmallar i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-templates.html)

   ![](../assets/do-not-localize/glass.png) Lär dig hur du konfigurerar en arbetsflödesmall i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html)

   ![](../assets/do-not-localize/book.png) Läs mer om e-postmallar i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-delivery-templates/about-templates.html){target="_blank"}


1. **Konfigurera typologiregler**

   Använd regler för kampanjtypologier för att filtrera, styra och övervaka leveransen. Trötthetsreglerna styr till exempel frekvens och kvantitet för meddelanden för att undvika att mottagarna blir för många. När typologireglerna är implementerade refereras de i leveranser.

   Läs mer om typologier och trötthetshantering i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html).

1. **Bekanta dig med Campaigns inbyggda datamodell**

   Adobe Campaign innehåller en fördefinierad datamodell. För att implementera och anpassa din miljö måste du känna till de inbyggda tabellerna i Adobe Campaign datamodell och hur de relaterar till varandra.

   ![](../assets/do-not-localize/glass.png) [Läs mer om Campaign-datamodellen](../dev/datamodel.md).

## Anpassa instansen{#implementation-custom-your-instance}

Ni kan anpassa många olika Campaign-områden och -funktioner. De flesta av våra kunder anpassar tre saker:

1. **Tabeller och scheman**

   Adobe Campaign innehåller vanliga scheman för att identifiera data som: mottagare, leveransloggar, prenumerationer med mera.

   ![](../assets/do-not-localize/glass.png) Mer information om [Inbyggd kampanjdatamodell](../dev/datamodel.md).

   ![](../assets/do-not-localize/glass.png) Du kan utöka befintliga scheman eller skapa nya scheman från grunden. Läs mer i [den här sidan](../dev/customize.md).

1. **Kontrollpaneler och listor**

   Du kan enkelt konfigurera listor, lägga till och ta bort fält och anpassa kolumner.

   ![](../assets/do-not-localize/glass.png) Lär dig hur du hanterar filter och listor i Campaign i [den här sidan](../dev/customize.md#gs-lists-and-filters).

   Du kan också skapa nya instrumentpaneler för att visa Campaign-data beroende på dina behov.

   ![](../assets/do-not-localize/glass.png)[ Läs mer på den här sidan](../dev/customize.md#gs-custom-dashboards).

1. **Rapporter**

   Campaign innehåller en uppsättning inbyggda rapporter om leveransövervakning, URL:er och klickströmmar, spårning, leveransindikatorer med mera.

   Förutom inbyggda rapporter kan du med Adobe Campaign generera rapporter i olika sammanhang och för att tillgodose olika behov. Principer för användning och implementeringslägen beskrivs i detta dokument.

   ![](../assets/do-not-localize/glass.png) Läs mer om rapportfunktioner i Campaign i [den här sidan](../reporting/gs-reporting.md).


## Ställ in kampanjautomatisering{#implementation-automation}

Använd automatiseringsfunktionerna i Campaign för att samordna komplexa marknadsföringskampanjer för olika målgrupper över flera kanaler.

* Använd **arbetsflöden** att hantera processer och data. Läs mer i [den här dokumentationen](../../automation/workflow/about-workflows.md)

* Konfigurera **prenumeration** processer och **landningssidor**.  Läs mer i [den här sidan](../start/subscriptions.md)

* Konfigurera **typologiregler** Definiera trötthet och kontrollhantering.  Läs mer i [den här dokumentationen](../../automation/campaign-opt/campaign-typologies.md)


## Utöka er driftsättning{#implementation-extend}

### Implementering av flera lösningar{#implementation-multi-solutions}

Om ni använder andra Adobe-lösningar kan ni koppla dem till er Campaign-miljö och kombinera funktioner.

* Campaign - Journey Orchestration
* Campaign - CDP i realtid
* Campaign - utlösare för Experience Cloud
* Campaign - Experience Manager
* Campaign - Target
* Campaign - Audience Manager / People core service
* Kampanj - tillgång
* Campaign - Analytics Data Connectors


Du kan också använda enkel inloggning (SSO) för att ansluta till Campaign. Läs mer i [den här sidan](connect.md).

![](../assets/do-not-localize/glass.png) Upptäck hela listan över Adobe som kan integreras med Adobe Campaign [på den här sidan](../connect/integration.md).

### Kopplingar{#implementation-connectors}

Koppla samman Campaign med tredjepartssystem för att kombinera ett stort antal funktioner och automatisera processer.

![](../assets/do-not-localize/glass.png) Läs mer om tillgängliga anslutningar i [det här avsnittet](../connect/integration.md).

**Koppla CRM till Campaign**

Du kan ansluta din Adobe Campaign-plattform till dina CRM-system från tredje part och synkronisera data: kontakter, konton, inköp osv.

![](../assets/do-not-localize/glass.png) Lär dig hur du ansluter ditt CRM-system till Campaign i [det här avsnittet](../connect/integration.md#gs-crm-connectors)

**Ansluta till en extern databas**

Du kan ansluta Campaign Cloud-databasen till externa system via FDA-modulen (Federated Data Access).

![](../assets/do-not-localize/glass.png) Lär dig hur du konfigurerar Campaign FDA-modulen för att definiera åtkomstparametrar i [det här avsnittet](../connect/integration.md#gs-fda)
