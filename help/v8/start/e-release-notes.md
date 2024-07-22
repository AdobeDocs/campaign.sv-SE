---
title: Versionsinformation om tidig kampanj v8
description: Tidig Campaign v8-version
feature: Release Notes
role: User
level: Beginner
hide: true
hidefromtoc: true
exl-id: a45f7b22-44c7-4dad-af0a-ae8f683ae3d9
source-git-commit: 65efda7469c5ad35e8d03703951c3d1480b015f4
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 8%

---

# Tidig versionsinformation {#e-new-release}

Den här sidan beskriver de förbättringar och korrigeringar som ingår i nästa Campaign v8-utgåva. **Noteringar om tidig version nedan kan ändras utan föregående meddelande till releasedatum**. Länkar, skärmar och uppdaterad dokumentation publiceras i [versionsinformationen](release-notes.md) på releasedatum.

## Version 8.7.2 {#release-8-7-2}

_30 juli 2024_


>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som användare av Campaign Standarden som går över till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/release-notes/acs-migration){target="_blank"}.

### Nya funktioner {#new-8-7-2}

* **Ny SMS-sändningsanslutare** - SMS-sändningsanslutaren har moderniserats och förbättrats för att aktivera SMPP-anslutningar i sändningsläge, aktivera beständiga SMPP-anslutningar och säkerställa bättre kompatibilitet för miljöer som övergår från Adobe Campaign Standard. Det finns nu ett nytt externt SMS-konto för alla nya SMS-implementeringar. Befintlig implementering stöds fortfarande, men vi rekommenderar att du går över till den nya moderna och utökade anslutningen.

* **Rich Push Notification (GA)** - Du kan nu skicka omfattande push-meddelanden. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. I den här versionen finns det nu en uppsättning mallar för push-meddelanden för dina iOS- och Android-appar. [Läs mer](../send/rich-push.md).

* **Varumärkning** - Det finns nu märkningsalternativ för alla kanaler, inklusive SMS och direktreklam. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/branding/branding-gs.html){target="_blank"}


### Korrigeringar {#fixes-8-7-2}

Följande problem har åtgärdats i den här versionen:

NEO-76592, NEO-75400, NEO-77406, NEO-77674, NEO-77899, NEO-73989, NEO-76064, NEO-760 39, NEO-76040, NEO-76845, NEO-7664, NEO-76682, NEO-76663, NEO-73602, NEO-72915, NEO-7 8134, NEO-77000, NEO-77002, NEO-76955, NEO-76864, NEO-76926, NEO-76495, NEO-77168 O-41058, NEO-75581, NEO-74647, NEO-74585, NEO-74586, NEO-74831, NEO-77319, NEO-7860 7.

## Version 8.6.3 {#release-8-6-3}

_30 juli 2024_

### Nya funktioner {#new-8-6-3}

* **Rich Push Notification** - Du kan nu skicka omfattande push-meddelanden. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. I den här versionen finns det nu en uppsättning mallar för push-meddelanden för dina iOS- och Android-appar. [Läs mer](../send/rich-push.md).

* Från och med den här versionen, med servicekontot (JWT) som inte längre används av Adobe, förlitar sig Campaign utgående integrationer med Adobes lösningar och appar nu på OAuth Server-to-Server-autentiseringsuppgift. [Läs mer](release-notes.md#change-8-7-1)

### Allmänna förbättringar {#improvements-8-6-3}

* För att öka säkerheten vid all kommunikation mellan program stöds nu mTLS för externa API-anrop.

### Korrigeringar {#fixes-8-6-3}

Följande problem har åtgärdats i den här versionen:

NEO-77014, NEO-76958, NEO-76097, NEO-75898, NEO-72504, NEO-70263, NEO-67620, NEO-631 97, NEO-58596, NEO-56832.

<!--
https://jira.corp.adobe.com/issues/?filter=585288&jql=fixVersion%20%3D%208.6.3%20AND%20type%20not%20in%20(epic%2C%20test%2C%20sub-task%2C%20Roadmap)%20AND%20resolution%20!%3D%20unresolved%20AND%20%22Fixed%20in%20Build%22%20is%20not%20EMPTY%20and%20type%20in%20(%22customer%20request%22)
-->