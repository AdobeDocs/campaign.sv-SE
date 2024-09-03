---
title: Versionsinformation för Campaign v8 (konsol) 2023
description: Lista över funktioner och förbättringar i 2023 års Campaign v8-utgåvor
feature: Release Notes
exl-id: 6a0a9486-19a9-4ec3-9030-48dbf419f45f
source-git-commit: 07e0bfdade0356eedb24641259aa754fdb1c6155
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 12%

---

# Versionsinformation 2024 {#2024-rn}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **2024 Campaign v8-utgåvorna**.



## Version 8.5.3 {#release-8-5-3}

_28 maj 2024_

### Migrering till autentiseringsuppgifter för OAuth Server-till-Server {#change-8-5-3}

Från och med den här versionen, med servicekontot (JWT) som inte längre används av Adobe, förlitar sig Campaign utgående integrationer med Adobes lösningar och appar nu på OAuth Server-to-Server-autentiseringsuppgift. [Läs mer](#change-8-7-1)

### Korrigeringar {#fixes-8-5-3}

Följande problem har åtgärdats i den här versionen:

NEO-70263, NEO-64984, NEO-63657, NEO-63387, NEO-62964, NEO-62750, NEO-62686, NEO-595 44, NEO-52542


## Maj-uppdateringar {#may-updates}

Följande ändring har släppts i maj och är nu tillgänglig för användare av Campaign v8:

* **Nytt tillägg för Förbättrat skydd**: För att göra nätverksanslutningen säkrare och ge bättre säkerhet för dina resurser erbjuder Adobe Campaign ett nytt tillägg för Förbättrat skydd, som innehåller två funktioner: Skyddad CMK-integrering och Säker VPN-tunnel. [Läs mer](../config/enhanced-security.md)


## Version 8.7.1 {#release-8-7-1}

_2 maj 2024_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som användare av Campaign Standarden som går över till Campaign v8 kan du läsa mer om den här övergången i [dokumentationen för webbanvändargränssnittet för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/release-notes/acs-migration){target="_blank"}.

### Nya funktioner {#new-8-7-1}

* **Mallar för push-meddelanden** - Du kan nu skicka omfattande push-meddelanden via Android. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. [Läs mer](../send/rich-push-ios.md).

* **Varumärke** - Som en Campaign Standard migrerad användare kan teknikadministratörer nu definiera ett eller flera varumärken för att centralisera parametrarna som påverkar ett varumärkes identitet. Detta inkluderar logotypen, domänen för landningssidans åtkomst-URL eller inställningar för meddelandespårning. Du kan skapa dessa varumärken och länka dem till meddelanden eller landningssidor. Den här konfigurationen hanteras i mallar. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/branding/branding-gs.html){target="_blank"}

* **Övriga API:er** - Som Campaign Standard migrerad användare kan du använda Rest API:er för att skapa integreringar för Adobe Campaign och skapa ett eget ekosystem genom att interagera med Adobe Campaign med den panel med tekniker som du använder. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/apis/get-started-apis.html){target="_blank"}

* **Dynamisk rapportering** - Som Campaign Standard migrerad användare kan du få tillgång till Dynamic Reporting som tillhandahåller fullt anpassningsbara realtidsrapporter för att mäta effekten av dina marknadsföringsaktiviteter. Det ger åtkomst till profildata, vilket möjliggör demografiska analyser efter profildimensioner som kön, ort och ålder, utöver funktionella e-postkampanjdata som öppningar och klick. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/reporting/get-started-reporting.html){target="_blank"}

### Kompatibilitetsuppdateringar {#comp-8-7-1}

* Databaser stöds nu som en extern databas med Adobe Campaign Federated Data Access (FDA). Läs mer [på den här sidan](compatibility-matrix.md#FederatedDataAccessFDA).

### Migrering till autentiseringsuppgifter för OAuth Server-till-Server {#change-8-7-1}

Från och med den här versionen, med servicekontot (JWT) som inte längre används av Adobe, förlitar sig Campaign utgående integrationer med Adobes lösningar och appar nu på OAuth Server-to-Server-autentiseringsuppgift. Adobe utför migreringen från JWT till OAuth för dina utgående integrationer, till exempel Campaign-Analytics-integration eller Experience Cloud Triggers-integration.

Om du har implementerat inkommande integreringar med Campaign måste du migrera ditt tekniska konto enligt beskrivningen i [den här dokumentationen](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/){target="_blank"}. Befintliga JWT-autentiseringsuppgifter (Service Account) fortsätter att fungera till den **27 januari 2025**.

### Allmänna förbättringar {#improvements-8-7-1}

* Flera scheman har ändrats från 32 till 64 bitar. Detta gäller endast kunder som migrerar från Campaign Standard. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/technotes/64-bit-tables.html){target="_blank"}

* I Campaign-tabeller fylls nu följande attribut i som standard med serverdatum och -tid: `lastModified` och `created`. Attributvärdet `createdBy-id` fylls nu i med det aktuella inloggnings-ID:t som standard. Värden som tillhandahålls av användare i API-anrop ignoreras. <!--This configuration can be changed in the Campaign server configuration file. As a Managed Cloud Services customer, you must reach out to Adobe to change this default configuration.-->

* För att öka säkerheten vid all kommunikation mellan program stöds nu mTLS för externa API-anrop.

### Korrigeringar {#fixes-8-7-1}

Följande problem har åtgärdats i den här versionen:

NEO-72648, NEO-71534, NEO-71473, NEO-70263, NEO-70195, NEO-69651, NEO-68704, NEO-681 92, NEO-67814, NEO-67702, NEO-67620, NEO-66022, NEO-65774, NEO-65633, NEO-64199, NEO-6 3706, NEO-63705, NEO-63287, NEO-63197, NEO-62575, NEO-60250, NEO-60192, NEO-58596, NEO O-58314, NEO-58004, NEO-40054


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

* Senast i februari 2024 skickar alla företag över 5 000 e-postmeddelanden via Google eller Yahoo! måste börja använda en autentiseringsteknik som kallas domänbaserad Message Authentication Reporting och Conformance (DMARC). Se till att du har ställt in DMARC-posten för alla underdomäner som du använder med Adobe Campaign. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=sv){target="_blank"}

* Från 1 juni 2024, Google och Yahoo! att kräva att avsändarna följer One-Click List-Unsubscribe. Adobe Campaign har nu stöd för det här alternativet. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html#one-click-list-unsubscribe){target="_blank"}


### Korrigeringar {#fixes-8-6-1}

Följande problem har åtgärdats i den här versionen:

NEO-67892, NEO-67235, NEO-66797, NEO-66462, NEO-65091, NEO-65036, NEO-64984, NEO-646 80, NEO-63973, NEO-63879, NEO-63815, NEO-63657, NEO-63539, NEO-63387, NEO-63294, NEO-6 3174, NEO-62964, NEO-62750, NEO-62686, NEO-62455, NEO-62406, NEO-61580, NEO-61199, NEO O-60786, NEO-59544, NEO-59198, NEO-59059, NEO-58637, NEO-55197, NEO-52542, NEO-5048 8, NEO-47789
