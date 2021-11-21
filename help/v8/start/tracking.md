---
title: Kom igång med funktioner för spårning och övervakning
description: Kom igång med funktioner för spårning och övervakning
feature: Overview
role: Data Engineer
level: Beginner
exl-id: f3de901f-519f-42ae-846c-f20c7cb560df
source-git-commit: 00a88cf9217faf32070a3cd34a2c1ae5243d9a6e
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 2%

---

# Spåra och övervaka meddelanden{#gs-ac-reports}

## Spårningsfunktioner i Campaign

Kampanjspårningsfunktioner spårar skickade meddelanden och hjälper dig att analysera mottagarnas beteende: öppna, klicka på länkar, prenumerationer/prenumerationer med mera. Ni kan få tillgång till dedikerade loggar, rapporter och mätvärden, fråga databasen för att granska insamlade data och mycket annat.

Mer information finns i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/profile-management/editing-a-profile.html?lang=en#tracking-tab){target=&quot;_blank&quot;}.

Kontrollpanelen för leverans är ett viktigt verktyg för att övervaka leveranser och potentiella problem när meddelanden skickas.

Mer information om detta finns i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html?lang=en#sending-messages){target=&quot;_blank&quot;}.

De nyckelspårningsfunktioner som är tillgängliga i Campaign listas nedan.

### Meddelandespårning {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Spårade länkar**

Du kan spåra mottagning av meddelanden och aktivering av länkar som infogats i meddelandeinnehållet för att bättre förstå mottagarnas beteende.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/how-to-configure-tracked-links.html?lang=en#sending-messages){target=&quot;_blank&quot;}

**URL-spårning**

Spårningsalternativen kan konfigureras genom att aktivera eller inaktivera spårade URL:er.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/personalizing-url-tracking.html?lang=en#sending-messages){target=&quot;_blank&quot;}


**Spårad länkpersonalisering**

Kampanjspårningsfunktionerna gör att ni kan lägga till länkar i e-postmeddelanden som kan personaliseras och som stöder spårning.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/tracking-personalized-links/tracking-personalized-links.html?lang=en#sending-messages){target=&quot;_blank&quot;}

**Spårningsloggar**

The **Spårning** tekniskt arbetsflöde hämtar spårningsdata när leveransen har skickats och spårningen har aktiverats. Dessa data finns på fliken Spårning för leveransen.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/accessing-the-tracking-logs.html?lang=en#sending-messages){target=&quot;_blank&quot;}

**Testa spårning**

Innan du skickar meddelanden med din spårning kan du testa spårningen på din spegelsida, e-postloggar och länkar.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/testing-tracking.html?lang=en#sending-messages){target=&quot;_blank&quot;}

### Spårning av webbprogram {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Spåra en webbapplikation**

Du kan också spåra och mäta besök på webbprogramsidor med hjälp av spårningstaggar. Den här funktionen kan användas för alla typer av webbprogram, t.ex. formulär och onlineundersökningar.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/tracking-a-web-application.html?lang=en#designing-content){target=&quot;_blank&quot;}

**Välj att inte delta i spårning av webbapplikation**

Med avanmälan om spårning av webbprogram kan du sluta spåra webbbeteenden för slutanvändare som avanmäler sig från beteendespårning. Du kan inkludera möjligheten att visa en banderoll i webbprogram eller landningssidor så att användarna kan välja bort den.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/web-application-tracking-opt-out.html?lang=en#designing-content){target=&quot;_blank&quot;}

### Spåra rapporter {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Spårningsstatistik**

Den här rapporten innehåller statistik om öppningar, klick och transaktioner och gör att du kan spåra marknadsföringseffekten av leveransen.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/about-message-tracking.html?lang=en#tracking-reports){target=&quot;_blank&quot;}

**URL:er och klickbara strömmar**

Den här rapporten innehåller en lista över besökta sidor efter en leverans.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html?lang=en#urls-and-click-streams){target=&quot;_blank&quot;}

**Person/personer och mottagare**

I det här exemplet är det lättare att förstå skillnaden mellan en person/person och en mottagare i Adobe Campaign.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/person-people-recipients.html?lang=en#reporting){target=&quot;_blank&quot;}

**Spårningsindikatorer**

I den här rapporten kombineras nyckelindikatorer för att spåra mottagarnas beteende när de får leveransen, till exempel öppnings- och klickfrekvens och klickströmmar.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html?lang=en#reporting){target=&quot;_blank&quot;}

**Indikatorberäkning**

De olika tabellerna ger dig en lista över indikatorer som används i de olika rapporterna och deras beräkningsformel beroende på leveranstyp.

[Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/indicator-calculation.html?lang=en#reporting){target=&quot;_blank&quot;}

## Riktlinjer för övervakning

Adobe Campaign har en uppsättning funktioner för att övervaka processerna och miljön.

### Övervaka leveranser

Att övervaka era leveranser efter att de har skickats är ett viktigt steg för att se till att era marknadsföringskampanjer är effektiva och når ut till era kunder.

Läs mer om den information du kan övervaka när du har skickat en leverans, förstå hur leveransfel och karantäner hanteras i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=en#sending-messages){target=&quot;_blank&quot;}

### Övervaka dina arbetsflöden

Lär dig övervaka arbetsflödeskörning i  [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/monitoring-workflows/monitoring-workflow-execution.html?lang=en#automating-with-workflows){target=&quot;_blank&quot;}

### Övervaka instansen

Riktlinjer för instansövervakning finns i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/monitoring-campaign-classic/introduction/monitoring-guidelines.html?lang=en#monitoring-campaign-classic){target=&quot;_blank&quot;}

Använd självbetjäningsgränssnittet för granskningsspår för att övervaka ändringar som görs i instansen. Granskningsspår innehåller en omfattande lista i realtid över åtgärder och händelser som inträffar i din Adobe Campaign-instans. Du kan få tillgång till en historik med data för att besvara frågor som: vad som hände med dina arbetsflöden och vem som senast uppdaterade dem eller vad gjorde användarna i instansen.

Läs mer om granskningsspår i  [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/monitoring-campaign-classic/production-procedures/audit-trail.html?lang=en#accessing-audit-trail){target=&quot;_blank&quot;}
