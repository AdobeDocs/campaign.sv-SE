---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-utgåvan
feature: Overview
role: Admin, Developer, User
level: Beginner, Intermediate, Experienced
hidefromtoc: false
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: 44743e585119e8cd81a8fcc9b4d667c25c0d438e
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 31%

---

# Senaste versionen{#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign v8**.

## Version 8.4.5 {#release-8-4-5}

_3 april 2023_

**Korrigeringar**

* Korrigerade ett problem som kunde leda till ett duplicerat nyckelbegränsningsfel om flera godkännandearbetsflöden hade angetts till samma schema. (NEO-48968)
* Korrigerade ett regressionsfel som introducerades av NEO-54474 (8.4.4) som ledde till att formategenskapen för body-taggen ändrades när en bild överfördes till Digital Content Editor (DCE). (NEO-57697)
* Korrigerade ett problem som kunde leda till ett fel när data exporterades med en CRM-koppling om den tillfälliga tabellen hade en primärnyckel definierad som lång i stället för uuid. (NEO-54153)
* Korrigerade ett regressionsproblem som introducerades i 8.4.1 som kunde leda till fel vid paketexport, FDA över HTTP och rapportering. (NEO-57731)
* Ett regressionsproblem som introducerades i 8.3.8 som kunde förhindra att leveransstatusen uppdateras korrekt för leveranser med negativa ID:n har åtgärdats. (NEO-54675)
* Ett problem med booleska fält vid import av data med Big Query-kopplingen (NEO-49181) har korrigerats

>[!CAUTION]
>
> Uppgradering av klientkonsolen är obligatorisk. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../start/connect.md#upgrade-ac-console).

## Version 8.4.4 {#release-8-4-4}

_8 mars 2023_

**Säkerhetsförbättring**

* För att förbättra säkerheten har Tomcat uppdaterats från version 8.5.81 till 8.5.85. (NEO-50530)

**Korrigeringar**

* Korrigerade ett problem som kunde förhindra dig från att skrolla i fliken **Redigera** i Redigeraren för digitalt innehåll (DCE). (NEO-54474)
* Ett fel som kan leda till att webbservern kraschar har åtgärdats under replikeringen. (NEO-53670)


>[!CAUTION]
>
> Uppgradering av klientkonsolen är obligatorisk. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../start/connect.md#upgrade-ac-console).


## Version 8.4.3 {#release-8-4-3}


_27 januari 2023_

**Förbättringar**

* Ett problem med synkronisering av leveransindikator mellan marknadsföringsservern och mellanleverantörsservern har korrigerats. (NEO-50724) <!--OKKKK-->
* Korrigerade ett problem som kunde leda till ett fel vid export av ett arbetsflöde. (NEO-50555) <!--OKKKK-->
* Ett problem som uppstod när ett tidigare utökat schema skulle utökas har åtgärdats. (NEO-49118) <!--OKKKK-->
* Ett problem har korrigerats vid användning av två anrikningsaktiviteter med samma identifierare i länkdefinitionen. (NEO-48851)
* Åtgärdade två fel vid leveransförberedelse. Förberedelsen kan misslyckas om antalet potentiella erbjudanden som manipuleras är för högt. Det andra problemet uppstod när bild-URL:erna definierades som URL:er att spåra i en textformatsleverans. (NEO-48807) <!--OKKKK-->
* Korrigerade ett problem som kunde leda till ett arbetsflödesfel där ett arbetsflöde skulle skriva över det lagerställenamn som definierats i det externa kontot för andra konton än FFDA. (NEO-43209) <!--OKKKK-->
* Förbättrad säkerhet för webbprogram för att förhindra DDoS-attacker. (NEO-50757) <!--OKKKK-->
* Hanteringen av konsoliderade spårningsdata har förbättrats i **[!UICONTROL Consolidated tracking]** (nms:trackingStats) FFDA-tabell för att undvika dubbletter. (NEO-46409)
* Ett problem med en logisk operator i arbetsflödesfrågor när en användare användes har korrigerats `enableIf` i ett logiskt operatorvillkor. Det föregående logiska villkoret skrevs över. (NEO-45815)  <!--OKKKK-->
* Genereringen av aktiva profiler har optimerats i faktureringsarbetsflödet för att förbättra prestandan. (NEO-47658) <!--OKKKK-->
* Korrigerade ett problem med import av HTML-fil när bildnoder (img) innehöll URL:er med personaliseringsfält. (NEO-48396)
* Ett problem med Snowflake (alla distributioner) när sorteringsparametern i en **Dela** arbetsflödesaktivitet. (NEO-45899) <!--OKKKK-->
* Korrigerade ett problem som orsakade ett fel när en användare med läsbehörighet i mappen nmsDeliveryMapping försökte köra en kampanj eller ett arbetsflöde. (NEO-48230)
* Korrigerade ett prestandaproblem på fliken HTML för en leverans som kan uppstå för stor HTML-kod. (NEO-47440)
<!-- * Fixed an issue which could lead to a "Character set mismatch" error when using certain functions such as `to_nclob` with an Oracle unicode database where NChar was not enabled. (NEO-49361)
* Fixed an issue which prevented users from inserting a Time datatype in a **Data Update** workflow activity on MSSQL. (NEO-47763)-->
* Ett problem som hindrade användare från att använda **Sammanfoga markerade rader** arbetsflödesalternativ. (NEO-48488)
* Korrigerade ett fel på Snowflake FDA-anslutningen som ledde till att poster utelämnades när alternativet &quot;0 eller 1 enkel kardinalitetsanslutning&quot; användes under anrikningen. (NEO-48737)
* Återstående referenser till log4j-biblioteket har tagits bort från Campaign-installationen i Windows. (NEO-44851)
* Korrigerade ett problem som kan leda till ett fel när indikatorn **Mottagare som har öppnat** (estimatedRecipientOpen) lades till i ytterligare data för arbetsflödesaktiviteten **Fråga**. (NEO-46665)
* Hanteringen av spårnings-URL:er har förbättrats i arbetsflöden med flera leveranser för att förbättra prestandan. (NEO-50894) <!--OKKKK-->
* Korrigerade ett problem som kunde göra så att replikering av scheman som använder Xtkfolder misslyckades. (NEO-46787) <!--OKKKK-->
* Korrigerat en felorsak som kan göra att den anpassade kolumnen&quot;lastModified&quot; tas bort i NmsSubscription-tabellen. (NEO-48402)


>[!CAUTION]
>
> Uppgradering av klientkonsolen är obligatorisk. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../start/connect.md#upgrade-ac-console).
