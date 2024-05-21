---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
role: User
level: Beginner
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: 247d687597c6784aec49b70f9e68f50e49d169dd
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 5%

---

# Senaste versionen{#latest-release}

Adobe Campaign uppdateras regelbundet. Denna regelbundna uppdateringsfrekvens syftar till att få den senaste och bästa informationen i händerna, hålla miljön säker och förbättra din upplevelse av produkten. Adobe rekommenderar varmt alla kunder att uppgradera till den senaste versionen.

Som användare av hanterade Cloud Service uppgraderas instansen av Adobe med alla nya versioner. Adobe kommer att kontakta dig och uppgradera dina miljöer. Kampanjklientkonsol **måste uppgraderas till samma version** som kampanjservrar. Lär dig hur du uppgraderar din klientkonsol i den här [page](../start/connect.md#upgrade-ac-console).

Som kund bör du dessutom se till att du använder de senaste versionerna av de system som stöds i [Kompatibilitetsmatris](compatibility-matrix.md).

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

<!--
* **New Enhanced security add-on**: To make your network connection more secure and provide improved security for your resources, Adobe Campaign offers a new Enhanced security add-on, which includes two features: Secure CMK integration and Secure VPN tunneling.
-->

### Kompatibilitetsuppdateringar {#comp-8-7-1}

Databaser stöds nu som en extern databas med Adobe Campaign Federated Data Access (FDA). Läs mer [på den här sidan](compatibility-matrix.md#FederatedDataAccessFDA).

### Allmänna förbättringar {#improvements-8-7-1}

* Flera scheman har ändrats från 32 till 64 bitar. Detta gäller endast kunder som migrerar från Campaign Standard. [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/campaign/technotes/64-bit-tables.html){target="_blank"}

* I Campaign-tabeller fylls nu följande attribut i som standard med serverdatum och -tid: `lastModified` och `created`. Värden som tillhandahålls av användare i API-anrop ignoreras. <!--This configuration can be changed in the Campaign server configuration file. As a Managed Cloud Services customer, you must reach out to Adobe to change this default configuration.-->

### Korrigeringar {#fixes-8-7-1}

Följande problem har åtgärdats i den här versionen: NEO-72648, NEO-71534, NEO-71473, NEO-70263, NEO-70195, NEO-69651, NEO-68704, NEO-68192, NEO-67814, NEO-67702, NEO-67620, NEO-66022, NEO-65774, NEO-65633, NEO-641 99, NEO-63706, NEO-63705, NEO-63287, NEO-63197, NEO-62575, NEO-60250, NEO-60192, NEO-5 8596, NEO-58314, NEO-58004, NEO-40054

## Version 8.6.2 {#release-8-6-2}

_23 feb 2024_

### Korrigeringar {#fixes-8-6-2}

Den här versionen åtgärdar följande problem:

* Korrigerade ett prestandaproblem som kan uppstå på mellankällarinstansen (NEO-72595).

## Version 8.6.1 {#release-8-6-1}

_14 feb 2024_

### Nya funktioner {#new-8-6-1}

* Från och med den här versionen har du tillgång till den nya **Kampanjwebbgränssnitt** som finns i Adobe Experience Cloud centrala miljö. Experience Cloud är en integrerad familj av program, produkter och tjänster för digital marknadsföring i Adobe. Från det intuitiva gränssnittet får du snabbt tillgång till dina molnprogram, produktfunktioner och tjänster. Lär dig ansluta till Adobe Experience Cloud och få tillgång till Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui).


* Adobe Campaign v8 kan nu integreras med **Adobe Experience Manager as a Cloud Service**, med redigering som endast är tillgängligt via Adobe Campaign webbgränssnitt. [Läs mer](../connect/ac-aem.md)

* Nu kan du använda **Adobe Experience Manager Assets-bibliotek** tillsammans med dina Experience Cloud Assets, även om integreringen med Adobe Experience Cloud-paketet är installerat på din Adobe Campaign-instans. [Läs mer](../connect/ac-aem.md#assets-library)

### Allmänna förbättringar {#improvements-8-6-1}

* Campaign v8.6 ger bättre genomströmning för **spårningsindikatorer för e-postleveranser**. Tack vare våra optimerade processer minskas tiden för att spåra intag och beräkning, och ni kan kontrollera leveransnyckelindikatorerna mycket snabbare.


### Leveransuppdateringar {#deliverability-8-6-1}

* Senast i februari 2024 skickar alla företag över 5 000 e-postmeddelanden via Google eller Yahoo! måste börja använda en autentiseringsteknik som kallas domänbaserad Message Authentication Reporting and Conformance (DMARC). Se till att du har ställt in DMARC-posten för alla underdomäner som du använder med Adobe Campaign. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=sv){target="_blank"}

* Från 1 juni 2024, Google och Yahoo! att kräva att avsändarna följer One-Click List-Unsubscribe. Adobe Campaign har nu stöd för det här alternativet. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html#one-click-list-unsubscribe){target="_blank"}


### Korrigeringar {#fixes-8-6-1}

Följande problem har åtgärdats i den här versionen: NEO-67892, NEO-67235, NEO-66797, NEO-66462, NEO-65091, NEO-65036, NEO-64984, NEO-64680, NEO-63973, NEO-63879, NEO-63815, NEO-63657, NEO-63539, NEO-63387, NEO-632 94, NEO-63174, NEO-62964, NEO-62750, NEO-62686, NEO-62455, NEO-62406, NEO-61580, NEO-6 1199, NEO-60786, NEO-59544, NEO-59198, NEO-59059, NEO-58637, NEO-55197, NEO-52542, NEO O-50488, NEO-47789