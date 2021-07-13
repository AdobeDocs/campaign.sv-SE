---
product: Adobe Campaign
title: 'Kom igång med datamodellen i Campaign '
description: 'Kom igång med datamodellen i Campaign '
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 200b60f1-04ae-4c3e-892f-3dd2bd22b896,b1319b34-ee07-48ed-9ab1-e2d12d3d99f8
source-git-commit: c61d8aa8e0a68ccc81a6141782f860daf061bc61
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 4%

---

# Kom igång med datamodellen i Campaign {#gs-ac-datamodel}

Adobe Campaign innehåller en fördefinierad datamodell. I det här avsnittet finns mer information om de inbyggda tabellerna i Adobe Campaign datamodell och hur de fungerar. Adobe Campaign förlitar sig på en molndatabas som innehåller tabeller som är länkade tillsammans.

Den grundläggande strukturen i Adobe Campaign datamodell beskrivs på följande sätt:

* **Mottagarregister**: Datamodellen bygger på en huvudtabell som som standard är mottagartabellen (nmsRecipient). Med den här tabellen kan alla marknadsföringsprofiler lagras.

   ? Mer information om mottagartabellen finns i [det här avsnittet](#ootb-profiles).

* **Leveransregister**: Datamodellen innehåller också en del som är avsedd för lagring av alla marknadsföringsaktiviteter. Vanligtvis är det Delivery Table (NmsDelivery). Varje post i den här tabellen representerar en leveransåtgärd eller en leveransmall. Den innehåller alla parametrar som krävs för att utföra leveranser som mål, innehåll osv.

* **Loggtabeller**: I dessa tabeller lagras alla loggar som är associerade med kampanjkörningen.

   Leveransloggar är alla meddelanden som skickas till mottagare eller enheter i alla kanaler. Huvudtabellen för leveransloggar (NmsBroadLogRcp) innehåller leveransloggarna för alla mottagare.
Registret för huvudspårningsloggar (NmsTrackingLogRcp) lagrar spårningsloggarna för alla mottagare. Spårningsloggarna refererar till mottagarnas reaktioner, t.ex. öppningar och klickningar via e-post. Varje reaktion motsvarar en spårningslogg.
Leveransloggar och spårningsloggar tas bort efter en viss period, som anges i Adobe Campaign och kan ändras. Vi rekommenderar därför att du exporterar loggarna regelbundet.

* **Tekniska tabeller**: Samla in tekniska data som används för ansökningsprocessen, inklusive operatorer och användarrättigheter (xtkGroup), mappar (XtkFolder).

>[!NOTE]
>
>Om du vill få åtkomst till beskrivningen av varje tabell går du till Admin > Konfiguration > Datascheman, markerar en resurs i listan och klickar på fliken **Dokumentation**.

När du börjar med Adobe Campaign måste du utvärdera standarddatamodellen för att kontrollera vilken tabell som är bäst lämpad för att lagra dina marknadsföringsdata.

Du kan använda den förvalda mottagartabellen med ej ifyllda fält, som beskrivs i [det här avsnittet](#ootb-profiles). Om det behövs kan du utöka den med två mekanismer:

* [Utöka en befintlig ](extend-schema.md) tabell med nya fält. Du kan till exempel lägga till ett nytt&quot;Lojalitet&quot;-fält i mottagartabellen.
* [Skapa en ny tabell](create-schema.md), t.ex. en&quot;Inköpstabell&quot; med alla inköp som gjorts av varje profil i databasen, och länka den till mottagartabellen.

? Upptäck bästa praxis när du arbetar med Campaign-datamodellen i [det här avsnittet](datamodel-best-practices.md).

## Inbyggd profiltabell {#ootb-profiles}

Den inbyggda mottagartabellen (nmsreceive) i Adobe Campaign är en bra startpunkt för att skapa din datamodell. Den har ett antal fördefinierade fält och tabelllänkar som enkelt kan utökas. Detta är särskilt användbart när du främst riktar dig till mottagare, eftersom det passar en enkel mottagarorienterad datamodell.

Fördelarna med att använda standardmottagartabellen är:

* Arbeta direkt med nyckelfunktioner som prenumerationer, listor med mera
* Tillhandahålla en marknadsföringsdatabas med en mottagarcentrerad datamodell
* Snabbare implementering
* Enkelt underhåll av support och partners

Det går att utöka mottagartabellen, men inte att minska antalet fält eller länkar i tabellen.

? Lär dig hur du utökar ett befintligt schema i [det här avsnittet](extend-schema.md).

↗️ Upptäck exempel på inbyggda mottagartabelltillägg i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/examples-of-schemas-edition.html?lang=en#extending-a-table)

Du kan också använda en annan mottagartabell för att bättre passa ditt företags eller dina funktionskrav. Den här metoden har begränsningar och beskrivs i [det här avsnittet](custom-recipient.md).

## Kampanjtabeller och molndatabas

Om du vill ha en bättre förståelse för tabellhantering i Campaign v8 kan du observera att tabeller replikeras mellan Campaign och dess Snowflake Cloud-databas.

? Läs mer om replikeringsstrategi och -mekanismer i [det här avsnittet](../config/replication.md).

**Relaterade ämnen**

? Läs om hur du importerar profiler i [det här avsnittet](../start/import.md)
? Läs mer om Campaign-målgrupper i [det här avsnittet](../start/audiences.md)
