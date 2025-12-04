---
title: Inbyggda leveransrapporter från Adobe Campaign
description: Inbyggda leveransrapporter från Adobe Campaign
feature: Reporting
exl-id: e9031d65-6e0e-49da-9990-7687d2a77591
source-git-commit: 3453820bb0eca7847ec55d7e6ea15766a57ab94e
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 1%

---

# Leveransrapporter {#delivery-reports}

Du kan spåra leveransen via olika rapporter som du når via leveransöversikten.

Följ stegen nedan för att få åtkomst till rapporter:

1. Bläddra till fliken **[!UICONTROL Campaigns]** och klicka på länken **[!UICONTROL Delivery]** för att visa listan över leveranser.
1. Klicka på namnet på den leverans som du vill få åtkomst till.
1. Välj fliken **[!UICONTROL Summary]** och klicka på länken **[!UICONTROL Reports]** för att komma åt rapporter som är specifika för leveransen.

   ![](assets/detailed-report-2.png)

   Som standard är följande rapporter tillgängliga:

   * **[!UICONTROL Delivery throughput]**
   * **[!UICONTROL Sharing to social networks]**
   * **[!UICONTROL Statistics on sharing activities]**
   * **[!UICONTROL Hot clicks]**
   * **[!UICONTROL Tracking statistics]**
   * **[!UICONTROL URLs and click streams]**
   * **[!UICONTROL Tracking indicators]**
   * **[!UICONTROL Non-deliverables and bounces]**
   * **[!UICONTROL User activities]**
   * **[!UICONTROL Delivery summary]**
   * **[!UICONTROL Subscription tracking]**
   * **[!UICONTROL Delivery statistics]**
   * **[!UICONTROL Breakdown of opens]**

## Spårningsindikatorer {#tracking-indicators}

I den här rapporten kombineras de viktigaste indikatorerna för att spåra mottagarnas beteende när de tar emot leveransen. Den ger tillgång till leverans- och mottagningsstatistik, öppnings- och klickfrekvens, genererade klickströmmar samt delar aktiviteter till sociala nätverk.

>[!NOTE]
>
>Värden som beräknas baserat på meddelandeöppning är alltid uppskattningar på grund av den felmarginal som är länkad till e-postmeddelanden i textformat. Indikatorerna **[!UICONTROL Distinct opens/Sum of opens for the population reached]** tar hänsyn till den här felmarginalen. [Läs mer](metrics-calculation.md#tracking-opens-).

![](assets/tracking-report-synthesis.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]**: Totalt antal meddelanden som ska levereras efter leveransanalys.
* **[!UICONTROL Success]**: Antal meddelanden som har bearbetats.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>De relaterade procentsatserna beräknas baserat på antalet meddelanden som har vidarebefordrats.

* **[!UICONTROL Distinct opens for the population reached]**: Uppskattning av antalet målmottagare som har öppnat ett meddelande minst en gång. Klickningar på spårade URL:er beaktas eftersom e-postmeddelanden måste öppnas för att du ska kunna klicka på en länk.
* **[!UICONTROL Sum of opens for the population reached]**: Uppskattning av det totala antalet öppningar av målmottagare.
* **[!UICONTROL Clicks on opt-out link]**: Antal klick på länken för att avbryta prenumerationen.
* **[!UICONTROL Clicks on the mirror page link]**: Antal klick på länken till [spegelsidan](../send/mirror-page.md). För att länken ska kunna beaktas måste den definieras som sådan i leveransguiden (spårade URL:er).
* **[!UICONTROL Estimation of forwards]**: Uppskattning av antalet e-postmeddelanden som vidarebefordrats av målmottagarna. Det här värdet beräknas genom att subtrahera antalet distinkta personer och antalet distinkta mottagare som klickade i e-postmeddelandet.

  >[!NOTE]
  >
  >Mer information om skillnaden mellan distinkta personer och målmottagare finns i [Målpersoner/mottagare](metrics-calculation.md#targeted-persons---recipients).

**[!UICONTROL 3. Open and click-through rate]**

Den här värdetabellen visar hur leveranser, öppningar, klickningar och råreaktivitet per Internetdomän är fördelade. Följande indikatorer används:

* **[!UICONTROL Sent]**: Totalt antal meddelanden som skickats på den här domänen.
* **[!UICONTROL Complaints]**: Antal meddelanden för den här domänen som har rapporterats som oönskade av mottagaren. Frekvensen beräknas baserat på det totala antalet meddelanden som skickas på den här domänen.
* **[!UICONTROL Opens]**: Antal distinkta målmottagare för den här domänen som har öppnat ett meddelande minst en gång. Frekvensen beräknas baserat på det totala antalet meddelanden som skickas på den här domänen.
* **[!UICONTROL Clicks]**: Antal distinkta målmottagare som klickade i samma leverans minst en gång. Frekvensen beräknas baserat på det totala antalet meddelanden som skickas på den här domänen
* **[!UICONTROL Raw reactivity]**: Procentandel av antalet mottagare som klickade i en leverans minst en gång jämfört med antalet mottagare som öppnade en leverans minst en gång.

>[!NOTE]
>
>Domännamnen som visas i den här rapporten definieras i den specificerade lista som används på kubnivå. Om du vill ändra, lägga till eller ta bort standarddomäner redigerar du den specificerade listan **[!UICONTROL Domains]** och ändrar värden och alias. Kategorin **[!UICONTROL Others]** innehåller domännamn som inte tillhör något värde i den specificerade listan.
>
>Lär dig hur du får åtkomst till och konfigurerar dina uppräkningar på [den här sidan](../config/enumerations.md).


**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>De relaterade procentsatserna beräknas baserat på antalet meddelanden som har vidarebefordrats.

* **[!UICONTROL Distinct clicks for the population reached]**: Antal distinkta personer som klickat på en leverans minst en gång.
* **[!UICONTROL Cumulated clicks]**: Totalt antal klickningar av målmottagare, exklusive prenumerationslänkar och spegelsidor.
* **[!UICONTROL Recipient clicks]**: Antal distinkta målmottagare som klickade i samma leverans minst en gång.
* **[!UICONTROL Estimated recipient reactivity]**: Förhållande mellan antalet mottagare som har klickat minst en gång i en leverans och det uppskattade antalet mottagare som har öppnat en leverans minst en gång. Klickningar på avanmälnings- och spegelsideslänkarna beaktas inte.
<!--
**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]**: Number of web pages visited following message reception.
* **[!UICONTROL Transactions]**: Number of purchases following message reception.
* **[!UICONTROL Total amount]**: Total amount of purchases following message reception. 
* **[!UICONTROL Average transaction amount]**: Average purchase made by distinct delivery recipients. 
* **[!UICONTROL Articles]**: Number of articles purchased by the delivery recipients. 
* **[!UICONTROL Average count of articles per transaction]**: Average number of items per purchase made by distinct recipients.
* **[!UICONTROL Average amount per message]**: Average amount of purchases generated per message.

  >[!NOTE]
  >
  >In order for a visited page, transaction, amount or article to be taken into account, a webtracking tag must be inserted into the matching web page. Webtracking configuration is presented in [this section](../../configuration/using/about-web-tracking.md).

**[!UICONTROL 6. Sharing activities to email and social networks]**

This section shows the number of messages shared on each social network. For more on this, refer to [Sharing to social networks](../../reporting/using/global-reports.md#sharing-to-social-networks).

## URLs and click streams {#urls-and-click-streams}

This report shows the list of pages visited following a delivery. 

![](assets/s_ncs_user_url_report.png)

You can configure the contents of this report by selecting: the score chart to be displayed, the time filter (since the action launch, over the first 6 hours following launch, etc.) and the data display mode (by label, by URL, by category. Click **[!UICONTROL Refresh]** to confirm your selection.

The following rates are displayed in the upper section of the report:

* **[!UICONTROL Reactivity]**: Ratio of the number of targeted recipients having clicked in a delivery, in relation to the estimated number of targeted recipients having opened a delivery. Clicks on the opt-out link and on the mirror page are not taken into account.

  >[!NOTE]
  >
  >For more information on tracking opens, refer to [this section](metrics-calculation.md#tracking-opens-).

* **[!UICONTROL Distinct clicks]**: Number of distinct people having clicked at least once (excluding unsubscription link and mirror page) in a delivery. The rate displayed is calculated based on the number of messages delivered successfully. 
* **[!UICONTROL Cumulated clicks]**: Total number of clicks by targeted recipients (excluding unsubscription link and mirror page). The rate displayed is calculated based on the number of messages forwarded successfully.

**[!UICONTROL Platform average]**: This average rate, displayed under each rate (reactivity, distinct clicks, and cumulated clicks), is calculated for deliveries sent over the previous six months. Only deliveries with the same typology and on the same channel are taken into account. Proofs are excluded.

The central table provides the following information:

* **[!UICONTROL Clicks]**: Number of cumulated clicks, per link. 
* **[!UICONTROL Clicks (in %)]**: Breakdown of the number of clicks per link, in relation to the total number of cumulated clicks.

**[!UICONTROL Breakdown of clicks in time]**

This chart shows the breakdown of cumulated clicks per day.
-->

## Leveranssammanfattning {#delivery-summary}

Den här rapporten innehåller all huvudinformation om leveransen.

![](assets/user-report-summary.png)

**[!UICONTROL Target population]**

Det här avsnittet har två indikatorer:

* **[!UICONTROL Initial population]**: Totalt antal mottagare som har angetts som mål för leveransen.
* **[!UICONTROL Messages rejected by the rule]**: Antal adresser som ignoreras under analysen när typologiregler tillämpas: adress som saknas, är i karantän, på blockeringslista osv. <!--For more information on typology rules, refer to this [page](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).-->

**[!UICONTROL Causes of exclusion]**

I mittdiagrammet visas uppdelningen per regel för meddelanden som avvisats under analysen.

**[!UICONTROL Delivery statistics]**

Detta avsnitt innehåller följande indikatorer:

* **[!UICONTROL Messages to be delivered]**: Totalt antal meddelanden som ska levereras efter leveransanalys.
* **[!UICONTROL Success]**: Antal meddelanden som har bearbetats. Den associerade frekvensen är förhållandet till antalet meddelanden som ska levereras.
* **[!UICONTROL Errors]**: Totalt antal fel som ackumulerats under leveranser och automatisk återinläsning. Den associerade frekvensen är förhållandet till antalet meddelanden som ska levereras.
* **[!UICONTROL New quarantines]**: Antal adresser i karantän efter en misslyckad leverans (okänd användare, ogiltig domän). Den associerade frekvensen är förhållandet till antalet meddelanden som ska levereras.

## Snabbklick {#hot-clicks}

Den här rapporten visar meddelandeinnehållet (HTML och/eller text) med procentandelen klickningar på länkar för varje länk. Personalisering blockerar prenumerationslänkar, länkar till spegelsidor och erbjudandelänkar som tas med i beräkningen i det totala antalet klickningar, men visas inte i rapporten.

>[!NOTE]
>
>Om leveransen innehåller erbjudanden (interaktion) visas en ruta i delen ovanför rapporten med procentandelen klick på erbjudandena.


## Spårningsstatistik {#tracking-statistics}

Rapporten innehåller statistik om öppningar, klick och transaktioner.

Med den kan ni spåra effekten av leveransen på marknaden. Du kan konfigurera hur värden visas genom att ändra tidsskalan (1 timme, 3 timmar eller 24 timmar). Klicka på **[!UICONTROL Refresh]** för att bekräfta ditt val.

Den här rapporten innehåller en värdetabell och ett Pareto-diagram som visar hur lång tid det tar att leverera för att uppnå maximal effektivitet. Följande indikatorer används:

* **[!UICONTROL Opens]**: Uppskattning av den tid som krävs för att nå en procentandel av det totala antalet meddelanden som öppnas. E-post i textformat tas inte med i beräkningen. [Läs mer](metrics-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]**: Uppskattning av den tid som krävs för att nå en procentandel av det totala antalet inspelade klick. Klicka på länken för avanmälan och spegelsidan beaktas inte.
<!--
* **[!UICONTROL Transactions]**: Time required to achieve a percentage of the total number of transactions following message reception. In order for a transaction to be taken into account, a transaction type webtracking tag must be inserted into the matching web page. Webtracking configuration is presented in [this section](../../configuration/using/about-web-tracking.md).
-->


## Kumulativa rapporter {#cumulated-reports}

Du kan visa kumulerade rapporter om leveranser. För att göra detta väljer du de leveranser som ska jämföras för att få en lista över rapporter för dessa leveranser.

Om du vill välja icke-närliggande leveranser från listan håller du ned CTRL medan du gör ditt val.

Om du vill välja leveranser som sparats i en annan mapp klickar du på ikonen **[!UICONTROL Display sub-levels]** som du kommer åt i verktygsfältet. De visas sedan i samma lista.
