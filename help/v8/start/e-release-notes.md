---
title: Versionsinformation om tidig kampanj v8
description: Tidig Campaign v8-version
feature: Overview
role: Admin, Developer, User
level: Beginner, Intermediate, Experienced
hide: true
hidefromtoc: true
source-git-commit: acb3223a9a70179ea1cb3a126ef17cf5e234b4ba
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 5%

---

# Tidig versionsinformation {#e-new-release}

Den här sidan beskriver de förbättringar och korrigeringar som ingår i nästa Campaign v8-version.

>[!CAUTION]
>
> Innehållet kan ändras utan föregående meddelande fram till releasedatum. Den officiella versionsinformationen finns här [page](../start/release-notes.md).

## Version 8.3.9 {#release-8-3-9}

_7 oktober 2022_

**Förbättringar**

* Ett problem som påverkade statusuppdateringarna för leveransloggen på MID-instansen när alternativet FeatureFlag_GZIP_Compression aktiverades har åtgärdats. (NEO-49183)
* The **Databasrensning** tekniskt arbetsflöde hanterar nu även anpassade staging-scheman. (NEO-48974)
* Korrigerat ett problem som kan leda till att leveranser stannar kvar i **Väntande** status även om kontaktdatumet har nåtts. (NEO-48079, NEO-48251)
* Förbättrad stabilitet vid hantering av ogiltiga XML-strängar under SOAP-anrop. (NEO-48027)
* Korrigerade ett problem som kunde göra leveransanalysen långsammare, med undantag för steget med blocklist mottagare, när stora volymer mottagare användes. (NEO-48019)
* För att undvika långsamhet när du skickar ett korrektur till dirigerade adresser grupperas nu alla efterföljande replikeringar av dirigerade medlemmar i en replikeringsbegäran. (NEO-44844)
* Korrigerade ett problem som ledde till personaliseringsproblem när SMS-meddelanden skickades med ett externt leveransläge. (NEO-46415)
* Korrigerade ett problem som visade ett fel när en leverans skulle förhandsgranskas i en arkiverad händelse i Message Center. (NEO-43620)
* Ett problem i arbetsflöden som kunde förhindra att filer uppdaterades på servern när **Inläsning av data (fil)** aktivitet. Processen stoppades till 100 % men tog aldrig slut. (NEO-47269)
* Korrigerade ett problem som ledde till att onödiga DeliveryParts skapades när leveransen använde kalender- och delningslägen. (NEO-48634)
* Ett prestandaproblem har korrigerats vid användning av kalenderbaserade påfyllnader. (NEO-48451)
* Korrigerade ett problem som kunde leda till ett felmeddelande på skärmen för leveranslistan efter att en ny målmappning skapades för ett anpassat schema. (NEO-49237)
* Korrigerade ett problem som kunde inträffa om en leverans nådde en viss storlek under MTA-processen. (NEO-46097)
* Ett problem som gjorde att spårningsloggar inte kunde returnera data som var relaterade till mottagarens webbläsare har korrigerats. (NEO-46612)
* Korrigerade ett problem under efteruppgraderingen i japanska miljöer. (NEO-46640)
* Ett problem som uppstod när **Fråga** och filtrera en tabell. När ett kolumnnamn innehöll ordet &quot;Uppdatera&quot; uppstod ett kompileringsfel med en ogiltig identifierare och följande meddelande: &quot;antal uppdaterade rader&quot;. (NEO-46485)
* Ett problem som förhindrade **[!UICONTROL Replicate Staging data]** (ffdaReplicateStagingData) tekniska arbetsflöden kan inte stoppas även om ett fel inträffar under körningen. (NEO-46280)
* Korrigerade ett problem som kunde orsaka dataförlust om mellanlagringsarbetsflödet var felaktigt och kvarhållningsperioden gick ut. (NEO-48975)
* Ett problem har korrigerats vid inmatning av data i molndatabasen i Snowflake med en kampanj **Fråga** aktivitet och **Ändra datakälla** aktivitet: processen misslyckades när det finns ett omvänt snedstreck i data. Källsträngen kunde inte escape-konverteras och data bearbetades inte korrekt på Snowflake. (NEO-45549)
