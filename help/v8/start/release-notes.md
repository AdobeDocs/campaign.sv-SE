---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: c6b4f4cee6f033218c77a495c39885e231c06126
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 1%

---

# Senaste releaser {#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i Campaign v8 (konsol) **de senaste versionerna**. Läs mer om Campaign-versioner, -versioner och -uppgraderingar på [den här sidan](upgrades.md). Andra versioner listas i avsnittet Tidigare versioner i den här dokumentationen.

>[!BEGINSHADEBOX]

**På den här sidan**

* Campaign v8.6 - [Version 8.6.4](#release-8-6-4)
* Campaign v8.7 - [Version 8.7.3](#release-8-7-3)

>[!ENDSHADEBOX]


## Version 8.7.3 {#release-8-7-3}

_14 feb 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som en Campaign Standard-användare som går över till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"}.

### Nya funktioner {#features-8-7-3}

* **Dynamisk rapportering för transaktionsmeddelanden** - Nu kan du övervaka dina transaktionsmeddelanden i gränssnittet för dynamisk rapportering. Dessa rapporter gör det möjligt för marknadsföraren att visa alla rapporteringsmått och dimensioner för transaktionsmeddelanden, uppdelning av leveranser som skickas via en mall i realtid. [Läs mer](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/reporting/get-started-reporting){target="_blank"}

* **REST API:er för transaktionsmeddelanden** - händelsebaserade transaktions-API:er är nu tillgängliga för e-postmeddelanden. [Läs mer](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/apis/managing-transactional-messages){target="_blank"}

### Korrigeringar {#fixes-8-7-3}

Följande problem har åtgärdats i den här versionen:

NEO-79373, NEO-81908, NEO-83081.


## Version 8.6.4 {#release-8-6-4}

_15 januari 2025_

### Allmänna förbättringar {#improvements-8-6-4}

* Stabiliteten för kampanjprogram har förbättrats under leveransanalysen i samband med en [företagsdistribution (FFDA)](../../v8/architecture/enterprise-deployment.md).
* Den här versionen innehåller förbättrade och förbättrade FDA-arkitekturmekanismer, inklusive nyckelhantering, mellanlagring och datareplikering.
* Nya tekniska arbetsflöden har introducerats för [Enterprise (FFDA)-distributionen](../../v8/architecture/enterprise-deployment.md). Dessa arbetsflöden replikerar leverans och relaterade data genom att centralisera förfrågningar om parallell replikering i motsvarande tabeller. Arbetsflödet börjar med `Replicate nms`. [Läs mer](../architecture/replication.md)
* Ett nytt **Aktivera övervakningsansvarig för att hålla arbetsflödet igång permanent** är nu tillgängligt i arbetsflödesegenskaperna. När det här alternativet är aktiverat startar arbetsflödena automatiskt om efter att ett fel har inträffat. Omstarten sker var 30:e sekund som standard om arbetsflödet fortfarande är felfritt. Om du vill justera det här intervallet kan du skapa ett nytt `XtkWorkflow_WatchdogRestartTimerTimeout`-alternativ och ange datatypen Integer för att ange den nya fördröjningen. Det här alternativet bör endast aktiveras i tekniska arbetsflöden. [Läs mer](../../automation/workflow/workflow-properties.md#execution)

### Säkerhetsförbättringar {#security-8-6-4}

Anslutningen till Adobe lösningar och appar via det externa **[!UICONTROL Adobe Experience Cloud]**-kontot har uppdaterats för att stärka säkerheten.

<!--
### Connection to Campaign {#ims-8-6-4}

**(Limited availability)** For a restricted list of customers, Campaign v8.6.4 can allow native authentication mode instead of Adobe Identity Management System (IMS). Note that if you are using Campaign native authentication, you cannot access to [Campaign Web User Interface](../start/campaign-ui.md#campaign-web-user-interface).-->

### Kompatibilitetsuppdateringar {#comp-8-6-4}

Följande FDA-anslutningar har lagts till. Se den här [sidan](compatibility-matrix.md#FederatedDataAccessFDA).

* Databaser stöds nu som en extern databas med Adobe Campaign Federated Data Access (FDA).

* Nu finns en ny Amazon Redshift FDA ODBC-anslutning. Det ger bättre anslutningsmöjligheter, enklare underhåll och förbättrad kompatibilitet. Den nya versionen innehåller följande förbättringar:

   * Den nya anslutningen baseras på ODBC-gränssnittet som är anpassat till våra senaste FDA-anslutningar. Detta garanterar långsiktig support.
   * Dessutom introduceras en ny datainläsningsmekanism som använder s3-bucket, vilket avsevärt förbättrar prestandan.

  Den gamla kopplingen kan fortfarande användas. Om du vill prova den nya bör du kontakta Adobe.

### Korrigeringar {#fixes-8-6-4}

Följande problem har åtgärdats i den här versionen:

NEO-48232, NEO-67814, NEO-71388, NEO-74855, NEO-75643, NEO-75962, NEO-76132, NEO-769 58, NEO-76986, NEO-77162, NEO-77452, NEO-78946, NEO-79373, NEO-80243, NEO-80314, NEO-8 1127, NEO-81209, NEO-81223, NEO-81287, NEO-81290, NEO-81312, NEO-81512, NEO-81520 O-81566, NEO-81704, NEO-81908, NEO-82195, NEO-82591, NEO-82592, NEO-82640, NEO-8266 5, NEO-82781, NEO-82920, NEO-83081, NEO-83096, NEO-83137, NEO-83143.

