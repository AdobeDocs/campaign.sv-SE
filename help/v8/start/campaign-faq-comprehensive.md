---
title: Frågor och svar om Campaign v8
description: Få svar på vanliga Adobe Campaign v8-frågor om konfiguration, konfiguration, meddelanden, arbetsflöden med mera
feature: Overview
role: User
level: Beginner
keywords: Vanliga frågor, Campaign v8, frågor, svar, hjälp, support, felsökning
hide: true
hidefromtoc: true
source-git-commit: 561893e593a6c6f85d4c469ac09dd2e35a9b37e1
workflow-type: tm+mt
source-wordcount: '10163'
ht-degree: 18%

---

# Vanliga frågor och svar {#faq}

Få snabba svar på de vanligaste frågorna om Adobe Campaign v8. Oavsett om du just har kommit igång eller letar efter avancerad konfigurationshjälp hittar du svar ordnade efter ämne nedan.

**Ny i Campaign?** Börja med [Allmänna frågor](#general) och [Nyckelbegrepp](#key-concepts).\
**Behöver du teknisk hjälp?** Kontrollera [Utvecklare](#developers) och [kampanjinställningar](#settings).\
**Hittar du inte ditt svar?** Besök våra [användarforum](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"} eller [kontakta support](#get-help).

>[!TIP]
>
>Använd Ctrl+F (Cmd+F på Mac) om du vill söka efter specifika nyckelord på den här sidan. Klicka på en fråga för att utöka svaret.


## Allmänna frågor {#general}

Få svar på de vanligaste frågorna om Adobe Campaign v8, inklusive hur du ansluter, uppgraderar och får support.

+++ Hur ansluter jag till Campaign v8?

Du måste hämta och installera Campaign-klientkonsolen för att kunna ansluta till Adobe Campaign.

[Klicka här för att läsa mer](connect.md).

Från och med Campaign v8.6 har du tillgång till användargränssnittet **Campaign-webben** som är tillgängligt via den centrala Adobe Experience Cloud-miljön. Experience Cloud är Adobe integrerade program, produkter och tjänster för digital marknadsföring.

Lär dig hur du ansluter till Adobe Experience Cloud och kommer åt Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui).

Läs mer i [Adobe Campaign webbgränssnittsdokumentation](https://experienceleague.adobe.com/en/docs/campaign-web/v8/campaign-web-home){target="_blank"}.

>[!TIP]
>
>**Felsökning av anslutningsproblem:**
>
>* Kontrollera att dina Adobe ID-autentiseringsuppgifter är korrekta
>* Kontrollera att klientkonsolversionen matchar serverversionen
>* Kontrollera nätverksanslutningar och brandväggsinställningar
>* Rensa klientkonsolens cache om problem uppstår
>* Kontakta administratören för att verifiera dina användarbehörigheter

**Relaterade ämnen:**

* [Installera klientkonsolen](connect.md)
* [Kampanjanvändargränssnitt](campaign-ui.md)
* [Användarbehörigheter](gs-permissions.md)

+++

+++ Kan Campaign v8 installeras på en lokal eller blandad miljö?

Campaign v8 är bara tillgängligt i Managed Cloud Services, som är värd för Adobe.

+++

+++ Hur uppgraderar jag Campaign till den senaste versionen?

Adobe Campaign uppdateras regelbundet. Mindre versioner släpps varje år med nya funktioner, förbättringar och korrigeringar. Dessutom släpper vi regelbundet mindre builder med kumulativa korrigeringar.

Denna regelbundna uppdateringsfrekvens syftar till att få den senaste och bästa informationen i händerna, hålla miljön säker och förbättra din upplevelse av produkten. Därför anser vi att det är viktigt att du kör den senaste versionen av Adobe Campaign.

>[!NOTE]
>
>Som användare av hanterade molntjänster uppgraderas din instans av Adobe med nya utgåvor.

+++

+++ Hur förbättrar man e-postleveransen?

E-postleveransen, som är en viktig del i varje avsändares marknadsföringsprogram, kännetecknas av ständigt föränderliga kriterier och regler. För effektiv navigering i den digitala världen krävs regelbunden anpassning av er e-poststrategi, med hänsyn till viktiga leveranstrender, för att ni ska nå era målgrupper på bästa sätt.

Läs den här guiden om du vill veta mer om [Bästa metoder för slutprodukter](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"}

Lär dig hur du implementerar levererbarhet i Campaign [i den här guiden](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html){target="_blank"}

>[!TIP]
>
>**Tips om nyckelleveransen:**
>
>* Underhåll en tom e-postlista och ta bort inaktiva prenumeranter regelbundet
>* Använd dubbel anmälan för att säkerställa engagerade mottagare
>* Övervaka avsändarens rykte och IP-anseende
>* Autentisera e-postmeddelanden med SPF, DKIM och DMARC
>* Påbörja avbeställningar direkt
>* Testa dina e-postmeddelanden innan du skickar dem till stora målgrupper

**Relaterade ämnen:**

* [Om levererbarhet](../send/about-deliverability.md)
* [Kontrollera meddelandeinnehåll](../send/control-message-content.md)
* [Skärmleverans](../send/monitoring-deliverability.md)
* [SpamAssassin](../send/spamassassin.md)

+++

+++ Hur kan jag vara säker på att min leverans skickas utan fel?

Adobe Campaign har en uppsättning instrumentpaneler och verktyg för att övervaka e-postleveranser.

[Läs igenom dokumentationen för Campaign Classic v7 och lär dig](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html){target="_blank"} hur du ser till att dina meddelanden skickas, övervakar körningen och utför en åtgärd om ett fel inträffar.

+++

+++ Kan jag övervaka arbetsflödeskörningen?

Förstå hur du övervakar körningen av Campaign-arbetsflödet [på den här sidan](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution){target="_blank"}

+++

+++ Vilka system och komponenter är Campaign v8 kompatibelt med?

Du kan hämta en lista över alla system och komponenter som stöds för den senaste versionen av Campaign i [kompatibilitetsmatrisen för Adobe Campaign](compatibility-matrix.md).

+++

+++ Hur laddar jag ned Campaign?

Du kan hämta installationsprogrammet och klientkonsolen från Adobe Download Center.

Som administratör kan du ladda ned Adobe Campaign via Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html){target="_blank"}.

Läs mer om Distribution Center [på den här sidan](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html){target="_blank"}.

+++

+++ Hur loggar jag ett problem?

Om du skapar ett ärende kan du kontakta Adobe kundsupportteam om problem som du har med dina Adobe-produkter. Adobe Admin Console hjälper dig att lösa eller felsöka problemen genom att chatta med Adobe kundsupport.

Anslut till [Adobe Admin Console](https://adminconsole.adobe.com/overview){target="_blank"} för att logga ett problem eller starta en chattsession i det nya systemet.

Det här systemet kräver enskilda konton för varje användare, med rätt behörigheter. Om du upptäcker att du inte kan logga in med ditt Adobe-ID begär du åtkomst via Experience League, så registrerar kundtjänstteamet dig så snart som möjligt. [Läs mer](https://helpx.adobe.com/sv/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}

Gå med i Campaign Community: sök efter svar i befintliga frågor eller fråga experterna. [Delta i konversationen](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}

+++


## Viktiga begrepp {#key-concepts}

Lär dig mer om grundläggande Campaign-koncept som autentisering, användargränssnitt, arbetsflöden och grundläggande funktioner för att komma igång effektivt.

+++ Kan jag ansluta till Campaign v8 med en Adobe ID?

Ja! Tack vare integreringen med IMS (Adobe Identity Management System) ansluter användarna till Adobe Campaign-konsolen med sin Adobe ID. Integreringen ger följande fördelar:

* Samma ID kan användas för alla Experience Cloud-lösningar.
* Anslutningen sparas när Adobe Campaign används med olika integreringar.
* Säkrare policy för lösenordshantering.
* Använda Federated ID-konton (extern ID-leverantör).

[Läs mer](connect.md) om hur du får tillgång till Campaign v8 med en Adobe ID.

+++

+++ Vad är min version av Campaign?

Kontrollera [versions- och build-numret](connect.md#ac-version) i menyn **Hjälp > Om ...** på klientkonsolen i Campaign.

+++

+++ Vilka är skillnaderna mellan Campaign Classic v7 och Campaign v8?

Campaign v8 är nästa generation av Campaign, som är utformad för hanterade molntjänster. Det ger avsevärda förbättringar när det gäller infrastruktur, säkerhet, slutbarhet och övervakning.

Adobe Campaign v8 är exklusivt tillgängligt som **hanterad Cloud Service** och kan inte distribueras på en lokal eller hybridmiljö.

[Läs mer om övergången från Campaign Classic v7 till v8](v7-to-v8.md).

+++

+++ Hur ställer jag in användarbehörigheter?

Som administratör för Campaign kan du konfigurera behörigheter för användare i organisationen.

Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar:

* Tillgång till vissa funktioner
* Åtkomst till vissa data
* Skapa, ändra och/eller ta bort data

[Läs mer](../start/gs-permissions.md) om användarbehörigheter i Campaign v8.

**Relaterade ämnen:**

* [Kom igång med behörigheter](gs-permissions.md)
* [Hantera användarbehörigheter](manage-permissions.md)
* [Lägg till behörigheter i mappar](folder-permissions.md)

+++

+++ Hur säkerställer jag integritetsefterlevnad med Campaign?

Adobe Campaign erbjuder en uppsättning verktyg som hjälper dig att följa sekretesskraven för GDPR, CCPA och andra sekretessbestämmelser.

[Läs mer](../start/privacy.md) om sekretesshantering och de verktyg och funktioner som Adobe Campaign tillhandahåller för att hjälpa dig med din sekretessefterlevnad.

+++

+++ Vad är Campaign-användargränssnittskoncept jag bör känna till?

Mer information om grunderna i användargränssnittet i Adobe Campaign finns i [det här avsnittet](campaign-ui.md).

Från och med Campaign v8.6 har du även tillgång till det nya **Campaign-webbgränssnittet** som är tillgängligt via den centrala Adobe Experience Cloud-miljön.

[Läs mer i dokumentationen för Adobe Campaign webbgränssnitt](https://experienceleague.adobe.com/en/docs/campaign-web/v8/campaign-web-home){target="_blank"}.

+++

+++ Hur väljer jag målgrupp för mina meddelanden?

Med Adobe Campaign kan du använda olika strategier för att skapa publiker och välja målmottagare.

[Läs mer](../audiences/gs-audiences.md) om hur du definierar målgrupper i Campaign v8.

+++

+++ Vad är ett arbetsflöde?

Med Adobe Campaign följer arbetsflöden för att orkestrera alla processer och uppgifter i olika moduler på programservern. I den omfattande grafiska miljön kan du utforma processer såsom segmentering, kampanjkörning, filhantering och mänskligt deltagande osv. Arbetsflödesmotorn kör och spårar dessa processer.

Du kan till exempel använda ett arbetsflöde för att ladda ned en fil från en server, expandera den och sedan importera poster som finns i databasen i Adobe Campaign.

Ett arbetsflöde kan även innefatta en eller flera operatörer som ska meddelas eller som kan göra val och godkänna processer. På så sätt kan du skapa en leveransinstruktion, tilldela en eller flera operatörer uppgiften att arbeta med innehåll, ange mål och godkänna korrekturer innan leveransen påbörjas.

[Läs mer](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html){target="_blank"} om arbetsflöden. Du kan även läsa om [bästa praxis för arbetsflödet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"}.

**Relaterade ämnen:**

* [Kom igång med arbetsflöden](../config/workflows.md)
* [Skapa ditt första arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"}
* [Användningsexempel för arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/about-workflow-use-cases.html){target="_blank"}
* [Övervaka arbetsflödeskörning](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}

+++

+++ Hur skapar och skickar jag ett första e-postmeddelande?

När du skapar ditt första e-postmeddelande i Campaign v8 måste du utföra flera viktiga steg:

1. **Skapa leveransen** - Börja med att skapa en ny e-postleverans från en mall eller från början
1. **Definiera målgruppen** - Välj målmottagare med frågor, listor eller arbetsflöden
1. **Designa innehållet** - Använd e-postdesignern för att skapa ditt meddelande med personalisering
1. **Testa med korrektur** - Skicka testmeddelanden via e-post för att validera innehåll och personalisering
1. **Analysera och skicka** - Kör leveransanalys för att kontrollera om det finns fel och skicka sedan din e-post

Campaign v8 erbjuder två gränssnitt för att skapa e-post:

* **Klientkonsol** - Skrivbordsprogram med alla funktioner och avancerade funktioner
* **Webbgränssnitt för kampanj** - Modernt, intuitivt webbgränssnitt för snabbare e-postgenerering

[Läs mer om e-postdesign och validering](../send/email.md) i Campaign v8.

**Relaterade ämnen:**

* [Skapa din första leverans](create-message.md) - steg-för-steg-guide
* [Arbeta med leveransmallar](../send/create-templates.md) - Spara tid med mallar
* [Bästa praxis för leverans](delivery-best-practices.md) - Rekommendationer för framgång
* [Definiera e-postinnehållet](../send/defining-the-email-content.md) - Alternativ för att skapa innehåll
* [Förhandsgranska och korrektur](../send/preview-and-proof.md) - Testa innan du skickar
* [Konfigurera och skicka](../send/configure-and-send.md) - Slutliga steg att skicka
* [Anpassa innehåll](../send/personalize.md) - Lägg till dynamisk personalisering

+++

+++ Hur skickar jag SMS-meddelanden?

För att skicka SMS-meddelanden med Campaign v8 krävs en inledande konfiguration och sedan följer en enkel leveransprocess:

**Inledande konfiguration (engångskonfiguration):**

1. **Konfigurera SMS-kanal** - Konfigurera SMS-leveransinställningar och externt konto
1. **Konfigurera SMPP-anslutning** - Anslut till SMS-tjänstleverantören via SMPP-protokollet
1. **Testa anslutningen** - Verifiera anslutningen med SMS-providern
1. **Konfigurera routning** - Definiera hur SMS-meddelanden dirigeras via din leverantör

**Skapar och skickar SMS:**

1. **Skapa SMS-leverans** - Starta en ny SMS-leverans från en mall
1. **Definiera mottagare** - Välj din mobila målgrupp med telefonnummerfält
1. **Skriv SMS-innehåll** - Skapa ditt meddelande (160 tecken standard eller längre med sammanfogning)
1. **Lägg till personalisering** - Inkludera dynamiska fält som är specifika för varje mottagare
1. **Skicka korrektur** - Testa SMS-leveransen för att validera innehåll och leverans
1. **Analysera och skicka** - Kör analyser och skicka till din publik

**Viktiga SMS-funktioner:**

* **Flera SMPP-anslutningar** - Stöd för olika SMS-providers och protokoll
* **Leveransrapporter** - spåra skickade, levererade och misslyckade meddelanden
* **Teckenkodning** - Stöd för GSM7, Unicode och specialtecken
* **Långt SMS-stöd** - Automatisk meddelandesammanfogning för längre texter
* **Tvåvägs-SMS** - Hantera inkommande SMS-svar med arbetsflöden

[Läs mer om SMS-konfiguration och skicka](../send/sms/sms.md) i Campaign v8.

**Relaterade ämnen:**

* [Kom igång med SMS](../send/sms/sms.md) - fullständig SMS-guide
* [SMS-leveransinställningar](../send/sms/sms-delivery-settings.md) - Konfigurationsalternativ
* [SMPP-inställningar för externt konto](../send/sms/smpp-external-account.md) - Providerinställningar
* [Skapa en SMS-leverans](../send/sms/create-sms.md) - Skapa steg för steg
* [SMS-innehåll](../send/sms/sms-content.md) - Riktlinjer för innehållsdesign
* [Skicka SMS-korrektur](../send/sms/sms-proofs.md) - Testar SMS
* [Övervaka SMS](../send/sms/sms-monitor.md) - Spåra och analysera leveranser

+++

+++ Hur skickar jag push-meddelanden?

Om du skickar push-meddelanden med Campaign v8 måste du konfigurera mobilappsintegreringen och skapa engagerande meddelanden:

**Inledande konfiguration (engångskonfiguration):**

1. **Konfigurera push-kanal** - Ange inställningar för push-meddelandekanal i Campaign
1. **Integrera Campaign SDK** - Lägg till Adobe Campaign SDK i din mobilapp (eller använd Datainsamling)
1. **Konfigurera mobilapp** - Registrera dina iOS- och Android-appar i Campaign
1. **Konfigurera certifikat** - Konfigurera APN-certifikat (iOS) och FCM-nyckel (Android)
1. **Testa registrering** - Verifiera att enheter kan registrera och ta emot tokens

**Skapar och skickar push-meddelanden:**

1. **Skapa push-leverans** - Starta ett nytt push-meddelande från en mall
1. **Välj plattform** - Välj iOS, Android eller båda plattformarna
1. **Definiera målgrupp** - Målappsprenumeranter med mobilappsprenumerationer
1. **Designmeddelande** - Skapa rubrik, meddelande och multimediematerial
1. **Konfigurera beteende** - Ange klickningsåtgärder, djuplänkar och anpassade data
1. **Skicka testmeddelanden** - Validera på riktiga enheter innan du skickar
1. **Analysera och skicka** - Granska målinriktning och skicka till din mobila målgrupp

**Funktioner för push-meddelanden:**

* **Omfattande push-meddelanden** - inkludera bilder, videoklipp och interaktiva knappar (iOS och Android)
* **Personalization** - dynamiskt innehåll baserat på användarprofil och beteende
* **Djuplänkning** - Direktanvändare till specifika appskärmar eller -innehåll
* **Schemaläggning** - Skicka vid optimala tidpunkter baserat på användarens tidszon
* **A/B-testning** - Testa olika meddelanden och optimera engagemanget
* **Spärra/knip** - Övervakaren öppnar, klickar och konverterar

**Plattformsspecifika funktioner:**

* **iOS** - Tysta meddelanden, meddelandekategorier, ljudanpassning
* **Android** - Omfattande push-mallar, meddelandekanaler, anpassade layouter

[Läs mer om konfigurationen för push-meddelanden](../send/push-settings.md) i Campaign v8.

**Relaterade ämnen:**

* [Skapa och skicka push-meddelanden](../send/push.md) - fullständig push-guide
* [Konfigurera push-meddelandekanal](../send/push-settings.md) - Kanalinställning
* [Designa en omfattande Android-push](../send/rich-push-android.md) - Android-meddelanden
* [Designa en omfattande iOS-push](../send/rich-push-ios.md) - iOS-meddelanden
* [Konfigurera med datainsamling](../send/push-data-collection.md) - Modern reviderad integreringsmetod
* [Spåra och övervaka](tracking.md) - Analysera push-prestanda

+++

+++ Hur skapar man landningssidor?

Du kan använda Adobe Campaign Digital Content Editor för att utforma landningssidor och definiera mappning med databasfält.

[Läs mer](../dev/landing-pages.md) i dokumentationen för Campaign v8.

Du kan också använda gränssnittet för Campaign-webben för att skapa och publicera landningssidor - [Läs mer](https://experienceleague.adobe.com/en/docs/campaign-web/v8/landing-pages/get-started-lp){target="_blank"}.

+++

+++ Hur kan jag spåra leveranser?

Du kan spåra leveranser som skickats med Campaign v8 via dedikerade [leveransrapporter](../reporting/delivery-reports.md) och sedan övervaka leveranserna.

Läs mer om spårningshantering i Campaign [på den här sidan](../start/tracking.md).

**Relaterade ämnen:**

* [Spåra och övervaka meddelanden](tracking.md)
* [Leveransrapporter](../reporting/delivery-reports.md)
* [Förstå leveransfel](../send/delivery-failures.md)
* [Konfigurera spårade länkar](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/how-to-configure-tracked-links.html){target="_blank"} (Campaign Classic v7-dokumentation)

+++

+++ Hur översätter jag ett felmeddelande?

Visas ett felmeddelande på ett främmande språk? Alla felmeddelanden och deras översättning listas på [den här sidan](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=sv){target="_blank"}.

+++

+++ Kan jag skapa ett webbformulär och samla in svar i Campaign?

Ja. Skapa webbformulär med **Campaign Web Applications &amp; Forms** (klientkonsol) för fullständig kontroll över formulärlogik och validering, eller använd **Campaign Landing Pages** (webbgränssnitt) med ett modernt dra och släpp-gränssnitt för prenumerationer och leadgenerering. Båda samlar in data direkt i Campaign och integreras med arbetsflöden för automatiserade åtgärder.

[Läs mer om webbprogram och formulär](../dev/webapps.md) | [Startsidor för Campaign Web UI &#x200B;](https://experienceleague.adobe.com/en/docs/campaign-web/v8/landing-pages/get-started-lp){target="_blank"}

+++



## Kampanj v8 jämfört med tidigare versioner {#v7-differences}

Förstå de viktigaste skillnaderna mellan Campaign v8 och tidigare versioner (Classic v7 och Standard), inklusive arkitektur, driftsättning, migreringsvägar och funktionsändringar. Oavsett om du kommer från Campaign Classic v7 eller Campaign Standard kan du ta reda på vad som är nytt och hur du smidigt kan gå över.

+++ Vilka är de viktigaste skillnaderna mellan Campaign v8 och tidigare versioner?

Campaign v8 är en helt omdesignad version av Adobe Campaign som tagits fram för modern molnbaserad arkitektur och som ger avsevärda förbättringar jämfört med Campaign Classic v7 och Campaign Standard:

**Distributionsmodell:**

* **v8:** Endast hanterade molntjänster - fullständigt värdhanterade och hanterade av Adobe
* **v7/Standard:** Tillgängliga alternativ för lokal installation, hybridinstallation eller värdtjänster
* **Fördelar:** Ingen infrastrukturhantering, automatisk skalning, säkerhet på enterprise-nivå, proaktiv övervakning

**Arkitektur och prestanda:**

* **v8:** Förbättrad FDA-arkitektur (Fullständig FDA) med PostgreSQL-databas
* **v8:** Batchbearbetning med upp till **20 miljoner åtgärder per timme**
* **v8:** Genomströmning av transaktionsmeddelanden på **1 miljoner per timme**
* **v8:** Utforska data i realtid och skapa snabbt målgrupper (minuter kontra timmar)
* **Fördelar:** Bättre prestanda för storskaliga och komplexa kampanjer

**Användargränssnitt:**

* **v8:** Nytt **Kampanjwebbgränssnitt** tillsammans med klientkonsolen - intuitivt, tillgängligt, idealiskt för marknadsförare
* **v8:** Modern, responsiv design med dra och släpp-funktioner
* **v8:** Förenklade arbetsflöden för att skapa och hantera kampanjer
* **v8:** Delar många likheter med Campaign Standard-gränssnittet
* **Fördelar:** Snabbare introduktion, enklare kampanjkörning, bättre tillgänglighet, minimal inlärningskurva

**Nya nyckelfunktioner:**

* **Omfattande push-meddelanden** med bilder, videoklipp, interaktiva knappar, karuseller och timers
* **AI-assistenten** för innehållsgenerering (e-post, SMS, push) med poängsättning för varumärkesjustering
* **Uppgraderad SMS-infrastruktur (SMS v2.0)** med förbättrad tillförlitlighet och kompatibilitet
* **Adobe Experience Manager as a Cloud Service-integrering** för smidig innehållshantering
* **Förbättrad rapportering** inklusive dynamisk rapportering för Campaign Standard-användare

**Uppgraderingar och underhåll:**

* **v8:** Automatiska uppgraderingar hanteras av Adobe - alltid i den senaste stabila versionen med kontinuerlig leveransmodell
* **v7/Standard:** Manuell planering och exekvering av uppgradering krävs
* **Fördel:** Minskad underhållsbörda, omedelbar tillgång till nya funktioner, inga driftavbrott

**API:er och integrering:**

* **v8:** Modern REST API:er med förbättrad prestanda och tillförlitlighet
* **v8:** Smidig integrering med Adobe Experience Cloud och Adobe Experience Platform
* **Fördelar:** Enklare integreringar, bättre interoperabilitet och modern utvecklingspraxis

[Läs mer om nyckelfunktionerna i Campaign v8](whats-new.md)

**Relaterade ämnen:**

* [Från Campaign Classic v7 till v8](v7-to-v8.md) | [&#x200B; Övergångshandbok för v7 till v8 &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/v7-to-v8){target="_blank"}
* [Från Campaign Standard till v8](acs-to-v8.md) | [Campaign Standard-övergång](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"}
* [Campaign v8 - Adoptionshandbok](https://experienceleague.adobe.com/sv/docs/campaign-web/acs-to-ac/home){target="_blank"}
* [Funktionsmatris för kampanj v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/capability-matrix){target="_blank"}
* [Kampanjarkitektur v8](../architecture/architecture.md)
* [Skyddsritningar och begränsningar](ac-guardrails.md)

+++

+++ Ska jag migrera från Campaign Classic v7 eller Campaign Standard till v8?

**Campaign v8 är idealiskt för organisationer som behöver:**

* **Kampanjer med stora volymer** - Skicka miljontals meddelanden med bättre prestanda och tillförlitlighet (20 miljoner åtgärder/timme)
* **Företagsskalbarhet** - Utöka databasen och era kampanjer utan prestandaproblem
* **Modernt webbgränssnitt** - Intuitivt, responsivt webbgränssnitt för Campaign för snabbare kampanjskapande och förbättrad användarupplevelse
* **Molnbaserade fördelar** - Utnyttja automatiska uppdateringar, hanterad infrastruktur, elastisk skalning och proaktiv övervakning
* **Långsiktig support** - Campaign v8 är Adobe strategiska plattform med utökad support, medan tidigare versioner kommer att få support till slutet av de närmaste åren
* **Minskade IT-kostnader** - eliminera infrastrukturhantering och uppgraderingsplanering
* **Avancerade funktioner** - AI Assistant, avancerad push, förbättrad SMS, integrering med Adobe Experience Platform

**För Campaign Standard-användare:**

Campaign Standard-användare har nu rätt att gå över till Campaign v8 Managed Cloud Services. Några viktiga fördelar:

* **Välbekant gränssnitt** - Webbgränssnittet för Campaign delar många likheter med Campaign Standard, vilket minimerar inlärningskurvan
* **Funktionsparitet** - Campaign Standard viktigaste funktioner har lagts till i v8 (Dynamic Reporting, Centralized Branding, REST API:er, Landing Pages, Visual Fragments)
* **Utökat stöd** - Inledande hjälp med smidig övergång och kontinuerlig plattformsövervakning
* **Datamigrering** - Alla data från Campaign Standard importeras med minimal störning
* **Enhetlig användarupplevelse** - Fortsätt arbeta med välbekanta arbetsflöden och gränssnitt

**För Campaign Classic v7-användare:**

Campaign v8 ger avsevärda förbättringar samtidigt som de centrala Campaign-funktionerna bibehålls:

* **Dubbelt gränssnitt** - få tillgång till både den kraftfulla klientkonsolen och det moderna webbgränssnittet i Campaign
* **Bättre prestanda** - avsevärt förbättrade frågeprestanda och databearbetning
* **Cloud-förmåner** - Automatiska uppgraderingar, säkerhetsuppdateringar, säkerhetskopiering/återställning hanteras av Adobe
* **Modern arkitektur** - Förbättrad FFDA-arkitektur med PostgreSQL för bättre skalbarhet

**Överväg migrering:**

* Din aktuella Campaign-instans hanterar stora datavolymer (miljoner profiler)
* Du har prestandaproblem med komplexa arbetsflöden eller målinriktning
* Du vill minska kostnaderna för hantering och underhåll av infrastruktur
* Du behöver smidig integrering med Adobe Experience Cloud eller Adobe Experience Platform
* Du planerar en större uppgradering eller infrastrukturuppdatering ändå
* **Du vill ha framtidssäkrad teknik** - Tidigare versioner når slutet av supporten
* **Teamet behöver ett modernt gränssnitt** - Webbgränssnittet för Campaign ger bättre tillgänglighet för marknadsförare

**Migreringsöverväganden:**

* Adobe tillhandahåller migreringsstöd, vägledning och verktyg
* v8 hanteras endast av Cloud Service (ingen lokal eller blandad driftsättning)
* Vissa tekniska implementeringar kan skilja sig åt - se [funktionsmatrisen](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/capability-matrix){target="_blank"}
* Datamigrering och testning kräver planering och resurser
* **För Campaign Standard-användare** - Övergången är utformad för att vara smidig med minimala arbetsflödesavbrott

**Nästa steg:**

Kontakta Adobe för att

* Utvärdera din migreringsberedskap och tidslinje
* Förstå de specifika fördelarna för ditt användningssätt
* Planera migreringsstrategin och resursallokeringen
* Migreringsverktyg för åtkomst och support

**Relaterade ämnen:**

**För Campaign Classic v7-användare:**

* [Från Campaign Classic v7 till v8](v7-to-v8.md)
* [v7 till v8, detaljerad guide](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/v7-to-v8){target="_blank"}

**För Campaign Standard-användare:**

* [Campaign Standard övergång till v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"}
* [Campaign v8 - Adoptionshandbok](https://experienceleague.adobe.com/sv/docs/campaign-web/acs-to-ac/home){target="_blank"}
* [Från Campaign Standard till v8 - översikt](https://experienceleague.adobe.com/en/docs/campaign-web/acs-to-ac/overview){target="_blank"}
* [Kom igång för marknadsförare](https://experienceleague.adobe.com/en/docs/campaign-web/acs-to-ac/marketers){target="_blank"}
* [Kom igång för administratör/utvecklare](https://experienceleague.adobe.com/en/docs/campaign-web/acs-to-ac/admin-developers){target="_blank"}

**Allmänna resurser:**

* [Funktionsmatris för kampanj v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/capability-matrix){target="_blank"}
* [Kompatibilitetsmatris](compatibility-matrix.md)

+++

+++ Vilka är de viktigaste terminologi- och funktionsskillnaderna i Campaign v8?

Campaign v8 har de flesta Campaign Classic v7- och Campaign Standard-funktioner med förbättringar, men vissa funktioner har förändrats på grund av den molnbaserade arkitekturen och vissa terminologer skiljer sig åt mellan versionerna.

**Skillnader i terminologi (Campaign Standard till v8):**

* **Anpassade resurser** är nu **Scheman**
* **Meddelanden** kallas **Leveranser**
* **Produktanvändare** är nu **Operatorer**
* **Roller** har konfigurerats med **Namngivna rättigheter**
* **Säkerhetsgrupper** är nu **Operatorgrupper**
* **Organisationsenheter** hanteras via **Mappbehörigheter**

**Uppdateringar av terminologi i webbgränssnittet för kampanj:**

Följande termer har uppdaterats i gränssnittet för Campaign-webben (klientkonsolen använder traditionella termer):

* **Mottagarna** är nu **Profiler**
* **Utdirigeringsadresser** är nu **Testprofiler**
* **Leveransanalys** är nu **Leveransförberedelse** (klicka på knappen **Förbered**)
* **Förhandsgranska e-post** är tillgängligt via knappen **Simulera innehåll**
* **Listor** är nu **Publiker**

**Inte tillgängligt i v8:**

* **Lokala och hybrida distributioner** - v8 är endast hanterade molntjänster
* **Direkt databasåtkomst** - Använd tillhandahållna API:er och verktyg i stället
* **Kundhanterad infrastruktur** - Adobe hanterar all infrastruktur
* **Manuella bygguppgraderingar** - nu automatiskt (hanterad av Adobe)

**Olika implementeringar i v8:**

* **Tekniska arbetsflöden** - Vissa optimerade för molnarkitektur kan fungera annorlunda
* **Databasstruktur** - Förbättrad FFDA-arkitektur kan kräva schemaanpassningar
* **Anpassade integreringar** - kan behöva uppdateras för molnbaserad arkitektur
* **Lågnivåanpassningar** - Vissa kräver olika metoder i hanterad miljö

**Förbättrat eller ersatt i v8:**

* **Bygg uppgraderingar** - Automatisk med kontinuerlig leveransmodell i stället för manuell
* **Prestandajustering** - hanteras av Adobe infrastrukturoptimering
* **Säkerhetsuppdateringar** - Används automatiskt av Adobe
* **Säkerhetskopiering och återställning** - hanteras av Adobe som en del av tjänsten
* **Användargränssnitt** - Nytt webbgränssnitt för Campaign tillsammans med klientkonsolen

**Funktioner som lagts till för Campaign Standard-användare som övergår till v8:**

* **Dynamisk rapportering** - Anpassningsbara realtidsrapporter med demografiska analyser
* **Centraliserad profilering** - Definiera riktlinjer för varumärkets visuella och tekniska egenskaper
* **REST API:er** - Skapa integreringar och bygg ditt ekosystem
* **Förbättringar av landningssidor** - Förbättrad funktionsparitet med Campaign Standard
* **Visuella fragment** - återanvändbara visuella komponenter för e-post och innehållsmallar

**Viktigt!** De flesta marknadsförings- och funktionsfunktioner är tillgängliga och har förbättrats i v8. Funktioner på teknik- och infrastrukturnivå hanteras av Adobe i molnmiljön.

**Relaterade ämnen:**

* [Funktionsmatris](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/capability-matrix){target="_blank"} - Jämför funktioner mellan gränssnitt
* [Kompatibilitetsmatris](compatibility-matrix.md) - System och komponenter som stöds
* [Skyddsritningar och begränsningar](ac-guardrails.md)
* [Övergångshandbok för v7 till v8](v7-to-v8.md)
* [Campaign Standard till v8-övergång](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"}

+++

## Profiler och målgrupper {#audiences}

Hitta svar på frågor om att hantera profiler, skapa målgrupper, importera data och målinrikta mottagare för era kampanjer.

+++ Hur skapar man mottagare?

Skapa mottagare manuellt i klientkonsolen för enskilda profiler, importera från filer (CSV/TXT) för att lägga till stora mängder, använda webbformulär för självregistrering eller integrera via API:er från externa system. Använd importarbetsflöden för återkommande datainläsningar.

[Skapa profiler manuellt](../audiences/create-profiles.md) | [Importera profiler från en fil &#x200B;](../audiences/import-profiles.md) | [Samla in profiler med webbformulär](../audiences/collect-profiles.md)

+++

+++ Hur importerar jag profiler?

Campaign innehåller flera importmetoder: enkel filimport med importguiden, arbetsflödesbaserad import för komplexa omformningar, återkommande importer med schemalagda arbetsflöden från SFTP och API-import för programmatisk integrering.

För filimport förbereder du datafilen (CSV/TXT, UTF-8-kodning), använder importguiden eller arbetsflödet, mappar kolumner till Campaign-fält, definierar uppdaterings-/infogningsregler och testar med ett litet exempel först. Använd arbetsflöden för återkommande importer och tillämpa regler för borttagning av dubbletter.

[Guiden Importera data](../start/import.md) | [Återkommande importarbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/recurring-import-workflow.html){target="_blank"} | [Datainläsningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"}

+++

+++ Hur definierar jag målpopulationen för en marknadsföringskampanj?

I Campaign finns flera metoder för målinriktning: skapa frågor med visuella kriterier, rikta befintliga listor eller segment, importera mottagare från externa filer (CSV, TXT) eller tillämpa fördefinierade filter. Du kan kombinera villkor med AND/OR-logik, exkludera specifika populationer, använda kontrollgrupper och dela upp för A/B-testning. Förhandsvisa alltid målpopulationsstorleken innan du skickar.

[Definiera kampanjmål](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html){target="_blank"} | [Frågeaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"} | [Skapa målgrupper](../audiences/create-audiences.md)

+++

+++ Hur skapar jag en lista med profiler?

En lista är en statisk uppsättning mottagare som ni kan rikta in er på leveranser och återanvända mellan kampanjer.

**Tre metoder:**

* **Manuellt skapande:** Navigera till **[!UICONTROL Profiles and Targets > Lists]** och klicka på **[!UICONTROL Create]**. Lägg till mottagare från en fråga, från ett enskilt val eller från en mapp.

* **Automatisering av arbetsflöden:** Använd aktiviteten **[!UICONTROL List update]** för att skapa och underhålla listor automatiskt utifrån frågeresultat eller importerade data.

* **Under import:** Skapa en lista när du importerar profiler för att spara dem som en återanvändbar grupp.

>[!TIP]
>
>Använd arbetsflöden för listor som kräver regelbundna uppdateringar och manuell framtagning för engångssegmentering.

[Skapa målgrupper](../audiences/create-audiences.md) | [Listuppdateringsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/list-update.html){target="_blank"}

+++

+++ Hur kan jag deduplicera en population innan jag skickar ett meddelande?

Använd aktiviteten **[!UICONTROL Deduplication]** i ett arbetsflöde för att ta bort dubblettmottagare före leverans. Placera den mellan dina **[!UICONTROL Query]**- och **[!UICONTROL Delivery]**-aktiviteter och välj sedan ditt dedupliceringsvillkor (vanligtvis e-postadress eller mottagar-ID) och vilken post som ska behållas.

>[!TIP]
>
>Ta alltid bort dubbletter innan du skickar iväg för att försäkra dig om att varje person bara får ditt meddelande en gång.

[Dedupliceringsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/deduplication.html){target="_blank"}

+++

+++ Hur identifierar och riktar man sig till dem som prenumererar på ett nyhetsbrev?

Campaign spårar automatiskt nyhetsbrevprenumerationer via informationstjänster. Så här riktar du dig till prenumeranter:

* Använd en **[!UICONTROL Query]**-aktivitet och filtrera **[!UICONTROL Subscriptions]** > välj nyhetsbrevstjänsten
* Ange abonnenter direkt från leveransen genom att välja **[!UICONTROL To > Subscribers of an information service]**
* Skapa prenumerationslistor med arbetsflödesaktiviteten **[!UICONTROL Subscription Services]**

Campaign spårar prenumerations-/prenumerationshistorik och hanterar automatiskt anmälan/avanmälan.

[Hantera prenumerationer](../start/subscriptions.md) | [Frågeaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}

+++

+++ Vilken är den bästa metoden att utesluta profiler från en målpopulation?

Använd aktiviteten **[!UICONTROL Exclusion]** i ett arbetsflöde för att ta bort oönskade profiler från målet. Placera den efter era målgruppsaktiviteter och definiera vilken population som ska uteslutas.

[Uteslutningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/exclusion.html){target="_blank"}

+++

+++ Kan jag använda externa profiler utan att importera dem i Campaign?

Ja, med Campaign v8 kan du arbeta med externa profiler som lagras i en extern databas utan att läsa in dem i Adobe Campaign. [Läs mer](../audiences/external-profiles.md).

+++

+++ Hur skapar jag testprofiler för mina leveranser?

Testprofiler är speciella mottagare som används för att skicka korrektur och validera leveranser utan att påverka produktionsdatabasen. Skapa dem i **[!UICONTROL Profiles and Targets > Test profiles]**, eller använd funktionen **[!UICONTROL Seed addresses]** för att automatiskt lägga till testmottagare till leveranserna för kvalitetssäkring och inkorgsövervakning.

[Testprofiler](../audiences/test-profiles.md)

+++

## Meddelandedesign {#design}

Lär dig hur du utformar effektiva marknadsföringsmeddelanden i Campaign v8, inklusive e-postmallar, personaliseringstekniker och flerspråkigt innehåll. Designa dina meddelanden i klientkonsolen eller använd det moderna **e-post-Designer** i webbgränssnittet för Campaign för en förbättrad visuell redigeringsupplevelse.

+++ Vilka är de bästa sätten att utforma e-postmeddelanden i Campaign?

Viktiga riktlinjer: se till att designen fungerar mobilt, använd HTML 4.0/XHTML-kompatibel kod med infogad CSS, optimera bilder (under 100 kB) med alternativ text, använd fält för sammanslagning av personalisering, testa mellan e-postklienter innan de skickar samt inkludera en vanlig textversion. Sikta mot en total e-poststorlek på mindre än 500 kB för optimal leverans.

[Guide för e-postdesign](../send/email.md) | [Bästa tillvägagångssätt vid leverans](delivery-best-practices.md)

+++

+++ Vad är en leveransmall?

En leveransmall är en förkonfigurerad leverans som sparar alla inställningar och parametrar för återanvändning i flera kampanjer. Mallarna innehåller målregler, innehållsdesign, personalisering, tekniska inställningar (avsändare, svar) och typologiregler. Skapa en gång och återanvänd för att bibehålla enhetligheten och snabba upp kampanjskapandet.

[Skapa leveransmallar](../send/create-templates.md)

+++

+++ Kan jag enkelt importera en befintlig HTML för att skapa ett e-postmeddelande i Campaign?

Ja. Importera HTML-material direkt i content editor, ladda upp filer från datorn eller ladda in från en webbadress. Se till att din HTML använder e-postkompatibel kod (HTML 4.0/XHTML) med intern CSS och lagra bilderna på en offentlig server. Campaign lägger automatiskt till personalisering och spårning till importerade HTML.

>[!TIP]
>
>Använd **E-post-Designer** i gränssnittet för Campaign-webben, som erbjuder moderna dra-och-släpp-funktioner och inbyggda responsiva mallar, i stället för att importera HTML i Raw-format.

[Importera HTML-innehåll](../send/defining-the-email-content.md)

+++

+++ Hur skapar jag ett prenumerationsbaserat nyhetsbrev i Campaign?

Ja. Använd Campaigns informationstjänster för att hantera prenumerationer på nyhetsbrev. Nyckelfunktioner är automatisk hantering av anmälan/avanmälan, prenumerationsspårning, efterlevnadshantering (GDPR, CAN-SPAM), stöd för flera nyhetsbrev, webbintegrering för registreringsformulär och riktad leverans till prenumeranter.

[Hantera prenumerationer](../start/subscriptions.md)

+++

+++ Hur kan jag personalisera meddelanden?

Campaign erbjuder personaliseringsfunktioner för att skapa relevanta, målinriktade meddelanden baserade på mottagardata, beteende och preferenser.

**Personalization-alternativ:**

* **Anpassningsfält** - Infoga mottagardata (t.ex. `"Hello {{firstName}}")`
* **Personaliseringsblock** - Använd fördefinierade eller anpassade innehållsblock
* **Villkorligt innehåll** - Visa annat innehåll baserat på mottagarvillkor
* **Beteendedata** - Utnyttja webbhistorik, inköpsmönster eller engagemangsmått

Testa personaliseringen innan du skickar för att verifiera att kopplingsfält och villkorslogik fungerar korrekt.

[Personalization-guide](../send/personalize.md) | [Anpassningsfält](../send/personalization-fields.md) | [Villkorligt innehåll](../send/conditions.md)

+++

+++ Kan jag skicka flerspråkiga meddelanden?

Ja. Campaign v8 erbjuder flerspråkiga funktioner, där **gränssnittet för Campaign-webben** är det enklaste sättet. Webbgränssnittet har inbyggt flerspråkigt stöd med språkvarianter - lägg till språkvarianter till leveransen så skickar Campaign automatiskt rätt version baserat på mottagarens språk. Finns för e-post, push-meddelanden, SMS och transaktionsmeddelanden.

Viktiga funktioner: automatisk kopiering av innehåll, automatisk språkbaserad sändning, standardspråkreservationer och enkel hantering av varianter.

Klientkonsolen stöder även flerspråkigt innehåll med villkorsstyrt innehåll och arbetsflöden, men kräver mer manuell konfiguration.

[Flerspråkiga leveranser (webbgränssnitt)](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/multilingual){target="_blank"} | [Villkorligt innehåll (klientkonsol) &#x200B;](../send/conditions.md)

+++

+++ Kan jag lokalisera ett webbformulär?

Ja. Kampanjwebbapplikationer har stöd för flerspråkig lokalisering. Definiera översättningar för alla formulärelement (etiketter, knappar, meddelanden, feltext) med automatisk språkidentifiering som baseras på mottagarprofil eller webbläsarinställningar. Flera språkversioner stöds i ett och samma webbprogram, med återgång till ett standardspråk vid behov.

[Webbprogramlokalisering](../dev/webapps.md)

+++

+++ Kan jag använda AI-baserat innehåll i mina e-postmeddelanden?

Ja, men **endast via Campaign Web-gränssnittet**. AI Assistant, som bygger på Microsoft Azure OpenAI och Adobe Firefly, hjälper dig att skapa professionellt, varumärkesenhetligt innehåll för e-post, SMS och push-meddelanden.

**Nyckelfunktioner:**

* Generera text (e-postkopia, ämnesrader, SMS/push-innehåll) och varumärkesanpassade bilder
* Skapa innehållsvariationer som är optimerade för olika målgrupper
* Förfina innehåll (bearbeta, sammanfatta, omformulera, förenkla)
* Överför varumärkesresurser och få poäng för varumärkesanpassning
* Använd befintligt innehåll som referens och överför stilreferensbilder

>[!NOTE]
>
>AI Assistant finns endast i gränssnittet för Campaign Web och har för närvarande endast stöd för engelska. Användarna behöver rätt behörigheter och måste godkänna ett användaravtal.

[Översikt över AI Assistant](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/generative-gs){target="_blank"} | [&#x200B; Användningsexempel för AI-assistenten &#x200B;](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/generative-uc){target="_blank"} | [Märkesjustering](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/ai-assistant/brands-score){target="_blank"}

+++

## Testa och skicka meddelanden {#send}

Lär dig de bästa sätten att testa, validera, skicka och spåra era marknadsföringsmeddelanden för att säkerställa att kampanjen kan levereras.

+++ Vad är leveransanalysen?

Leveransanalys är en valideringsfas Kampanjen körs innan den skickas. Den beräknar målpopulationen, validerar innehållet, söker efter fel, tillämpar typologiregler och beräknar leveransvolym.

Campaign genererar loggar med varningar och fel. Fel vid blockleverans och måste åtgärdas. Varningar är rådgivande. Granska alltid analysloggarna innan de skickas.

[Leveransanalysguide](../send/delivery-analysis.md)

+++

+++ Varför ska jag skapa korrektur?

Korrektur är testmeddelanden som validerar leveransen innan de skickas till huvudmålgruppen. Använd korrektur för att verifiera personalisering, testa innehållsåtergivning mellan e-postklienter, bekräfta länkar och spåra arbete, kontrollera bilder och bilagor och validera mobilrespons.

Korrektur hjälper till att fånga upp fel innan de når tusentals mottagare, aktivera godkännande av intressenter och testa placeringen av inkorgen. Skicka korrektur till flera e-postklienter och enheter och få alltid godkännande före produktionens utskick.

[Korrektur och förhandsgranskningshandbok](../send/preview-and-proof.md)

+++

+++ Hur använder man startadresser i Adobe Campaign?

Seed-adresserna läggs automatiskt till i varje leverans för testning, kvalitetssäkring och övervakning, utan att de uppfyller målvillkoren. Användbar för kontinuerlig övervakning, testning av inkorgsplacering, direktreklamvalidering och synlighet för intressenter.

**Viktiga skillnader jämfört med korrektur:**

* **Utdirigerade adresser** - har lagts till automatiskt i produktionsleveranser och räknas som utskicksvolym
* **Korrektur** - Testet skickar före produktion, räkna inte med volymen som används för validering

Hantera dirigerade adresser i **[!UICONTROL Resources > Campaign management > Seed addresses]**. Håll listorna små så att leveransstatistik inte påverkas.

[Guiden för dirigerade adresser](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/delivery-control.html){target="_blank"}

+++

+++ Hur kan jag konfigurera en godkännandeprocess innan jag skickar meddelanden?

Campaign tillhandahåller arbetsflöden för godkännande för att säkerställa att meddelandena uppfyller kvalitetsstandarderna innan de skickas. Konfigurera godkännanden för innehåll, mål, extrahering (direktreklam) och budget på kampanj- eller leveransnivå.

**Inställningar:**

Skapa operatorgrupper i **[!UICONTROL Administration > Access management > Operator groups]** och tilldela sedan godkännandegrupper i kampanj- eller leveransegenskaper. Campaign skickar e-postmeddelanden till granskare som kan godkänna, avvisa eller begära ändringar.

**För fristående leveranser (inte i en kampanj):**

Använd **korrektur som godkännandeprocess**. Skicka korrektur till godkännandegruppen för validering och skicka alltid ett nytt bevis efter att ha gjort ändringar för att säkerställa att alla intressenter granskar den senaste versionen.

[Leveransvalidering](../send/preview-and-proof.md) | [Kampanjgodkännanden](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html){target="_blank"}

+++

+++ Vad är en typologiregel?

Typologiregler är automatiserade affärslogik som tillämpas under leveransanalysen för att validera och optimera meddelandeutskick. De säkerställer att marknadsföringsprinciperna följs, skyddar slutresultatet och förhindrar att kunderna tröttnar.

**Huvudregeltyper:**

* **Filtreringsregler** - Uteslut mottagare (blocklist, ej prenumererade, i karantän)
* **Tryckregler** - Kontrollera meddelandefrekvensen för att undvika överväldigande mottagare
* **Kapacitetsregler** - Begränsa meddelandevolymen för bearbetningskapacitet eller ISP-begränsningar
* **Kontrollregler** - Kontrollera meddelandets giltighet (ämnesrad, länk för att avbryta prenumerationen, avsändarformat)

Reglerna grupperas i typologier och tillämpas under leveransanalysen. Kampanjen kan utesluta mottagare, blockera leveransen eller generera varningar baserat på reglerna.

[Guiden för typologiregler](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html){target="_blank"}

+++

+++ Hur kan jag skicka e-post i påfyllnader?

Ja. Våg som skickar delar upp leveransen i flera batchar som skickas enligt schemalagda intervall. Detta är nödvändigt för stora kampanjer för att balansera serverbelastningen, förhindra strypning av Internet-leverantörer, bygga upp avsändarens anseende med nya IP-adresser och hantera avanmälningar/studsar mellan vågor.

**Konfiguration:**

Aktivera påfyllnadssändning i leveransegenskaperna och definiera antalet påfyllnader (eller batchstorlek), intervallet mellan påfyllnader och vågfördelningen (linjära eller anpassade procentsatser). Campaign delar automatiskt upp målpopulationen och skickar varje våg i tid.

Använd vågor för stora kampanjer, övervaka första vågens prestanda innan du fortsätter och ge tillräckligt med tid mellan vågor för att bearbeta studsar och avanmäla dig.

[Konfigurera påfyllnadssändning](../send/configure-and-send.md#sending-using-multiple-waves)

+++

+++ Vilka är de viktigaste stegen för att skapa ett e-postmeddelande i Campaign?

Att skapa ett e-postmeddelande i Campaign v8 inbegriper följande viktiga steg: skapa leveransen, definiera målgruppen, utforma innehållet, lägga till personalisering, konfigurera inställningar (avsändare, ämne, svar), köra leveransanalys, skicka korrektur för testning och slutligen skicka eller schemalägg.

**Viktiga steg:**

1. **Skapa leveransen** - Välj e-post som kanal och välj en leveransmall om du vill.
1. **Definiera målet** - Välj mottagare med hjälp av frågor, listor eller importerade filer
1. **Designa innehållet** - Skapa ditt meddelande med e-postredigeraren (e-post för webbgränssnitt, Designer eller klientkonsolredigeraren)
1. **Lägg till personalisering** - Infoga dynamiska fält, anpassningsblock och villkorligt innehåll
1. **Konfigurera inställningar** - Ange avsändaradress, ämnesrad, svar och leveransparametrar
1. **Kör leveransanalys** - Kampanjen validerar innehåll, beräknar målet och söker efter fel
1. **Skicka korrektur** - Testa din e-post med godkännandegrupper för att validera återgivning och innehåll
1. **Skicka eller schemalägg** - Skicka omedelbart till huvudmålet eller schemat för ett senare datum

**Två gränssnittsalternativ:**

* **Webbgränssnitt för kampanj** - Modernt gränssnitt med förbättrade funktioner för e-post, Designer, AI Assistant och flera språk
* **Klientkonsol** - Traditionellt gränssnitt med avancerade målnings- och arbetsflödesfunktioner


>[!TIP]
>
>Använd Campaigns webbgränssnitt för att skapa e-postmeddelanden snabbare och mer intuitivt med moderna designverktyg. Använd klientkonsolen för komplex målgruppsanpassning eller avancerade arbetsflödesbaserade kampanjer.

[Skapa ditt första e-postmeddelande](create-message.md) | [Guide för e-postdesign](../send/email.md)

+++

+++ Hur schemalägger jag en leverans?

Med Campaign kan ni schemalägga leveranser för framtida sändningar för att optimera sändningstiderna och samordna kampanjer.

**Schemaläggningsalternativ:**

* **Leveransegenskaper** - Skicka omedelbart, schemalägg för ett specifikt datum/tid eller vänta i timmar/dagar
* **Kampanjnivå** - Koordinera alla leveranser i en kampanj
* **Schemaläggaraktivitet för arbetsflöde** - För återkommande leveranser, komplexa mönster och händelseutlösta kampanjer

Campaign har också stöd för optimering av kontaktdatum (bästa sändningstid per mottagare) och anpassning av tidszon (samma lokala tid för alla mottagare).

[Schemalägg leverans](../send/configure-and-send.md#schedule-delivery-sending)

+++

+++ Kan jag lägga till en bilaga i e-postmeddelanden?

Ja. Campaign stöder statiska bilagor (samma fil för alla mottagare) och anpassade bilagor (olika filer per mottagare baserat på profildata). Lägg till bifogade filer i avsnittet **[!UICONTROL Attachments]** i leveransegenskaperna.

**Viktiga överväganden:**

* Behåll bilagor under 1 MB för optimal leverans
* Bifogade filer kan utlösa skräppostfilter; testa noggrant innan de skickas
* Undvik filtyper som ofta blockeras av e-postklienter (.exe, .zip, .js)
* För stora filer bör du använda spårade nedladdningslänkar i stället

Använd säkra filformat (PDF, JPEG, PNG, DOCX) och testa med dirigerade adresser innan produktionen skickas.

[Guiden för e-postbilagor](../send/email.md#attachments)

+++

+++ Hur konfigurerar jag spårade länkar i en e-postleverans?

Campaign konverterar automatiskt alla URL:er i ditt e-postmeddelande till spårade länkar för att övervaka mottagarnas engagemang. Gå till avsnittet **[!UICONTROL Tracking]** i leveransen för att konfigurera spårningsinställningar för varje länk.

**Konfigurationsalternativ:**

* **Aktivera/inaktivera spårning** - Kontrollspårning per länk
* **Länketiketter** - Lägg till beskrivande namn för rapportering (t.ex. &quot;Shop Now CTA&quot;)
* **Länkkategorier** - Gruppera länkar efter typ för aggregerad analys
* **Spårningstyp** - Spåra klick, öppningar eller båda

Campaign spårar innehållslänkar, länkar till spegelsidor, länkar för att avbryta prenumerationen och kan innehålla en valfri spårningspixel för att öppna e-postmeddelanden. Använd meningsfulla etiketter och kategorier för att förenkla rapporteringen och snabbt identifiera högpresterande innehåll.

[Länkspårningsguide](../start/tracking.md) | [Följ upp bästa praxis](../send/send.md)

+++

+++ Var kan jag komma åt leverans- och spårningsloggar?

Få åtkomst till leverans- och spårningsloggar direkt från varje kontrollpanel. Klicka på fliken **[!UICONTROL Delivery]** längst ned i klientkonsolen. Navigera till avsnittet **[!UICONTROL Logs]** i webbgränssnittet för Campaign.

**Tillgängliga loggar:**

* **Leveransloggar** - Skickade meddelanden med mottagarinformation och status (skickade, väntande, misslyckades)
* **Spårningsloggar** - Mottagarinteraktioner (öppnas, klickas) med tidsstämplar
* **Uteslutningsloggar** - Uteslutna mottagare med orsaker (karantän, typologiregler, dubbletter)
* **Sändningsloggar** - Slutför sändningshistorik inklusive återförsök och fel

Använd dessa loggar för att felsöka leveransproblem, analysera engagemang och upprätthålla listhygienen.

[Leveransövervakning](../send/send.md) | [Spårningsguide](../start/tracking.md)

+++

+++ Var kan jag få leveransrapporter?

Campaign innehåller omfattande inbyggda rapporter för att analysera leveransresultat, mottagarnas engagemang och kampanjens effektivitet. Få åtkomst till rapporter från fliken **[!UICONTROL Reports]** i alla leveranser, från kontrollpanelen för kampanjer eller från den globala **[!UICONTROL Reports]**-menyn för analys av olika kampanjer.

**Viktiga rapporter omfattar:**

* **Leveranssammanfattning** - Skicka statistik, öppna, klicka, studsa och avsluta prenumerationer
* **Snabbklickningar** - Visuell heatmap för länkprestanda
* **Spårningsindikatorer** - Genomklickningsfrekvenser och engagemangsmått
* **Ej levererbara** - Studsanalys med felorsaker

Rapporter finns både i klientkonsolen och i webbgränssnittet för Campaign med moderna visualiseringar.

[Inbyggda leveransrapporter](../reporting/delivery-reports.md) | [Kampanjrapportering](../reporting/gs-reporting.md)

+++

+++ Hur kvalificerar och hanterar Adobe Campaign karantänadresser?

Campaign hanterar automatiskt en karantänlista för att skydda avsändarens rykte och förbättra leveransen. Adresser i karantän exkluderas automatiskt från framtida leveranser tills de valideras eller tas bort från karantän.

**Varför adresser sätts i karantän:**

* **Hårda gränser** - Permanenta leveransfel (ogiltig e-postadress, domänen finns inte, postlådan har tagits bort)
* **Tröskelvärde för avhoppning** - Upprepade tillfälliga fel (postlådan är full, servern är tillfälligt otillgänglig) överskrider feltröskeln
* **Skräppost** - Mottagare markerar dina e-postmeddelanden som skräppost
* **Ogiltiga adresser** - Adresser med syntaxfel eller som inte kan valideras
* **Blocklist** - Mottagare som har avanmält sig eller begärt att bli undantagna

**Så här fungerar karantän:**

Kampanjen spårar leveransfel för varje adress. När en adress når det konfigurerade feltröskelvärdet sätts den automatiskt i karantän och utesluts från alla framtida leveranser under analysen. Hårda studsar (permanenta fel) sätts i karantän omedelbart, medan mjuka studsar kräver flera fel före karantänen.

**Hantera adresser i karantän:**

Åtkomst till karantänhantering i **[!UICONTROL Administration > Campaign Management > Non deliverables Management]**. Du kan visa adresser i karantän, ta bort verifierade adresser manuellt från karantän eller konfigurera automatiska rensningsregler.

>[!TIP]
>
>Övervaka din karantänlista regelbundet. Om du ökar karantänfrekvenserna signaleras ofta problem med datakvaliteten som behöver åtgärdas innan de påverkar avsändarens anseende.

[Karantänhanteringsguide](../send/quarantines.md) | [Studshantering](../send/delivery-failures.md)

+++

## Arbetsflöden {#workflows}

Upptäck hur du använder arbetsflöden för att automatisera processer, hantera data och samordna komplexa marknadsföringskampanjer i Adobe Campaign.

+++ Vilka är de viktigaste stegen för att skapa ett arbetsflöde?

Skapa arbetsflöden för att automatisera marknadsföringsprocesser i Campaign:

1. **Skapa ett nytt arbetsflöde** - Navigera till **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** eller **[!UICONTROL Administration > Production > Technical workflows]** och klicka på **[!UICONTROL Create]**
1. **Lägg till aktiviteter** - Dra och släpp aktiviteter från paletten (mål, flödeskontroll, åtgärdsaktiviteter)
1. **Konfigurera aktiviteter** - Dubbelklicka på varje aktivitet för att ange parametrar och definiera logik
1. **Koppla aktiviteter** - Länka aktiviteter med övergångar för att definiera körningsflödet
1. **Testa och validera** - Använd arbetsflödesdiagrammet för att kontrollera logiken och testa sedan med en liten datauppsättning
1. **Kör** - Starta arbetsflödet manuellt eller schemalägg det för automatisk körning

Vanliga arbetsflödesmönster: dataimport, målgruppssegmentering, leverans, databerikning och flerkanalsmarknadsföring.

**Relaterade ämnen:**

* [Bygga ett arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"}
* [Arbetsflödesaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/about-activities.html){target="_blank"}
* [God praxis för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}
* [Användningsexempel för arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/about-workflow-use-cases.html){target="_blank"}

+++

+++ Hur importerar jag data i Campaign?

Importera data till Campaign på flera olika sätt beroende på era behov:

**Enkel filimport:**

* Använd importguiden för engångsimporter av CSV/TXT med guidat gränssnitt
* Perfekt för manuella överföringar och snabba dataladdningar

**Arbetsflödesbaserad import:**

* Skapa arbetsflöden med **[!UICONTROL Data loading (file)]**-aktivitet för komplexa importer
* Lägg till dataomvandlingar, anrikning och borttagning av dubbletter
* Schemalägg återkommande importer från SFTP, lokala kataloger eller molnlagring

**API-integrering:**

* Använd REST API:er för att importera data programmatiskt från externa system
* Perfekt för synkronisering i realtid med CRM, e-handel eller andra plattformar

**Bästa tillvägagångssätt:** Testa alltid med små samplingar, använd UTF-8-kodning, mappa fält korrekt, tillämpa dedupliceringsregler och schemalägg stora importer under tider med låg belastning.

**Relaterade ämnen:**

* [God praxis för import](../start/import.md)
* [Datainläsningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"}
* [Återkommande importarbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/recurring-import-workflow.html){target="_blank"}

+++

+++ Kan jag övervaka arbetsflödeskörningen?

Ja. Campaign innehåller omfattande funktioner för arbetsflödesövervakning för att spåra körning, identifiera problem och optimera prestanda.

**Övervakningsalternativ:**

* **Kontrollpanel för arbetsflöde** - Visa körningsstatus, förlopp och aktivitetstillstånd i realtid
* **Körningsloggar** - Få åtkomst till detaljerade loggar för varje aktivitet och övergång
* **Granskningsspår** - Spåra ändringar i arbetsflödet och körningshistorik
* **Varningar och meddelanden** - Konfigurera e-postvarningar för fel eller specifika villkor

**Viktiga övervakningsfunktioner:**

* Visuella statusindikatorer (väntande, pågående, slutförd, misslyckades)
* Spåra körningstid för prestandaoptimering
* Felmeddelanden på aktivitetsnivå för felsökning
* Pausa, stoppa eller starta om arbetsflöden efter behov

Åtkomstövervakning från **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]** eller direkt från arbetsflödets kontrollpanel.

**Relaterade ämnen:**

* [Övervaka arbetsflödeskörning](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}
* [God praxis för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}
* [Starta ett arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/executing-a-workflow/start-a-workflow.html){target="_blank"}

+++

+++ Hur uppdaterar jag Campaign-data med ett arbetsflöde?

Använd aktiviteten **[!UICONTROL Update data]** i arbetsflöden för att utföra massåtgärder på din databas:

**Åtgärder som stöds:**

* **Infoga** - Lägg till nya poster i databasen
* **Uppdatera** - Ändra befintliga poster baserat på matchande villkor
* **Infoga eller uppdatera** - Lägg till nya poster eller uppdatera befintliga (upsert)
* **Ta bort** - Ta bort poster som matchar specifika villkor

**Vanliga användningsområden:**

* Uppdatera profilattribut efter databerikning
* Synkronisera data med externa system
* Underhåll listmedlemskap baserat på beteende
* Rensa och deduplicera data
* Använda statusändringar (t.ex. avanmälan, karantän)

Konfigurera avstämningsnycklar så att de matchar poster korrekt och välj uppdateringsalternativ (uppdatera alla fält eller endast tomma fält).

**Relaterade ämnen:**

* [Uppdatera dataaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html){target="_blank"}
* [Datahanteringsaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/about-action-activities.html){target="_blank"}

+++

+++ Hur kan jag utnyttja datahanteringsfunktionerna?

Kampanjens datahanteringsaktiviteter möjliggör sofistikerade dataåtgärder i arbetsflöden för komplex målinriktning och segmentering.

**Viktiga datahanteringsaktiviteter:**

* **Berikning** - Lägg till data från relaterade tabeller eller externa källor i din arbetspopulation
* **Dela** - Segmentera populationer baserat på kriterier eller fördela slumpmässigt
* **Deduplicering** - Ta bort dubblettposter baserat på angivna nycklar
* **Uppdatera data** - Utför massinfogning, uppdatering eller borttagning
* **Ändra dimension** - Växla målinriktningsdimensioner (t.ex. från mottagare till prenumerationer)
* **Tvärsnitt/Förening/Uteslutning** - Kombinera eller filtrera flera populationer

**Vanliga användningsområden:**

* Förbättra profiler med inköpshistorik eller beteendedata
* Segmentera målgrupper i flera grupper för olika budskap
* Ta bort dubbletter före leverans
* Integrera data från externa databaser (FDA - Federated Data Access)
* Skapa komplexa flertabellsfrågor och kopplingar

Med de här aktiviteterna kan du arbeta med data som inte finns direkt i huvudmottagartabellen och utföra avancerade databasåtgärder.

**Relaterade ämnen:**

* [Datahanteringsaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/about-targeting-activities.html){target="_blank"}
* [Målarbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}
* [Anrikningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}

+++

+++ Kan jag automatisera utskick av personaliserade meddelanden?

Ja. Arbetsflödena möjliggör helautomatiserade, personaliserade meddelandekampanjer baserade på mottagardata, beteende och anpassade kriterier.

**Struktur för automatiseringsarbetsflöde:**

1. **Fråga** - Välj målgrupp baserat på kriterier
1. **Anrikning** - Lägg till personaliseringsdata från relaterade tabeller
1. **Dela** - Segmentera i grupper för olika meddelandevarianter (valfritt)
1. **Leverans** - Skicka personliga meddelanden med kopplingsfält
1. **Schemaläggaren** - Konfigurera återkommande körning för automatiska kampanjer

**Personalization-alternativ:**

* Använd data för mottagarprofil (namn, plats, inställningar)
* Inkludera beteendedata (inköpshistorik, engagemangspoäng)
* Använd villkorsstyrt innehåll baserat på segment eller attribut
* Beräkna dynamiska värden (förmånspoäng, utgångsdatum)

Vanliga scenarier: födelsedagskampanjer, övergivna varukorgar, lojalitetsprogram, återvinnningskampanjer och händelseutlösta meddelanden.

**Relaterade ämnen:**

* [Personalization Guide](../send/personalize.md)
* [Användningsexempel för arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/send-a-birthday-email.html){target="_blank"}
* [Anrikningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}

+++

+++ Hur kan jag dela en målgrupp i delmängder med ett arbetsflöde?

Använd aktiviteten **[!UICONTROL Split]** för att dela upp en enskild population i flera deluppsättningar baserat på kriterier eller distributionsregler.

**Delade metoder:**

* **Filtreringsvillkor** - Skapa delmängder baserade på villkor (t.ex. åldersgrupper, plats, VIP-status)
* **Procentfördelning** - Dela slumpmässigt i lika eller anpassade procentandelar för A/B-testning
* **Begränsa poster** - Begränsa delmängdsstorlekar (första N-poster, övre X%, slumpmässigt urval)
* **Datagrupper** - Skapa en delmängd per distinkt värde (t.ex. en delmängd per land)

**Vanliga användningsområden:**

* A/B-testning med kontrollgrupper
* Kanalinställningsroutning (e-post kontra SMS)
* Progressiv utrullning (skicka till 10 %, sedan 90 %)
* Segmentspecifika meddelanden (VIP, vanliga, nya kunder)
* Belastningsutjämning mellan flera leveransservrar

Varje delmängd flödar till en separat övergång, vilket ger olika bearbetning eller leverans för varje grupp.

**Relaterade ämnen:**

* [Delad aktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}
* [A/B-testguide](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/a-b-testing.html){target="_blank"}

+++

+++ Hur uppdaterar jag mottagardata från en extern fil?

Ja. Använd arbetsflöden för att uppdatera kampanjdata med värden från externa filer (CSV, TXT).

**Arbetsflödesstruktur:**

1. **Datainläsning (fil)** - Läs in den externa filen och mappa kolumner
1. **Berikning** (valfritt) - Lägg till ytterligare data eller omformningar
1. **Avstämning** - Definiera nycklar för att matcha filposter med databasposter (t.ex. e-postadress, mottagar-ID)
1. **Uppdatera data** - Välj uppdateringsalternativ:
   * Uppdatera endast matchade poster
   * Uppdatera befintliga fält eller bara tomma fält
   * Infoga nya poster om ingen matchning hittades

**Vanliga scenarier:**

* Uppdatera profilattribut från CRM-exporter
* Uppdatera prenumerationsstatus från externa system
* Synkronisera kundpoäng
* Uppdatera inställningar för anmälan/avanmälan
* Förbättra profiler med beteendedata

**God praxis:** Använd unika identifierare för avstämning, validera data före uppdatering, testa med små samplingar och schemalägg regelbundna uppdateringar för pågående synkronisering.

**Relaterade ämnen:**

* [Importera dataguide](../start/import.md)
* [Datainläsningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"}
* [Uppdatera dataaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html){target="_blank"}

+++

+++ Hur kan jag identifiera och inrikta mig på nya mottagare?

Använd arbetsflöden med frågeaktiviteter för att identifiera nyligen tillagda mottagare och utlösa automatiska välkomstkampanjer.

**Frågesätt:**

Skapa en frågefiltrering i fältet **[!UICONTROL Created date]** för att välja mottagare som lagts till inom en viss tidsram (t.ex. senaste 24 timmarna, förra veckan).

**Automatiserad struktur för välkomstarbetsflöde:**

1. **Schemaläggaren** - Kör dagligen eller med specifika intervall
1. **Fråga** - Välj mottagare som har skapats sedan den senaste körningen
1. **Deduplicering** (valfritt) - Kontrollera inga dubbletter
1. **Leverans** - Skicka välkomstmeddelande
1. **Uppdatera data** (valfritt) - Markera mottagare som &quot;välkomna&quot;

**Avancerad teknik med mängder:**

Använd sammanställningsfunktioner för att dynamiskt identifiera de senaste tilläggen och jämföra dem med tidigare bearbetade mottagare för avancerad identifiering av nya mottagare.

**Relaterade ämnen:**

* [Frågeaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}
* [Använda aggregat](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/using-aggregates.html){target="_blank"}
* [Välkomstprogram](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/send-a-birthday-email.html){target="_blank"}

+++

+++ Hur använder jag arbetsflödesaktiviteter?

Kampanjarbetsflöden byggs med fyra huvudkategorier av aktiviteter, som alla har specifika syften:

**Målinriktade aktiviteter** - Definiera och förfina din målgrupp

* Fråga, dela, ta bort dubbletter, anrikning, skärning, union, uteslutning
* Använd dessa för att välja mottagare, segmentera populationer och kombinera datakällor

**Flödeskontrollaktiviteter** - Hantera arbetsflödeslogik och timinginställningar

* Schemaläggaren, Vänta, Testa, Fork, AND-join, OR-join, Jump
* Styr körningsflödet, lägg till villkor och hantera parallella banor

**Åtgärdsaktiviteter** - Utför åtgärder och skicka meddelanden

* Leverans, Uppdatera data, Inläsning av data (fil), Dataextrahering (fil), JavaScript-kod
* Kör databasåtgärder, filöverföringar och meddelandeöverföring

**Händelseaktiviteter** - Reagera på externa utlösare

* Extern signal, filinsamlare, HTTP-överföring, SMS, e-post
* Hantera inkommande data och externa systeminteraktioner

Om du vill använda aktiviteter drar du dem från paletten till arbetsytan, dubbelklickar för att konfigurera parametrar och kopplar dem till övergångar.

**Relaterade ämnen:**

* [Referens för målaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/targeting-activities.html){target="_blank"}
* [Referens för flödeskontrollaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/flow-control-activities.html){target="_blank"}
* [Åtgärdsaktivitetsreferens](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html){target="_blank"}
* [Händelseaktiviteter - referens](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/event-activities.html){target="_blank"}

+++

+++ Vad är de effektivaste strategierna för arbetsflöden?

Följ dessa standarder för att skapa effektiva, underhållbara och tillförlitliga arbetsflöden:

**Design och organisation:**

* Använd tydliga, beskrivande namn för arbetsflöden och aktiviteter
* Lägga till etiketter och beskrivningar i dokumentlogiken
* Gruppera relaterade aktiviteter visuellt för läsbarhet
* Dela upp komplexa processer i flera mindre arbetsflöden

**Prestandaoptimering:**

* Begränsa frågeresultatstorlekar med lämpliga filter
* Använd temporära tabeller för mellanlagring av data
* Schemalägg resurskrävande arbetsflöden under tider med låg belastning
* Undvik onödiga slingor och alltför många iterationer

**Felhantering och övervakning:**

* Lägga till felhanteringssökvägar med ansvariga
* Konfigurera varningar för misslyckade arbetsflöden
* Testa med små dataprov innan hela exekveringen är klar
* Granska körningsloggar regelbundet för att se om det finns prestandaproblem

**Underhåll och styrning:**

* Arkivera eller ta bort föråldrade arbetsflöden
* Ändringar i arbetsflödet för versionskontroll och dokumentändringar
* Begränsa arbetsflödets komplexitet (mål för &lt; 20 aktiviteter)
* Använd arbetsflödesmallar för återkommande mönster

**Säkerhet och datahantering:**

* Använd lämpliga behörigheter för operatorn
* Rensa tillfälliga data med arbetsflödesrensning
* Undvik hårdkodsvärden - använd variabler och alternativ
* Granska och optimera dåligt fungerande arbetsflöden regelbundet

**Relaterade ämnen:**

* [Handbok om arbetsflöden för bästa praxis](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}
* [Bygga ett arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"}
* [Övervaka arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}

+++

## Kampanjinställningar {#settings}

Konfigurera Campaign-instansen med rätt inställningar, integreringar och konfigurationer för att optimera era marknadsföringsåtgärder.

+++ Kan jag ändra språket i Campaign-gränssnittet?

Språket i Campaign väljs när instansen skapas. Du kan inte ändra det i efterhand. Mer information om detta finns i [det här avsnittet](../start/connect.md).

Adobe Campaign användargränssnitt finns på flera språk: engelska, franska, tyska, japanska med flera. Observera att klientkonsolen och servern måste vara inställda på samma språk. Varje instans i Campaign kan bara köras på ett språk.

När du installerar Campaign på engelska kan du välja antingen amerikansk engelska eller brittisk engelska: de skiljer sig åt när det gäller datum- och tidsformat.

+++

+++ Kan jag använda Campaign v8 med andra Adobe-lösningar?

Du kan kombinera leveransfunktionerna och de avancerade funktionerna för kampanjhantering i Adobe Campaign med en uppsättning lösningar som hjälper till att personalisera användarnas upplevelse.

[Lär dig hur du arbetar med andra Adobe-lösningar](../connect/integration.md) och [hur du konfigurerar IMS i Campaign](../start/connect.md).

+++

+++ Hur ställer jag in spårningsfunktioner för min Campaign-instans?

Som erfaren användare kan du konfigurera spårningsfunktioner i Campaign-instansen.

[Läs mer](../start/tracking.md).

+++

+++ Hur konfigurerar man e-postleveransen?

Förutom [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"} kan du läsa de tekniska rekommendationerna för slutbarhet för att förstå hur du konfigurerar instansen för att maximera leveransen av funktioner i Campaign.

[Läs mer](../send/about-deliverability.md).

+++

+++ Hur kan jag implementera innehållsgodkännande?

Med Campaign kan du skapa godkännandeprocesser för de viktigaste stegen i marknadsföringskampanjen i samarbetsläge. För varje kampanj kan du godkänna leveransmålet, innehållet och kostnaderna. Adobe Campaign-operatörer som ansvarar för godkännande kan meddelas via e-post och kan godkänna eller avvisa godkännanden från konsolen eller via en webbanslutning.

[Läs mer](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html){target="_blank"} och upptäck steg för att implementera ditt godkännande av leveransinnehåll i Campaign.

+++

+++ Hur får jag åtkomst till data som lagras i en extern databas?

Adobe Campaign tillhandahåller alternativet federerad dataåtkomst (FDA) för att bearbeta information som lagras i en eller flera externa databaser. Du kan få åtkomst till externa data utan att ändra datastrukturen i Adobe Campaign.

[Läs mer](../connect/fda.md).

+++

+++ Vilka externa databaser kan jag ansluta Campaign till?

Externa databaser som är kompatibla med Campaign via federerad dataåtkomst (FDA) listas i [kompatibilitetsmatrisen](compatibility-matrix.md).

+++

+++ Kan Adobe Campaign integreras med CRM-system?

Adobe Campaign tillhandahåller olika CRM-kopplingar för att länka din plattform i Adobe Campaign till dina tredjepartssystem. Med dessa CRM-kopplingar kan du synkronisera kontakter, konton och inköp osv. De låter dig enkelt integrera din applikation med olika tredjeparts- och företagsapplikationer.

Dessa kopplingar möjliggör snabb och enkel dataintegrering: Adobe Campaign tillhandahåller en dedikerad assistent för att samla in och välja mellan de tabeller som är tillgängliga i CRM. Detta garanterar dubbelriktad synkronisering för att säkerställa att data alltid är aktuella i alla system.

[Läs mer](../connect/crm.md) om hur du synkroniserar CRM-verktyget med Adobe Campaign.

+++

+++ Hur rensar jag klientkonsolcachen?

Om du har problem med till exempel nya logotyper som inte återspeglas korrekt, eller problem med att exportera data, kan du behöva rensa klientkonsolens cache.

Logga ut och stäng klientkonsolen. Navigera till följande plats baserat på ditt operativsystem:

* Windows: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
* Mac: `~/Library/Application Support/Neolane/NL_5/`

Ta bort XML-konfigurationsfilerna (med `nlclient_cnx.xml`) och logga sedan in på klientkonsolen igen.

+++

+++ Kan jag konfigurera gränssnittsinställningar?

Ja, som administratör kan du anpassa gränssnittsinställningarna för kampanjer för dina användare. [Läs mer](../config/ui-settings.md).

+++

+++ Kan jag skapa anpassade fält och tabeller?

Ja, med Campaign v8 kan ni utöka datamodellen med anpassade fält och tabeller. Lär dig [utöka scheman](../dev/extend-schema.md).

+++

## Rapportering {#reporting}

Få insikter om Campaigns rapporteringsfunktioner, inklusive inbyggda rapporter, anpassade rapporter och verktyg för dataanalys som kuber.

+++ Hur skapar jag nya rapporter?

Förutom inbyggda rapporter kan du med Adobe Campaign generera rapporter i olika sammanhang och för att tillgodose olika behov.

Adobe Campaign är inte ett specialiserat rapporteringsverktyg. Rapporter som skapas i Adobe Campaign låter dig i huvudsak se aggregerade data.

[Läs mer](../reporting/gs-reporting.md) om rapportfunktioner för Campaign.

+++

+++ Hur kan jag utforma och dela statistiska rapporter om populationer?

Med Adobe Campaign [beskrivande analysrapporter](../reporting/built-in-reports.md) kan du utforma och dela statistiska rapporter om dina populationer.

[Läs mer](../reporting/built-in-reports.md).

+++

+++ Hur kan jag utforma avancerade rapporter på mina data?

Med Campaign v8 kan du [skapa avancerade rapporter](../reporting/custom-reports.md). Som expertanvändare kan du skapa, uppdatera och distribuera anpassade rapporter utifrån dina data.

Du kan också använda gränssnittet för webben i Campaign för att skapa rapporter och instrumentpaneler. [Läs mer](https://experienceleague.adobe.com/en/docs/campaign-web/v8/reports/gs-reports){target="_blank"}.

+++

+++ Vad är en kub och hur skapar man en sådan rapport?

Du kan utöka databasens undersöknings- och analyskapacitet samtidigt som det blir enklare för slutanvändarna att konfigurera rapporter och tabeller. Allt de behöver göra är att välja en befintlig (helt konfigurerad) kub när de skapar sin rapport eller tabell för att bearbeta beräkningar, mått och statistik.

När de har skapats och konfigurerats används kuber i frågeformulär för rapportering och webbapplikationer. De kan användas och ändras i pivottabeller.

Läs mer om hur du kan [utforskar data](../reporting/gs-cubes.md) med kuber.

+++

+++ Kan jag skapa en rapport från svaren till en nätundersökning?

Campaign v8 har ingen inbyggd undersökningsfunktion. Du kan använda Adobe Experience Manager eller andra webblösningar för att skapa enkäter.

Du kan dock använda rapportfunktioner för att analysera insamlade data och skapa anpassade rapporter.

+++

+++ Hur kan jag dela åtkomst till min rapport i Campaign-gränssnittet?

Du kan definiera i vilket sammanhang rapporten ska visas i användargränssnittet i Adobe Campaign. Mer information om åtkomst till rapporter finns i [det här avsnittet](../reporting/custom-reports.md).

+++

+++ Kan jag exportera rapporter i olika format?

Ja, du kan exportera Campaign-rapporter i olika format som Excel, PDF eller CSV. [Läs mer](../reporting/custom-reports.md).

+++

## Utvecklare {#developers}

Få tillgång till teknisk information för utvecklare, inklusive information om datamodeller, scheman, API:er och anpassningsfunktioner.

+++ Vad är Campaign-datamodellen?

Den konceptuella datamodellen av databasen i Adobe Campaign består av en uppsättning inbyggda tabeller och deras interaktion. Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den lyder under en grammatik som är specifik för Adobe Campaign och som kallas schema.

[Läs mer om Campaign-datamodellen](../dev/datamodel.md).

[Den här sidan innehåller bästa praxis](../dev/datamodel-best-practices.md).

+++

+++ Hur arbetar man med Campaign-scheman?

I Adobe Campaign används datascheman för att:

* Definiera hur dataobjekt i programmet länkas till underliggande databastabeller.
* Definiera länkar mellan olika dataobjekt i programmet Campaign.
* Definiera och beskriva de enskilda fälten som ingår i varje objekt.

[Kom igång med tabeller och scheman](../dev/schemas.md) för att förstå hur du kan arbeta med dataram, utöka och anpassa Campaign efter dina behov.

+++

+++ Hur använder man en anpassad mottagartabell?

Du kan skapa och implementera en icke-inbyggd mottagartabell i Campaign för att skicka meddelanden.

[Läs mer](../dev/custom-recipient.md)

+++

+++ Vilka är de bästa sätten att definiera frågor i Campaign?

Frågeredigeraren i Adobe Campaign är ett kraftfullt verktyg som låter dig utforska data och bygga segment.

Du kan hitta frågeverktyget i Adobe Campaign på flera nivåer i programmet. Du kan skapa en målgrupp, segmentera kunder, extrahera och filtrera spårningsloggar och bygga filter osv.

Du kan fråga databasen i Campaign med den generiska frågeredigeraren. Den öppnas via menyn **Verktyg > Allmän frågeredigerare ...**. Den låter dig extrahera information som finns lagrad i en databas och ordna, gruppera och sortera osv. Användaren kan till exempel hämta mottagare som har klickat mer än &quot;n&quot; gånger på länken i ett nyhetsbrev under en viss period. Med det här verktyget kan du samla in, sortera och visa resultat utifrån dina behov.

[Läs mer](../start/query-editor.md). Du kan även läsa [guiden för kampanjautomatisering](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}.

+++

+++ Hur importerar jag ett datapaket?

Med Adobe Campaign kan du exportera eller importera plattformskonfigurationen och data via ett paketsystem. Med datapaket kan enheter i databasen i Adobe Campaign visas via filer i XML-format. Varje entitet i ett paket representeras med alla dess data.

Principen med datapaket är att exportera en datakonfiguration och integrera den i ett annat system i Adobe Campaign.

[Läs mer](../dev/packages.md) om hur du arbetar med datapaket för att importera och exportera kampanjkonfigurationer.

+++

+++ Var hittar jag listan över API:er för Campaign v8?

Alla API:er i Campaign inklusive deras fullständiga beskrivning finns i den här [dedikerade dokumentationen](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv){target="_blank"}.

+++

+++ Vad är Campaign REST API?

Campaign v8 innehåller en uppsättning REST-API:er som gör att ni kan skapa integreringar för Adobe Campaign och bygga ett eget ekosystem genom att interagera med Adobe Campaign med den panel med tekniker som ni använder.

[Läs mer](../dev/api/get-started-apis.md).

+++

+++ Hur övervakar jag arbetsflöden från API?

Lär dig hur du övervakar arbetsflöden med Campaign API:er i [den här dedikerade sidan](../dev/api/controlling-a-workflow.md).

+++

+++ Hur uppdaterar jag databasstrukturen?

Om du ändrar Campaign-datascheman måste du uppdatera databasstrukturen. Lär dig hur i [det här avsnittet](../dev/update-database-structure.md).

+++

+++ Vilka är begränsningarna med Campaign v8?

Campaign v8 har vissa begränsningar jämfört med Campaign Classic v7, som beskrivs i [den här sidan](../start/v7-to-v8.md#limitations).

+++

## Sekretess {#privacy}

Förstå hur Adobe Campaign hjälper er att följa sekretessregler som GDPR och CCPA samt hantera förfrågningar från registrerade personer.

+++ Vilka är de huvudsakliga villkoren gällande sekretess?

Punkterna nedan är länkade till de viktigaste villkoren och begreppen relaterade till integritet och medgivande i Adobe Campaign:

* [Reglering gällande integritetshantering](../start/privacy.md#privacy-regulations)
* [Personuppgifter och personer](../start/privacy.md#personal-data)
* [Åtkomsträttigheter och rätt att glömmas](../start/privacy.md#right-access-forgotten)
* [Medgivande, lagring och roller](../start/privacy.md#consent-retention-roles)

+++

+++ Vad föreslår Adobe Campaign för att följa de senaste regelverken gällande sekretess?

Adobe lämnar ingen juridisk rådgivning. Du bör samarbeta med eget juridiskt ombud för att säkerställa att de vidtar alla nödvändiga åtgärder gällande GDPR, CCPA, PDPA, LGPD eller någon annan tillämplig beredskap för reglering.

**Förbered för dataåtkomst och -radering**

* Identifiera en process för att ta emot/besvara förfrågningar från registrerade, inklusive att utse en kontaktperson för integritet.

* Granska de olika kunddata som finns lagrade i Adobe Campaign och identifiera unika identifierare (det finns troligen fler än en).

* Bestäm en policy och process med validering/autentisering för att bekräfta identiteten på registrerade.

* Se till att svar till den registrerade är lätta att förstå.

**Överväg medgivande**

* Ange och uppdatera vid behov alla kontaktpunkter gällande datainsamling för GDPR (dvs. överväg språk, mekanismer för medgivande och medgivandeloggar).

* Se till att alla e-postmeddelanden med marknadsföring innehåller länkarna för att avbryta prenumerationen.

* Utvärdera den globala strategin för marknadsföring via e-post för att fastställa geografiskt specifika implementeringar.

**Förstå dina data**

* Granska alla import- och insamlingskällor där data flödar in i Adobe Campaign och dokumentera vilka fält som används i marknadsföringssyfte.

* Ta bort oanvända dataattribut från databasen i Adobe Campaign.

* Använd data som finns i Adobe Campaign i det syfte de har samlats in och ge dina mottagare bättre personaliserade upplevelser.

* Granska och uppdatera behörigheter gällande dataåtkomst för att säkerställa att användare av Adobe Campaign kan dra nytta av endast de data som behövs för att köra sina kampanjer och inte komma åt data utöver det.

* Se till att alla användare av Adobe Campaign har rätt åtkomstbehörighet för att utföra de uppgifter de behöver men inte några andra rättigheter att utföra ytterligare uppgifter.

+++

+++ Hur kan personuppgiftsansvariga erhålla medgivande med minimal inverkan på användarengagemang?

I de fall där medgivande behövs för vissa marknadsföringsaktiviteter måste konsumentens samtycke vara aktivt (dvs. tystnad får inte räknas som medgivande eller förkryssade kryssrutor), fristående och det får inte vara ett villkor för att tjänsterna ska erbjudas.

Det kan till och med finnas tillfällen då vissa medgivanden behöver uppdateras för att kunna fortsätta använda data i framtiden.

Marknadsförarna bör ta hänsyn till de här kraven på ökat medgivande som en sann indikator på varumärkesengagemang och varumärkeslojalitet, samt på kundnöjdhet och förtroende.

+++

+++ Hur kan personuppgiftsansvariga hantera medgivande i Adobe Campaign?

Adobe Campaign erbjuder redan funktioner för att hantera medgivande på fler nivåer än de flesta marknadsförare använder via anpassade datafält eller via en eller flera tjänster.

Marknadsförare bör kontakta sina juridiska ombud om hur de ska gå vidare och sedan dra nytta av de funktioner som redan finns i Adobe Campaign.

Du kan t.ex. utöka datamodellen i Adobe Campaign så att den inte bara spårar om någon har anmält sig utan även tidsstämpeln för anmälan och en typ av indikator som anger det exakta tillämpningsområdet för medgivandet.

+++

+++ Vilka data kan personuppgiftsansvariga radera i Adobe Campaign som svar på en kundförfrågan från en registrerad?

Alla data som är kopplade till den registrerade tas bort inklusive färdiga och anpassade tabeller.

Tekniskt sett tas alla data bort som är länkade till den registrerade med `integrity="own"`.

Som personuppgiftsansvarig har du möjligheten att anpassa detta genom att ändra integriteten hos länkar som definieras i dataschemat (t.ex. om du har en affärsmässig motivering för att inte ta bort vissa data).

+++

+++ Hur påverkas rapporter när leverans- och spårningsloggar raderas?

Rapporter i Adobe Campaign baseras på indikatorer som beräknas med aggregerade data från leverans- och spårningsloggar. Om du tar bort de enskilda loggarna påverkas därför inte de mätvärden som visas i rapporterna.

+++

+++ Måste jag tänka på att importera data igen vid ett senare datum?

I Adobe Campaign överförs ofta poster från en extern datakälla.

Som personuppgiftsansvarig måste du se till att radera alla nödvändiga data om den registrerade från alla dina system när du tar emot en begäran om radering.

+++

+++ Kan en registrerad person, vars data har raderats från Adobe Campaign, anmäla sig igen senare?

En registrerad person kan ansluta sig igen eller läggas till som ny mottagare efter att dennes data har raderats från Adobe Campaign.

Du kan använda granskningsspåret som anger när den föregående borttagningen utfördes och när den nya mottagaren har skapats.

+++

## Behöver du fortfarande hjälp? {#get-help}

Hittar du inte det du letar efter? Här finns ytterligare resurser som hjälper dig att lyckas med Adobe Campaign v8.

### Community-stöd

Kommunicera med andra Campaign-användare och Adobe-experter för att dela kunskap och få svar.

* **[Adobe Campaign Community](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}** - Ställ frågor, dela lösningar och få kontakt med Campaign-communityn
* **[Experience League-forum](https://experienceleaguecommunities.adobe.com/){target="_blank"}** - Sök i diskussioner i alla Adobe-produkter
* **[Kampanjens kontorstider](https://experienceleague.adobe.com/){target="_blank"}** - Delta i live-sessioner med Adobe experter

### Dokumentation och utbildning

Få tillgång till omfattande guider, självstudiekurser och utbildningsmaterial.

* **[Kampanjdokumentation v8 - startsida](../campaign-home.md)** - fullständig produktdokumentation
* **[Kampanjsjälvstudiekurser](https://experienceleague.adobe.com/docs/campaign-learn/tutorials/overview.html){target="_blank"}** - Stegvisa videoguider och praktiska självstudiekurser
* **[Nyheter](whats-new.md)** - de senaste funktionerna
* **[Versionsinformation](release-notes.md)** - Aktuell och föregående versionsinformation
* **[Bästa praxis](delivery-best-practices.md)** - Rekommenderade strategier för vanliga uppgifter

### Tekniska resurser

Detaljerad teknisk dokumentation och resurser för utvecklare.

* **[Kampanj-API:er](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv){target="_blank"}** - fullständig API-referensdokumentation
* **[Campaign GitHub](https://github.com/AdobeDocs/campaign.en)** - Bidra till dokumentation
* **[Teknisk information](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/technotes-home){target="_blank"}** - Detaljerade tekniska artiklar
* **[Kompatibilitetsmatris](compatibility-matrix.md)** - system och versioner som stöds

### Support och tjänster

Få hjälp av Adobe supportteam och hantera instansen.

* **[Adobe Admin Console](https://adminconsole.adobe.com/){target="_blank"}** - Logga supportärenden och hantera användare
* **[Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}** - Kontakta supportteamet
* **[Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv){target="_blank"}** - Hantera inställningarna för Campaign-instansen
* **[Systemstatus](https://status.adobe.com/){target="_blank"}** - Kontrollera status för Adobe-tjänster

### Utbildning och certifiering

Utveckla dina färdigheter med Adobe officiella utbildnings- och certifieringsprogram.

* **[Adobe Digital Learning Services](https://learning.adobe.com/){target="_blank"}** - instruktörsledda och självstudiekurser
* **[Adobe Campaign-certifiering](https://experienceleague.adobe.com/docs/certification/program/overview.html){target="_blank"}** - Verifiera dina kunskaper med professionell certifiering
* **[Experience League utbildningsvägar](https://experienceleague.adobe.com/?lang=en#dashboard/learning){target="_blank"}** - guidade utbildningsresor

### Andra användbara resurser

* **[Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=sv){target="_blank"}** - referens för användare av Classic v7
* **[Webbgränssnittsdokumentation för kampanj](https://experienceleague.adobe.com/en/docs/campaign-web/v8/campaign-web-home){target="_blank"}** - guide för nytt webbgränssnitt
* **[Bästa praxis för slutleverans](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"}** - Optimera e-postleveransen
* **[Produktuppdateringar](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current){target="_blank"}** - senaste Adobe Experience Cloud-uppdateringar

**Senast uppdaterad:** november 2025 | **Gäller för:** Campaign v8.6 och senare

*Hittade ett fel eller vill du föreslå en förbättring? [Redigera den här sidan på GitHub](https://github.com/AdobeDocs/campaign.en/edit/main/help/v8/start/campaign-faq-comprehensive.md)*

