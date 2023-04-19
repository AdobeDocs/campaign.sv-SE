---
title: Skicka och övervaka transaktionsmeddelanden
description: Lär dig hur du skickar och övervakar transaktionsmeddelanden
feature: Transactional Messaging
role: User
level: Beginner, Intermediate
exl-id: 084607f6-47d8-40c0-89ba-bfbb88fc2e53
source-git-commit: c044b391c900e8ff82147f2682e2e4f91845780c
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 2%

---

# Skicka och övervaka transaktionsmeddelanden {#delivery-execution}

## Skicka meddelanden{#send-transactional-msg}

När anrikningen är klar och en leveransmall har länkats till händelsen skickas leveransen från körningsinstansen.

>[!NOTE]
>
>Transaktionsmeddelandena prioriteras framför annan leverans.

Alla leveranser grupperas i **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** mapp.

Som standard sorteras de i undermappar efter leveransmånad. Detta kan ändras i meddelandemallens egenskaper.

## Övervaka meddelanden {#monitor-transactional-msg}

Om du vill övervaka dina transaktionsmeddelanden ska du kontrollera [leveransloggar](send.md).

Transaktionsleveranser som skickas från körningsinstansen synkroniseras tillbaka till kontrollinstansen via ett tekniskt arbetsflöde (**[!UICONTROL Message Center execution instance]**) som går varje timme.

>[!NOTE]
>
>Leveranserna varje vecka samlar ihop händelserna baserat på den senaste händelseuppdateringen och inte på datumet då händelsen skapades. När du extraherar leveransloggar för transaktionsmeddelanden från kontrollinstansen kan det leverans-ID som är kopplat till varje leveranslogg-ID därför ändras över tiden när loggen uppdateras (till exempel när en inkommande avhoppning tas emot för händelsen).

<!--
To monitor the activity and running of the execution instance(s), see [Transactional messaging reports](transactional-messaging-reports.md).-->

## Rapportering{#reporting-transactional-msg}

Adobe Campaign erbjuder flera rapporter som gör att du kan styra aktiviteten och köra körningsinstanserna smidigt.

Du kommer åt dessa rapporter från meddelandecentret via **[!UICONTROL Reports]** -fliken i **kontrollinstans**.

![](assets/mc-reports.png)

### Händelshistorik för meddelandecenter {#history-events}

The **[!UICONTROL Message Center event history]** rapporten innehåller en översikt över aktiviteten i Message Center-modulen, dvs. antalet händelser som bearbetas och levereras som transaktionsmeddelanden.

När rapporten öppnas sammanfaller den information som visas som standard med hastigheten för skickade transaktionsmeddelanden. Om du vill visa fler nivåer kan du öppna de olika noderna och placera markören på lämplig nivå för att markera den.

Du kan visa data som är specifika för varje händelsetyp, per tidsperiod. The **[!UICONTROL Events]** -kolumnen motsvarar antalet händelser som tas emot per kontrollinstans. Antalet händelser som omvandlats till personaliserade transaktionsmeddelanden beskrivs i **[!UICONTROL Sent]** kolumn.


### Bearbetningstid för meddelandecentret {#processing-time}

The **[!UICONTROL Message Center processing time]** rapporten visar de viktigaste indikatorerna för realtidskön. Den här rapporten kan också nås via **[!UICONTROL Monitoring]** -fliken i kontrollinstansen.

![](assets/mc-processing-time-report.png)

Du kan välja att visa global statistik eller den som är relativ till en viss körningsinstans. Du kan också filtrera data efter kanal och under en viss period.

Indikatorerna som visas i **[!UICONTROL Indicators over the period]** -avsnittet beräknas över den valda perioden:

* **[!UICONTROL Average queuing time]**: Genomsnittlig tid som har bearbetat händelser som har ägnats åt i meddelandecentret. Endast bearbetningstiden beaktas.
* **[!UICONTROL Average message sending time (s)]**: Genomsnittlig tid som har bearbetat händelser som har ägnats åt i meddelandecentret. Endast den maximala leveranstiden beaktas.
* **[!UICONTROL Average processing time (s)]**: Genomsnittlig tid som har bearbetat händelser som har ägnats åt i meddelandecentret. Beräkningen tar hänsyn till bearbetningstiden och den maximala sändningstiden.
* **[!UICONTROL Maximum number of queued events]**: maximalt antal händelser i Message Center-kön vid en given tidpunkt.
* **[!UICONTROL Minimum number of queued events]**: minsta antal händelser som finns i Message Center-kön vid en given tidpunkt.
* **[!UICONTROL Average number of queued events]**: Genomsnittligt antal händelser i Message Center-kön vid en given tidpunkt.

>[!NOTE]
>
>Tröskelvärdena för varningsmeddelanden (orange) och varningsmeddelanden (röda) kan konfigureras i Adobe Campaign distributionsguide. Se [Skärmtrösklar](#thresholds).



### Tjänstenivå för meddelandecentret {#service-level}

The **[!UICONTROL Message Center service level]** rapporten visar leveransstatistik för transaktionsmeddelanden samt en beskrivning av felen. Du kan klicka på en feltyp för att visa information om den.

Den här rapporten kan också nås via **[!UICONTROL Monitoring]** -fliken i kontrollinstansen.

Du kan välja att visa global statistik eller den som är relativ till en viss körningsinstans. Du kan också filtrera data efter kanal och under en viss period.

Indikatorerna som visas i **[!UICONTROL Indicators over the period]** -avsnittet beräknas över den valda perioden:

* **[!UICONTROL Incoming (throughput event/h)]**: genomsnittligt antal händelser per timme som anges i Message Center-kön.
* **[!UICONTROL Incoming (event vol)]**: antal händelser som anges i Message Center-kön.
* **[!UICONTROL Outgoing (throughput msg/h)]**: Genomsnittligt antal utgående Message Center-händelser per timme (skickas av en leverans).
* **[!UICONTROL Outgoing (msg vol)]**: Antal slutförda utgående Message Center-händelser (skickade av en leverans).
* **[!UICONTROL Average sending time (seconds)]**: Genomsnittlig tid i meddelandecentret för lyckade bearbetade händelser. Beräkningen tar hänsyn till bearbetningstiden och den maximala sändningstiden.
* **[!UICONTROL Error rate]**: antal händelser med fel jämfört med antalet händelser som har angetts i Message Center-kön. Följande fel beaktas: routningsfel, utgången händelse (händelse som har varit i kön för lång), leveransfel, ignoreras av leveransen (karantän, osv.).

>[!NOTE]
>
>Tröskelvärdena för varningsmeddelanden (orange) och varningsmeddelanden (röda) kan konfigureras i Adobe Campaign distributionsguide. Se [Skärmtrösklar](#thresholds).

### Övervaka gränsvärden {#thresholds}

Du kan konfigurera varningströskeln (orange) och varningströskeln (röd) för indikatorerna som visas i **Tjänstnivå för meddelandecenter** och **Bearbetningstid för meddelandecenter** rapporter.

Följ stegen nedan för att göra detta:

1. Öppna distributionsguiden på **körningsinstans** och bläddra till **[!UICONTROL Message Center]** sida.
1. Använd pilarna för att ändra tröskelvärdena.

   ![](assets/mc-thresholds.png)
