---
title: Kom igång med funktioner för spårning och övervakning
description: Kom igång med funktioner för spårning och övervakning
feature: Monitoring
role: User
level: Beginner, Intermediate
exl-id: f3de901f-519f-42ae-846c-f20c7cb560df
source-git-commit: a78019d11a0a2acbd8c0d9ba7c2082c09f90356c
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 4%

---

# Spåra och övervaka meddelanden{#gs-ac-reports}

## Spårningsfunktioner i Campaign

Kampanjspårningsfunktioner spårar skickade meddelanden och hjälper dig att analysera mottagarnas beteende: öppna, klicka på länkar, prenumerationer/avprenumerationer och mycket annat. Ni kan få tillgång till dedikerade loggar, rapporter och mätvärden, fråga databasen för att granska insamlade data och mycket annat.

Mer information finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/profile-management/editing-a-profile.html#tracking-tab){target="_blank"}.

Kontrollpanelen för leverans är ett viktigt verktyg för att övervaka leveranser och potentiella problem när meddelanden skickas.

Mer information finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#sending-messages){target="_blank"}.

De nyckelspårningsfunktioner som är tillgängliga i Campaign listas nedan.

### Meddelandespårning {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Spårade länkar**

Du kan spåra mottagning av meddelanden och aktivering av länkar som infogats i meddelandeinnehållet för att bättre förstå mottagarnas beteende.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/how-to-configure-tracked-links.html#sending-messages){target="_blank"}

**URL-spårning**

Spårningsalternativen kan konfigureras genom att aktivera eller inaktivera spårade URL:er.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/personalizing-url-tracking.html#sending-messages){target="_blank"}


**Spårad länkpersonalisering**

Kampanjspårningsfunktionerna gör att ni kan lägga till länkar i e-postmeddelanden som kan personaliseras och som stöder spårning.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/tracking-personalized-links/tracking-personalized-links.html#sending-messages){target="_blank"}

**Spårningsloggar**

Det tekniska arbetsflödet **Spårning** hämtar spårningsdata när leveransen har skickats och spårningen har aktiverats. Dessa data finns på fliken Spårning för leveransen.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/accessing-the-tracking-logs.html#sending-messages){target="_blank"}

**Testa spårning**

Innan du skickar meddelanden med din spårning kan du testa spårningen på din spegelsida, e-postloggar och länkar.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/testing-tracking.html#sending-messages){target="_blank"}

### Spårning av webbprogram {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Spåra en webbapplikation**

Du kan också spåra och mäta besök på webbprogramsidor med hjälp av spårningstaggar. Den här funktionen kan användas för alla typer av webbprogram, t.ex. formulär och onlineundersökningar.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/tracking-a-web-application.html#designing-content){target="_blank"}

**Välj att inte delta i spårning av webbapplikation**

Med avanmälan om spårning av webbprogram kan du sluta spåra webbbeteenden för slutanvändare som avanmäler sig från beteendespårning. Du kan inkludera möjligheten att visa en banderoll i webbprogram eller landningssidor så att användarna kan välja bort den.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/web-application-tracking-opt-out.html#designing-content){target="_blank"}

### Spåra rapporter {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Spårningsstatistik**

Den här rapporten innehåller statistik om öppningar, klick och transaktioner och gör att du kan spåra marknadsföringseffekten av leveransen.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/about-message-tracking.html#tracking-reports){target="_blank"}

**URL:er och klickbara strömmar**

Den här rapporten innehåller en lista över besökta sidor efter en leverans.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html#urls-and-click-streams){target="_blank"}

**Person/personer och mottagare**

I det här exemplet är det lättare att förstå skillnaden mellan en person/en person och en mottagare i Adobe Campaign.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/person-people-recipients.html#reporting){target="_blank"}

**Spårningsindikatorer**

I den här rapporten kombineras nyckelindikatorer för att spåra mottagarnas beteende när de får leveransen, till exempel öppnings- och klickfrekvens och klickströmmar.

[Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html#reporting){target="_blank"}

**Indikatorberäkning**

De olika tabellerna ger dig en lista över indikatorer som används i de olika rapporterna och deras beräkningsformel beroende på leveranstyp.

[Läs mer](../reporting/metrics-calculation.md)

## Riktlinjer för övervakning

Adobe Campaign har en uppsättning funktioner för att övervaka processerna och miljön.

### Övervaka leveranser

Att övervaka era leveranser efter att de har skickats är ett viktigt steg för att se till att era marknadsföringskampanjer är effektiva och når ut till era kunder.

Läs mer om den information du kan övervaka när du har skickat en leverans, förstå hur leveransfel och karantäner hanteras i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html#sending-messages){target="_blank"}

### Övervaka dina arbetsflöden

Lär dig övervaka arbetsflödeskörning i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html)

### Övervaka instansen

Riktlinjer för instansövervakning finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/monitoring-campaign-classic/introduction/monitoring-guidelines.html#monitoring-campaign-classic){target="_blank"}

Använd självbetjäningsgränssnittet för granskningsspår för att övervaka ändringar som görs i instansen. Granskningsspår innehåller en omfattande lista i realtid över åtgärder och händelser som inträffar i din Adobe Campaign-instans. Du kan komma åt en datahistorik för att få hjälp med att besvara frågor som t.ex. vad som hände med dina arbetsflöden och vem som senast uppdaterade dem eller vad användarna gjorde i instansen.

Läs mer om granskningsspår på den här [sidan](../reporting/audit-trail.md){target="_blank"}
