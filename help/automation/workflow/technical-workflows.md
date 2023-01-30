---
product: campaign
title: Tekniska arbetsflöden
description: Läs mer om de tekniska arbetsflödena i Campaign
feature: Workflows
exl-id: 2693856c-80b2-4e35-be8e-2a9760f8311f
source-git-commit: 6464e1121b907f44db9c0c3add28b54486ecf834
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 2%

---

# Tekniska arbetsflöden{#about-technical-workflows}

Adobe Campaign innehåller en uppsättning inbyggda tekniska arbetsflöden. De hanterar åtgärder och jobb som schemalagts för periodisk körning på servern. De gör att du kan utföra underhåll i databasen, vidarebefordra spårningsinformation om leveranser eller konfigurera provisoriska processer för leveranser. Tekniska arbetsflöden konfigureras via **[!UICONTROL Administration > Production > Technical workflows]** nod.

![](assets/navtree.png)

Inbyggda mallar finns för att skapa tekniska arbetsflöden. De kan konfigureras så att de passar dina behov.

The **[!UICONTROL Campaign process]** undermappen centraliserar de arbetsflöden som krävs för att köra processer i kampanjer: aktivitetsavisering, lagerhantering, kostnadsberäkning osv.

![](assets/campaign-processes-wf.png)


>[!NOTE]
>
>En lista över tekniska arbetsflöden som installeras med varje modul finns i en [dedikerad sektion](technical-workflows.md).

Du kan skapa andra tekniska arbetsflöden i **[!UICONTROL Administration > Production > Technical workflows]** trädstrukturens nod. Den här processen är dock reserverad för expertanvändare.

De aktiviteter som erbjuds är desamma som för arbetsflöden med målinriktning. [Läs mer](targeting-workflows.md)

De arbetsflöden som beskrivs i det här avsnittet installeras med olika inbyggda Adobe Campaign-paket. Dessa paket och tillhörande tekniska arbetsflöden beror på licensavtalet.

Som standard är tekniska arbetsflöden tillgängliga i en undermapp till följande nod: **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

Observera att tekniska arbetsflöden bara kan startas och ändras av operatorer med administrationsbehörighet.

>[!NOTE]
>
>Tekniska arbetsflöden som är relaterade till tillägget Message Center är som standard tillgängliga i **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]** nod.

Lär dig övervaka tekniska arbetsflöden i det här [dedikerad sektion](monitor-technical-workflows.md).


## Förteckning över tekniska arbetsflöden {#list-technical-workflows}

| Tekniskt arbetsflöde | Paket | Beskrivning |
|------|--------|-----------|
| **Rensa alias** (aliasCleansing) | Installerad som standard | Det här arbetsflödet standardiserar uppräkningsvärden. Den aktiveras varje dag klockan tre som standard. |
| **Fakturering** (fakturering) | Installerad som standard | Det här arbetsflödet skickar systemaktivitetsrapporten till faktureringsoperatorn via e-post. Den utlöses den 25:e varje månad på marknadsinstansen. |
| **Kampanjjobb** (operationMgt) | Installerad som standard | Det här arbetsflödet hanterar jobben för marknadsföringskampanjer (lanserar målinriktning, filextrahering osv.). Det skapar också arbetsflöden för återkommande och periodiska kampanjer. |
| **Samla in data för tjänsten HeatMap** (collectDataHeatMapService) | Installerad som standard | Det här arbetsflödet hämtar data som krävs av HeatMap-tjänsten. |
| **Samla in sekretessförfrågningar** (collectPrivacyRequests) | Sekretessdataskyddsförordningen | Det här arbetsflödet genererar mottagarens data som lagras i Adobe Campaign och gör dem tillgängliga för hämtning på skärmen för sekretesspolicy. |
| **Kostnadsberäkning** (budgetMgt) | Installerad som standard | Det här arbetsflödet startar beräkningen av utgifts- och kostnadsrader för budgetar, planer, program, kampanjer, leveranser och uppgifter. |
| **Databasrensning** (rensa) | Installerad som standard | Det här arbetsflödet är arbetsflödet för databasunderhåll: utför olika beräkningar från statistiken och processerna och tar bort föråldrade data från databasen enligt den definierade konfigurationen i distributionsassistenten. Den aktiveras varje dag klockan fyra som standard. |
| **Ta bort blockerade LINE-användare** (deleteBlockedLineUsersV2) | LINE-kanal | Det här arbetsflödet säkerställer att LINE V2-användarnas data tas bort efter att de har blockerat LINE-kontot i 180 dagar. |
| **Ta bort data för sekretessförfrågningar** (deletePrivacyRequestsData) | Sekretessdataskyddsförordningen | Det här arbetsflödet tar bort mottagarens data som lagras i Adobe Campaign. |
| **Leveransindikatorer** (deliveryIndicators) | Plattform för mid-sourcing | Det här arbetsflödet uppdaterar leveransspårningsindikatorer för en leverans. Det här arbetsflödet aktiveras som standard varje timme. |
| **Distribuerade marknadsföringsprocesser** (centralLocalMgt) | Central/lokal marknadsföring (distribuerad marknadsföring) | Det här arbetsflödet påbörjar bearbetning som är relaterad till användning av den distribuerade marknadsföringsmodulen. Det startar skapandet av lokala kampanjer och hanterar meddelanden relaterade till order och tillgänglighet för kampanjpaket. |
| **Rensa händelse** (webAnalyticsPurgeWebEvents) | Web Analytics-anslutningar | Med det här arbetsflödet kan du ta bort alla händelser från databasfältet enligt den period som har konfigurerats i fältet Livslängd. |
| **Exportera målgrupper till Adobe Experience Cloud** (exportSharedAudience) | Integrering med Adobe Experience Cloud | Det här arbetsflödet exporterar målgrupper som delade målgrupper/segment. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. |
| **Prognos** (prognoser) | Leverans | Det här arbetsflödet analyserar leveranser som sparats i den preliminära kalendern (skapar preliminära loggar). Den utlöses som standard varje dag klockan 1:00. |
| **Fullständig aggregerad beräkning (propositionskub)** (agg_nmsproposition_cp_full) | Erbjudandemotor (interaktion) | Det här arbetsflödet uppdaterar den fullständiga sammanställningen för erbjudandekuben. Den aktiveras varje dag kl. 6.00 som standard. Den här sammanställningen fångar följande dimensioner: Kanal, leverans, marknadsföringserbjudande och datum. Bufferterbjudandekuben används sedan för att generera rapporter baserat på erbjudanden. Läs mer om kuber i  [det här avsnittet](../../v8/reporting/gs-cubes.md). |
| **Identifiering av konverterade kontakter** (webAnalyticsFindConverted) | Web Analytics-anslutningar | Det här arbetsflödet indexerar besökare som har slutfört sitt köp efter en ny marknadsföringskampanj. De data som återställs av det här arbetsflödet finns i rapporten Effektivare återmarknadsföring (se den här sidan). |
| **Importera målgrupper från Adobe Experience Cloud** (importSharedAudience) | Integrering med Adobe Experience Cloud | Med det här arbetsflödet kan du importera målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. |
| **Jobb för leveranser i kampanjer** (deliveryMgt) | Installerad som standard | Det här arbetsflödet utlöser de godkända leveranserna och påbörjar efterbearbetning av tjänsteleverantören för en extern leverans. Dessutom skickas meddelanden och påminnelser om godkännande. |
| **Jobb för tjänsteleverantörer** (providerMgt) | Installerad som standard | Det här arbetsflödet börjar bearbeta providern (e-post till routern och efterbearbetning) när leveranser har godkänts. |
| **MID till LineUserID-migrering** (MIDToUserIDMigration) | LINE-kanal | Det här arbetsflödet genererar användar-ID:t för LINE V2 för migrering från LINE V1 till LINE V2. |
| **Meddelandecenter &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | Kontroll av transaktionsmeddelanden (Message Center - Control) | Det här arbetsflödet: <ul><li>återställer listan över händelser som bearbetats av åtgärderna.</li><li>synkroniserar med tabellen NmsBroadLogMsg för att återställa leveranskunskaper.</li><li>återställer händelseloggar så snart synkroniseringen med tabellen NmsBroadLogMsg har slutförts.</li><li>synkroniserar med NmsTrackingUrl-tabellen för att återställa spårningen för leverans-URL:er.</li><li>återställer URL:er för händelsespårning så snart synkroniseringen med tabellen NmsTrackingUrl har slutförts.</li><li>Med kan du återställa alla e-postadresser som placerats i karantän var tredje timme efter att en leverans har skickats.</li></ul> |
| **Fullständig mängdberäkning för MessageCenter** (agg_messageCenter_full) | Kontroll av transaktionsmeddelanden (Message Center - Control) | Det här arbetsflödet uppdaterar den fullständiga sammanställningen för Message Center-kuben. Den aktiveras varje dag klockan tre som standard. Den här sammanställningen fångar följande dimensioner: Typ av kanal, datum, status och händelse. Meddelandecenterkuben används sedan för att generera rapporter baserade på händelser. Du kan lära dig mer om kuber i  |
| **Mid-sourcing (leveransräknare)** (defaultMidSourcingDlv) | Överföring till mid-sourcing | Det här arbetsflödet samlar in räkningsinformation för leveranser på servern för mellanlagring. Räkningsinformation omfattar allmänna leveransindikatorer, t.ex. antalet skickade leveranser. Spårningsinformation som öppningar inkluderas inte. Den aktiveras var tionde minut som standard. |
| **Mid-sourcing (leveransloggar)** (defaultMidSourcingLog) | Överföring till mid-sourcing | Det här arbetsflödet samlar in leveransloggar på servern med mellanleverantörer. Den aktiveras som standard varje timme. |
| **Hantering av NMAC-avanmälan** (mobileAppOptOutMgt) | Mobilappskanal (push) | Det här arbetsflödet uppdaterar meddelanden om att prenumerationen har avbrutits på mobila enheter. Den utlöses var 6: e timme mellan 1:00 och 24:00. |
| **Meddelande om erbjudande** (offerMgt) | Installerad som standard | Det här arbetsflödet distribuerar godkända erbjudanden i onlinemiljön samt i alla kategorier i erbjudandekatalogen. |
| **Rensa pausade arbetsflöden** (cleanupPausedWorkflows) | Installerad som standard | Det här arbetsflödet analyserar pausade arbetsflöden som har allvarlighetsgraden inställd på normal och utlöser varningar och meddelanden när de har pausats för länge. Efter en månad stoppas de pausade tekniska arbetsflödena ovillkorligt. Som standard utlöses den varje måndag kl. 5. Mer information finns i [Hantering av pausade arbetsflöden](monitor-workflow-execution.md#handling-of-paused-workflows). |
| **Rensa sekretessbegäran** (cleanupPrivacyRequests) | Sekretessdataskyddsförordningen | Det här arbetsflödet raderar filer för åtkomstbegäran som är äldre än 90 dagar. |
| **Bearbetar grupphändelser** (batchEventsProcessing) | Körning av transaktionsmeddelande (Message Center - Execution) | Med det här arbetsflödet kan du placera grupphändelser i en kö innan du associerar dem med en meddelandemall. |
| **Bearbeta realtidshändelser** (rtEventsProcessing) | Körning av transaktionsmeddelande (Message Center - Execution) | Med det här arbetsflödet kan du placera realtidshändelser i en kö innan du associerar dem med en meddelandemall. |
| **Förslagssynkronisering** (propositionSynch) | Kontroll över erbjudandemotorn med körningsinstans | Det här arbetsflödet synkroniserar förslag mellan marknadsinstansen och körningsinstansen som används för interaktioner. |
| **Återställning av webbhändelser** (webAnalyticsGetWebEvents) | Web Analytics-anslutningar | Varje timme laddar det här arbetsflödet ned segment för internetanvändare på en viss webbplats, placerar dem i Adobe Campaign-databasen och startar arbetsflödet för ommarknadsföring. |
| **Rapporteringsaggregat** (reportingAggregates) | Leverans | Det här arbetsflödet uppdaterar aggregat som används i rapporter. Den aktiveras varje dag klockan 2 som standard. |
| **Skicka indikatorer och kampanjattribut** (webAnalyticsSendMetrics) | Web Analytics-anslutningar | Med det här arbetsflödet kan ni skicka kampanjindikatorer från Adobe Campaign till Adobe Experience Cloud Suite via Adobe® Analytics-kontakten. De berörda indikatorerna är följande: Skickat (Skickat), Totalt antal öppningar (iTotalRecipientOpen), Totalt antal mottagare som klickat (iTotalRecipientClick), Fel (iError), Avanmäl (avanmäl dig) (iOptOut). |
| **Stock: Beställningar och varningar** (stockMgt) | Installerad som standard | Det här arbetsflödet startar lagerberäkning på orderraderna och hanterar varningsaviseringströsklar. |
| **Spårning** (spårning | Installerad som standard | Det här arbetsflödet utför återställning och konsolidering av spårningsinformation. Dessutom säkerställs omberäkningen av spårnings- och leveransstatistik, särskilt sådan som används i arbetsflöden för meddelandecentrets arkivering. Som standard aktiveras den en gång per timme. |
| **Uppdatera händelsestatus** (updateEventsStatus) | Körning av transaktionsmeddelande (Message Center - Execution) | Med det här arbetsflödet kan du tilldela en status till en händelse. Händelsestatus är följande:<ul><li>Väntande: händelsen finns i en kö. Ingen meddelandemall har ännu kopplats till den.</li><li>Väntande leverans: Om händelsen finns i en kö har en meddelandemall kopplats till den och bearbetas av leveransen.</li><li>Skickat: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.</li><li>Ignoreras av leveransen: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har ignorerats.</li><li>Leveransfel: den här statusen kopieras från leveransloggarna. Det innebär att leveransen har misslyckats.</li><li>Händelsen omfattas inte: händelsen inte har kopplats till en meddelandemall. Händelsen kommer inte att bearbetas på nytt.</li></ul> |
| **Uppdatering för leverans** (deliverabilityUpdate) | Installerad som standard | När paketet för leveransövervakning (E-postleverans) har installerats körs det här arbetsflödet nattetid och hanterar kvalificeringsreglerna för studsmeddelanden samt listan över domäner och MX. Detta kräver att HTTPS-porten är öppen på plattformen. |
