---
title: Versionsinformation för Campaign v8 (konsol) 2025
description: Lista över funktioner och förbättringar i 2025 års Campaign v8-utgåvor
feature: Release Notes
exl-id: 3f91d83e-594e-49ee-a898-606e3de00bf3
source-git-commit: b52308bcbe68a7c382918fe28f8166e3bfcb6cde
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 14%

---

# Versionsinformation 2025 {#2025-rn}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **2025 Campaign v8-utgåvorna**. Den senaste versionen finns på [den här sidan](release-notes.md).

Installera [den senaste utgåvan](release-notes.md) för alla nya implementeringar eller uppgraderingar till en befintlig miljö.

>[!BEGINSHADEBOX]

**På den här sidan**

* [Version 8.6.5](#release-8-6-5)
* [Version 8.6.4](#release-8-6-4)
* [Version 8.7.4](#release-8-7-4)
* [Version 8.7.3](#release-8-7-3)


>[!ENDSHADEBOX]

## Version 8.6.5 {#release-8-6-5}

_25 april 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA).

### Nya funktioner {#features-8-6-5}

**Ny SMS-sändningsanslutare** - SMS-sändningsanslutaren har moderniserats och förbättrats för att aktivera SMPP-anslutningar i sändningsläge, aktivera beständiga SMPP-anslutningar och säkerställa bättre kompatibilitet för miljöer som övergår från Adobe Campaign Standard. Det finns nu ett nytt externt SMS-konto för alla nya SMS-implementeringar. Befintlig implementering stöds fortfarande, men vi rekommenderar att du går över till den nya moderna och utökade anslutningen. [Läs mer](../send/sms/sms.md).

### Allmänna förbättringar {#improvements-8-6-5}

* Programmets globala prestanda har förbättrats i samband med en Enterprise-distribution (FFDA), inklusive leverans- och databasrensning.

* För att öka säkerheten vid all kommunikation mellan program stöds nu mTLS för externa API-anrop.

* MTA (Mail Transfer Agent) – korrigerade ett överblivet MTA-underordnat element som ska ha statusen **[!UICONTROL Start pending]**.

### Korrigeringar {#fixes-8-6-5}

Följande problem har också korrigerats i den här versionen:

NEO-67620, NEO-71534, NEO-80245, NEO-81105, NEO-81758, NEO-81908, NEO-82351, NEO-82742, NEO-83044, NEO-83138, NEO-83350, NEO-83729, NEO-83793, NEO-83809, NEO-84038, NEO-84108, NEO-85269, NEO-86121, NEO-86556, NEO-86739

## Version 8.7.4 {#release-8-7-4}

_10 april 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som övergår till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/sv/docs/campaign-web/v8/start/acs-migration){target="_blank"}.

### Nya funktioner {#features-8-7-4}

* **Stöd för SMS REST API** - Transactional Messaging REST API är nu tillgängligt för SMS-kanalen. När både e-post och mobilePhone finns i nyttolasten kan du använda fältet&quot;önskekanal&quot; för att ange kanalen. Om det inte anges används e-post som standard, såvida inte önskadChannel uttryckligen begär SMS.

* **Flerspråkiga leveranser** - Från och med Campaign-webbanvändargränssnittet i april kan du skicka flera e-postleveranser på olika språk och få tillgång till relaterade dynamiska rapporter. Den här funktionen är bara tillgänglig i Adobe Campaign webbanvändargränssnitt i slutet av april och kräver en serveruppdatering till Campaign v8.7.4.

### Korrigeringar {#fixes-8-7-4}

Följande problem har åtgärdats i den här versionen:

NEO-80245, NEO-83559

## Version 8.7.3 {#release-8-7-3}

_14 feb 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som övergår till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/sv/docs/campaign-web/v8/start/acs-migration){target="_blank"}.

### Nya funktioner {#features-8-7-3}

* **Dynamisk rapportering för transaktionsmeddelanden** - Nu kan du övervaka dina transaktionsmeddelanden i gränssnittet för dynamisk rapportering. Dessa rapporter gör det möjligt för marknadsföraren att visa alla rapporteringsmått och dimensioner för transaktionsmeddelanden, uppdelning av leveranser som skickas via en mall i realtid. [Läs mer](https://experienceleague.adobe.com/docs/campaign-web/v8/reports/dynamic-reporting/get-started-reporting.html?lang=sv-SE){target="_blank"}

* **REST API:er för transaktionsmeddelanden** - händelsebaserade transaktions-API:er är nu tillgängliga för e-postmeddelanden. [Läs mer](../dev/api/get-started-apis.md)

### Korrigeringar {#fixes-8-7-3}

Följande problem har åtgärdats i den här versionen:

NEO-79373, NEO-81908, NEO-83081

## Version 8.6.4 {#release-8-6-4}

_15 januari 2025_

### Allmänna förbättringar {#improvements-8-6-4}

* Stabiliteten för kampanjprogram har förbättrats under leveransanalysen i samband med en [företagsdistribution (FFDA)](../../v8/architecture/enterprise-deployment.md).
* Den här versionen innehåller förbättrade och förbättrade FDA-arkitekturmekanismer, inklusive nyckelhantering, mellanlagring och datareplikering.
* Nya tekniska arbetsflöden har introducerats för [Enterprise (FFDA)-distributionen](../../v8/architecture/enterprise-deployment.md). Dessa arbetsflöden replikerar leverans och relaterade data genom att centralisera förfrågningar om parallell replikering i motsvarande tabeller. Arbetsflödet börjar med `Replicate nms`. [Läs mer](../architecture/replication.md)
* Ett nytt **Aktivera övervakningsansvarig för att hålla arbetsflödet igång permanent** är nu tillgängligt i arbetsflödesegenskaperna. När det här alternativet är aktiverat startar arbetsflödena automatiskt om efter att ett fel har inträffat. Omstarten sker var 30:e sekund som standard om arbetsflödet fortfarande är felfritt. Om du vill justera det här intervallet kan du skapa ett nytt `XtkWorkflow_WatchdogRestartTimerTimeout`-alternativ och ange datatypen Integer för att ange den nya fördröjningen. Det här alternativet bör endast aktiveras i tekniska arbetsflöden. [Läs mer](../../automation/workflow/workflow-properties.md#execution)

### Säkerhetsförbättringar {#security-8-6-4}

Anslutningen till lösningar och appar från Adobe via det externa **[!UICONTROL Adobe Experience Cloud]**-kontot har uppdaterats för att stärka säkerheten.

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

