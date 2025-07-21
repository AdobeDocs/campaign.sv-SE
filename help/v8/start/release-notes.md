---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: 5c5d19c9b9b413bb630a4e5738c6697d2341665a
workflow-type: tm+mt
source-wordcount: '2170'
ht-degree: 7%

---

# Senaste releaser {#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i Campaign v8 (konsol) **de senaste versionerna**. Läs mer om Campaign-versioner, -versioner och -uppgraderingar på [den här sidan](upgrades.md). Andra versioner listas i avsnittet Tidigare versioner i den här dokumentationen.

## Version 8.8.1 {#release-8-8-1}

_9 juli 2025_

### Nya funktioner {#features-8-8-1}

Tidigare släppt för en liten uppsättning kunder är följande funktioner nu tillgängliga för alla Campaign FDA-miljöer:

* **Ny SMS-sändningsanslutare** - SMS-sändningsanslutaren har moderniserats och förbättrats för att aktivera SMPP-anslutningar i sändningsläge, aktivera beständiga SMPP-anslutningar och säkerställa bättre kompatibilitet. Det finns nu ett nytt externt SMS-konto för alla nya SMS-implementeringar. Befintlig implementering stöds fortfarande, men vi rekommenderar att du går över till den nya moderna och utökade anslutningen. [Läs mer](../send/sms/sms.md)

  >[!NOTE]
  >
  >Den här funktionen är **inte** tillgänglig för [Campaign FFDA-distributioner](../architecture/enterprise-deployment.md).

<!-- (from ACC rn, aleady in the product, to remove?) -->

<!-- * **Enrichment in transactional messages** (to remove?) -->

<!--
* **Multilingual delivery creation** in the Web UI - You can now send multiple email deliveries in different languages in Adobe Campaign Web User Interface. The Multilingual delivery feature allows you to choose the default language of your delivery as well as the different languages in which the delivery can be sent. You can also preview these deliveries in the languages you have chosen. [Read more](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/email/edit-content.html)

ACC - Multilingual deliveries - Starting Campaign Web User interface April release, you will be able to send multiple email deliveries in different languages, and access the related dynamic reports. This capability will only be available in Adobe Campaign Web User Interface at the end of April, and require a server update to Campaign v8.7.4.
-->

<!--
*  **Visual fragments** in the Web UI - You can now create, use and archive content fragments. Visual fragments are pre-defined visual blocks that you can reuse across multiple email deliveries, or in content templates. [Learn more](https://experienceleague.adobe.com/docs/campaign-web/v8/content/manage-reusable-content/fragments/fragments.html){target="_blank"}

(already available in console and web, to remove?) 
web - * Visual fragments - You can now archive visual content fragments. Learn more
-->

<!--
* **Delivery alerting** in the Web UI - The Delivery alerting feature is an alert management system that enables a group of users to automatically receive notifications containing information on the execution of their deliveries. [Read more](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/delivery-alerting/delivery-alerting.html){target="_blank"}
-->

<!--
* **Landing pages improvements**  in the Web UI- The following improvements to landing pages are now available:

    * You can now reference a default subscription/unsubscription landing page when configuring a service. When designing an email, if you define a link to that landing page, users submitting the landing page form are automatically subscribed to or unsubscribed from this service. [Read more](https://experienceleague.adobe.com/docs/campaign-web/v8/audiences/work-with-services/manage-services.html#create-service){target="_blank"}
    * A new option in the landing page configuration allows anonymous visitors to access the landing page. If you unselect this option, only identified users can access and submit the form. [Read more](https://experienceleague.adobe.com/docs/campaign-web/v8/landing-pages/create-lp.html#create-landing-page){target="_blank"}
    * A new option in the landing page configuration allows to store additional internal data when the landing page is being submitted. [Read more](https://experienceleague.adobe.com/docs/campaign-web/v8/landing-pages/create-lp.html#create-landing-page){target="_blank"}
    * A new option enables to use a landing page for several services, making it dynamic. When adding a link to an email, if you select a dynamic landing page, you can select any service. If you select a landing page that has a specific service associated, this service will be automatically used (you cannot select another one). [Read more](https://experienceleague.adobe.com/docs/campaign-web/v8/landing-pages/create-lp.html#define-actions-on-form-submission){target="_blank"}
    * Conditional content is now supported in landing pages. [Read more](https://experienceleague.adobe.com/docs/campaign-web/v8/landing-pages/lp-content.html){target="_blank"}
    * You can link a landing page to a service, and send a confirmation message when users validate it. [Learn more](https://experienceleague.adobe.com/docs/campaign-web/v8/landing-pages/lp-content.html#lp-message){target="_blank"}
    * You can add captcha to protect your landing page from spam and abuse caused by bots. This is non-intrusive for your customers since it does not require any interaction from them and is based on interactions with your site. [Learn more](https://experienceleague.adobe.com/docs/campaign-web/v8/landing-pages/create-lp.html#captcha){target="_blank"}

web - * **Subscriptions with Landing pages** - You can now link a landing page to a service, and send a confirmation message when users validate it. [Learn more](../landing-pages/lp-content.md#lp-message){target="_blank"}.
Web - * **Captcha in landing pages** - You can now add captcha to protect your landing page from spam and abuse caused by bots. This is non-intrusive for your customers since it does not require any interaction from them and is based on interactions with your site. [Learn more](../landing-pages/create-lp.md#captcha)
-->

<!--
* (from ACC rn, already in product, to remove?) **Rich Push Notification (GA)** - You can now send rich push notifications. Rich push notification is an enhanced form of mobile notification that goes beyond simple text messages by incorporating multimedia elements such as images, interactive buttons, or other rich media content. With this version, a set of templates for rich push notifications are now available for your iOS and Android apps. [Read more](../send/rich-push-android.md). 
ACC * Rich Push Notification templates - You can now send rich push notifications via Android. Rich push notification is an enhanced form of mobile notification that goes beyond simple text messages by incorporating multimedia elements such as images, interactive buttons, or other rich media content. Read more.
-->

Tidigare släppt i Begränsad tillgänglighet är följande funktion nu tillgänglig **på begäran**:

<!--
* **Dynamic Reporting** - You can now access Dynamic Reporting which provides fully customizable and real-time reports to measure the impact of your marketing activities. It adds access to profile data, enabling demographic analysis by profile dimensions such as gender, city and age in addition to functional email campaign data like opens and clicks. Dynamic reporting is also available for multilingual email deliveries and transactional messages. [Read more](https://experienceleague.adobe.com/docs/experience-cloud/campaign/reporting/get-started-reporting.html){target="_blank"}

ACC **Dynamic Reporting for Transactional messages** - You can now monitor your transactional messages in the Dynamic Reporting user interface. These reports provide the ability to the marketer to view the all the reporting metrics and dimensions of transactional messages, breakdown of deliveries sent through a template in real time. [Read more](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/reporting/get-started-reporting){target="_blank"}
ACC - Dynamic Reporting - As a Campaign Standard migrated user, you can access Dynamic Reporting which provides fully customizable and real-time reports to measure the impact of your marketing activities. It adds access to profile data, enabling demographic analysis by profile dimensions such as gender, city and age in addition to functional email campaign data like opens and clicks. Read more
* **Dynamic Reporting for Multilingual** - Dynamic reporting is now available for multilingual email deliveries. For more information, refer to the [detailed documentation](../reporting/global-reports.md).
-->

* **Övriga API:er** - Nu kan du använda Rest API:er för att skapa integreringar för Adobe Campaign och skapa ett eget ekosystem genom att interagera med Adobe Campaign med den panel med tekniker som du använder. Transactional Messaging REST API är också tillgängligt för SMS-kanalen. När både e-post och mobilePhone finns i nyttolasten kan du använda fältet&quot;önskekanal&quot; för att ange kanalen. Om det inte anges används e-post som standard, såvida inte önskadChannel uttryckligen begär SMS. Händelsebaserade transaktions-API:er är också tillgängliga för e-postmeddelanden. [Läs mer](../dev/api/get-started-apis.md)

  >[!NOTE]
  >
  >Den här funktionen är **inte** tillgänglig för [Campaign FFDA-distributioner](../architecture/enterprise-deployment.md).

<!--
ACC - Rest APIs - As a Campaign Standard migrated user, you can use Rest APIs to create integrations for Adobe Campaign and build your own ecosystem by interfacing Adobe Campaign with the panel of technologies that you use. Read more
* **SMS REST API support (LA)** - The Transactional Messaging REST API is now available for the SMS channel. When both email and mobilePhone are present in the payload, you can use the "wishedChannel" field to specify the channel. If not provided, email will be used by default unless wishedChannel explicitly requests SMS. For more information, refer to the [detailed documentation](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/apis/managing-transactional-messages){target=_blank}.
ACC - SMS REST API support - The Transactional Messaging REST API is now available for the SMS channel. When both email and mobilePhone are present in the payload, you can use the "wishedChannel" field to specify the channel. If not provided, email will be used by default unless wishedChannel explicitly requests SMS.
ACC * **Transactional messaging REST APIs** - Event-based Transactional APIs are now available for Emails. [Read more](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/apis/managing-transactional-messages){target="_blank"}
-->

Utöver funktionerna som listas ovan innehåller den här versionen även en uppsättning funktioner som är tillgängliga i användargränssnittet för Campaign-webben:

* [Skapa flerspråkig leverans](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/email/edit-content.html#multilingual-delivery){target="_blank"}
* [Leveransvarning](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/delivery-alerting/delivery-alerting.html){target="_blank"}
* [Förbättringar av landningssidor](https://experienceleague.adobe.com/docs/campaign-web/v8/landing-pages/get-started-lp.html){target="_blank"}
* [Dynamisk rapportering](https://experienceleague.adobe.com/docs/campaign-web/v8/reports/dynamic-reporting/get-started-reporting.html){target="_blank"} (på begäran)
* [Centraliserad profilering](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html){target="_blank"} (on demand, nya implementeringar)

Se versionsinformationen för Campaign Web UI [](https://experienceleague.adobe.com/docs/campaign-web/v8/release-notes/release-notes.html){target="_blank"}

### Allmänna förbättringar {#improvements-8-8-1}

* Microsoft Fabrics stöds nu som en extern databas med Adobe Campaign Federated Data Access (FDA). [Läs mer](../config/external-accounts.md#transfer-data-external-accounts)
* Campaign v8 har nu stöd för Android 15 och iOS 18 för push-meddelanden. [Läs mer](../start/compatibility-matrix.md#MobileSDK)
* Molndatabaser stöds nu utöver lokala databaser för säker tunnling med virtuella privata nätverk. [Läs mer](../config/enhanced-security.md#vpn-databases)
* En ny uppsättning med &quot;Provider ID&quot;-fält har lagts till i avsnittet &quot;Inkommande trafik&quot; i SMS 2.0-kopplingen. [Läs mer](../send/sms/smpp-external-account.md#incoming-traffic)
* Mottagare som avbeställer prenumerationen genom metoden&quot;mailto&quot; List-Unsubscribe skickas inte längre till karantänen. De avbeställer tjänsten som är kopplad till leveransen, eller skickas till blockeringslista (profilens&quot;Ingen längre kontakt&quot;-avsnitt) om ingen tjänst har definierats för leveransen. [Läs mer](../send/quarantines.md)
* En omgjord version av rapporten för inkorgsåtergivning finns nu tillgänglig i Adobe Campaign klientkonsol. [Läs mer](../send/inbox-rendering.md)
* Filen `setup-client.exe` har ersatts med en `ac-client.msi`-fil, vilket ger en enklare metod för administratörer att utföra massuppgraderingar utan att användaren behöver göra något.

### Korrigeringar {#fixes-8-8-1}

* Ett problem har korrigerats där autosvar inte togs emot på grund av en ogiltig giltighetsperiod i SMS 2.0. Detta garanterar korrekt meddelandeleverans efter migrering. (NEO-88088)
* Ett problem i SMS 2.0 där vissa fält i tabellen `inSms` inte uppdaterades korrekt har åtgärdats, vilket säkerställer korrekt infogning av data för SMS-funktioner. (NEO-87906)
<!--
* NOOOO Addressed delivery preparation failures for IndiGo Aviation after upgrading to v7.4.2. This fix resolves personalization and deduplication-related errors, enabling smooth delivery workflows. (NEO-87693)
* NOOOO Corrected Redshift database function definitions in version 8.6.4, ensuring proper execution of functions like `AddDays`, `AddHours`, `AddMinutes`, and `AddSeconds`. (NEO-87305)
* Provided a silent installation mechanism for the client console to facilitate mass upgrades without user intervention. This resolves challenges with manual installations. (NEO-69772)
-->
* Korrigerade fel i databasrensningsarbetsflödet på grund av saknade eller felaktiga kolumnreferenser i SQL-frågor. Detta garanterar att loggar och besöksdata rensas ordentligt. (NEO-86813)
* Ett problem där händelsedatum saknades i leveransloggar har åtgärdats. Den här korrigeringen säkerställer korrekt ifyllning av händelsedatum, vilket är viktigt för schemalagda utlösare och arbetsflöden. (NEO-86708)
* Ett problem med infogning av SMS-leveranslogg i SMS 2.0 har korrigerats, vilket säkerställer korrekt loggning i tabellen `nmsBroadLogMid`. (NEO-86556)
* Åtgärdade problem med extrahering av filer med externt leveransläge i Direct Mail-mallar för att säkerställa kompatibilitet och funktionalitet. (NEO-86520)
* Löste problem med leveransbearbetning, bland annat delad routning över flera MID-instanser, och säkerställde korrekta statusuppdateringar och dataflöden för leveransen. (NEO-86500)
* Korrigerade saknade spårningsdata i dynamiska rapporter efter migrering från Campaign Standard till Campaign v8 och säkerställde korrekt rapportering för leveransspårningsloggar. (NEO-86419)
* Löst arbetsflöde som utlöste problem där arbetsflöden kördes två gånger, vilket orsakade dubblettnyckelfel. Den här korrigeringen säkerställer korrekt händelsehantering och exekvering. (NEO-86154)
* Korrigerade kompatibilitetsproblem med SQL-funktioner för OOTB-växling efter distribution, vilket säkerställer att funktioner som `GetDate()` körs korrekt i arbetsflöden. (NEO-85834)
* Åtgärdade renderingsproblem i e-postbyggen där bilderna försvann när URL:er bifogades. Med den här korrigeringen ser du till att bilden visas korrekt i inkorgsförhandsvisningar. (NEO-85716)
* Korrigerad återgivning av typografiska citattecken i WebUI, vilket ger korrekt teckenvisning i e-postleveranser. (NEO-85687)
* Spegelsidlänkens funktion har åtgärdats så att rätt navigering mellan språkvarianter på spegelsidor säkerställs. (NEO-85625)
* Löste problem med datumformat i datumväljare för webbprogram, vilket säkerställer kompatibilitet med japanska datumformat (`yyyy-mm-dd`). (NEO-85234)
* Ett problem med alternativa routningsinställningar i midsourcing som säkerställer att arbetsflödet körs korrekt har åtgärdats. (NEO-85111)
* Förbättrad leveransgenomströmning i Android när du använder vågor, vilket säkerställer att leveransdelarna bearbetas i rätt ordning baserat på schemaläggning. (NEO-84324)
* Fel vid leveransförberedelser har korrigerats på grund av null-bearbetningsfel i funktionen `to_varchar`, vilket ger smidiga kampanjstarter. (NEO-84108)
* Löste problem med SFTP-anslutningen orsakade av inaktuella `libcurl`- och `libssh2`-versioner, vilket säkerställer kompatibilitet med Azure-värdservrar för SFTP-servrar. (NEO-84038)
* Korrigerade problem med Snowflake FDA-anslutningen som inbegriper nyckelpars autentiseringsfel, vilket säkerställde att databasanslutningarna lyckades. (NEO-84024)
* Åtgärdade problem med typologiregelns funktionalitet och säkerställde korrekt tillämpning av tryckreglerna i PUSH-leveranser. (NEO-84010)
* Åtgärdade fel i BigQuery-frågan som orsakats av felaktig matchning av datum- och tidsstämpeljämförelser efter uppgraderingen, vilket säkerställer kompatibilitet med filtreringsvillkoren. (NEO-83826)
* Ett problem där leveransaktiviteter misslyckades vid återupptagande av pausade leveranser på grund av personaliseringsfel har åtgärdats. Med den här korrigeringen får du smidigare arbetsflöden för leverans och förhindrar fel som beror på pausade aktiviteter. (NEO-83809)
* Korrigera ett problem i FFDA när alternativet &quot;Läs in målpost&quot; används. Stöd för&quot;order by&quot;- och&quot;where&quot;-klausuler lades till. (NEO-83793)
* Åtgärdade återkommande leveransfel som orsakats av att null-värden skrivits till kolumner som inte kan ha värdet null i tabellen broadLogRcp. Korrigeringen förbättrar leveranstillförlitligheten och förhindrar fel under livekampanjer. (NEO-83729)
* Ett problem där dirigerade adresser duplicerades under leveransförberedelsen löste ett problem där antalet meddelanden inte stämde. Med den här korrigeringen får du en korrekt målinriktning och undviker dupliceringsfel. (NEO-83703)
* Korrigerade ett kritiskt problem där produktionsleveranser skickades efter deras giltighetsperiod, vilket potentiellt kunde orsaka rättsliga problem. Leveranserna följer nu strikt sina definierade giltighetsperioder. (NEO-83350)
* Ett utrymmesproblem uppstod när stora datavolymer lästes in i Teradata-tabeller. Med den här korrigeringen optimeras databearbetningen och tillfälliga fel i produktionsmiljöer åtgärdas. (NEO-83252)
* Ett tekniskt arbetsflödesfel relaterat till SendMetricsToNewRelic-fel som orsakade fördröjningar i bearbetningen av RT-händelser har åtgärdats. Med den här korrigeringen får du ett smidigare arbetsflöde och förhindrar händelsereloggar. (NEO-83143)
* Korrigerade ett fel i databasrensningsarbetsflödet som orsakas av ID till UUID-konverteringsproblem i FFDA-interaktionsinstanser. Denna uppdatering säkerställer att rensningen går som den ska och minskar belastningen på systemet. (NEO-83138)
* Löste leveransfel på grund av begränsningar för interna namn för dirigeringsmedlemmar. Med den här korrigeringen får du längre interna namn utan att det påverkar leveranspersonaliseringen. (NEO-83044)
* Korrigerade ett problem där leveranser fastnade i personalisering på grund av slumpmässiga fel. Denna uppdatering ger smidigare personaliseringsprocesser och tillförlitlig leverans. (NEO-82781)
* Åtgärdade ett problem där offertförslag inte kunde granskas i konsolen på grund av API-fel och långsamhet. Den här korrigeringen förbättrar svarstiderna i användargränssnittet och säkerställer korrekta erbjudandefunktioner. (NEO-82742)
* Löste återkommande krascher i Adobe Campaign-konsolen när anpassade leveransobjekt användes. Den här korrigeringen säkerställer stabilitet och tillförlitlighet när du arbetar med anpassade arbetsflöden. (NEO-82675)
* Korrigerade långsamma behandlings- och arbetsflödesfel som rapporterades efter migrering från v7 till v8. Den här uppdateringen optimerar kampanjarbetsflödena och ser till att de körs i rätt tid. (NEO-82665)

<!--
* Resolved an issue where sysfilters were generating incorrect SQL queries after upgrading to v8.6.3. This fix ensures proper query generation and restores sysfilter functionality. (NEO-82591)
-->

* Korrigerade ett kritiskt problem där underordnade MTA-processer fastnade, som blockerade leveranser av Push och WhatsApp. Denna uppdatering ger smidigare arbetsflöden för kommunikation och förhindrar flaskhalsar i leveransen. (NEO-82351)
* Ett datamigreringsproblem har åtgärdats där strängfält från GCP-tabeller orsakade fel under uppdateringar av Teradata. Med den här korrigeringen elimineras behovet av tillfälliga lösningar och arbetsflödets effektivitet förbättras. (NEO-82260)
* Databasrensningslogik har uppdaterats för att ta hänsyn till primära databaser i FFDA-instanser, vilket förhindrar onödiga försök att rensa bort tabeller som inte finns. Den här korrigeringen optimerar rensningsåtgärder. (NEO-81879)
* Lösta konsolkrascher orsakade av användning av delarbetsflöden i kombination med uppräkningsfält. Den här korrigeringen säkerställer stabilitet när du arbetar med förbättrade arbetsflöden. (NEO-81864)
* Ett problem har korrigerats där deltillhörighetsfält i målmappningar ändrades felaktigt efter leveransduplicering, vilket orsakade arbetsflödesfel. Den här uppdateringen garanterar konsekventa värden för undertillhörighet. (NEO-81809)
* Stöd för jokertecken har lagts till i filöverföringsaktiviteter i Adobe Campaign Classic v8, vilket gör att användare kan överföra filer med dynamiska namn (t.ex. `abc_*`) i arbetsflöden. (NEO-81758)
* Ett alternativ för att aktivera flaggan `content-available` i iOS push-meddelanden för Adobe Campaign Classic v8 introducerades. Den här förbättringen gör att mobilappar kan lagra meddelanden i inkorgen och ha stöd för bakgrundsuppdateringar, vilket åtgärdar problem med att ta bort leveranser som orsakas av APNS-begränsningar. (NEO-81721)

<!--
* Updated the Campaign 7.4.1 release upgrade process to require manual installation of dependencies. Documentation has been provided to guide users on installing required libraries such as `epel-release`, `java-11-openjdk-headless`, and others. (NEO-81433)
-->

* Ett timeout-konfigurationsalternativ för BigQuery-anslutningar har lagts till i Adobe Campaign Classic v8. Den här förbättringen gör att användare kan justera tidsgränsen för frågor och lösa problem med frågefel på grund av standardtidsgränsen. (NEO-81222)
* Korrigerade ett intermittent problem där URL:er för spegelsidor misslyckades för leveranser som skickats via delade och alternativa routningsexterna konton efter v8-migrering. De underliggande leveransdelarna kopieras nu korrekt till `mirrorPageInfo`. (NEO-81105)

<!--
* Resolved an authentication failure issue with inMail caused by token expiration. Restarting the `nlserver` process now resolves the error. (NEO-80683)
-->

* Knappen Åtkomst till det nya webbgränssnittet i klientkonsolen har korrigerats så att den pekar på rätt URL (`https://experience.adobe.com`) för produktionsinstanser. Detta löser problem med ogiltiga URL:er i produktionsmiljöer. (NEO-80673)
* Korrigerade ett problem i den delade aktiviteten där användning av både Sortering och Storlek (som en procentandel av segmentet) orsakade SQL-fel. Funktionen fungerar nu korrekt. (NEO-80432)
* Åtgärdade ett kraschproblem i arbetsflöden med `CCurlAzureBlobStorage::UploadStream`. Arbetsflödena körs nu utan segmenteringsfel under överföringar av Azure Blob Storage. (NEO-79598)
* Ett problem där spegelsidor inte kunde visas från klientkonsolen i produktionsmiljöer har åtgärdats. Spegla sidlänkar fungerar nu korrekt i både e-post- och konsolvyer. (NEO-78946)
* Ett leveransloggproblem har korrigerats där vissa loggar felaktigt markerats som&quot;Leveransen avbröts&quot; trots att meddelandet levererades. Rotorsaken som är relaterad till kontaktdatum och händelsedatumsavvikelser har åtgärdats. (NEO-78933)
* Biblioteket `com.google.code.gson:gson` har uppdaterats för att förbättra säkerheten. (NEO-78299)
* Löste dubblettnyckelbegränsningsfel i FDA-anslutningsloggar (`nmsconnectionlogs`) som orsakade arbetsflödesfel. Infogningslogiken har justerats för att förhindra dubblett-ID:n. (NEO-78050)
* Ett problem har korrigerats där e-postadresser i karantän felaktigt markerades som mobila i adresstabellen, vilket orsakade leveransanalysfel. Avstämningslogiken mellan leveransobjekt har korrigerats. (NEO-76986)
* Ett leveransförberedelsefel har åtgärdats när kontrollgrupper används med en Oracle-databas. SQL-frågegenereringen har korrigerats för att säkerställa kompatibilitet med Oracle-databaser. (NEO-76947)
* Löste leveransfel på grund av att mappar skapades samtidigt under övergångar för nya månader. Logiken för att skapa leveransmappar har justerats för att förhindra dubblettnyckelfel. (NEO-76824)
* Inkonsekventa problem med tidszonskonvertering i Teradata externa konton har åtgärdats. De tidsstämplar som visas justeras nu korrekt med de konfigurerade tidszonsinställningarna. (NEO-76716)
* Förbättrade arbetsflöden för databasrensning för effektiv hantering av stora datauppsättningar. Ett nytt sätt att använda rad-ID och bind-variabler har implementerats för att optimera borttagningsprestanda. (NEO-76439)
* Ett problem där externa leveranser med kanalen &quot;Annat&quot; inte genererade utdatafiler har åtgärdats. Leveransegenskaperna innehåller nu korrekt filsökväg för genererade filer. (NEO-75962)
* Korrigerade fel i arbetsflödet `ffdaReplicateStagingData` som orsakas av stora datauppdateringar. Timeoutinställningar och hantering av tabellstorlek har optimerats för att förhindra arbetsflödesfel. (NEO-75643)
* Ett problem har korrigerats där kontrollpanelerna blev tomma när utdatafiler för direktreklam förhandsvisades. Kontrollpanelen visas nu korrekt efter filförhandsvisningar. (NEO-75359)
* Förbättrade spårningsindikatorer för push-meddelanden som inkluderar klickningar och öppningar. Indikatorer som `@recipientClick`, `@personClick` och `@totalRecipientClick` tar nu hänsyn till klickningar på mobilmeddelanden. (NEO-75240)
* Korrigerade fel i rensningsarbetsflöden för leveranser med externa status som väntar på att avbrytas. Databaspostens hämtningslogik har korrigerats. (NEO-74833)
* Ett problem med tidszonsavvikelser i Ryssland (UTC+3:00 Moskva) där `nlserver` utdatatider var felaktiga har åtgärdats. Tidssynkroniseringslogiken har uppdaterats. (NEO-74754)
* Korrigerade fel i arbetsflödet `defaultMidSourcingDlvStat` som orsakas av felaktig SQL-syntax för MSSQL-databaser. Frågegenereringslogiken har justerats för kompatibilitet. (NEO-74156)
* Flera krascher i webbprocessen har åtgärdats. (NEO-73174)
* Korrigerade ett problem med BigQuery-frågor som misslyckades när apostrofer fanns i villkoren. Frågehanteringslogiken har uppdaterats så att specialtecken tolkas korrekt. (NEO-72547)
* Ett problem där typologiregler med exkluderingsfilter inte fungerade korrekt har åtgärdats. SQL-frågegenereringen för leveransförberedelser har korrigerats. (NEO-72292)
* Åtgärdade diskrepanser i händelsedatum och kontaktdatum för hantering av avhopp. Tidszonshanteringslogiken har förbättrats. (NEO-72277)
* Förbättrad hantering av felaktigt konverterade UTF-8-tecken i direktutskick. Dolda tecken bearbetas nu korrekt för att förhindra leveransfel. (NEO-72148)
* Korrigerade fel i aktiviteten för inkommande SMS där filter orsakade problem med sparandet. Arbetsflödet sparas nu korrekt utan att några fel genereras. (NEO-70427)
* SQL-frågegenereringen för grupperade berättigandevillkor i erbjudandeblanksteg har korrigerats. Parenteser som saknas i SQL-villkor har lagts till för att säkerställa korrekt filtrering. (NEO-70425)

<!--
* Updated the public documentation link in the `ffdaUnicity` workflow email template to point to the correct page for key management in v8. (NEO-67996)
-->

* Åtgärdade återkommande fel i arbetsflöden för BigQuery-datainläsning som orsakas av HTTP-innehåll eller överföringskodningsproblem. Logiken för anslutningshantering har förbättrats. (NEO-66989)

