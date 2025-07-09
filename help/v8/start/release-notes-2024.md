---
title: Versionsinformation för Campaign v8 (konsol) 2024
description: Lista över funktioner och förbättringar i 2024 års Campaign v8-utgåvor
feature: Release Notes
exl-id: 6a0a9486-19a9-4ec3-9030-48dbf419f45f
source-git-commit: b52308bcbe68a7c382918fe28f8166e3bfcb6cde
workflow-type: tm+mt
source-wordcount: '1568'
ht-degree: 12%

---

# Versionsinformation 2024 {#2024-rn}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **2024 Campaign v8-utgåvorna**. Den senaste versionen finns på [den här sidan](release-notes.md).

Installera [den senaste utgåvan](release-notes.md) för alla nya implementeringar eller uppgraderingar till en befintlig miljö.


>[!BEGINSHADEBOX]

**På den här sidan**

* Campaign v8.7 - [Version 8.7.1](#release-8-7-1) | [Version 8.7.2](#release-8-7-2)
* Campaign v8.6 - [Version 8.6.1](#release-8-6-1) | [Version 8.6.2](#release-8-6-2) | [Version 8.6.3](#release-8-6-3)
* Campaign v8.5 - [Version 8.5.3](#release-8-5-3)

>[!ENDSHADEBOX]

## Version 8.7.2 {#release-8-7-2}

_3 sept 2024_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som övergår till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/sv/docs/campaign-web/v8/start/acs-migration){target="_blank"}.

### Nya funktioner {#new-8-7-2}

* **Ny SMS-sändningsanslutare** - SMS-sändningsanslutaren har moderniserats och förbättrats för att aktivera SMPP-anslutningar i sändningsläge, aktivera beständiga SMPP-anslutningar och säkerställa bättre kompatibilitet för miljöer som övergår från Adobe Campaign Standard. Det finns nu ett nytt externt SMS-konto för alla nya SMS-implementeringar. Befintlig implementering stöds fortfarande, men vi rekommenderar att du går över till den nya moderna och utökade anslutningen. [Läs mer](../send/sms/sms.md).

* **Rich Push Notification (GA)** - Du kan nu skicka omfattande push-meddelanden. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. I den här versionen finns det nu en uppsättning mallar för push-meddelanden för dina iOS- och Android-appar. [Läs mer](../send/rich-push-android.md).

* **Varumärkning** - Det finns nu märkningsalternativ för alla kanaler, inklusive SMS och direktreklam. [Läs mer](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html){target="_blank"}

### Korrigeringar {#fixes-8-7-2}

Följande problem har åtgärdats i den här versionen:

NEO-48232, NEO-56832, NEO-72504, NEO-74855, NEO-75898, NEO-76097, NEO-76958, NEO-77014, NEO-7 7795, NEO-78843, NEO-79328.

## Version 8.7.1 {#release-8-7-1}

_2 maj 2024_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som övergår till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/sv/docs/campaign-web/v8/start/acs-migration){target="_blank"}.

### Nya funktioner {#new-8-7-1}

* **Mallar för push-meddelanden** - Du kan nu skicka omfattande push-meddelanden via Android. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. [Läs mer](../send/rich-push-ios.md).

* **Varumärke** - Som en migrerad Campaign Standard-användare kan teknikadministratörer nu definiera ett eller flera varumärken för att centralisera parametrarna som påverkar ett varumärkes identitet. Detta inkluderar logotypen, domänen för landningssidans åtkomst-URL eller inställningar för meddelandespårning. Du kan skapa dessa varumärken och länka dem till meddelanden eller landningssidor. Den här konfigurationen hanteras i mallar. [Läs mer](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html){target="_blank"}

* **Övriga API:er** - Som en Campaign Standard-migrerad användare kan du använda Rest API:er för att skapa integreringar för Adobe Campaign och skapa ett eget ekosystem genom att interagera med Adobe Campaign med den panel med tekniker som du använder. [Läs mer](../dev/api/get-started-apis.md)

* **Dynamisk rapportering** - Som migrerad Campaign Standard-användare har du tillgång till Dynamic Reporting som tillhandahåller fullt anpassningsbara realtidsrapporter för att mäta effekten av dina marknadsföringsaktiviteter. Det ger åtkomst till profildata, vilket möjliggör demografiska analyser efter profildimensioner som kön, ort och ålder, utöver funktionella e-postkampanjdata som öppningar och klick. [Läs mer](https://experienceleague.adobe.com/docs/campaign-web/v8/reports/dynamic-reporting/get-started-reporting.html){target="_blank"}

### Kompatibilitetsuppdateringar {#comp-8-7-1}

Följande FDA-anslutningar har lagts till. Se den här [sidan](compatibility-matrix.md#FederatedDataAccessFDA).

* Databaser stöds nu som en extern databas med Adobe Campaign Federated Data Access (FDA).

* Nu finns en ny Amazon Redshift FDA ODBC-anslutning. Det ger bättre anslutningsmöjligheter, enklare underhåll och förbättrad kompatibilitet. Den nya versionen innehåller följande förbättringar:

   * Den nya anslutningen baseras på ODBC-gränssnittet som är anpassat till våra senaste FDA-anslutningar. Detta garanterar långsiktig support.
   * Dessutom introduceras en ny datainläsningsmekanism som använder s3-bucket, vilket avsevärt förbättrar prestandan.

  Den gamla kopplingen kan fortfarande användas. Om du vill prova den nya bör du kontakta Adobe.

### Migrering till autentiseringsuppgifter för OAuth Server-till-Server {#change-8-7-1}

Från och med den här versionen, med servicekontot (JWT) som inte längre används av Adobe, förlitar sig Campaign utgående integrationer med Adobes lösningar och appar nu på OAuth Server-to-Server-autentiseringsuppgift. Adobe utför migreringen från JWT till OAuth för dina utgående integrationer, till exempel Campaign-Analytics-integration eller Experience Cloud Triggers-integration.

Om du har implementerat inkommande integreringar med Campaign måste du migrera ditt tekniska konto enligt beskrivningen i [den här dokumentationen](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/){target="_blank"}. Befintliga JWT-autentiseringsuppgifter (Service Account) fortsätter att fungera till den **30 juni 2025**.

### Allmänna förbättringar {#improvements-8-7-1}

* Flera scheman har ändrats från 32 till 64 bitar. Detta gäller endast kunder som migrerar från Campaign Standard. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/technotes/64-bit-tables.html?lang=sv-SE){target="_blank"}

* I Campaign-tabeller fylls nu följande attribut i som standard med serverdatum och -tid: `lastModified` och `created`. Attributvärdet `createdBy-id` fylls nu i med det aktuella inloggnings-ID:t som standard. Värden som tillhandahålls av användare i API-anrop ignoreras. <!--This configuration can be changed in the Campaign server configuration file. As a Managed Cloud Services customer, you must reach out to Adobe to change this default configuration.-->

* För att öka säkerheten vid all kommunikation mellan program stöds nu mTLS för externa API-anrop.

### Korrigeringar {#fixes-8-7-1}

Följande problem har åtgärdats i den här versionen:

NEO-72648, NEO-71534, NEO-71473, NEO-70263, NEO-70195, NEO-69651, NEO-68704, NEO-68192, NEO-66 7814, NEO-67702, NEO-67620, NEO-66022, NEO-65774, NEO-65633, NEO-64199, ¹-63706, båge-637 05, periodisering-63287, periodisering-63197, periodisering-62575, periodisering-60250, periodisering-60192, periodisering-58596, budg-58004 båge-40054



## Version 8.6.3 {#release-8-6-3}

_30 juli 2024_

### Nya funktioner {#new-8-6-3}

* **Rich Push Notification** - Du kan nu skicka omfattande push-meddelanden. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. I den här versionen finns det nu en uppsättning mallar för push-meddelanden för dina iOS- och Android-appar. [Läs mer](../send/rich-push-android.md).

* Från och med den här versionen, med servicekontot (JWT) som inte längre används av Adobe, förlitar sig Campaign utgående integrationer med Adobes lösningar och appar nu på OAuth Server-to-Server-autentiseringsuppgift. [Läs mer](release-notes-2024.md#change-8-7-1)

### Allmänna förbättringar {#improvements-8-6-3}

* För att öka säkerheten vid all kommunikation mellan program stöds nu mTLS för externa API-anrop.

### Korrigeringar {#fixes-8-6-3}

Följande problem har åtgärdats i den här versionen:

NEO-79328, NEO-78843, NEO-77795, NEO-77014, NEO-76958, NEO-76097, NEO-75898, NEO-72504, NEO-7 0263, NEO-67620, NEO-63197, NEO-58596, NEO-56832.

<!--
https://jira.corp.adobe.com/issues/?filter=585288&jql=fixVersion%20%3D%208.6.3%20AND%20type%20not%20in%20(epic%2C%20test%2C%20sub-task%2C%20Roadmap)%20AND%20resolution%20!%3D%20unresolved%20AND%20%22Fixed%20in%20Build%22%20is%20not%20EMPTY%20and%20type%20in%20(%22customer%20request%22)
-->


## Uppdateringar 24 maj {#may-updates}

Följande ändring har släppts i maj och är nu tillgänglig för användare av Campaign v8:

* **Nytt tillägg för Förbättrat skydd**: För att göra nätverksanslutningen säkrare och ge bättre säkerhet för dina resurser erbjuder Adobe Campaign ett nytt tillägg för Förbättrat skydd, som innehåller två funktioner: Skyddad CMK-integrering och Säker VPN-tunnel. [Läs mer](../config/enhanced-security.md)

## Version 8.6.2 {#release-8-6-2}

_23 feb 2024_

### Korrigeringar {#fixes-8-6-2}

Den här versionen åtgärdar följande problem:

* Korrigerade ett prestandaproblem som kan uppstå på mellankällarinstansen (NEO-72595).

## Version 8.6.1 {#release-8-6-1}

_14 feb 2024_

### Nya funktioner {#new-8-6-1}

* Från och med den här versionen har du tillgång till det nya **Campaign-webbgränssnittet** som är tillgängligt via den centrala Adobe Experience Cloud-miljön. Experience Cloud är Adobe integrerade program, produkter och tjänster för digital marknadsföring. Från det intuitiva gränssnittet får du snabbt tillgång till dina molnprogram, produktfunktioner och tjänster. Lär dig hur du ansluter till Adobe Experience Cloud och kommer åt Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui).

  >[!AVAILABILITY]
  >
  >Användargränssnittet för Campaign-webben är bara tillgängligt för användare som ansluter till Adobe Campaign med sin Adobe ID. Läs mer om [Adobe Identity Management System (IMS)](https://helpx.adobe.com/se/enterprise/using/identity.html){target="_blank"}.
  >

* Adobe Campaign v8 kan nu integreras med **Adobe Experience Manager as a Cloud Service** och redigeringen är exklusivt tillgänglig via Adobe Campaign webbanvändargränssnitt. [Läs mer](../connect/ac-aem.md)

* Du kan nu använda ditt **Adobe Experience Manager Assets-bibliotek** tillsammans med din Experience Cloud Assets även om integreringen med Adobe Experience Cloud-paketet är installerat på din Adobe Campaign-instans. [Läs mer](../connect/ac-aem.md#assets-library)

### Allmänna förbättringar {#improvements-8-6-1}

* Campaign v8.6 ger förbättrad genomströmning för **spårningsindikatorer för e-postleveranser**. Tack vare våra optimerade processer minskas tiden för att spåra intag och beräkning, och ni kan kontrollera leveransnyckelindikatorerna mycket snabbare.


### Leveransuppdateringar {#deliverability-8-6-1}

* Senast i februari 2024 skickar alla företag över 5 000 e-postmeddelanden via Google eller Yahoo! måste börja använda en autentiseringsteknik som kallas domänbaserad Message Authentication Reporting och Conformance (DMARC). Se till att du har ställt in DMARC-posten för alla underdomäner som du använder med Adobe Campaign. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=sv){target="_blank"}

* Från 1 juni 2024, Google och Yahoo! att kräva att avsändarna följer One-Click List-Unsubscribe. Adobe Campaign har nu stöd för det här alternativet. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=sv-SE#list-unsubscribe){target="_blank"}


### Korrigeringar {#fixes-8-6-1}

Följande problem har åtgärdats i den här versionen:

NEO-67892, NEO-67235, NEO-66797, NEO-66462, NEO-65091, NEO-65036, NEO-64984, NEO-64680, NEO-6 3973, NEO-63879, NEO-63815, NEO-63657, NEO-63539, NEO-63387, NEO-63294, ¹-63174, bud-629 64, periodisering-62750, periodisering-62686, periodisering-62455, periodisering-62406, 61580, periodisering-61199, budgivning-60786, periodisering-554, bådafrikansk-59198, periodiserings-59059, periodiserings-58637, periodiserings-55197, budg-52542, 2013-30 32



## Version 8.5.3 {#release-8-5-3}

_28 maj 2024_

### Migrering till autentiseringsuppgifter för OAuth Server-till-Server {#change-8-5-3}

Från och med den här versionen, med servicekontot (JWT) som inte längre används av Adobe, förlitar sig Campaign utgående integrationer med Adobes lösningar och appar nu på OAuth Server-to-Server-autentiseringsuppgift. [Läs mer](#change-8-7-1)

### Korrigeringar {#fixes-8-5-3}

Följande problem har åtgärdats i den här versionen:

NEO-70263, NEO-64984, NEO-63657, NEO-63387, NEO-62964, NEO-62750, NEO-62686, NEO-59544, NEO-5 2542