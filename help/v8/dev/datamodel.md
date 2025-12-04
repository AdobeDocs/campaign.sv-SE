---
title: Kom igång med Campaign-datamodellen
description: Kom igång med datamodellen i Campaign och utnyttja data från dina källor för att gynna dina kommunikations- och marknadsföringsresultat.
feature: Data Model
role: Developer
level: Beginner
exl-id: 200b60f1-04ae-4c3e-892f-3dd2bd22b896
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 4%

---

# Kom igång med Campaign-datamodellen {#gs-ac-datamodel}

Adobe Campaign innehåller en fördefinierad datamodell. I det här avsnittet finns mer information om de inbyggda tabellerna i Adobe Campaign datamodell och hur de fungerar. Adobe Campaign förlitar sig på en molndatabas som innehåller tabeller som är länkade tillsammans.

Den grundläggande strukturen i Adobe Campaign datamodell beskrivs på följande sätt:

* **Mottagartabell**: Datamodellen bygger på en huvudtabell som som standard är mottagartabellen (**nmsRecipient**). I det här registret lagras alla marknadsföringsprofiler. Läs mer om mottagartabellen i [det här avsnittet](#ootb-profiles).

* **Leveranstabell**: Den här tabellen lagrar en post per leveransåtgärd. Vanligtvis är det leveranstabellen (**NmsDelivery**). i den här tabellen representerar en leveransåtgärd eller en leveransmall. Den innehåller alla parametrar som krävs för att utföra leveranser som mål, innehåll osv. Varje post uppdateras flera gånger för att återspegla leveransförloppet

* **Loggar tabeller**: I de här tabellerna lagras alla loggar som är associerade med kampanjkörningen.

   * Leveransloggar är alla meddelanden som skickas till mottagare eller enheter i alla kanaler. Huvudtabellen för leveransloggar (**NmsBroadLogRcp**) innehåller leveransloggarna för alla mottagare.
   * Tabellen **nmsBroadlog** är den största tabellen i systemet. Den lagrar en post per skickat meddelande och dessa poster infogas, uppdateras för att spåra leveransstatus och tas bort när historiken rensas.
   * Huvudspårningsloggtabellen (**NmsTrackingLogRcp**) lagrar spårningsloggarna för alla mottagare. Spårningsloggarna refererar till mottagarnas reaktioner, t.ex. öppningar och klickningar via e-post. Varje reaktion motsvarar en spårningslogg.

  Leveransloggar och spårningsloggar tas bort efter en viss period, som anges i Adobe Campaign och kan ändras. Vi rekommenderar därför att du exporterar loggarna regelbundet.

* **Tekniska tabeller**: Samla in tekniska data som används för programprocessen, inklusive operatorer och användarrättigheter (**xtkGroup**), användarsessioner (**xtkSessionInfo**), mappar i utforskarträdet (**XtkFolder**), arbetsflöden (**xtkWorkflow**) med mera.

>[!NOTE]
>
>Om du vill få åtkomst till beskrivningen av varje tabell går du till **Administration > Konfiguration > Datamodeller**, markerar en resurs i listan och klickar på fliken **Dokumentation** .

När du börjar med Adobe Campaign måste du utvärdera standarddatamodellen för att kontrollera vilken tabell som är bäst lämpad för att lagra dina marknadsföringsdata.

Du kan använda den förvalda mottagartabellen med körklara fält, som beskrivs i [det här avsnittet](#ootb-profiles). Om det behövs kan du utöka den med två mekanismer:

* [Utöka en befintlig tabell](extend-schema.md) med nya fält. Du kan till exempel lägga till ett nytt&quot;Lojalitet&quot;-fält i mottagartabellen.
* [Skapa en ny tabell](create-schema.md), t.ex. en&quot;Inköpstabell&quot; som listar alla inköp som gjorts av varje profil i databasen, och länka den till mottagartabellen.

Upptäck bästa praxis när du arbetar med Campaign-datamodellen i [det här avsnittet](datamodel-best-practices.md).

## Inbyggd profiltabell {#ootb-profiles}

Den inbyggda mottagartabellen (nmsreceive) i Adobe Campaign är en bra startpunkt för att skapa din datamodell. Den har ett antal fördefinierade fält och tabelllänkar som enkelt kan utökas. Detta är särskilt användbart när du främst riktar dig till mottagare, eftersom det passar en enkel mottagarorienterad datamodell.

Fördelarna med att använda standardmottagartabellen är:

* Arbeta direkt med nyckelfunktioner som prenumerationer, listor med mera
* Tillhandahålla en marknadsföringsdatabas med en mottagarcentrerad datamodell
* Snabbare implementering
* Enkelt underhåll av support och partners

Det går att utöka mottagartabellen, men inte att minska antalet fält eller länkar i tabellen.

Lär dig att utöka ett befintligt schema i [det här avsnittet](extend-schema.md).

Upptäck exempel på inbyggda mottagartabelltillägg i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/examples-of-schemas-edition.html?lang=sv-SE#extending-a-table){target="_blank"}

Du kan också använda en annan mottagartabell för att bättre passa ditt företags eller dina funktionskrav. Den här metoden har begränsningar och beskrivs i [det här avsnittet](custom-recipient.md).

## Kampanjtabeller och molndatabas

Om du vill få en bättre förståelse för tabellhantering i Campaign v8 kan du observera att tabeller replikeras mellan Campaign och dess Snowflake Cloud-databas i samband med en [Enterprise-distribution](../architecture/enterprise-deployment.md).

Läs mer om replikeringsstrategi och -mekanismer i [det här avsnittet](../architecture/replication.md).

**Relaterade ämnen**

Upptäck hur du importerar profiler i [det här avsnittet](../start/import.md)
Läs mer om Campaign-målgrupper i [det här avsnittet](../start/audiences.md)
