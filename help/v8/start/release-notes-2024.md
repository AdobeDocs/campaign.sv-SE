---
title: Versionsinformation för Campaign v8 (konsol) 2023
description: Lista över funktioner och förbättringar i 2023 års Campaign v8-utgåvor
feature: Release Notes
exl-id: 6a0a9486-19a9-4ec3-9030-48dbf419f45f
source-git-commit: 69ef7e81d5fc0f5cf0dc74fa16d970ef89607331
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 4%

---

# Versionsinformation 2024 {#2024-rn}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **2024 Campaign v8-utgåvorna**.


## Version 8.6.2 {#release-8-6-2}

_23 feb 2024_

### Korrigeringar {#fixes-8-6-2}

Den här versionen åtgärdar följande problem:

* Korrigerade ett prestandaproblem som kan uppstå på mellankällarinstansen (NEO-72595).

## Version 8.6.1 {#release-8-6-1}

_14 feb 2024_

### Nya funktioner {#new-8-6-1}

* Från och med den här versionen har du tillgång till det nya **Campaign-webbgränssnittet** som är tillgängligt via den centrala Adobe Experience Cloud-miljön. Experience Cloud är en integrerad familj av program, produkter och tjänster för digital marknadsföring i Adobe. Från det intuitiva gränssnittet får du snabbt tillgång till dina molnprogram, produktfunktioner och tjänster. Lär dig hur du ansluter till Adobe Experience Cloud och kommer åt Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui).


* Adobe Campaign v8 kan nu integreras med **Adobe Experience Manager as a Cloud Service** och redigeringen är exklusivt tillgänglig via Adobe Campaign webbanvändargränssnitt. [Läs mer](../connect/ac-aem.md)

* Du kan nu använda ditt **Adobe Experience Manager Assets-bibliotek** tillsammans med din Experience Cloud Assets även om integreringen med Adobe Experience Cloud-paketet är installerat på din Adobe Campaign-instans. [Läs mer](../connect/ac-aem.md#assets-library)

### Allmänna förbättringar {#improvements-8-6-1}

* Campaign v8.6 ger förbättrad genomströmning för **spårningsindikatorer för e-postleveranser**. Tack vare våra optimerade processer minskas tiden för att spåra intag och beräkning, och ni kan kontrollera leveransnyckelindikatorerna mycket snabbare.


### Leveransuppdateringar {#deliverability-8-6-1}

* Senast i februari 2024 skickar alla företag över 5 000 e-postmeddelanden via Google eller Yahoo! måste börja använda en autentiseringsteknik som kallas domänbaserad Message Authentication Reporting and Conformance (DMARC). Se till att du har ställt in DMARC-posten för alla underdomäner som du använder med Adobe Campaign. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=sv){target="_blank"}

* Från 1 juni 2024, Google och Yahoo! att kräva att avsändarna följer One-Click List-Unsubscribe. Adobe Campaign har nu stöd för det här alternativet. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html#one-click-list-unsubscribe){target="_blank"}


### Korrigeringar {#fixes-8-6-1}

Följande problem har åtgärdats i den här versionen:

NEO-67892, NEO-67235, NEO-66797, NEO-66462, NEO-65091, NEO-65036, NEO-64984, NEO-646 80, NEO-63973, NEO-63879, NEO-63815, NEO-63657, NEO-63539, NEO-63387, NEO-63294, NEO-6 3174, NEO-62964, NEO-62750, NEO-62686, NEO-62455, NEO-62406, NEO-61580, NEO-61199, NEO O-60786, NEO-59544, NEO-59198, NEO-59059, NEO-58637, NEO-55197, NEO-52542, NEO-5048 8, NEO-47789
