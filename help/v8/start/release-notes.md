---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: e119c415ce363a635f9f0318e3fd70f90f4bde06
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 4%

---

# Senaste releaser {#latest-release}

Adobe Campaign uppdateras regelbundet. Denna regelbundna uppdateringsfrekvens syftar till att få den senaste och bästa informationen i händerna, hålla miljön säker och förbättra din upplevelse av produkten. Adobe rekommenderar varmt alla kunder att uppgradera till den senaste versionen. Den här sidan innehåller nya funktioner, förbättringar och korrigeringar som ingår i de senaste versionerna av Campaign v8 (konsol). Läs mer om Campaign-versioner och uppdateringar i [den här sidan](upgrades.md).

Som användare av hanterade Cloud Service uppgraderas instansen av Adobe med alla nya versioner. Adobe kommer att kontakta dig och uppgradera dina miljöer. Kampanjklientkonsol **måste uppgraderas till samma version** som kampanjservrar. Lär dig hur du uppgraderar din klientkonsol i [den här sidan](../start/connect.md#upgrade-ac-console).

Som kund bör du dessutom se till att du använder de senaste versionerna av de system som stöds i [Kompatibilitetsmatris](compatibility-matrix.md).

## Version 8.5.3 {#release-8-5-3}

_28 maj 2024_

### Migrering till autentiseringsuppgifter för OAuth Server-till-Server {#change-8-5-3}

Från och med den här versionen, med JWT-autentiseringsuppgifter (Service Account) borttaget av Adobe, är Campaign-integreringar med Adobe-lösningar och appar nu beroende av autentiseringsuppgifter för OAuth Server-till-Server. [Läs mer](#change-8-7-1)

### Korrigeringar {#fixes-8-5-3}

Följande problem har åtgärdats i den här versionen:

NEO-70263, NEO-64984, NEO-63657, NEO-63387, NEO-62964, NEO-62750, NEO-62686, NEO-595 44, NEO-52542


## Maj-uppdateringar {#may-updates}

Följande ändring har släppts i maj och är nu tillgänglig för användare av Campaign v8:

* **Nytt tillägg för Förbättrat skydd**: För att göra nätverksanslutningen säkrare och ge bättre säkerhet för dina resurser erbjuder Adobe Campaign ett nytt tillägg för Förbättrat skydd, som innehåller två funktioner: säker CMK-integrering och säker VPN-tunnel. [Läs mer](../config/enhanced-security.md)


## Version 8.7.1 {#release-8-7-1}

_2 maj 2024_

>[!AVAILABILITY]
>
>Den här versionen finns i **Begränsad tillgänglighet** (LA). Den är begränsad till kunder som migrerar **från Adobe Campaign Standard till Adobe Campaign v8** och kan inte distribueras i någon annan miljö.
>
>Som Campaign Standard-användare som går över till Campaign v8 får du veta mer om övergången i [Dokumentation för webbgränssnittet i Campaign v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/release-notes/acs-migration){target="_blank"}.

### Nya funktioner {#new-8-7-1}

* **Mallar för push-meddelanden** - Du kan nu skicka omfattande push-meddelanden via Android. Rich push notification är en förbättrad form av mobilmeddelanden som går utöver enkla textmeddelanden genom att införliva multimediaelement som bilder, interaktiva knappar eller annat multimediematerial. [Läs mer](../send/rich-push.md).

* **Varumärke** - Som en Campaign Standard migrerad användare kan era tekniska administratörer nu definiera ett eller flera varumärken för att centralisera de parametrar som påverkar ett varumärkes identitet. Detta inkluderar logotypen, domänen för landningssidans åtkomst-URL eller inställningar för meddelandespårning. Du kan skapa dessa varumärken och länka dem till meddelanden eller landningssidor. Den här konfigurationen hanteras i mallar. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/branding/branding-gs.html){target="_blank"}

* **Övriga API:er** - Som användare med migrerad Campaign Standard kan du använda de övriga API:erna för att skapa integreringar för Adobe Campaign och bygga ett eget ekosystem genom att interagera med Adobe Campaign med den tekniska panel som du använder. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/apis/get-started-apis.html){target="_blank"}

* **Dynamisk rapportering** - Som användare med migrerad Campaign Standard har ni tillgång till Dynamic Reporting, som tillhandahåller fullt anpassningsbara realtidsrapporter för att mäta effekten av era marknadsföringsaktiviteter. Det ger åtkomst till profildata, vilket möjliggör demografiska analyser efter profildimensioner som kön, ort och ålder, utöver funktionella e-postkampanjdata som öppningar och klick. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/reporting/get-started-reporting.html){target="_blank"}




### Kompatibilitetsuppdateringar {#comp-8-7-1}

* Databaser stöds nu som en extern databas med Adobe Campaign Federated Data Access (FDA). Läs mer [på den här sidan](compatibility-matrix.md#FederatedDataAccessFDA).

### Migrering till autentiseringsuppgifter för OAuth Server-till-Server {#change-8-7-1}

Från och med den här versionen, med JWT-autentiseringsuppgifter (Service Account) borttaget av Adobe, är Campaign-integreringar med Adobe-lösningar och appar nu beroende av autentiseringsuppgifter för OAuth Server-till-Server. Adobe kommer att genomföra migreringen från JWT till OAuth för dina utgående integreringar, som integrering med Campaign-Analytics eller integrering med Experience Cloud Triggers.

Om du har implementerat inkommande integreringar med Campaign måste du migrera ditt tekniska konto enligt informationen i [den här dokumentationen](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/){target="_blank"}. Befintliga JWT-referenser (Service Account) fortsätter att fungera tills **27 januari 2025**. Dessutom kommer Developer Console att ha fortsatt stöd för att skapa nya JWT-autentiseringsuppgifter (Service Account) tills **3 juni 2024**. Det går inte att skapa eller lägga till en ny JWT-autentiseringsuppgift (Service Account) i ett projekt efter detta datum.


### Allmänna förbättringar {#improvements-8-7-1}

* Flera scheman har ändrats från 32 till 64 bitar. Detta gäller endast kunder som migrerar från Campaign Standard. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/technotes/64-bit-tables.html){target="_blank"}

* I Campaign-tabeller fylls nu följande attribut i som standard med serverdatum och -tid: `lastModified` och `created`. The `createdBy-id` attributvärdet fylls nu i med aktuellt inloggnings-ID som standard. Värden som tillhandahålls av användare i API-anrop ignoreras. <!--This configuration can be changed in the Campaign server configuration file. As a Managed Cloud Services customer, you must reach out to Adobe to change this default configuration.-->

### Korrigeringar {#fixes-8-7-1}

Följande problem har åtgärdats i den här versionen: NEO-72648, NEO-71534, NEO-71473, NEO-70263, NEO-70195, NEO-69651, NEO-68704, NEO-68192, NEO-67814, NEO-67702, NEO-67620, NEO-66022, NEO-65774, NEO-65633, NEO-641 99, NEO-63706, NEO-63705, NEO-63287, NEO-63197, NEO-62575, NEO-60250, NEO-60192, NEO-5 8596, NEO-58314, NEO-58004, NEO-40054
