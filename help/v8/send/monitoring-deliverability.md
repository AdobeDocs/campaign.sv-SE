---
product: campaign
title: Skärmleverans i Adobe Campaign
description: Läs om verktyg och riktlinjer för övervakning av slutprodukter i Adobe Campaign
feature: Deliverability
role: User, Admin
version: Campaign v8, Campaign Classic v7
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 11c8c4c51c7901ba0d119323c564a64b940428b7
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 2%

---

# Övervaka leveransen{#monitoring-deliverability}

Nedan hittar du information om de olika övervakningsverktygen i Adobe Campaign samt ytterligare riktlinjer för hur du utnyttjar de funktioner som Adobe Campaign erbjuder för att övervaka din plattforms leveransbarhet.

## Övervakningsverktyg {#monitoring-tools}

Adobe Campaign ger tillgång till alla verktyg som listas nedan.

* Återgivningsrapporten [Inkorgen](inbox-rendering.md) gör det möjligt att förhandsgranska meddelanden på större e-postklienter för att kunna skanna innehåll och anseende.

* Rapporten **[!UICONTROL Delivery throughput]** ger dig en översikt över hela plattformens dataflöde under en viss period. Mer information finns i [det här avsnittet](../reporting/global-reports.md#delivery-throughput).
* Varje leverans genererar en utsändningsstatistikrapport för olika internetleverantörer. Den visar vissa data- och anseendemått som kan påverka leveransförmågan, inklusive följande tal:
   * **[!UICONTROL Hard bounces]** anger datakvalitet. Talet ska vara mindre än 2%.
   * **[!UICONTROL Soft bounces]** anger rykte. Talet får inte vara högre än 10 % för någon ISP.

  <!--For more on this, see the [Delivery statistics](../reporting/global-reports.md#delivery-statistics) section.-->

* Mer generellt ger [kontrollpanelen för leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html?lang=sv-SE#sending-messages){target="_blank"} dig tillgång till:
   * Leveranssammanfattning, som visar detaljerna i sändningen och antalet meddelanden som ska skickas, bearbetas och skickas utan fel.
   * Leveransloggar och leveranshistorik som visar vilket mål som har uteslutits och varför.
   * spårningsloggarna, som visar spårningsinformation som öppningar och klickningar.

## Riktlinjer för övervakning {#monitoring-guidelines}

Här följer ytterligare riktlinjer för leveransövervakning:

* Kontrollera regelbundet [leveransdataflödet](../reporting/global-reports.md#delivery-throughput) för hela plattformen för att kontrollera om den stämmer överens med den ursprungliga konfigurationen.
* Kontrollera att [återförsök](delivery-failures.md#retries) har konfigurerats korrekt (30 minuter för återförsöksperiod och mer än 20 återförsök) i leveransmallar.
* Kontrollera regelbundet att postlådan [bounce](delivery-failures.md#bounce-mail-qualification) är tillgänglig och att kontot inte håller på att förfalla.
* Kontrollera varje leveransflöde, som du kommer åt från [leveransinstrumentpanelen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html?lang=sv-SE#sending-messages){target="_blank"}, för att se till att det stämmer överens med leveransinnehållets giltighet (t.ex. ska &#39;flash sales&#39; levereras på några minuter, inte dagar). är ett viktigt verktyg för att övervaka leveranser och potentiella problem när meddelanden skickas.
* När du använder [vågor](configure-and-send.md#sending-using-multiple-waves) bör du kontrollera att varje våg har tillräckligt med tid för att slutföra innan nästa utlöses.
* Kontrollera att antalet fel och nya [karantäner](quarantines.md) stämmer överens med andra leveranser.
* Läs noggrant igenom [leveransloggarna](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html?lang=sv-SE#delivery-logs-and-history){target="_blank"} för att kontrollera vilken typ av fel som markeras (blockeringslista, DNS-problem, skräppostregler osv.).
