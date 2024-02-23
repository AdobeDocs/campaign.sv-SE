---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
role: User
level: Beginner
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: 3b790305984436f1168f9c73aa09df509b2217f0
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 2%

---

# Senaste versionen{#latest-release}

Adobe Campaign uppdateras regelbundet. Denna regelbundna uppdateringsfrekvens syftar till att få den senaste och bästa informationen i händerna, hålla miljön säker och förbättra din upplevelse av produkten. Adobe rekommenderar varmt alla kunder att uppgradera till den senaste versionen. Läs mer om Campaign-versioner och rekommendationer [på den här sidan](upgrades.md).

Som användare av hanterade Cloud Service uppgraderas instansen av Adobe med alla nya versioner. Adobe kommer att kontakta dig och uppgradera dina miljöer. Kampanjklientkonsol **måste uppgraderas till samma version** som kampanjservrar. Lär dig hur du uppgraderar din klientkonsol i den här [page](../start/connect.md#upgrade-ac-console).

Som kund bör du dessutom se till att du använder de senaste versionerna av de system som stöds i [Kompatibilitetsmatris](compatibility-matrix.md).


## Version 8.6.2 {#release-8-6-2}

_23 feb 2024_

### Korrigeringar {#fixes-8-6-2}

Den här versionen åtgärdar följande problem:

* Korrigerade ett prestandaproblem som kan uppstå på mellankällarinstansen (NEO-72595).

## Version 8.6.1 {#release-8-6-1}

_14 feb 2024_

### Nya funktioner {#new-8-6-1}

* Från och med den här versionen har du tillgång till den nya **Kampanjwebbgränssnitt** som finns i Adobe Experience Cloud centrala miljö. Experience Cloud är en integrerad familj av program, produkter och tjänster för digital marknadsföring i Adobe. Från det intuitiva gränssnittet får du snabbt tillgång till dina molnprogram, produktfunktioner och tjänster. Lär dig ansluta till Adobe Experience Cloud och få tillgång till Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui).


* Adobe Campaign v8 kan nu integreras med **Adobe Experience Manager as a Cloud Service**, med redigering som endast är tillgängligt via Adobe Campaign webbgränssnitt. [Läs mer](../connect/ac-aem.md)

* Nu kan du använda **Adobe Experience Manager Assets-bibliotek** tillsammans med dina Experience Cloud Assets, även om integreringen med Adobe Experience Cloud-paketet är installerat på din Adobe Campaign-instans. [Läs mer](../connect/ac-aem.md#assets-library)

### Allmänna förbättringar {#improvements-8-6-1}

* Campaign v8.6 ger bättre genomströmning för **spårningsindikatorer för e-postleveranser**. Tack vare våra optimerade processer minskas tiden för att spåra intag och beräkning, och ni kan kontrollera leveransnyckelindikatorerna mycket snabbare.


### Leveransuppdateringar {#deliverability-8-6-1}

* Senast i februari 2024 skickar alla företag över 5 000 e-postmeddelanden via Google eller Yahoo! måste börja använda en autentiseringsteknik som kallas domänbaserad Message Authentication Reporting and Conformance (DMARC). Se till att du har ställt in DMARC-posten för alla underdomäner som du använder med Adobe Campaign. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=sv){target="_blank"}

* Från 1 juni 2024, Google och Yahoo! kommer att kräva att avsändarna följer One-Click List-Unsubscribe. Adobe Campaign har nu stöd för det här alternativet. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html#one-click-list-unsubscribe){target="_blank"}


### Korrigeringar {#fixes-8-6-1}

Följande problem har åtgärdats i den här versionen: NEO-67892, NEO-67235, NEO-66797, NEO-66462, NEO-65091, NEO-65036, NEO-64984, NEO-64680, NEO-63973, NEO-63879, NEO-63815, NEO-63657, NEO-63539, NEO-63387, NEO-632 94, NEO-63174, NEO-62964, NEO-62750, NEO-62686, NEO-62455, NEO-62406, NEO-61580, NEO-6 1199, NEO-60786, NEO-59544, NEO-59198, NEO-59059, NEO-58637, NEO-55197, NEO-52542, NEO O-50488, NEO-47789