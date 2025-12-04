---
product: campaign
title: Skärmleverans i Adobe Campaign
description: Läs om verktyg och riktlinjer för övervakning av slutprodukter i Adobe Campaign
feature: Deliverability
role: User, Admin
version: Campaign v8, Campaign Classic v7
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 3dd4f6041ef193a0d7ea74a0b2c06183861c2797
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 3%

---

# Övervaka leveransen{#monitoring-deliverability}

Nedan hittar du information om de olika övervakningsverktygen i Adobe Campaign samt ytterligare riktlinjer för hur du utnyttjar de funktioner som Adobe Campaign erbjuder för att övervaka din plattforms leveransbarhet.

## Övervakningsverktyg {#monitoring-tools}

Adobe Campaign ger dig tillgång till de leveransverktyg som listas nedan.

### Inkorgsåtergivning {#inbox-rendering-tool}

Återgivningsrapporten [Inkorgen](inbox-rendering.md) gör det möjligt att förhandsgranska meddelanden på större e-postklienter för att kunna skanna innehåll och anseende.

### Leveranskapacitet {#throughput-reports}

Rapporten **[!UICONTROL Delivery throughput]** ger dig en översikt över hela plattformens dataflöde under en viss period. Mer information finns i [det här avsnittet](../reporting/global-reports.md#delivery-throughput).

### Sändningsstatistik {#broadcast-statistics}

Varje leverans genererar en utsändningsstatistikrapport för olika internetleverantörer. Den visar vissa data- och anseendemått som kan påverka leveransförmågan, inklusive följande tal:

**[!UICONTROL Hard bounces]** anger datakvalitet. Talet ska vara mindre än 2%.

**[!UICONTROL Soft bounces]** anger rykte. Talet får inte vara högre än 10 % för någon ISP.

<!--For more on this, see the [Delivery statistics](../reporting/global-reports.md#delivery-statistics) section.-->

### Kontrollpanel för leverans {#delivery-dashboard-monitoring}

Mer generellt ger [kontrollpanelen för leverans](delivery-dashboard.md) dig tillgång till:

Leveranssammanfattningen, som visar detaljerna för sändningen och antalet meddelanden som ska skickas, bearbetas och skickas utan fel.

Leveransloggarna och historiken som visar vilket mål som har uteslutits och varför.

Spårningsloggarna, som visar spårningsinformation som öppningar och klickningar.

### SpamAssassin testing {#spam-testing}

Använd [SpamAssassin](spamassassin.md) för att testa ditt e-postinnehåll och poängsätta det för att avgöra om ett meddelande löper risk att betraktas som skräppost av de skräppostverktyg som används vid mottagande.

### Kontrollpanelen {#control-panel-monitoring}

>[!NOTE]
>
>Kontrollpanelen är tillgänglig för användare av hanterade molntjänster i Campaign v8. Läs mer om [Kontrollpanelen](../config/self-service.md).

Kontrollpanelen [Kampanj](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv){target="_blank"} innehåller övervakningsfunktioner för levererbarhet, inklusive hantering av underdomäner och certifikat, övervakning av aktiva profiler samt leveransgenomströmning och fördröjningsmått.

## Riktlinjer för övervakning {#monitoring-guidelines}

Här följer ytterligare riktlinjer för leveransövervakning:

### Plattformsgenomströmningsövervakning

Kontrollera regelbundet [leveransdataflödet](../reporting/global-reports.md#delivery-throughput) för hela plattformen för att kontrollera om den stämmer överens med den ursprungliga konfigurationen.

### Försök konfigurera igen

Kontrollera att [återförsök](delivery-failures.md#retries) har konfigurerats korrekt (30 minuter för återförsöksperiod och mer än 20 återförsök) i leveransmallar.

### Verifiering av studsande postlåda

Kontrollera regelbundet att postlådan [bounce](delivery-failures.md#bounce-mail-qualification) är tillgänglig och att kontot inte håller på att förfalla.

### Prestandakontroller för leverans

Kontrollera varje leveransflöde, som du kommer åt från [leveransinstrumentpanelen](delivery-dashboard.md), för att se till att det stämmer överens med leveransinnehållets giltighet (t.ex. ska &#39;flash sales&#39; levereras på några minuter, inte dagar).

### Validering av vågtiming

När du använder [vågor](configure-and-send.md#sending-using-multiple-waves) bör du kontrollera att varje våg har tillräckligt med tid för att slutföra innan nästa utlöses.

### Karantänövervakning

Kontrollera att antalet fel och nya [karantäner](quarantines.md) stämmer överens med andra leveranser.

### Analys av leveranslogg

Läs noggrant igenom [leveransloggarna](delivery-dashboard.md#delivery-logs-and-history) för att kontrollera vilken typ av fel som markeras (blockeringslista, DNS-problem, skräppostregler osv.).

## Relaterade ämnen

[Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"} innehåller omfattande vägledning om leveransstrategi, definition, mätvärden och bästa praxis.

[Vad som är leveransbarhet](about-deliverability.md) introducerar viktiga leveransbegrepp och hur ni kan förbättra leveransgraden i Campaign.

[Leveransfel och studsar](delivery-failures.md) beskriver olika typer av leveransfel, hur Campaign hanterar dem och innehåller felsökningsanvisningar för vanliga problem.

[Karantänhantering](quarantines.md) förklarar hur Campaign hanterar adresser i karantän för att skydda ditt sändningsrykte.

[Kontrollmeddelandeinnehåll](control-message-content.md) ger vägledning om hur du ser till att innehållet är optimerat för leverans.
