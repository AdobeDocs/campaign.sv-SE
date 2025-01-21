---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: 4a4bcb0b540d6e8a426839e77bf81ad30eb93653
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 3%

---

# Senaste releaser {#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i Campaign v8 (konsol) **de senaste versionerna**. Läs mer om Campaign-versioner, -versioner och -uppgraderingar på [den här sidan](upgrades.md). Andra versioner listas i avsnittet Tidigare versioner i den här dokumentationen.

## Version 8.6.4 {#release-8-6-4}

_15 januari 2025_

### Allmänna förbättringar {#improvements-8-6-4}

* Stabiliteten för kampanjprogram har förbättrats under leveransanalysen i samband med en [företagsdistribution (FFDA)](../../v8/architecture/enterprise-deployment.md).
* Den här versionen innehåller förbättrade och förbättrade FDA-arkitekturmekanismer, inklusive nyckelhantering, mellanlagring och datareplikering.
* Nya tekniska arbetsflöden har introducerats för [Enterprise (FFDA)-distributionen](../../v8/architecture/enterprise-deployment.md). Dessa arbetsflöden replikerar leverans och relaterade data genom att centralisera förfrågningar om parallell replikering i motsvarande tabeller. Arbetsflödet börjar med `Replicate nms`. [Läs mer](../architecture/replication.md)
* Ett nytt **Aktivera övervakningsansvarig för att hålla arbetsflödet igång permanent** är nu tillgängligt i arbetsflödesegenskaperna. När det här alternativet är aktiverat startar arbetsflödena automatiskt om efter att ett fel har inträffat. Omstarten sker var 30:e sekund som standard om arbetsflödet fortfarande är felfritt. Om du vill justera det här intervallet kan du skapa ett nytt `XtkWorkflow_WatchdogTimerTimeout`-alternativ och ange datatypen Integer för att ange den nya fördröjningen. Det här alternativet bör endast aktiveras i tekniska arbetsflöden. [Läs mer](../../automation/workflow/workflow-properties.md#execution)

### Säkerhetsförbättringar {#security-8-6-4}

Anslutningen till lösningar och appar från Adobe via det externa **[!UICONTROL Adobe Experience Cloud]**-kontot har uppdaterats för att stärka säkerheten.

<!--
### Connection to Campaign {#ims-8-6-4}

**(Limited availability)** For a restricted list of customers, Campaign v8.6.4 can allow native authentication mode instead of Adobe Identity Management System (IMS). Note that if you are using Campaign native authentication, you cannot access to [Campaign Web User Interface](../start/campaign-ui.md#campaign-web-user-interface).-->

### Kompatibilitetsuppdateringar {#comp-8-6-4}

Databaser stöds nu som en extern databas med Adobe Campaign Federated Data Access (FDA). Läs mer [på den här sidan](compatibility-matrix.md#FederatedDataAccessFDA).

### Korrigeringar {#fixes-8-6-4}

Följande problem har åtgärdats i den här versionen:

NEO-48232, NEO-67814, NEO-71388, NEO-74855, NEO-75643, NEO-75962, NEO-76132, NEO-769 58, NEO-76986, NEO-77162, NEO-77452, NEO-78946, NEO-79373, NEO-80243, NEO-80314, NEO-8 1127, NEO-81209, NEO-81223, NEO-81287, NEO-81290, NEO-81312, NEO-81512, NEO-81520 O-81566, NEO-81704, NEO-81908, NEO-82195, NEO-82591, NEO-82592, NEO-82640, NEO-8266 5, NEO-82781, NEO-82920, NEO-83081, NEO-83096, NEO-83137, NEO-83143.

## Version 8.7.2 {#release-8-7-2}

_3 sept 2024_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som användare av Campaign Standarden som går över till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"}.

### Nya funktioner {#new-8-7-2}

* **Ny SMS-sändningsanslutare** - SMS-sändningsanslutaren har moderniserats och förbättrats för att aktivera SMPP-anslutningar i sändningsläge, aktivera beständiga SMPP-anslutningar och säkerställa bättre kompatibilitet för miljöer som övergår från Adobe Campaign Standard. Det finns nu ett nytt externt SMS-konto för alla nya SMS-implementeringar. Befintlig implementering stöds fortfarande, men vi rekommenderar att du går över till den nya moderna och utökade anslutningen. [Läs mer](../send/sms/sms.md).

* **Rich Push Notification (GA)** - Du kan nu skicka omfattande push-meddelanden. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. I den här versionen finns det nu en uppsättning mallar för push-meddelanden för dina iOS- och Android-appar. [Läs mer](../send/rich-push-android.md).

* **Varumärkning** - Det finns nu märkningsalternativ för alla kanaler, inklusive SMS och direktreklam. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/branding/branding-gs.html){target="_blank"}

### Korrigeringar {#fixes-8-7-2}

Följande problem har åtgärdats i den här versionen:

NEO-48232, NEO-56832, NEO-72504, NEO-74855, NEO-75898, NEO-76097, NEO-76958, NEO-770 14, NEO-77795, NEO-78843, NEO-79328