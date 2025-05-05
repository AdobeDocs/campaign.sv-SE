---
title: Versionsinformation för Campaign v8 (konsol) 2025
description: Lista över funktioner och förbättringar i 2025 års Campaign v8-utgåvor
feature: Release Notes
exl-id: 3f91d83e-594e-49ee-a898-606e3de00bf3
source-git-commit: 66e4b59915eae595b28076622f7bcfb5b5a0ffa4
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 6%

---

# Versionsinformation 2025 {#2025-rn}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **2025 Campaign v8-utgåvorna**. De senaste versionerna visas på [den här sidan](release-notes.md).

>[!BEGINSHADEBOX]

**På den här sidan**

* Campaign v8.7 - [Version 8.7.2](#release-8-7-2) | [Version 8.7.3](#release-8-7-3)


>[!ENDSHADEBOX]


## Version 8.7.3 {#release-8-7-3}

_14 feb 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Det är begränsat till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som övergår till Campaign v8 kan du läsa mer om den här övergången i dokumentationen[&#128279;](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"} för webbanvändargränssnittet i Campaign v8.

### Nya funktioner {#features-8-7-3}

* **Dynamisk rapportering för transaktionsmeddelanden** - Nu kan du övervaka dina transaktionsmeddelanden i gränssnittet för dynamisk rapportering. Dessa rapporter gör det möjligt för marknadsföraren att visa alla rapporteringsmått och dimensioner för transaktionsmeddelanden, uppdelning av leveranser som skickas via en mall i realtid. [Läs mer](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/reporting/get-started-reporting){target="_blank"}

* **REST API:er för transaktionsmeddelanden** - händelsebaserade transaktions-API:er är nu tillgängliga för e-postmeddelanden. [Läs mer](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/apis/managing-transactional-messages){target="_blank"}

### Korrigeringar {#fixes-8-7-3}

Följande problem har åtgärdats i den här versionen:

NEO-79373, NEO-81908, NEO-83081

## Version 8.7.2 {#release-8-7-2}

_Den 3 september 2024_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Det är begränsat till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som övergår till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"}.

### Nya funktioner {#new-8-7-2}

* **Ny SMS-sändningsanslutare** - SMS-sändningsanslutaren har moderniserats och förbättrats för att aktivera SMPP-anslutningar i sändningsläge, aktivera beständiga SMPP-anslutningar och säkerställa bättre kompatibilitet för miljöer som övergår från Adobe Campaign Standard. Det finns nu ett nytt externt SMS-konto för alla nya SMS-implementeringar. Befintlig implementering stöds fortfarande, men vi rekommenderar att du går över till den nya moderna och utökade anslutningen. [Läs mer](../send/sms/sms.md).

* **Rich Push Notification (GA)** - Du kan nu skicka omfattande push-meddelanden. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. I den här versionen finns det nu en uppsättning mallar för push-meddelanden för dina iOS- och Android-appar. [Läs mer](../send/rich-push-android.md).

* **Branding** - Branding-alternativ är nu tillgängliga för alla kanaler, inklusive SMS och direktreklam. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/branding/branding-gs.html){target="_blank"}

### Korrigeringar {#fixes-8-7-2}

Följande problem åtgärdas i den här versionen:

NEO-48232, NEO-56832, NEO-72504, NEO-74855, NEO-75898, NEO-76097, NEO-76958, NEO-770 14, NEO-77795, NEO-78843, NEO-79328
