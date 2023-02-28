---
title: Kom igång med datamodellen i Campaign
description: Kom igång med datamodellen i Campaign och utnyttja data från dina källor för att gynna dina kommunikations- och marknadsföringsresultat.
feature: Data Model
role: Data Engineer
level: Beginner
exl-id: 200b60f1-04ae-4c3e-892f-3dd2bd22b896
source-git-commit: 507f30d16eecf5400ee88a4d29913e4cdaca9cba
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 6%

---

# Kom igång med datamodellen i Campaign {#gs-ac-datamodel}

Adobe Campaign innehåller en fördefinierad datamodell. I det här avsnittet finns mer information om de inbyggda tabellerna i Adobe Campaign datamodell och hur de fungerar. Adobe Campaign förlitar sig på en molndatabas som innehåller tabeller som är länkade tillsammans.

Den grundläggande strukturen i Adobe Campaign datamodell beskrivs på följande sätt:

* **Mottagarregister**: Datamodellen bygger på en huvudtabell som som standard är mottagartabellen (nmsRecipient). I det här registret lagras alla marknadsföringsprofiler.

   ![](../assets/do-not-localize/glass.png) Mer information om mottagartabellen finns i [det här avsnittet](#ootb-profiles).

* **Leveransregister**: Datamodellen innehåller också en del som är avsedd för lagring av alla marknadsföringsaktiviteter. Vanligtvis är det Delivery Table (NmsDelivery). Varje post i den här tabellen representerar en leveransåtgärd eller en leveransmall. Den innehåller alla parametrar som krävs för att utföra leveranser som mål, innehåll osv.

* **Loggtabeller**: I dessa tabeller lagras alla loggar som är associerade med kampanjkörningen.

   Leveransloggar är alla meddelanden som skickas till mottagare eller enheter i alla kanaler. Huvudtabellen för leveransloggar (NmsBroadLogRcp) innehåller leveransloggarna för alla mottagare.
Registret för huvudspårningsloggar (NmsTrackingLogRcp) lagrar spårningsloggarna för alla mottagare. Spårningsloggarna refererar till mottagarnas reaktioner, t.ex. öppningar och klickningar via e-post. Varje reaktion motsvarar en spårningslogg.
Leveransloggar och spårningsloggar tas bort efter en viss period, som anges i Adobe Campaign och kan ändras. Vi rekommenderar därför att du exporterar loggarna regelbundet.

* **Tekniska tabeller**: Samla in tekniska data som används för ansökningsprocessen, inklusive operatorer och användarrättigheter (xtkGroup), mappar (XtkFolder).

>[!NOTE]
>
>Om du vill komma åt beskrivningen av varje tabell går du till Admin > Konfiguration > Datamodeller, markerar en resurs i listan och klickar på **Dokumentation** -fliken.

När du börjar med Adobe Campaign måste du utvärdera standarddatamodellen för att kontrollera vilken tabell som är bäst lämpad för att lagra dina marknadsföringsdata.

Du kan använda den förvalda mottagartabellen med färdiga fält, som beskrivs i [det här avsnittet](#ootb-profiles). Om det behövs kan du utöka den med två mekanismer:

* [Utöka en befintlig tabell](extend-schema.md) med nya fält. Du kan till exempel lägga till ett nytt&quot;Lojalitet&quot;-fält i mottagartabellen.
* [Skapa en ny tabell](create-schema.md), t.ex. en&quot;Inköpstabell&quot; som visar alla inköp som gjorts av varje profil i databasen och länkar den till mottagartabellen.

![](../assets/do-not-localize/glass.png) Upptäck bästa praxis när du arbetar med Campaign-datamodellen i [det här avsnittet](datamodel-best-practices.md).

## Inbyggd profiltabell {#ootb-profiles}

Den inbyggda mottagartabellen (nmsreceive) i Adobe Campaign är en bra startpunkt för att skapa din datamodell. Den har ett antal fördefinierade fält och tabelllänkar som enkelt kan utökas. Detta är särskilt användbart när du främst riktar dig till mottagare, eftersom det passar en enkel mottagarorienterad datamodell.

Fördelarna med att använda standardmottagartabellen är:

* Arbeta direkt med nyckelfunktioner som prenumerationer, listor med mera
* Tillhandahålla en marknadsföringsdatabas med en mottagarcentrerad datamodell
* Snabbare implementering
* Enkelt underhåll av support och partners

Det går att utöka mottagartabellen, men inte att minska antalet fält eller länkar i tabellen.

![](../assets/do-not-localize/glass.png) Lär dig hur du utökar ett befintligt schema i [det här avsnittet](extend-schema.md).

![](../assets/do-not-localize/book.png) Upptäck exempel på inbyggda mottagartabelltillägg i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/examples-of-schemas-edition.html?lang=en#extending-a-table){target="_blank"}

Du kan också använda en annan mottagartabell för att bättre passa ditt företags eller dina funktionskrav. Den här metoden har begränsningar och beskrivs i [det här avsnittet](custom-recipient.md).

## Kampanjtabeller och molndatabas

För att få en bättre förståelse för tabellhantering i Campaign v8 bör du tänka på att i ett sammanhang där [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), replikeras tabeller mellan Campaign och dess Snowflake Cloud-databas.

![](../assets/do-not-localize/glass.png) Läs mer om replikeringsstrategi och -mekanismer i [det här avsnittet](../architecture/replication.md).

**Relaterade ämnen**

![](../assets/do-not-localize/glass.png) Läs om hur du importerar profiler i [det här avsnittet](../start/import.md)
![](../assets/do-not-localize/glass.png) Läs mer om Campaign-målgrupper i [det här avsnittet](../start/audiences.md)
