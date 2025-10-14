---
title: Genomförande av riktlinjer
description: Lär dig implementera Campaign v8
feature: Overview
role: User
level: Intermediate
exl-id: 09562b6c-3d3d-4808-a70b-202172867f46
source-git-commit: 96f1518f252be7ffa27ba8157b8a090bf4d4510d
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 3%

---

# Riktlinjer för kampanjimplementering{#gs-implementation}

I det här avsnittet får du lära dig hur du anpassar Adobe Campaign efter företagets behov. Använd följande riktlinjer för att strukturera och organisera implementeringen.

1. **Definiera inställningar**: bevilja åtkomst, dela klientkonsolen, konfigurera kanaler (e-post, push, sms). [Läs mer](#implementation-ac-settings)
1. **Förbered din miljö**: importera profiler, skapa målgrupper, utforma arbetsflöden och kampanjmallar, skapa typologiregler. [Läs mer](#implementation-prepare-your-env)
1. **Anpassa instansen**: skapa nya datafält, lägg till tabeller/scheman. [Läs mer](#implementation-custom-your-instance)
1. **Automatisera processerna**: konfigurera Adobe Campaign automatiseringsfunktioner. [Läs mer](#implementation-automation)
1. **Utöka din distribution**: anslut till Adobe-lösningar, andra produkter och system - anslutningar, inställningar för flera lösningar. [Läs mer](#implementation-extend)

>[!CAUTION]
>
>Med **Kampanjhanterade molntjänster** ställs din miljö och den inledande konfigurationen in av Adobe enligt villkoren i licensavtalet. Du får inte ändra installerade inbyggda paket, inbyggda scheman eller rapporter.
>
>Om du behöver använda ett Campaign-tillägg eller en viss funktion som inte har etablerats för dig måste du kontakta **Adobe Transition Manager**.

## Före start{#before-starting}

Det här avsnittet innehåller viktig information om sekretess och säkerhet som måste granskas och beaktas innan den faktiska implementeringen kan påbörjas.

### Sekretess{#implementation-privacy}

Adobe Campaign innehåller processer och inställningar som gör att ni kan använda Campaign i enlighet med gällande datasekretesslagstiftning och mottagarens önskemål. Du kan hantera:

* **Datainsamling**: Med Adobe Campaign kan du samla in data, inklusive personlig och känslig information. Det är därför viktigt att du får och hanterar samtycke från dina mottagare.

  Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html#data-acquisition){target="_blank"}

* **Användarens samtycke och datalagring**: du måste få användarens samtycke, konfigurera prenumerationsmekanismer för dubbel anmälan, underlätta avanmälan och konfigurera datalagring.

  Läs mer i [Sekretessdokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html#consent){target="_blank"}

* **Sekretess- och dataskyddsbestämmelser**: se [det här avsnittet](privacy.md) för information om sekretesskrav och hur dessa bestämmelser påverkar din organisation och Adobe Campaign.

### Säkerhet

Läs säkerhetsriktlinjer och principer med Adobe Campaign i [checklistan för kampanjsäkerhet](../config/security.md).

## Definiera kampanjinställningar{#implementation-ac-settings}

### Lägga till användare och bevilja behörigheter{#implementation-add-users}

Du kan lägga till användare manuellt i Campaign och associera dem med grupper, justerade mot din rollhierarki. Användarna kan sedan logga in och komma åt de data och behörigheter som är lämpliga för dem.

Lär dig hur du lägger till användare i Adobe Campaign i [det här avsnittet](../start/gs-permissions.md).

### Installera Campaign-klientkonsolen{#implementation-install-console}

Programmets huvudanvändargränssnitt är en avancerad klient, d.v.s. ett inbyggt program (Windows) som kommunicerar med Adobe Campaign-programservern enbart med standardInternetprotokoll (SOAP, HTTP osv.). Adobe Campaign klientkonsol är mycket användarvänlig, har mycket liten bandbredd (med hjälp av ett lokalt cacheminne) och är utformad för enkel driftsättning. Konsolen kan distribueras från en webbläsare, kan uppdateras automatiskt och kräver ingen specifik nätverkskonfiguration eftersom den bara genererar HTTP(S)-trafik.

[Läs mer om Campaign-klientkonsolen](connect.md).

## Förbered din miljö{#implementation-prepare-your-env}

Innan du börjar skicka meddelanden och skapa marknadsföringskampanjer måste du:

1. **Importera profiler och skapa målgrupper**

   Med Campaign kan du lägga till kontakter i molndatabasen. Du kan läsa in en fil, schemalägga och automatisera flera kontaktuppdateringar, samla in data på webben eller ange profilinformation direkt i mottagartabellen.

   [Lär dig hur du importerar profiler](import.md).

   Målgrupper grupperas i listor och kan skapas med arbetsflöden. De kan sedan användas för flerkanalsleveranser.

   [Lär dig definiera målgrupper](audiences.md).

1. **Använda mallar**

   Kampanjer, leveranser, jobb eller arbetsflöden är alla baserade på en mall som lagrar viktiga inställningar och funktioner. En inbyggd mall tillhandahålls för varje komponent som ingen specifik konfiguration har definierats för. Du måste konfigurera och anpassa mallar efter dina behov och göra dem tillgängliga för slutanvändarna.


   Lär dig hur du arbetar med kampanjmallar på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-templates.html){target="_blank"}.

   Lär dig konfigurera en arbetsflödesmall på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"}.

   Läs mer om e-postmallar på den här [sidan](../send/create-templates.md).


1. **Konfigurera typologiregler**

   Använd regler för kampanjtypologier för att filtrera, styra och övervaka leveransen. Trötthetsreglerna styr till exempel frekvens och kvantitet för meddelanden för att undvika att mottagarna blir för många. När typologireglerna är implementerade refereras de i leveranser.

   Läs mer om typologier och trötthetshantering i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html){target="_blank"}.

1. **Bekanta dig med Campaigns inbyggda datamodell**

   Adobe Campaign innehåller en fördefinierad datamodell. För att implementera och anpassa din miljö måste du känna till de inbyggda tabellerna i Adobe Campaign datamodell och hur de relaterar till varandra.

   [Läs mer om Campaign-datamodellen](../dev/datamodel.md).

## Anpassa instansen{#implementation-custom-your-instance}

Ni kan anpassa många olika Campaign-områden och -funktioner. De flesta av våra kunder anpassar tre saker:

1. **Tabeller och scheman**

   Adobe Campaign innehåller scheman för att identifiera t.ex. mottagare, leveransloggar, prenumerationer med mera.

   Mer information om [Kampanjens inbyggda datamodell](../dev/datamodel.md) finns i det här avsnittet.

   Du kan utöka befintliga scheman eller skapa nya scheman från grunden. Läs mer på [den här sidan](../dev/customize.md).

1. **Kontrollpaneler och listor**

   Du kan enkelt konfigurera listor, lägga till och ta bort fält och anpassa kolumner.

   Lär dig hur du hanterar filter och listor i Campaign på [den här sidan](../dev/customize.md#gs-lists-and-filters).

   Du kan också skapa nya instrumentpaneler för att visa Campaign-data beroende på dina behov.

   Läs mer på [den här sidan](../dev/customize.md#gs-custom-dashboards).

1. **Rapporter**

   Campaign innehåller en uppsättning inbyggda rapporter om leveransövervakning, URL:er och klickströmmar, spårning, leveransindikatorer med mera.

   Förutom inbyggda rapporter kan du i Adobe Campaign generera rapporter i olika sammanhang och för att tillgodose olika behov. Principer för användning och implementeringslägen beskrivs i detta dokument.

   Läs mer om rapportfunktioner i Campaign på [den här sidan](../reporting/gs-reporting.md).


## Ställ in kampanjautomatisering{#implementation-automation}

Använd automatiseringsfunktionerna i Campaign för att samordna komplexa marknadsföringskampanjer för olika målgrupper över flera kanaler.

* Använd **arbetsflöden** för att hantera processer och data. Läs mer i [den här dokumentationen](../../automation/workflow/about-workflows.md)

* Konfigurera **prenumerationsprocesser** och **landningssidor**.  Läs mer på [den här sidan](../start/subscriptions.md)

* Konfigurera **typologiregler** för att definiera trötthet och kontrollhantering.  Läs mer i [den här dokumentationen](../../automation/campaign-opt/campaign-typologies.md)


## Utöka er driftsättning{#implementation-extend}

### Implementering av flera lösningar{#implementation-multi-solutions}

Om ni använder andra Adobe-lösningar kan ni koppla dem till er Campaign-miljö och kombinera funktioner.

* Campaign - Journey Orchestration
* Campaign - CDP i realtid
* Campaign - Experience Cloud Triggers
* Campaign - Experience Manager
* Campaign - Target
* Campaign - Audience Manager/People core service
* Kampanj - tillgång
* Campaign - Analytics Data Connectors


Du kan bara använda enkel inloggning (SSO) för att ansluta till Campaign. Läs mer på [den här sidan](connect.md).

Upptäck den fullständiga listan över Adobe-lösningar som kan integreras med Adobe Campaign [på den här sidan](../connect/integration.md).

### Kopplingar{#implementation-connectors}

Koppla samman Campaign med tredjepartssystem för att kombinera ett stort antal funktioner och automatisera processer.

Läs mer om tillgängliga anslutningar i [det här avsnittet](../connect/integration.md).

**Anslut CRM till kampanj**

Du kan ansluta din Adobe Campaign-plattform till dina CRM-system från tredje part och synkronisera data: kontakter, konton, inköp osv.

Lär dig hur du ansluter CRM-systemet till Campaign i [det här avsnittet](../connect/integration.md#gs-crm-connectors)

**Anslut till en extern databas**

Du kan ansluta Campaign Cloud-databasen till externa system via FDA-modulen (Federated Data Access).

Lär dig konfigurera Campaign FDA-modulen för att definiera åtkomstparametrar i [det här avsnittet](../connect/integration.md#gs-fda)
