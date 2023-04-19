---
title: Samla in och bearbeta händelser
description: Läs om hur Campaign Transactional Messaging samlar in och bearbetar händelser
feature: Transactional Messaging
role: User
level: Beginner, Intermediate
exl-id: c1deb0a1-aeba-4813-b674-a6a164b98b02
source-git-commit: c044b391c900e8ff82147f2682e2e4f91845780c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Händelsebearbetning {#event-processing}

Vid transaktionsmeddelanden genereras en händelse av ett externt informationssystem och skickas till Adobe Campaign via **[!UICONTROL PushEvent]** och **[!UICONTROL PushEvents]** metoder. Dessa metoder beskrivs i [det här avsnittet](event-description.md).

Den här händelsen innehåller data som är länkade till händelsen, till exempel:

* sin [type](transactional.md#create-event-types): orderbekräftelse, kontoskapande på en webbplats, osv.,
* e-postadress eller telefonnummer,
* all annan information som berikar och personaliserar transaktionsmeddelandet före leverans: kundens kontaktinformation, meddelandespråk, e-postformat osv.

Exempel på händelsedata:

![](assets/mc-event-request.png)

För att bearbeta transaktionsmeddelandehändelser tillämpas följande steg på körningsinstansen/instanserna:

1. [Händelsesamling](#event-collection)
1. [Händelseöverföring till en meddelandemall](#routing-towards-a-template)
1. Evenemangsberikning med personaliseringsdata
1. [Leveranskörning](delivery-execution.md)
1. [Återvinning av händelser](#event-recycling) vars länkade leverans misslyckades (via ett Adobe Campaign-arbetsflöde)

När alla steg är klara får varje målmottagare ett personligt meddelande.

## Samla in händelser {#event-collection}

Händelser som genereras av informationssystemet kan samlas in på två sätt:

* Anrop till SOAP-metoder gör att du kan skicka händelser i Adobe Campaign: Med metoden PushEvent kan du skicka en händelse i taget. Med metoden PushEvents kan du skicka flera händelser samtidigt. [Läs mer](event-description.md).

* Genom att skapa ett arbetsflöde kan du återställa händelser genom att importera filer eller via en SQL-gateway med [Åtkomst till federerade data](../connect/fda.md) -modul.

När de har samlats in delas händelser upp i tekniska arbetsflöden mellan körningsinstansens (instansernas) realtids- och batchköer, medan händelser väntar på att länkas till en [meddelandemall](transactional-template.md).

![](assets/mc-event-queues.png)

>[!NOTE]
>
>På körningsinstanserna visas **[!UICONTROL Real time events]** eller **[!UICONTROL Batch events]** mappar får inte anges som vyer eftersom detta kan leda till problem med åtkomst. Mer information om hur du anger en mapp som en vy finns i [det här avsnittet](../audiences/folders-and-views.md#turn-a-folder-to-a-view).

## Överföra en händelse till en mall {#event-to-template}

När meddelandemallen har publicerats på körningsinstansen/körningsinstanserna genereras två mallar automatiskt: en som ska länkas till en realtidshändelse och en som ska länkas till en batchhändelse.

Vägningssteget består i att länka en händelse till rätt meddelandemall baserat på:

* Händelsetypen som anges i egenskaperna för själva händelsen:

   ![](assets/event-type-sample.png)

* Händelsetypen som anges i meddelandemallens egenskaper:

   ![](assets/event-type-select.png)

Som standard används följande information för routning:

* Händelsetypen
* Den kanal som ska användas (som standard: e-post)
* Den senaste leveransmallen, baserad på publiceringsdatumet

## Kontrollera händelsestatus {#event-statuses}

Alla bearbetade händelser grupperas i en enda vy i **Händelsehistorik** eller Utforskaren. De kan kategoriseras efter händelsetyp eller efter **status**.

Möjliga statusar är:

* **Väntande**

   * En väntande händelse kan vara en händelse som precis har samlats in och som ännu inte har bearbetats. The **[!UICONTROL Number of errors]** kolumnen visar värdet 0. E-postmallen har ännu inte länkats.
   * En väntande händelse kan också vara en händelse som bearbetas, men vars bekräftelse är felaktig. The **[!UICONTROL Number of errors]** kolumnen visar ett värde som inte är 0. Om du vill veta när den här händelsen ska behandlas igen kan du läsa **[!UICONTROL Process requested on]** kolumn.

* **Väntande leverans**
Händelsen bearbetades och leveransmallen är länkad. E-postmeddelandet väntar på att levereras och den klassiska leveransprocessen tillämpas. Du kan öppna leveransen om du vill ha mer information.
* **Skickat**, **Ignorerad** och **Leveransfel**
Dessa leveransstatusvärden återställs via 
**updateEventsStatus** arbetsflöde. Mer information får du genom att öppna den relevanta leveransen.
* **Händelsen täcks inte**
Transactional Messaging-routningsfasen misslyckades. Adobe Campaign hittade till exempel inte e-postmeddelandet som fungerar som mall för händelsen.
* **Händelsen har upphört**
Det maximala antalet sändningsförsök har uppnåtts. Händelsen betraktas som null.

## Återvinningshändelser {#event-recycling}

Om det inte går att skicka ett meddelande via en viss kanal kan Adobe Campaign skicka meddelandet igen via en annan kanal. Om till exempel en leverans på SMS-kanalen misslyckas, skickas meddelandet igen med e-postkanalen.

För att göra detta måste du konfigurera ett arbetsflöde som återskapar alla händelser med **Leveransfel** och tilldelar dem en annan kanal.

>[!CAUTION]
>
>Det här steget kan bara utföras med ett arbetsflöde och är därför reserverat för expertanvändare. Kontakta er kontoansvarige på Adobe för mer information.
