---
title: Genomförande av riktlinjer
description: Lär dig implementera Campaign v8
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 09562b6c-3d3d-4808-a70b-202172867f46
source-git-commit: d2f4e54b0c37cc019061dd3a7b7048cd80876ac0
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 3%

---

# Riktlinjer för kampanjgenomförande

I det här avsnittet får du lära dig hur du anpassar Adobe Campaign efter företagets behov. Använd följande riktlinjer för att strukturera och organisera implementeringen.

1. **Definiera inställningar**: ge åtkomst, dela klientkonsolen, konfigurera kanaler (e-post, push, sms)
1. **Förbered din miljö**: importera profiler, skapa målgrupper, utforma arbetsflöden och kampanjmallar, skapa typologiregler
1. **Anpassa instansen**: skapa nya datafält, lägga till tabeller/scheman
1. **Utöka er driftsättning**: ansluta till Adobe-lösningar, andra produkter och system - anslutningar, inställningar för flera lösningar

>[!CAUTION]
>
>Med **Kampanjhanterade Cloud Services**, din miljö och den ursprungliga konfigurationen har angetts av Adobe enligt villkoren i licensavtalet. Du får inte ändra installerade inbyggda paket, inbyggda scheman eller rapporter.
>
>Om du behöver använda ett Campaign-tillägg eller en specifik funktion som inte har etablerats för dig måste du kontakta **Adobe kundtjänst**.

## Före start

Det här avsnittet innehåller viktig information om sekretess och säkerhet som måste granskas och beaktas innan den faktiska implementeringen kan påbörjas.

### Sekretess

Adobe Campaign innehåller processer och inställningar som gör att ni kan använda Campaign i enlighet med gällande datasekretesslagstiftning och mottagarens önskemål. Du kan hantera:

* **Datainsamling**: Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du får och hanterar samtycke från dina mottagare. Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html?lang=en#data-acquisition)

* **Användarens samtycke och datalagring**: Lär dig hur du får användarens samtycke, konfigurerar prenumerationsmekanismer för dubbel anmälan, underlättar avanmälan och konfigurerar datalagring i [Sekretessdokumentation för Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html?lang=en#consent)

* **Sekretess- och dataskyddsbestämmelser**: referera till [Sekretessdokumentation för Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html){target=&quot;_blank&quot;} för information om EU:s allmänna dataskyddsförordning (GDPR), California Consumer Privacy Act (CCPA) och andra internationella integritetskrav, och hur dessa bestämmelser påverkar din organisation och Adobe Campaign.

### Säkerhet

Läs säkerhetsriktlinjer och principer med Adobe Campaign i [Checklista för kampanjsäkerhet](../config/security.md).

## Definiera kampanjinställningar

### Lägga till användare och bevilja behörigheter

Du kan lägga till användare manuellt i Campaign och associera dem med grupper, justerade mot din rollhierarki. Användarna kan sedan logga in och komma åt de data och behörigheter som passar dem.

![](../assets/do-not-localize/book.png) Lär dig hur du lägger till användare i Adobe Campaign i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management.html?lang=en#getting-started){target=&quot;_blank&quot;}.

### Installera Campaign Client Console

Programmets huvudanvändargränssnitt är en avancerad klient, d.v.s. ett inbyggt program (Windows) som kommunicerar med Adobe Campaign programserver enbart med standardInternetprotokoll (SOAP, HTTP osv.). Adobe Campaign Client Console är mycket användarvänligt för ökad produktivitet och använder mycket liten bandbredd (genom att använda ett lokalt cacheminne) och är utformat för enkel driftsättning. Konsolen kan distribueras från en webbläsare, kan uppdateras automatiskt och kräver ingen specifik nätverkskonfiguration eftersom den bara genererar HTTP(S)-trafik.

![](../assets/do-not-localize/glass.png) [Läs mer om Campaign Client Console](connect.md).

## Förbered din miljö

Innan du börjar skicka meddelanden och skapa marknadsföringskampanjer måste du:

1. Importera profiler och skapa målgrupper

   Med Campaign kan du lägga till kontakter i molndatabasen. Du kan läsa in en fil, schemalägga och automatisera flera kontaktuppdateringar, samla in data på webben eller ange profilinformation direkt i mottagartabellen.

   ![](../assets/do-not-localize/glass.png) [Så här importerar du profiler](import.md).

   Målgrupper grupperas i listor och kan skapas med arbetsflöden. De kan sedan användas för flerkanalsleveranser.

   ![](../assets/do-not-localize/glass.png) [Lär dig definiera målgrupper](audiences.md).

1. Skapa mallar

   Kampanjer, leveranser, jobb eller arbetsflöden är alla baserade på en mall som lagrar viktiga inställningar och funktioner. En inbyggd mall tillhandahålls för varje komponent som ingen specifik konfiguration har definierats för. Du måste konfigurera och anpassa mallar efter dina behov och göra dem tillgängliga för slutanvändarna.

   ![](../assets/do-not-localize/book.png) [Läs mer om e-postmallar](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-delivery-templates/about-templates.html){target=&quot;_blank&quot;}

   ![](../assets/do-not-localize/book.png) Lär dig hur du arbetar med kampanjmallar i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-templates.html?lang=en#orchestrating-campaigns){target=&quot;_blank&quot;}

   ![](../assets/do-not-localize/book.png) Lär dig hur du konfigurerar en arbetsflödesmall i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/building-a-workflow.html?lang=en#workflow-templates){target=&quot;_blank&quot;}

1. Konfigurera typologiregler

   Använd regler för kampanjtypologier för att filtrera, styra och övervaka leveransen. Trötthetsreglerna styr till exempel frekvens och kvantitet för meddelanden för att undvika att mottagarna blir för många. När typologireglerna är implementerade refereras de i leveranser.

   ![](../assets/do-not-localize/book.png) Läs mer om typologier och trötthetshantering i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html?lang=en#orchestrating-campaigns){target=&quot;_blank&quot;}

1. Bekanta dig med Campaigns inbyggda datamodell

   Adobe Campaign innehåller en fördefinierad datamodell. För att implementera och anpassa din miljö måste du känna till de inbyggda tabellerna i Adobe Campaign datamodell och hur de relaterar till varandra.

   ![](../assets/do-not-localize/glass.png) [Läs mer om Campaign-datamodellen](../dev/datamodel.md).

## Anpassa instansen

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

   ![](../assets/do-not-localize/glass.png) Läs mer om rapportfunktioner i Campaign i [den här sidan](reporting.md).


## Ställ in kampanjautomatisering

Använd automatiseringsfunktionerna i Campaign för att samordna komplexa marknadsföringskampanjer för olika målgrupper över flera kanaler.

* Arbetsflöden: hantera processer och data

* Prenumerationer och landningssidor

* Typologiregler: Trötthet och kontrollhantering

## Utöka er driftsättning

### Implementering av flera lösningar

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

### Kopplingar

Koppla samman Campaign med tredjepartssystem för att kombinera ett stort antal funktioner och automatisera processer.

![](../assets/do-not-localize/glass.png) Läs mer om tillgängliga anslutningar i [det här avsnittet](../connect/integration.md).

**Koppla CRM till Campaign**

Du kan ansluta din Adobe Campaign-plattform till dina CRM-system från tredje part och synkronisera data: kontakter, konton, inköp osv.

![](../assets/do-not-localize/glass.png) Lär dig hur du ansluter ditt CRM-system till Campaign i [det här avsnittet](../connect/integration.md#gs-crm-connectors)

**Ansluta till en extern databas**

Du kan ansluta Campaign Cloud-databasen till externa system via FDA-modulen (Federated Data Access).

![](../assets/do-not-localize/glass.png) Lär dig hur du konfigurerar Campaign FDA-modulen för att definiera åtkomstparametrar i [det här avsnittet](../connect/integration.md#gs-fda)
