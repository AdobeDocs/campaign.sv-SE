---
title: Versionsinformation för Campaign v8 (konsol) 2025
description: Lista över funktioner och förbättringar i 2025 års Campaign v8-utgåvor
feature: Release Notes
exl-id: 3f91d83e-594e-49ee-a898-606e3de00bf3
source-git-commit: ff874a8e06303625b4c96f49fdf4f303b50fb908
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 6%

---

# Versionsinformation 2025 {#2025-rn}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **2025 Campaign v8-utgåvorna**. De senaste versionerna visas på [den här sidan](release-notes.md).

## Version 8.7.3 {#release-8-7-3}

_14 feb 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som övergår till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration).

### Nya funktioner {#features-8-7-3}

* **Dynamisk rapportering för transaktionsmeddelanden** - Nu kan du övervaka dina transaktionsmeddelanden i gränssnittet för dynamisk rapportering. Dessa rapporter gör det möjligt för marknadsföraren att visa alla rapporteringsmått och dimensioner för transaktionsmeddelanden, uppdelning av leveranser som skickas via en mall i realtid. [Läs mer](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/reporting/get-started-reporting)

* **REST API:er för transaktionsmeddelanden** - händelsebaserade transaktions-API:er är nu tillgängliga för e-postmeddelanden. [Läs mer](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/apis/managing-transactional-messages)

### Korrigeringar {#fixes-8-7-3}

Följande problem har åtgärdats i den här versionen:

NEO-79373, NEO-81908, NEO-83081

## Version 8.7.2 {#release-8-7-2}

_3 sept 2024_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som övergår till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration).

### Nya funktioner {#new-8-7-2}

* **Ny SMS-sändningsanslutare** - SMS-sändningsanslutaren har moderniserats och förbättrats för att aktivera SMPP-anslutningar i sändningsläge, aktivera beständiga SMPP-anslutningar och säkerställa bättre kompatibilitet för miljöer som övergår från Adobe Campaign Standard. Det finns nu ett nytt externt SMS-konto för alla nya SMS-implementeringar. Befintlig implementering stöds fortfarande, men vi rekommenderar att du går över till den nya moderna och utökade anslutningen. [Läs mer](../send/sms/sms.md).

* **Rich Push Notification (GA)** - Du kan nu skicka omfattande push-meddelanden. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. I den här versionen finns det nu en uppsättning mallar för push-meddelanden för dina iOS- och Android-appar. [Läs mer](../send/rich-push-android.md).

* **Varumärkning** - Det finns nu märkningsalternativ för alla kanaler, inklusive SMS och direktreklam. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/branding/branding-gs.html)

### Korrigeringar {#fixes-8-7-2}

Följande problem har åtgärdats i den här versionen:

NEO-48232, NEO-56832, NEO-72504, NEO-74855, NEO-75898, NEO-76097, NEO-76958, NEO-770 14, NEO-77795, NEO-78843, NEO-79328
