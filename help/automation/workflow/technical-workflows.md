---
product: campaign
title: Tekniska arbetsflöden
description: Läs mer om de tekniska arbetsflödena i Campaign
feature: Workflows
role: User, Admin
exl-id: 2693856c-80b2-4e35-be8e-2a9760f8311f
source-git-commit: 97ab8259c0044b65fec2ad5ddc44d28f0cbf65e5
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 0%

---

# Tekniska arbetsflöden{#about-technical-workflows}

Adobe Campaign innehåller en uppsättning inbyggda tekniska arbetsflöden. De styr åtgärder och jobb som schemalagts för periodisk körning på servern. Tekniska arbetsflöden utför underhållsåtgärder på er Campaign-databas, hanterar spårningsdata för leveranser och konfigurerar även provisoriska processer för leveranser.

Som standard är tekniska arbetsflöden tillgängliga i en undermapp till följande nod: **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

![](assets/navtree.png){width="50%" align="center" zoomable="yes"}

>[!NOTE]
>
>* En lista över tekniska arbetsflöden som installeras med varje modul finns i [det här avsnittet](#list-technical-workflows).
>
>* Tekniska arbetsflöden som är relaterade till tillägget Message Center lagras som standard i noden **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]** .

Undermappen **[!UICONTROL Campaign process]** centraliserar de arbetsflöden som krävs för att köra processer inom kampanjer: aktivitetsmeddelande, lagerhantering, kostnadsberäkning osv.

![](assets/campaign-processes-wf.png){width="70%" align="center" zoomable="yes"}


## Hantera och skapa tekniska arbetsflöden {#manage-tech-workflows}

Kampanjtekniska arbetsflöden kan bara startas och ändras av operatorer med **administratörsbehörighet**. Lär dig hur du övervakar tekniska arbetsflöden i det här [dedikerade avsnittet](monitor-technical-workflows.md).

Du kan skapa anpassade tekniska arbetsflöden i noden **[!UICONTROL Administration > Production > Technical workflows]** i trädstrukturen. Inbyggda mallar finns för att skapa tekniska arbetsflöden. De kan konfigureras så att de passar dina behov. Den här processen är dock reserverad för expertanvändare. De aktiviteter som är tillgängliga i tekniska arbetsflöden är desamma som för riktade arbetsflöden. [Läs mer](targeting-workflows.md).

## Förteckning över tekniska arbetsflöden {#list-technical-workflows}

De arbetsflöden som beskrivs på den här sidan installeras med Adobe Campaign inbyggda paket. Dessa paket och tillhörande tekniska arbetsflöden är beroende av ditt licensavtal och tillägg.

| Tekniskt arbetsflöde | Paket | Beskrivning |
|------|--------|-----------|
| **Aliasrensning** (aliasCleansing) | Installerad som standard | Det här arbetsflödet standardiserar uppräkningsvärden. Den aktiveras varje dag klockan tre som standard. |
| **Fakturering** (fakturering) | Installerad som standard | Det här arbetsflödet skickar systemaktivitetsrapporten till faktureringsoperatorn via e-post. Den utlöses den 25:e varje månad på marknadsinstansen. |
| **Kampanjjobb** (operationMgt) | Installerad som standard | Det här arbetsflödet hanterar jobben för marknadsföringskampanjer (lanserar målinriktning, filextrahering osv.). Det skapar också arbetsflöden för återkommande och periodiska kampanjer. |
| **Samla in data för HeatMap-tjänsten** (collectDataHeatMapService) | Installerad som standard | Det här arbetsflödet hämtar data som krävs av HeatMap-tjänsten. |
| **Samla in sekretessförfrågningar** (collectPrivacyRequests) | Skyddsförordningen för personuppgifter | Det här arbetsflödet genererar mottagarens data som lagras i Adobe Campaign och gör dem tillgängliga för hämtning på skärmen för sekretesspolicy. |
| **Kostnadsberäkning** (budgetMgt) | Installerad som standard | Det här arbetsflödet startar beräkningen av utgifts- och kostnadsrader för budgetar, planer, program, kampanjer, leveranser och uppgifter. |
| **Databasrensning** (rensning) | Installerad som standard | Det här arbetsflödet är arbetsflödet för databasunderhåll: det utför andra beräkningar än statistik och processer och tar bort föråldrade data från databasen enligt den definierade konfigurationen i distributionsassistenten. Den aktiveras varje dag klockan fyra som standard. |
| **Ta bort blockerade LINE-användare** (deleteBlockedLineUsersV2) | LINE-kanal | Det här arbetsflödet säkerställer att LINE V2-användarnas data tas bort efter att de har blockerat LINE-kontot i 180 dagar. |
| **Ta bort data för sekretessförfrågningar** (deletePrivacyRequestsData) | Skyddsförordningen för personuppgifter | Det här arbetsflödet tar bort mottagarens data som lagras i Adobe Campaign. |
| **Leveransindikatorer** (deliveryIndicators) | Installerad som standard | Det här arbetsflödet uppdaterar leveransspårningsindikatorer för en leverans. Det här arbetsflödet aktiveras som standard varje timme. |
| **Distribuerade marknadsföringsprocesser** (centralLocalMgt) | Central/lokal marknadsföring (distribuerad marknadsföring) | Det här arbetsflödet påbörjar bearbetning som är relaterad till användning av den distribuerade marknadsföringsmodulen. Det startar skapandet av lokala kampanjer och hanterar meddelanden relaterade till order och tillgänglighet för kampanjpaket. |
| **Rensa händelser** (webAnalyticsPurgeWebEvents) | Web Analytics-anslutningar | Med det här arbetsflödet kan du ta bort alla händelser från databasfältet enligt den period som har konfigurerats i fältet Livslängd. |
| **Exportera målgrupper till Adobe Experience Cloud** (exportSharedAudience) | Integrering med Adobe Experience Cloud | Det här arbetsflödet exporterar målgrupper som delade målgrupper/segment. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. |
| **ffdaUnsubscribe** | Installerad som standard | Det här arbetsflödet hanterar avbeställningar som tagits emot som studsade e-postmeddelanden (genom att använda metoden `<mailto>` List-Unsubscribe). Den körs varje dag, var 1:e timme, endast på marknadsföringsinstanser med en Enterprise-distribution (FFDA).<br/><br/>Arbetsflödet kontrollerar utsändningar från ett visst tidsintervall (den senaste bearbetningstiden och den aktuella tiden) som markeras som obundet prenumerationsläge av modulen inMail (markeringen anges i kolumnen iFlags i tabellen NmsBroadLog) och bearbetar en avprenumeration beroende på om tjänsten i utsändaren är inställd eller inte:<ul><li>Om serviceId är 0 (inte definierad) blocklist mottagaren.</li><li>Om serviceId inte är 0 (länkat till en befintlig tjänst) kommer mottagaren att avbryta prenumerationen på tjänsten.</li></ul><br/>Obs! Det här arbetsflödet hanterar endast avbrutna prenumerationer. Avanmälan via avanmälningslänk och Avanmälan med ett klick (URL-metod) hanteras separat utanför det här arbetsflödet. |
| **Prognos** (prognos) | Installerad som standard | Det här arbetsflödet analyserar leveranser som sparats i den preliminära kalendern (skapar preliminära loggar). Den utlöses som standard varje dag klockan 1:00. |
| **Fullständig aggregeringsberäkning (propositionCp-kub)** (agg_nmspropositionCp_full) | Erbjudandemotor (interaktion) | Det här arbetsflödet uppdaterar den fullständiga sammanställningen för erbjudandekuben. Den aktiveras varje dag kl. 6.00 som standard. Sammanställningen innehåller följande dimensioner: kanal, leverans, marknadsföringserbjudande och datum. Bufferterbjudandekuben används sedan för att generera rapporter baserat på erbjudanden. Läs mer om kuber i [det här avsnittet](../../v8/reporting/gs-cubes.md). |
| **Identifiering av konverterade kontakter** (webAnalyticsFindConverted) | Web Analytics-anslutningar | Det här arbetsflödet indexerar besökare som har slutfört sitt köp efter en ny marknadsföringskampanj. De data som återställs av det här arbetsflödet finns i rapporten Effektivare återmarknadsföring (se den här sidan). |
| **Importera målgrupper från Adobe Experience Cloud** (importSharedAudience) | Integrering med Adobe Experience Cloud | Med det här arbetsflödet kan du importera målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. |
| **Jobb för leveranser i kampanjer** (deliveryMgt) | Installerad som standard | Det här arbetsflödet utlöser de godkända leveranserna och påbörjar efterbearbetning av tjänsteleverantören för en extern leverans. Dessutom skickas meddelanden och påminnelser om godkännande. |
| **Jobb på tjänstleverantörer** (providerMgt) | Installerad som standard | Det här arbetsflödet börjar bearbeta providern (e-post till routern och efterbearbetning) när leveranser har godkänts. |
| **MID till LineUserID-migrering** (MIDToUserIDMigration) | LINE-kanal | Det här arbetsflödet genererar användar-ID:t för LINE V2 för migrering från LINE V1 till LINE V2. |
| **Meddelandecenter &lt;externt_kontonamn>** (mcSynch_&lt;externt_kontonamn>) | Kontroll av transaktionsmeddelanden (Message Center - Control) | Det här arbetsflödet: <ul><li>återställer listan över händelser som bearbetats av åtgärderna.</li><li>synkroniserar med tabellen NmsBroadLogMsg för att återställa leveranskunskaper.</li><li>återställer händelseloggar så snart synkroniseringen med tabellen NmsBroadLogMsg har slutförts.</li><li>synkroniserar med NmsTrackingUrl-tabellen för att återställa spårningen för leverans-URL:er.</li><li>återställer URL:er för händelsespårning så snart synkroniseringen med tabellen NmsTrackingUrl har slutförts.</li><li>Med kan du återställa alla e-postadresser som placerats i karantän var tredje timme efter att en leverans har skickats.</li></ul> |
| **Fullständig mängdberäkning för MessageCenter** (agg_messageCenter_full) | Kontroll av transaktionsmeddelanden (Message Center - Control) | Det här arbetsflödet uppdaterar den fullständiga sammanställningen för Message Center-kuben. Den aktiveras varje dag klockan tre som standard. Den här sammanställningen fångar följande dimensioner: Kanal, Datum, Status och Händelsetyp. Meddelandecenterkuben används sedan för att generera rapporter baserade på händelser. Du kan lära dig mer om kuber i  |
| **Mid-sourcing (leveransräknare)** (defaultMidSourcingDlv) | Överföring till Mid-sourcing | Det här arbetsflödet samlar in räkningsinformation för leveranser på servern för mellanlagring. Räkningsinformation omfattar allmänna leveransindikatorer, t.ex. antalet skickade leveranser. Spårningsinformation som öppningar inkluderas inte. Den aktiveras var tionde minut som standard. |
| **Mid-sourcing (leveransloggar)** (defaultMidSourcingLog) | Överföring till Mid-sourcing | Det här arbetsflödet samlar in leveransloggar på servern med mellanleverantörer. Den aktiveras som standard varje timme. |
| **Hantering av NMAC-avanmälan** (mobileAppOptOutMgt) | Mobilappskanal (push) | Det här arbetsflödet uppdaterar meddelanden om att prenumerationen har avbrutits på mobila enheter. Den utlöses var 6: e timme mellan 1:00 och 24:00. |
| **Erbjudandemeddelande** (offerMgt) | Installerad som standard | Det här arbetsflödet distribuerar godkända erbjudanden i onlinemiljön samt i alla kategorier i erbjudandekatalogen. |
| **Rensning av pausade arbetsflöden** (cleanupPausedWorkflows) | Installerad som standard | Det här arbetsflödet analyserar pausade arbetsflöden som har allvarlighetsgraden inställd på normal och utlöser varningar och meddelanden när de har pausats för länge. Efter en månad stoppas tekniska arbetsflöden ovillkorligt. Som standard utlöses den varje måndag kl. 5. Mer information finns i [Hantera pausade arbetsflöden](monitor-workflow-execution.md#handling-of-paused-workflows). |
| **Rensa sekretessbegäran** (cleanupPrivacyRequests) | Skyddsförordningen för personuppgifter | Det här arbetsflödet raderar filer för åtkomstbegäran som är äldre än 90 dagar. |
| **Bearbetar grupphändelser** (batchEventsProcessing) | Körning av transaktionsmeddelande (Message Center - Execution) | Med det här arbetsflödet kan du placera grupphändelser i en kö innan du associerar dem med en meddelandemall. |
| **Bearbetar realtidshändelser** (rtEventsProcessing) | Körning av transaktionsmeddelande (Message Center - Execution) | Med det här arbetsflödet kan du placera realtidshändelser i en kö innan du associerar dem med en meddelandemall. |
| **Propositionssynkronisering** (propositionSynch) | Kontroll över erbjudandemotorn med körningsinstans | Det här arbetsflödet synkroniserar förslag mellan marknadsinstansen och körningsinstansen som används för interaktioner. |
| **Återställning av webbhändelser** (webAnalyticsGetWebEvents) | Web Analytics-anslutningar | Varje timme laddar det här arbetsflödet ned segment för internetanvändare på en viss webbplats, placerar dem i Adobe Campaign-databasen och startar arbetsflödet för ommarknadsföring. |
| **Rapportera aggregat** (reportingAggregates) | Leverans | Det här arbetsflödet uppdaterar aggregat som används i rapporter. Den aktiveras varje dag kl. 2.00 som standard. |
| **Skickar indikatorer och kampanjattribut** (webAnalyticsSendMetrics) | Web Analytics-anslutningar | Med det här arbetsflödet kan ni skicka kampanjindikatorer från Adobe Campaign till Adobe Experience Cloud Suite via Adobe® Analytics-kontakten. De berörda indikatorerna är följande: Skickat (Skickat), Totalt antal öppningar (iTotalRecipientOpen), Totalt antal mottagare som klickat (iTotalRecipientClick), Fel (iError), Avanmäl (avanmäl dig) (iOptOut). |
| **Stock: Beställningar och aviseringar** (stockMgt) | Installerad som standard | Det här arbetsflödet startar lagerberäkning på orderraderna och hanterar varningsaviseringströsklar. |
| **Synkronisera mobilappar från Adobe Experience Platform Data Collection** (syncWithLaunch) | Installerat som standard från v8.5 | Det här arbetsflödet synkroniserar automatiskt mobila egenskaper till Adobe Campaign från datainsamling. |
| **Spårning** (spårning) | Installerad som standard | Det här arbetsflödet utför återställning och konsolidering av spårningsinformation. Dessutom säkerställs omberäkningen av spårnings- och leveransstatistik, särskilt sådan som används i arbetsflöden för meddelandecentrets arkivering. Som standard aktiveras den en gång per timme. |
| **Uppdatera händelsestatus** (updateEventsStatus) | Körning av transaktionsmeddelande (Message Center - Execution) | Med det här arbetsflödet kan du tilldela en status till en händelse. Händelsestatus är följande:<ul><li>Väntande: händelsen finns i en kö. Ingen meddelandemall har ännu kopplats till den.</li><li>Väntande leverans: händelsen finns i en kö, en meddelandemall har kopplats till den och bearbetas för närvarande av leveransen.</li><li>Skickat: Den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.</li><li>Ignoreras av leveransen: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har ignorerats.</li><li>Leveransfel: den här statusen kopieras från leveransloggarna. Det innebär att leveransen har misslyckats.</li><li>Händelsen täcks inte: händelsen kunde inte kopplas till en meddelandemall. Händelsen kommer inte att bearbetas på nytt.</li></ul> |
| **Uppdatering för levererbarhet** (deliverabilityUpdate) | Installerad som standard | När paketet för leveransövervakning (E-postleverans) har installerats körs det här arbetsflödet nattetid och hanterar kvalificeringsreglerna för studsmeddelanden samt listan över domäner och MX. Detta kräver att HTTPS-porten är öppen på plattformen. |
