---
title: Importera profiler i Campaign
description: Lär dig hur du importerar kontakter i Campaign
feature: Audiences, Profiles
role: Data Engineer
level: Beginner
exl-id: b6a5083f-2b5a-4f5b-ad30-d91363752896
source-git-commit: 59046a11c3e057cf41c322f190a9d8aef310c356
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 6%

---

# Importera profiler från en fil{#create-profiles}

Om du vill fylla i Campaign-databasen kan du [lägga till profiler manuellt](create-profiles.md) eller importera profiler enligt nedan. Du kan också använda importerade filer för att uppdatera kontaktdata.

## Importera profiler med ett arbetsflöde {#import-profiles-with-a-wf}

Arbetsflöden kan vara ett användbart sätt att automatisera vissa importprocesser. Oavsett om du importerar data från en lokal fil eller från en SFTP kan du använda arbetsflöden för att standardisera datahanteringsprocesserna.

### Använd data från en lista: Läslista {#data-from-read-list}

Förbered och strukturera data i en fil för att importera dem med ett arbetsflöde. [Läs mer](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/read-list.html).

### Läsa in data från en fil {#data-from-a-file}

Data som bearbetas i ett arbetsflöde kan extraheras från en strukturerad fil så att de kan importeras till Adobe Campaign. [Läs mer](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading--file-.html).

När data har samlats in kan du använda dem i dina arbetsflöden, till exempel för att förbättra en leverans eller uppdatera databasen. Mer information om detta finns i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/use-workflow-data.html).

## Import av enstaka bilder{#import-jobs}

Adobe Campaign har en generisk importfunktion som gör att du till exempel kan extrahera en lista över kunder eller potentiella kunder som sedan blir en del av målpopulationen eller förse din databas med data från externa filer.

Allmän import hanteras från **[!UICONTROL Profiles and Targets > Jobs]** på Adobe Campaign hemsida.

![](assets/new-import-job.png)

Stegen för att utföra en allmän import beskrivs i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/generic-imports-exports/about-generic-imports-exports.html){target=&quot;_blank&quot;}.
