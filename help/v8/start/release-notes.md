---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: 0b4fc6da8761d2efe57d8eb0ff87cd11d0e2d250
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 15%

---

# Senaste releaser {#latest-release}

Adobe Campaign uppdateras regelbundet. Denna regelbundna uppdateringsfrekvens syftar till att få den senaste och bästa informationen i händerna, hålla miljön säker och förbättra din upplevelse av produkten. Adobe rekommenderar varmt alla kunder att uppgradera till den senaste versionen. Den här sidan innehåller nya funktioner, förbättringar och korrigeringar som ingår i de senaste versionerna av Campaign v8 (konsol). Läs mer om Campaign-versioner och -uppdateringar på [den här sidan](upgrades.md).

Som användare av hanterade Cloud Service uppgraderas instansen av Adobe med alla nya versioner. Adobe kommer att kontakta dig och uppgradera dina miljöer. Kampanjklientkonsolen **måste uppgraderas till samma version** som Campaign-servrar. Lär dig hur du uppgraderar din klientkonsol på [den här sidan](../start/connect.md#upgrade-ac-console).

Som kund ska du dessutom kontrollera att du använder de senaste versionerna av systemen som stöds i [kompatibilitetsmatrisen](compatibility-matrix.md).



## Version 8.6.3 {#release-8-6-3}

_30 juli 2024_

### Nya funktioner {#new-8-6-3}

* **Rich Push Notification** - Du kan nu skicka omfattande push-meddelanden. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. I den här versionen finns det nu en uppsättning mallar för push-meddelanden för dina iOS- och Android-appar. [Läs mer](../send/rich-push-android.md).

* Från och med den här versionen, med servicekontot (JWT) som inte längre används av Adobe, förlitar sig Campaign utgående integrationer med Adobes lösningar och appar nu på OAuth Server-to-Server-autentiseringsuppgift. [Läs mer](release-notes.md#change-8-7-1)

### Allmänna förbättringar {#improvements-8-6-3}

* För att öka säkerheten vid all kommunikation mellan program stöds nu mTLS för externa API-anrop.

### Korrigeringar {#fixes-8-6-3}

Följande problem har åtgärdats i den här versionen:

NEO-79328, NEO-78843, NEO-77795, NEO-77014, NEO-76958, NEO-76097, NEO-75898, NEO-725 4, NEO-70263, NEO-67620, NEO-63197, NEO-58596, NEO-56832.

<!--
https://jira.corp.adobe.com/issues/?filter=585288&jql=fixVersion%20%3D%208.6.3%20AND%20type%20not%20in%20(epic%2C%20test%2C%20sub-task%2C%20Roadmap)%20AND%20resolution%20!%3D%20unresolved%20AND%20%22Fixed%20in%20Build%22%20is%20not%20EMPTY%20and%20type%20in%20(%22customer%20request%22)
-->


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
