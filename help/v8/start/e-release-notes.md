---
title: Versionsinformation om tidig kampanj v8
description: Tidig Campaign v8-version
feature: Release Notes
role: User
level: Beginner
hide: true
hidefromtoc: true
exl-id: a45f7b22-44c7-4dad-af0a-ae8f683ae3d9
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 5%

---

# Tidig versionsinformation {#e-new-release}

Den här sidan beskriver de förbättringar och korrigeringar som ingår i nästa Campaign v8-utgåva. Innehållet kan ändras utan föregående meddelande fram till releasedatum. Den officiella versionsinformationen finns här [page](../start/release-notes.md).

## Version 8.6.1 {#release-8-6-1}

_14 feb 2024_


### Nya funktioner {#new-8-6-1}

* Från och med den här versionen har du tillgång till den nya **Kampanjwebbgränssnitt** som finns i Adobe Experience Cloud centrala miljö. Experience Cloud är en integrerad familj av program, produkter och tjänster för digital marknadsföring i Adobe. Från det intuitiva gränssnittet får du snabbt tillgång till dina molnprogram, produktfunktioner och tjänster. Lär dig ansluta till Adobe Experience Cloud och få tillgång till Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui).

* 32-bitarsversionen av klientkonsolen är nu inaktuell. Från och med 8.6 är klientkonsolen endast tillgänglig med 64 bitar. Uppgraderingen till 64-bitarsversionen av klientkonsolen är smidig. Mer information om hur du uppgraderar ditt operativsystem finns i [technote](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/console.html){target="_blank"}.


### Allmänna förbättringar {#improvements-8-6-1}

* Campaign v8.6 ger bättre genomströmning för **spårningsindikatorer för e-postleveranser**. Tack vare våra optimerade processer minskas tiden för att spåra intag och beräkning, och ni kan kontrollera leveransnyckelindikatorerna mycket snabbare.

* Nu kan du ansluta Campaign v8-instansen till din externa Azure synapse-databas. Den här anslutningen hanteras via ett nytt externt konto.

* Adobe Campaign v8 kan nu integreras med **Adobe Experience Manager as a Cloud Service**, med redigering som endast är tillgängligt via Adobe Campaign webbgränssnitt.

* Nu kan du använda **Adobe Experience Manager Assets-bibliotek** tillsammans med Experience Cloud Assets även om **Integrering med Adobe Experience Cloud** paketet installeras på din Adobe Campaign-instans.

* Du kan inte längre skapa operatorer från klientkonsolen. Nu måste du använda Admin Console. [Läs mer](../start/gs-permissions.md).

* Flera tredjepartsverktyg har uppdaterats för att optimera säkerheten.

### Leveransuppdateringar {#deliverability-8-6-1}

* Senast i februari 2024 skickar alla företag över 5 000 e-postmeddelanden via Google eller Yahoo! måste börja använda en autentiseringsteknik som kallas domänbaserad Message Authentication Reporting and Conformance (DMARC). Se till att du har ställt in DMARC-posten för alla underdomäner som du använder med Adobe Campaign. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=sv){target="_blank"}

* Från 1 juni 2024, Google och Yahoo! att kräva att avsändarna följer One-Click List-Unsubscribe. Adobe Campaign har nu stöd för det här alternativet. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html#one-click-list-unsubscribe){target="_blank"}


### Korrigeringar {#fixes-8-6-1}

Följande problem har åtgärdats i den här versionen: NEO-67892, NEO-67235, NEO-66797, NEO-66462, NEO-65091, NEO-65036, NEO-64984, NEO-64680, NEO-63973, NEO-63879, NEO-63815, NEO-63657, NEO-63539, NEO-63387, NEO-632 94, NEO-63174, NEO-62964, NEO-62750, NEO-62686, NEO-62455, NEO-62406, NEO-61580, NEO-6 1199, NEO-60786, NEO-59544, NEO-59198, NEO-59059, NEO-58637, NEO-55197, NEO-52542, NEO O-50488, NEO-47789