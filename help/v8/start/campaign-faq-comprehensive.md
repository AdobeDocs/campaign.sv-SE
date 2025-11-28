---
title: Frågor och svar om Campaign v8
description: Få svar på vanliga Adobe Campaign v8-frågor om konfiguration, konfiguration, meddelanden, arbetsflöden med mera
feature: Overview
role: User
level: Beginner
keywords: Vanliga frågor, Campaign v8, frågor, svar, hjälp, support, felsökning
hide: true
hidefromtoc: true
source-git-commit: 4f9b580ed4aeec0666fcb3343861b955a6787f01
workflow-type: tm+mt
source-wordcount: '12425'
ht-degree: 4%

---

# Vanliga frågor och svar {#faq}

Få snabba svar på de vanligaste frågorna om Adobe Campaign v8. Oavsett om du just har kommit igång eller letar efter avancerad konfigurationshjälp hittar du svar ordnade efter ämne nedan.

**Ny i Campaign?** Börja med [Allmänna frågor](#general) och [Nyckelbegrepp](#key-concepts).\
**Behöver du teknisk hjälp?** Kontrollera [Utvecklare](#developers) och [kampanjinställningar](#settings).\
**Hittar du inte ditt svar?** Besök våra [användarforum](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"} eller [kontakta support](#get-help).

**Tips!** Använd Ctrl+F (Cmd+F i Mac) om du vill söka efter specifika nyckelord på den här sidan. Klicka på en fråga för att utöka svaret.


## Allmänna frågor {#general}

Få svar på de vanligaste frågorna om Adobe Campaign v8, inklusive hur du ansluter, uppgraderar och får support.

+++ Hur ansluter jag till Campaign v8?

Du måste hämta och installera Campaign-klientkonsolen för att kunna ansluta till Adobe Campaign.

[Klicka här för att läsa mer](connect.md).

Från och med Campaign v8.6 har du tillgång till användargränssnittet **Campaign-webben** som är tillgängligt via den centrala Adobe Experience Cloud-miljön. Experience Cloud är Adobe integrerade program, produkter och tjänster för digital marknadsföring.

Lär dig hur du ansluter till Adobe Experience Cloud och kommer åt Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui). Läs mer i [Adobe Campaign webbgränssnittsdokumentation](https://experienceleague.adobe.com/en/docs/campaign-web/v8/campaign-web-home){target="_blank"}.


**Relaterade ämnen:**

* [Installera klientkonsolen](connect.md)
* [Kampanjanvändargränssnitt](campaign-ui.md)
* [Användarbehörigheter](gs-permissions.md)

+++

+++ Kan Campaign v8 installeras på en lokal eller blandad miljö?

Nej. Campaign v8 är exklusivt tillgänglig som en **hanterad Cloud Service**, som Adobe är värd för.

**Viktiga fördelar med hanterade molntjänster:**

* Överlägsna prestanda och skalbarhet
* Automatiska uppgraderingar - alltid med den senaste versionen
* Förbättrat skydd med kontinuerlig övervakning
* Ingen infrastrukturhantering eller IT-personal
* Inbyggd hög tillgänglighet och katastrofåterställning

Läs mer om [Campaign v8-arkitekturen](../architecture/architecture.md) och [skillnaderna mellan Campaign v8 och Classic v7](../start/v7-to-v8.md).

+++

+++ Hur uppgraderar jag Campaign till den senaste versionen?

Adobe Campaign uppdateras regelbundet. Mindre versioner släpps varje år med nya funktioner, förbättringar och korrigeringar. Dessutom släpper vi regelbundet mindre builder med kumulativa korrigeringar.

Denna regelbundna uppdateringsfrekvens syftar till att få den senaste och bästa informationen i händerna, hålla miljön säker och förbättra din upplevelse av produkten. Därför anser vi att det är viktigt att du kör den senaste versionen av Adobe Campaign.

**Obs!** Som användare av hanterade molntjänster uppgraderas din instans av Adobe med nya versioner.

Läs mer om [Kampanjversioner och uppgraderingar](upgrades.md).

+++

+++ Hur förbättrar man e-postleveransen?

E-postleveransen, som är en viktig del i varje avsändares marknadsföringsprogram, kännetecknas av ständigt föränderliga kriterier och regler. För effektiv navigering i den digitala världen krävs regelbunden anpassning av er e-poststrategi, med hänsyn till viktiga leveranstrender, för att ni ska nå era målgrupper på bästa sätt.

Läs den här guiden om du vill veta mer om [Bästa metoder för slutprodukter](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"}

Lär dig hur du implementerar levererbarhet i Campaign [i den här guiden](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html){target="_blank"}

**Relaterade ämnen:**

[Om levererbarhet](../send/about-deliverability.md) | [ Kontrollera meddelandeinnehåll ](../send/control-message-content.md) | [Skärmleverans](../send/monitoring-deliverability.md) | [SpamAssassin](../send/spamassassin.md)

+++

+++ Hur kan jag vara säker på att min leverans skickas utan fel?

Följ de här stegen för att säkerställa att leveransen lyckas:

**Innan du skickar:**

* Kör leveransanalys för att identifiera fel (personalisering saknas, ogiltiga mottagare, innehållsproblem)
* Skicka testkorrektur för att verifiera återgivning och personalisering
* Granska varningar under förberedelsen
* Verifiera målpopulationsantal

**Under och efter sändning:**

* Övervaka kontrollpanelen för leveransstatistik i realtid (skickat, levererat, studsar, fel)
* Kontrollera leveransloggar för meddelandestatus
* Spåra antalet lyckade försök, avhoppsfrekvens och felmeddelanden
* Granska adresser i karantän

**God praxis:**

* Ställ in aviseringar för feltrösklar
* Använd vågor (batchsändning) för stora volymer
* Testa med små volymer först
* Rensa mottagardatabasen regelbundet
* Övervaka avsändarens rykte

Läs mer om [övervakning av leveranser](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html){target="_blank"} och [bästa sättet att leverera](delivery-best-practices.md).

+++

+++ Kan jag övervaka arbetsflödeskörningen?

Ja. Campaign innehåller flera verktyg för att övervaka arbetsflödeskörningen:

* **Kontrollpanel för arbetsflöde** - Visa status, förlopp och fel i realtid för varje arbetsflödesaktivitet
* **[Arbetsflödesloggar](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution#displaying-logs){target="_blank"}** - Använd detaljerade körningsloggar för att felsöka problem
* **[Heatmap](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/monitoring-workflows/heatmap){target="_blank"}** - Visualisera arbetsflödesaktivitet och identifiera flaskhalsar för prestanda
* **[Granskningsspår](../reporting/audit-trail.md)** - Spåra alla ändringar som gjorts i arbetsflöden
* **[Varningar](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/use-cases/monitoring/send-alerts-to-operators){target="_blank"}** - Konfigurera meddelanden om arbetsflödesfel eller fördröjningar

Om du vill övervaka ett arbetsflöde öppnar du det och klickar på fliken **Loggar**. Misslyckade aktiviteter markeras med rött och du kan visa felinformation genom att klicka på dem.

Läs mer om [övervakning av arbetsflödeskörning](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution){target="_blank"} och [arbetsflödets bästa praxis](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}.

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

Kontrollera [versions- och build-numret](upgrades.md#version) i menyn **Hjälp > Om ...** på klientkonsolen i Campaign.

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

[Läs mer om webbprogram och formulär](../dev/webapps.md) | [Startsidor för Campaign Web UI ](https://experienceleague.adobe.com/en/docs/campaign-web/v8/landing-pages/get-started-lp){target="_blank"}

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

* [Från Campaign Classic v7 till v8](v7-to-v8.md) | [ Övergångshandbok för v7 till v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/v7-to-v8){target="_blank"}
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

[Skapa profiler manuellt](../audiences/create-profiles.md) | [Importera profiler från en fil ](../audiences/import-profiles.md) | [Samla in profiler med webbformulär](../audiences/collect-profiles.md)

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

**Tips!** Använd arbetsflöden för listor som kräver regelbundna uppdateringar och skapa manuellt för engångssegmentering.

[Skapa målgrupper](../audiences/create-audiences.md) | [Listuppdateringsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/list-update.html){target="_blank"}

+++

+++ Hur kan jag deduplicera en population innan jag skickar ett meddelande?

Använd aktiviteten **[!UICONTROL Deduplication]** i ett arbetsflöde för att ta bort dubblettmottagare före leverans. Placera den mellan dina **[!UICONTROL Query]**- och **[!UICONTROL Delivery]**-aktiviteter och välj sedan ditt dedupliceringsvillkor (vanligtvis e-postadress eller mottagar-ID) och vilken post som ska behållas.

**Tips!** Ta alltid bort dubbletter innan du skickar för att försäkra dig om att alla får ditt meddelande endast en gång.

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

**Tips!** Använd **e-post-Designer** i gränssnittet för Campaign-webben, som erbjuder moderna dra-och-släpp-funktioner och inbyggda responsiva mallar, i stället för att importera HTML i Raw-format för att få den bästa e-postdesignupplevelsen.

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

[Flerspråkiga leveranser (webbgränssnitt)](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/multilingual){target="_blank"} | [Villkorligt innehåll (klientkonsol) ](../send/conditions.md)

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

**Obs!** AI-assistenten är endast tillgänglig i gränssnittet för Campaign-webben och har för närvarande endast stöd för engelska. Användarna behöver rätt behörigheter och måste godkänna ett användaravtal.

[Översikt över AI Assistant](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/generative-gs){target="_blank"} | [ Användningsexempel för AI-assistenten ](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/generative-uc){target="_blank"} | [Märkesjustering](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/ai-assistant/brands-score){target="_blank"}

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

**Tips!** Använd gränssnittet för Campaign-webben för att skapa e-postmeddelanden snabbare och mer intuitivt med moderna designverktyg. Använd klientkonsolen för komplex målgruppsanpassning eller avancerade arbetsflödesbaserade kampanjer.

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

**Tips!** Övervaka din karantänlista regelbundet. Om du ökar karantänfrekvenserna signaleras ofta problem med datakvaliteten som behöver åtgärdas innan de påverkar avsändarens anseende.

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

Det beror på vilket gränssnitt du använder. **klientkonsolens** språk är fast, men med **Webbgränssnittet för kampanj** kan enskilda användare ändra sina språkinställningar.

**Klientkonsol (skrivbordsprogram):**

* Språk anges när instansen skapas och kan inte ändras
* Klientkonsolen och servern måste använda samma språk
* Varje Campaign-instans fungerar på ett enda språk
* För engelska installationer kan du välja mellan amerikansk engelska och brittisk engelska (de skiljer sig åt i datum- och tidsformat)

**Webbgränssnitt för kampanj:**

* Användarna kan ändra sitt gränssnittsspråk separat via sina profilinställningar
* Flera språk stöds med språkspecifik formatering för datum, tid och tal
* Webbgränssnittets språkinställning är oberoende av Campaign-servern och klientkonsolens språk


[Ändra språk i webbgränssnittet för kampanj](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/connect-to-campaign#language-pref){target="_blank"} | [Kom igång med Campaign-klientkonsolen](connect.md)

+++

+++ Kan jag använda Campaign v8 med andra Adobe-lösningar?

Ja. Campaign v8 kan integreras smidigt med Adobe Experience Cloud lösningar för att skapa ett kraftfullt, enhetligt ekosystem för marknadsföring. Som hanterad Cloud Service är v8 utformat för inbyggd integrering med Adobe företagsapplikationer.

**Tillgängliga nyckelintegreringar:**

* **Adobe Experience Platform** - Utnyttja enhetliga kundprofiler och realtidsdata
* **Adobe Analytics** - Mät kampanjresultat och kundbeteende i alla kanaler
* **Adobe Target** - Anpassa innehåll baserat på kundsegment och beteende
* **Adobe Experience Manager** - Centralisera skapandet av innehåll och resurshantering
* **Adobe Audience Manager** - Skapa och aktivera målgruppssegment för olika plattformar

**Fördelar:** Enhetliga kunddata, enhetliga användarupplevelser, smidiga arbetsflöden och förbättrade personaliseringsfunktioner.

**Installationsprogram:** Integrering med Adobe-lösningar kräver Adobe Identity Management System-autentisering (IMS), automatiskt konfigurerad för Campaign v8 Managed Cloud Services.

[Adobe Campaign-integreringar](../connect/integration.md) | [Anslut med Adobe ID](connect.md)

+++

+++ Hur ställer jag in spårningsfunktioner för min Campaign-instans?

Campaign v8 erbjuder omfattande spårning för att övervaka mottagarnas interaktioner med era meddelanden. Spårning kräver att du konfigurerar instansen och meddelandeinställningarna korrekt.

**Vad du kan spåra:**

* **E-post öppnas** - Via spårning av pixel (1x1 transparent bild)
* **Länkklickningar** - Alla URL:er konverteras automatiskt till spårade länkar
* **Avbeställ** - Avanmäl länkspårning
* **Spegla sidvyer** - När mottagarna visar webbversionen
* **Anpassade parametrar** - Lägg till spårningsdata i URL:er för avancerad analys

**Nyckelkonfigurationssteg:**

1. Konfigurera URL för spårningsserver i instansinställningarna (hanteras av Adobe för v8)
2. Aktivera spårning i leveransegenskaper
3. Ställ in spårning för enskilda länkar eller alla länkar automatiskt
4. Definiera giltighetsperiod för spårning och kvarhållande av logg

**Bästa praxis:** Testa alltid spårning med korrektur innan du skickar till huvudmålgruppen för att se till att länkarna fungerar korrekt och att data hämtas.

[Spåra och övervaka leveranser](tracking.md) | [Konfigurera spårade länkar](../send/email.md)

+++

+++ Hur konfigurerar man e-postleveransen?

E-postleverans beror på teknisk konfiguration, innehållskvalitet och avsändarens anseende. Campaign v8 innehåller verktyg och inställningar för att optimera placeringen av inkorgen.

**Grundläggande konfigurationssteg:**

* **Domänautentisering** - Konfigurera SPF-, DKIM- och DMARC-poster för att verifiera den avsändande domänen
* **IP-uppvärmning** - Öka volymen gradvis på nya IP-adresser för att skapa rykte
* **Avsändarkonfiguration** - Använd konsekventa, identifierbara avsändaradresser och namn
* **Studshantering** - Konfigurera karantänregler för att automatiskt hantera hårda och mjuka studsar
* **Feedback-slingor** - Konfigurera klagshantering för att hantera skräppostrapporter

**Bästa praxis för innehåll:**

* Testa e-postmeddelanden med SpamAssassin för att kontrollera spampoäng
* Bevara rätt text-till-bild-förhållande
* Inkludera oformaterad text tillsammans med HTML
* Ange alltid länken för att avbryta prenumerationen
* Undvik skräppostutlösande ord och stora versaler

**Övervakning:** Använd Campaigns leveransrapporter för att spåra avhoppsfrekvenser, klagomål och inkorgsplacering. För Campaign v8 erbjuder Adobe optimering av leveranser på infrastrukturnivå.

[Om leveransbarhet i kampanj](../send/about-deliverability.md) | [Guide till bästa praxis för slutprodukter](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"}

+++

+++ Vilka externa databaser kan jag ansluta Campaign till?

Campaign v8 har stöd för FDA-anslutningar (Federated Data Access) till större företagsdatabassystem, vilket gör att ni kan utnyttja befintlig datainfrastruktur.

**Databaser som stöds:**

* **Molndatabaser:** Amazon Redshift, Google BigQuery, Snowflake, Azure Synapse Analytics
* **Enterprise-databaser:** Oracle, Microsoft SQL Server, PostgreSQL, MySQL
* **Datalager:** Teradata, Vertica, SAP HANA
* **Big data:** Hadoop via Hive

**Plattformsspecifika överväganden:** Databasversioner som stöds och anslutningskrav varierar. Campaign v8 som hanterad Cloud Service kan ha specifika nätverks- och säkerhetskrav för extern databasåtkomst.

**Viktigt!** Kontrollera alltid den officiella kompatibilitetsmatrisen för Campaign v8-versionen för att bekräfta stöd för specifika databasversioner och för att säkerställa korrekt licensiering för externa databasanslutningar.

[Kompatibilitetsmatris](compatibility-matrix.md) | [Konfigurera FDA-anslutningar](../connect/fda.md)

+++

+++ Kan Adobe Campaign integreras med CRM-system?

Ja. Campaign tillhandahåller inbyggda CRM-anslutningar för smidig dubbelriktad synkronisering mellan Campaign och ditt CRM-system, vilket ger enhetliga kunddata på olika plattformar.

**CRM-system som stöds:**

* **Salesforce** - Leads, kontakter, konton, möjligheter, kampanjer
* **Microsoft Dynamics 365** - Kontakter, konton, leads, anpassade entiteter
* Andra CRM:er via anpassade API-integreringar

**Vad synkroniserar:**

* **Från CRM till Campaign:** Kontaktposter, kontoinformation, leads, anpassade fält, segmenteringsdata
* **Från kampanj till CRM:** Leveransloggar, spårningsdata, engagemangsmått, kampanjsvar, prenumerationsstatus

**Synkroniseringslägen:**

* **Schemalagd** - Automatisk synkronisering vid definierade intervall (timme, dag)
* **Manuell** - Synkronisering på begäran utlöses av operatorer
* **Realtid** - Via API för omedelbara uppdateringar (anpassad utveckling)

**Konfiguration:** Använd Campaigns inbyggda CRM-anslutningsassistent för att mappa CRM-fält till Campaign-attribut, markera tabeller som ska synkroniseras och schemalägga synkronisering. Kopplingen hanterar konfliktlösning och upprätthåller datakonsekvens.

**Bästa praxis:** Börja med skrivskyddad synkronisering för att testa mappningen och aktivera sedan dubbelriktad synkronisering. Övervaka synkroniseringsloggar för fel och underhåll rena data i båda systemen.

[CRM-anslutningskonfiguration](../connect/crm.md) | [CRM-arbetsflödesaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/crm-connector.html){target="_blank"}

+++

+++ Hur rensar jag klientkonsolcachen?

När du rensar klientkonsolens cache löses många vanliga problem med visning och funktionalitet. Cacheminnet lagrar lokala konfigurationsfiler som ibland kan bli skadade eller inaktuella.

**När cache ska rensas:**

* Nya varumärkningselement (logotyper, färger) visas inte korrekt
* Export-/importfunktioner misslyckas oväntat
* Gränssnittselement uppdateras inte efter konfigurationsändringar
* Prestandaproblem eller långsam konsolrespons
* Efter uppgradering till en ny klientkonsolversion

**Steg för att rensa cache:**

1. Öppna Campaign-klientkonsolen
2. Gå till menyn **[!UICONTROL File]**
3. Välj **[!UICONTROL Clear the local cache...]**
4. Bekräfta åtgärden när du uppmanas till det
5. Starta om klientkonsolen



[Installera och konfigurera klientkonsolen](connect.md)

+++

+++ Kan jag konfigurera gränssnittsinställningar?

Ja. Kampanjadministratörer kan anpassa användargränssnittet så att det matchar organisationens varumärke och optimerar användarupplevelsen. Konfigurera inställningar på instans- eller användarnivå.

**Vad du kan anpassa:**

* **Varumärke** - logotyp, färger och visuella identitetselement
* **Standardvyer** - Layout för startsida, synlighet för mappstruktur
* **Listkonfigurationer** - Standardkolumner, sorteringsordning, filter i datalistor
* **Navigering** - Tillgängliga menyalternativ och genvägar
* **Regionala inställningar** - Datum-/tidsformat, talformat, tidszoner
* **Meddelanden** - E-postaviseringar, meddelanden i appen, arbetsflödesaviseringar

**Konfigurationsnivåer:**

* **Instansövergripande** - Använd för alla användare (kräver administratörsbehörighet)
* **Användarspecifik** - Individuella inställningar och personliga inställningar
* **Operatorgrupp** - Inställningar ärvda av alla gruppmedlemmar


[Konfigurera gränssnittsinställningar](../config/ui-settings.md) | [Användarbehörigheter](gs-permissions.md)

+++

+++ Kan jag skapa anpassade fält och tabeller?

Ja. Med Campaigns flexibla datamodell kan ni utöka inbyggda scheman med anpassade fält och skapa helt nya tabeller som uppfyller era specifika affärsbehov.

**Vad du kan anpassa:**

* **Lägg till fält i befintliga tabeller** - Utöka mottagartabellen med förmånspunkter, anpassade inställningar, externa ID:n
* **Skapa nya anpassade tabeller** - Butiksprodukter, transaktioner, lojalitetsnivåer, anpassade entiteter
* **Definiera relationer** - Länka anpassade tabeller till befintliga kampanjtabeller
* **Utöka formulär** - Uppdatera användargränssnittet för att visa och redigera anpassade fält

**Vanliga användningsområden:**

* Lagra ytterligare profilattribut (kundens livstidsvärde, butikens namn, VIP-status)
* Hantera produktkataloger med anpassade attribut
* Spåra anpassade händelser och interaktioner
* Integrera externa system-ID:n för datasynkronisering
* Skapa branschspecifika datamodeller (detaljhandel, ekonomi, resor)


[Utöka datamodell](../dev/extend-schema.md) | [ Schemastruktur ](../dev/schemas.md) | [Bästa praxis för datamodell](../dev/datamodel-best-practices.md)

+++

## Rapportering {#reporting}

Få insikter om Campaigns rapporteringsfunktioner, inklusive inbyggda rapporter, anpassade rapporter och verktyg för dataanalys som kuber.

+++ Hur skapar jag nya rapporter?

Campaign erbjuder flera rapportalternativ beroende på era behov och er tekniska expertis. Du kan använda inbyggda rapporter, skapa anpassade rapporter i klientkonsolen eller utforma visuella instrumentpaneler i gränssnittet för Campaign Web.

**Rapporteringsalternativ:**

* **Inbyggda rapporter** - Klar att använda leverans-, kampanj- och spårningsrapporter som är tillgängliga på fliken **[!UICONTROL Reports]**
* **Beskrivande analys** - Snabba statistiska rapporter för alla data med ett guidestyrt gränssnitt
* **Anpassade rapporter** - Avancerade rapporter skapade av tekniska användare med rapportredigeraren
* **Kontrollpaneler för webbgränssnitt** - Moderna visuella rapporter och instrumentpaneler med dra-och-släpp-gränssnitt
* **Kuber** - Multidimensionell datautforskning och pivottabellanalys

**Viktigt!** Kampanjen är utformad för marknadsföringsaktivitetsrapportering, inte som ett specialiserat affärsintelligensverktyg. För komplexa analysbehov kan du överväga att integrera med Adobe Analytics eller särskilda BI-plattformar.

[Kom igång med rapportering](../reporting/gs-reporting.md) | [Webbgränssnittsrapporter för kampanj ](https://experienceleague.adobe.com/en/docs/campaign-web/v8/reports/gs-reports){target="_blank"}

+++

+++ Hur kan jag utforma och dela statistiska rapporter om populationer?

Använd Campaigns beskrivande analysverktyg för att snabbt generera statistiska rapporter om alla populationsdata. Den här guidedrivna funktionen hjälper dig att analysera distributioner, trender och mönster utan tekniska kunskaper.

**Vad du kan analysera:**

* Demografi och segmentering av mottagare
* Mätvärden för kampanjresultat och svarsfrekvens
* Distribution av profilattribut (ålder, plats, inställningar)
* Leveransstatistik och engagemangsmönster
* Anpassade fältvärden och mätvärden för datakvalitet

**Så här skapar du:** Välj en lista eller ett frågeresultat → Högerklicka → **[!UICONTROL Actions > Analyze]** → Välj analystyp (kvalitativ eller kvantitativ) → Konfigurera visningsalternativ → Generera rapport.

**Dela:** Exportera rapporter till Excel/PDF eller spara dem i mappen **[!UICONTROL Reports]** för att ge teamet rätt behörighet.

[Beskrivning av analys](../reporting/built-in-reports.md)

+++

+++ Hur kan jag utforma avancerade rapporter på mina data?

Campaign erbjuder två metoder för att skapa avancerade anpassade rapporter: tekniska rapporter i klientkonsolen för komplex analys och visuella instrumentpaneler för enklare rapportskapande.

På klientkonsolen kan du:

* Bygg komplexa rapporter med SQL-frågor och anpassade beräkningar
* Skapa flersidiga rapporter med diagram, tabeller och pivottabeller
* Designa villkorsstyrd formatering och dynamiskt innehåll
* Få tillgång till den fullständiga Campaign-datamodellen och externa databaser (FDA)


[Skapa anpassade rapporter (klientkonsol)](../reporting/custom-reports.md)

+++

+++ Vad är en kub och hur kan jag använda den för rapportering?

Kuber är flerdimensionella datastrukturer som gör det möjligt för företagsanvändare att utforska och analysera Campaign-data via pivottabeller utan tekniska kunskaper. Tänk på dem som förkonfigurerade datamodeller som förenklar komplex rapportering.


* Tekniska användare skapar och konfigurerar kuber som definierar dimensioner (tid, geografi, kanaler) och mått (öppningar, klick, intäkter)
* Affärsanvändare väljer en kub när de skapar rapporter och drar och släpper dimensioner för att utforska data
* Data sammanställs automatiskt och beräknas baserat på kubkonfigurationen
* Resultaten kan visas som pivottabeller, diagram eller exporteras till Excel


[Utforska data med kuber](../reporting/gs-cubes.md)

+++

+++ Kan jag skapa en rapport från svaren till en nätundersökning?

Ja! Campaign innehåller en undersökningsmodul där du kan skapa onlineenkäter och generera inbyggda rapporter om enkätsvar.

**Viktigt!** Enkäthantering är inte tillgängligt i distributioner av Campaign v8 Enterprise (FFDA). [Läs mer](../architecture/enterprise-deployment.md).

**Undersökningsfunktioner:**

* Skapa onlineenkäter med flera sidor och frågetyper
* Samla in svar i databasen eller lokala variabler
* Visa spårning av undersökningssvar i realtid
* Generera dedikerade rapporter om enkätsvar (uppdelning på fråga, allmän statistik)
* Exportera enkätsvar till Excel, PDF eller CSV för vidare analys
* Använd enkätdata i målgruppsarbetsflöden för att personalisera kampanjer

**Inbyggda undersökningsrapporter:**

* **Allmän rapport** - Svarstrender över tid, fördelning efter ursprung och språk
* **Uppdelning av svar** - Detaljerad uppdelning av svar för varje fråga
* **Dokumentationsrapport** - Visuell representation av undersökningsstrukturen

**Avancerad analys:**

* Få åtkomst till enkätsvar från fliken **[!UICONTROL Responses]** och exportera data
* Använd aktiviteten **[!UICONTROL Survey responses]** i arbetsflöden för att rikta mottagare baserat på deras svar
* Kombinera enkätdata med andra kampanjdata för segmentering och personalisering
* Skapa anpassade rapporter och kuber för flerdimensionell undersökningsanalys


[Kom igång med enkäter](https://experienceleague.adobe.com/en/docs/campaign-classic/using/online-surveys/about-surveys){target="_blank"} | [Undersökningsrapporter](https://experienceleague.adobe.com/en/docs/campaign-classic/using/online-surveys/publish-track-and-use-collected-data#reports-on-surveys){target="_blank"}

+++

+++ Hur kan jag dela åtkomst till mina rapporter?

Campaign erbjuder flexibla alternativ för att dela rapporter med olika användargrupper och styr synlighet och åtkomstbehörigheter baserat på roller och ansvarsområden.

**Rapportåtkomstkontroll:**

* **Mappbehörigheter** - Placera rapporter i mappar med lämplig läs- och skrivbehörighet för användargrupper
* **Namngivna rättigheter** - Tilldela specifika rättigheter för att visa, skapa eller ändra rapporter
* **Visningssammanhang** - Definiera var rapporter visas: i mappen **[!UICONTROL Reports]**, på kampanjflikar eller på leveransskärmar
* **Delning av webbgränssnitt** - Dela instrumentpanelslänkar med gruppmedlemmar via gränssnittet för Campaign Web

**Konfigurera åtkomst:**

1. Spara rapporten till en viss mapp i klientkonsolen
2. Konfigurera mappåtkomstbehörigheter för relevanta operatorgrupper
3. Definiera rapportegenskaper: rapporttyp, visningssammanhang och tillgänglighet
4. Testa åtkomsten med en användare från målgruppen före en bredare utrullning

**Bästa praxis:** Skapa dedikerade rapportmappar för olika team (marknadsföring, åtgärder, hantering) med anpassade åtkomstbehörigheter. Dokumentrapportens syfte och uppdateringsscheman.

[Anpassade rapporter](../reporting/custom-reports.md) | [Användarbehörigheter](gs-permissions.md)

+++

+++ Kan jag exportera rapporter i olika format?

Ja, Campaign har stöd för flera exportformat för både klientkonsolen och Web UI-rapporter, vilket gör det enkelt att dela med intressenter och integrera med andra verktyg.

**Tillgängliga exportformat:**

* **Excel (.xlsx)** - bäst för datahantering, ytterligare analys och pivottabeller
* **PDF** - Perfekt för presentationer, sammanfattningar och tryckta rapporter
* **CSV** - Perfekt för dataimport till andra system och BI-verktyg
* **OpenDocument (.ods)** - kalkylbladsformat med öppen källkod
* **XML** - För systemintegreringar och automatiserad bearbetning

**Så här exporterar du:**

* **Klientkonsol:** Öppna rapport → Klicka på knappen **[!UICONTROL Export]** → Välj format → Spara fil
* **Webbgränssnitt:** Öppna instrumentpanel → Klicka på exportikonen → Välj format → Hämta
* **Automatisk export:** Schemalägg regelbunden export med arbetsflöden med exportaktiviteter

**God praxis:**

* Använd Excel för rapporter som kräver analyser och kommentarer från intressenter
* Använd PDF för statiska rapporter som skickas till chefer eller arkiveras för regelefterlevnad
* Använd CSV för integrering med datalager eller externa analysverktyg
* Testa exporterade rapporter för att säkerställa formatering och datakvalitet

[Anpassade rapporter](../reporting/custom-reports.md) | [Webbgränssnittsrapporter för kampanj ](https://experienceleague.adobe.com/en/docs/campaign-web/v8/reports/gs-reports){target="_blank"}

+++

## Utvecklare {#developers}

Få tillgång till teknisk information för utvecklare, inklusive information om datamodeller, scheman, API:er och anpassningsfunktioner.

+++ Vad är Campaign-datamodellen?

Campaigns datamodell är en schemadriven relationsdatabasstruktur som definierar hur marknadsföringsdata är organiserade och relaterade. Det består av inbyggda tabeller för viktiga marknadsföringsobjekt (mottagare, leveranser, kampanjer) och kan utökas för att uppfylla just era affärsbehov.

**Viktiga begrepp i datamodellen:**

* **Scheman** - XML-definitioner som beskriver tabellstruktur, fält och relationer
* **Inbyggda tabeller** - Viktiga marknadsföringsenheter (mottagare, leveranser, arbetsflöden, kampanjer)
* **Länkar** - Relationer mellan tabeller (1-1, 1-N, N-N)
* **Uppräkningar** - fördefinierade värdelistor för listrutor
* **Tillägg** - Anpassade fält och tabeller har lagts till i standardmodellen

**Huvudinbyggda scheman:**

* **Mottagare (nms:recipient)** - Kundprofiler och kontaktinformation
* **Leverans (nms:delivery)** - e-post, SMS och push-kampanjer
* **Arbetsflöde (xtk:workflow)** - Automatiseringsprocesser
* **Kampanj (nms:operation)** - Marknadsföringskampanjsamordning
* **Spårningsloggar** - Öppnar, klickar och engagemangsdata

**Därför är det viktigt:** Att förstå datamodellen är nödvändigt för att skapa arbetsflöden, bygga frågor, utöka scheman och utveckla anpassade integreringar. Den schemabaserade metoden säkerställer att data är konsekventa och möjliggör kraftfulla frågefunktioner.

[Kampanjdatamodell](../dev/datamodel.md) | [Bästa praxis för datamodell](../dev/datamodel-best-practices.md)

+++

+++ Hur arbetar man med Campaign-scheman?

Scheman är grunden till Campaigns datastruktur, som definierar tabeller, fält och relationer i XML-format. Att förstå scheman är avgörande för anpassning, integrering och avancerad arbetsflödesutveckling.

**Vilka scheman definierar:**

* **Tabellstruktur** - Databastabeller och deras motsvarande programobjekt
* **Fältegenskaper** - Datatyper, etiketter, verifieringsregler och standardvärden
* **Relationer** - Länkar mellan tabeller (kopplingar) och kardinalitet
* **Index** - Databasoptimering för frågeprestanda
* **Åtkomstkontroll** - Vilka fält som användare kan visa och ändra

**Arbeta med scheman:**

* **Visa scheman:** Åtkomst via **[!UICONTROL Administration > Configuration > Data schemas]** i klientkonsolen
* **Utöka scheman:** Skapa tilläggsscheman (t.ex. `cus:recipient` extends `nms:recipient`) för att lägga till anpassade fält utan att ändra huvudscheman
* **Skapa anpassade scheman:** Skapa helt nya tabeller för företagsspecifika data
* **Uppdatera databas:** Tillämpa schemaändringar med **[!UICONTROL Tools > Advanced > Update database structure]**

**Vanliga användningsområden:**

* Lägga till anpassade fält i mottagarregister (företag-ID, lojalitetsnivå, inställningar)
* Skapa anpassade tabeller för produkter, butiker eller transaktioner
* Definiera relationer mellan anpassade och inbyggda tabeller
* Implementera affärsspecifika datamodeller

**Viktigt!** Ändra aldrig inbyggda scheman direkt. Använd alltid tilläggsscheman för att bevara uppgraderingskompatibiliteten och Adobe-stödet.

[Kom igång med scheman](../dev/schemas.md) | [Utöka ett schema](../dev/extend-schema.md)

+++

+++ Hur använder man en anpassad mottagartabell?

Med Campaign kan ni använda en anpassad tabell i stället för den inbyggda mottagartabellen när ert företag behöver en annan datastruktur för målinriktning (t.ex. B2B-konton, prenumeranter, leads eller externa kontakter).

**Varför använda en anpassad mottagartabell:**

* Rikta B2B-företag eller organisationsenheter istället för enskilda kontakter
* Avgränsa prenumerationsdata från huvudkunddatabasen
* Använd en befintlig kundtabell från ett annat system
* Implementera arkitekturer för flera varumärken med separata kontakttabeller
* Följ specifika datastyrningskrav

**Implementeringssteg:**

1. Skapa ett anpassat schema som definierar mottagartabellens struktur
2. Inkludera obligatoriska fält (e-post, primärnyckel, exkluderingsflaggor)
3. Konfigurera målmappningar för att länka registret med leveranser
4. Uppdatera leveransmallar för att använda den nya målmappningen
5. Anpassa arbetsflöden och frågor så att de refererar till den anpassade tabellen

**Viktiga överväganden:**

* Anpassade mottagartabeller måste innehålla obligatoriska fält för leveranser (e-post, undantag, spårning)
* Arbetsflöden och formulär behöver anpassas för att fungera med den anpassade strukturen
* Vissa inbyggda funktioner kan behöva anpassas
* Testning är viktigt innan produktionskampanjer migreras

**Bästa praxis:** Börja med att utöka den vanliga mottagartabellen innan du överväger en anpassad tabell. Anpassade mottagartabeller ger ökad komplexitet och bör bara användas när det är absolut nödvändigt.

[Anpassad mottagartabell](../dev/custom-recipient.md) | [Målmappningar](../audiences/target-mappings.md)

+++

+++ Vilka är de bästa sätten att definiera frågor i Campaign?

Kampanjens frågeredigerare är ett kraftfullt visuellt verktyg för att skapa databasfrågor utan SQL-kunskap. Effektiv målinriktning, segmentering och dataanalys är avgörande om det ska gå att effektivisera målgruppsanpassningen.

**Var frågor används:**

* **Arbetsflödesaktiviteter** - Fråga, Dela, Uppdatera data, Berika aktiviteter
* **Leveransmål** - Definiera mottagarpopulationer för kampanjer
* **Listor** - Skapa dynamiska eller statiska mottagarlistor
* **Rapporter** - Bygg anpassade dataextraheringar och analyser
* **Filter** - Skapa återanvändbara riktningsvillkor

**Fråga efter bästa praxis:**

* **Starta enkelt** - Skapa frågor stegvis, testa i varje steg
* **Använd filtreringsdimensioner** - Utnyttja relationer mellan tabeller (mottagare → leveranser → spårningsloggar)
* **Optimera prestanda** - Indexera fält med ofta frågor, undvik komplexa beräkningsfält
* **Utnyttja fördefinierade filter** - Återanvänd och kombinera befintliga filter för konsekvens
* **Testa med små samplingar** - Verifiera frågelogiken innan den körs i den fullständiga databasen
* **Dokumentkomplexa frågor** - Lägg till beskrivningar för underhåll och kunskapsöverföring

**Vanliga frågemönster:**

* Målmottagare som öppnade en viss leverans: Filtrera efter loggar som är länkade till mottagare
* Sök efter inaktiva kontakter: Fråga på senaste leveransdatum eller spårningsaktivitet
* Segmentera efter beteende: Kombinera leverans-, spårnings- och profilkriterier
* Exkludera tidigare mottagare: Använd uppsättningsåtgärder (union, skärning, exkludering)

**Använd allmän frågeredigerare:** **[!UICONTROL Tools > Generic query editor]** för ad hoc-databasutforskning och dataextrahering utanför arbetsflöden.

[Frågeredigeraren](../start/query-editor.md) | [Frågeaktivitet i arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}

+++

+++ Hur importerar jag ett datapaket?

Med datapaket kan du exportera och importera Campaign-konfigurationer (scheman, arbetsflöden, typologier, filter) och data mellan instanser. Detta är nödvändigt för att driftsätta konfigurationer från utveckling till produktion eller för att dela komponenter mellan olika organisationer.

**Vad kan paketeras:**

* **Konfigurationsobjekt** - scheman, arbetsflöden, typologiregler, formulär, filter
* **Kampanjkomponenter** - Leveransmallar, kampanjmallar, innehållsblock
* **Programinställningar** - Operatorer, operatorgrupper, mappstrukturer
* **Data** - mottagarlistor, dirigerade adresser, innehållsfragment
* **Anpassad utveckling** - JavaScript-kod, SQL-skript, webbprogram


**Pakettyper:**

* **Användarpaket** - Anpassade konfigurationer som du skapar och exporterar
* **Plattformspaket** - funktioner och uppdateringar som tillhandahålls av Adobe
* **Datapaket** - Innehåller faktiska dataposter, inte bara struktur

**God praxis:**

* Exportera alltid paket från samma eller äldre Campaign-version
* Testa paketimport i utvecklingsmiljö före produktion
* Innehåll och beroenden för dokumentpaket
* Använda versionskontroll för paket-XML-filer
* Säkerhetskopiera instans före större paketimporter

[Arbeta med datapaket](../dev/packages.md)

+++

+++ Var hittar jag listan över API:er för Campaign v8?

Campaign v8 innehåller omfattande API-dokumentation som omfattar både SOAP API:er (för klientkonsolinteraktioner) och REST API:er (för moderna integreringar). API-referensen innehåller alla tillgängliga metoder, parametrar och svarsformat.

**Kampanj-API-typer:**

* **SOAP API:er** - Traditionella API:er för Campaign-klientkonsolåtgärder, schemaändring och arbetsflödeskontroll
* **REST API:er** - Moderna HTTP API:er för externa systemintegreringar, profilhantering och händelseutlösande
* **JavaScript API:er** - Skript-API:er på serversidan för arbetsflödesaktiviteter och anpassad affärslogik

**API-dokumentationsresurser:**

* **Fullständig API-referens:** Omfattande SOAP API-dokumentation med metodsignaturer, parametrar och exempel
* **REST API-guide:** Modern REST-slutpunkt för profiler, händelser och organisationsenheter
* **JavaScript API:** Serverfunktioner som är tillgängliga i arbetsflödesskript och webbprogram

**Vanliga API-användningsfall:**

* Integrera Campaign med CRM-, ERP- eller anpassade applikationer
* Automatisera kampanjåtgärder och arbetsflödeskörning
* Synkronisera data mellan system i realtid
* Skapa anpassade övervaknings- och varningslösningar
* Skapa externa gränssnitt för Campaign-data och -åtgärder

**Åtkomst:** [API-dokumentation för Campaign v8](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv){target="_blank"}

+++


+++ Hur övervakar jag arbetsflöden från API?

Med kampanj-API:er kan ni programmässigt styra och övervaka arbetsflödeskörningen, vilket möjliggör externa övervakningssystem, automatiska varningar och anpassade orkestreringslösningar.

**Vad du kan göra via API:**

* **Starta arbetsflöden** - Utlös arbetsflödeskörning programmatiskt
* **Pausa/återuppta arbetsflöden** - Kontrollera arbetsflödets körningsflöde
* **Stoppa arbetsflöden** - Avsluta pågående arbetsflöden
* **Fråga efter arbetsflödesstatus** - Kontrollera om arbetsflöden körs, pausas eller slutförs
* **Hämta loggar** - Få åtkomst till körningsloggar för arbetsflöden och felmeddelanden
* **Övervaka aktivitetsförlopp** - Spåra enskilda arbetsflödesaktivitetsslutföranden

**API-metoder:**

* `xtk:workflow#Start` - Starta en arbetsflödesinstans
* `xtk:workflow#Pause` - Pausa pågående arbetsflöde
* `xtk:workflow#Stop` - Stoppa arbetsflödeskörning
* `xtk:workflow#GetState` - Hämta aktuellt arbetsflödestillstånd
* `xtk:workflow#GetLogs` - Hämta körningsloggar

**Vanliga användningsområden:**

* Skapa anpassade kontrollpaneler för övervakning som visar arbetsflödets hälsa
* Implementera automatiska varningar när arbetsflöden misslyckas eller körs för länge
* Samordna arbetsflöden från externa schemaläggare eller händelsesystem
* Skapa arbetsflödesberoenden för flera Campaign-instanser
* Generera rapporter över anpassade arbetsflödeskörningar

**Bästa praxis:** Kombinera API-övervakning med arbetsflödets granskningsspår för omfattande arbetsflödesstyrning. Använd externa övervakningsverktyg för att spåra arbetsflödes-SLA och prestandamått.

[Styra arbetsflöden via API](../dev/api/controlling-a-workflow.md)

+++

+++ Hur uppdaterar jag databasstrukturen?

När du har ändrat Campaign-scheman (lagt till fält, skapat tabeller, ändrat datatyper) måste du uppdatera den fysiska databasstrukturen för att tillämpa ändringarna. Synkroniseringen säkerställer att databasen matchar dina schemadefinitioner.

**När databasuppdateringar krävs:**

* Lägga till nya fält i befintliga scheman
* Skapa anpassade tabeller eller utöka inbyggda tabeller
* Ändra fältegenskaper (datatyp, längd, obligatorisk status)
* Lägga till eller ta bort länkar mellan tabeller
* Skapa nya index för frågeoptimering


**Viktiga överväganden:**

* **Säkerhetskopiera först** - Säkerhetskopiera alltid databasen före strukturella ändringar
* **Testa i utveckling** - Verifiera schemaändringar i dev-miljön före produktion
* **Planering av driftstopp** - Stora strukturella ändringar kan kräva korta underhållsperioder
* **För hanterade molntjänster** - Koordinera större ändringar med Adobe support
* **Återsynlighet** - Vissa ändringar (som att ta bort fält) kan orsaka dataförlust

**Bästa praxis:** Använd schemaversion och ändringsspårning. Dokumentera alla anpassade schemaändringar för underhåll och felsökning.

[Uppdatera databasstrukturen](../dev/update-database-structure.md) | [Utöka schema](../dev/extend-schema.md)

+++

+++ Vilka är begränsningarna med Campaign v8?

I Campaign v8 introduceras arkitektoniska förändringar (särskilt i FFDA-distributioner) som ger betydande prestandaförbättringar men också vissa skillnader jämfört med Campaign Classic v7. Genom att förstå dessa kan du planera migreringar och ställa upp lämpliga förväntningar.

**Viktiga v8-överväganden:**

* **FFDA-arkitektur** - Företagsdistributioner använder molndatabas (Snowflake) med olika dataåtkomstmönster
* **Enhetsuppdateringar** - Datauppdateringar ska göras i arbetsflöden, inte via API:er eller direkt databasåtkomst
* **Realtidsskrivningar** - Optimerad för gruppåtgärder i stället för högfrekventa individuella uppdateringar
* **Datamodell** - Vissa schemaanpassningar kräver olika metoder
* **Extern databasåtkomst** - FDA-konfigurationen (Federated Data Access) skiljer sig från v7

**Funktioner som inte är tillgängliga i FFDA-distributioner:**

* Undersökningar (finns i v8-standarddriftsättningar)
* Marknadsföringsresurshantering (MRM)
* Vissa specifika kopplingskonfigurationer

**Migreringsöverväganden:**

* Anpassad kod som använder direkt databasskrivning måste omfaktoriseras
* API-integreringar kan kräva anpassning för gruppbearbetning
* Arbetsflödena ska följa bästa praxis för dataåtgärder från FFDA
* Testning är nödvändigt för att validera anpassad utveckling

**Viktigt!** Dessa begränsningar utvecklas allt eftersom Adobe fortsätter att förbättra v8. Läs den senaste dokumentationen om aktuell status och färdplan.

[Campaign v7 till v8-migrering](../start/v7-to-v8.md#limitations) | [FFDA-arkitektur](../architecture/enterprise-deployment.md)

+++

## Sekretess {#privacy}

Förstå hur Adobe Campaign hjälper er att följa sekretessregler som GDPR och CCPA samt hantera förfrågningar från registrerade personer.

+++ Vilka är de viktigaste sekretessbegreppen i Campaign?

Campaign hjälper er att följa sekretesslagstiftningen (GDPR, CCPA, PDPA, LGPD) genom verktyg för att hantera den registrerades rättigheter, samtycke och datalagring. Viktiga begrepp är sekretessbestämmelser, identifiering av personuppgifter, registrerade rättigheter (åtkomst, radering, mobilitet), samtyckeshantering och regler för datalagring.

Som Data Controller är du ansvarig för att hantera förfrågningar från registrerade, upprätthålla godkännandeposter och säkerställa transparent dataanvändning.

[Integritetshantering](../start/privacy.md)

+++

+++ Hur säkerställer jag integritetsefterlevnad i Campaign?

Campaign innehåller verktyg för sekretessefterlevnad, men det juridiska ansvaret ligger hos er. Samarbeta med jurister för ert sekretessprogram.

**Grundläggande åtgärder:**

* Upprätta processer för att hantera förfrågningar från registrerade (åtkomst, radering)
* Implementera samtyckeshantering med tidsstämplar och spårning av omfattning
* Inkludera länkar för att avbryta prenumerationen i alla marknadsföringsmeddelanden
* Granska datakällor och ta bort oanvända data
* Använd åtkomstkontroller med låg behörighet

Campaign erbjuder integrering av bastjänsten för integritetsskydd, spårning av samtycke, automatiserade arbetsflöden för borttagning och verifieringskedjor för regelefterlevnad.

[Integritetshantering](../start/privacy.md)

+++

+++ Hur ska jag samla in och hantera användarens samtycke?

Giltigt samtycke kräver ett aktivt, specifikt, informerat och återkallbart avtal. Användarna måste vidta explicita åtgärder - inga förkryssade rutor eller tystnad som samtycke. Separata samtycke för olika syften (separat), ge tydliga förklaringar och underhåll poster med tidsstämplar.

**God praxis:** Ange detaljerade alternativ för deltagande, uppdatera regelbundet samtycke, gör det enkelt för dig att komma åt inställningscentren och ramsamtycke som att bygga förtroende.

Campaign erbjuder prenumerationstjänster, inställningscenter, anpassade medgivandefält med tidsstämpelspårning och arbetsflödesbaserad uppdatering av samtycke.

[Prenumerationer](../start/subscriptions.md) | [Sekretess och samtycke](../start/privacy.md#consent-retention-roles)

+++

+++ Hur implementerar jag samtyckeshantering i Campaign?

Campaign innehåller prenumerationstjänster, inställningscenter, avanmälningsflaggor och anpassade medgivandefält för spårning av samtycke.

**Implementeringsmetod:** Utöka mottagarschema för medgivandefält (datum, typ, källa), skapa prenumerationstjänster för varje medgivandetyp, skapa inställningscenters webbformulär, använd arbetsflöden för att framtvinga samtycke i målinriktning och upprätthålla granskningsspår.

Kontakta jurister för att kontrollera att implementeringen uppfyller gällande krav.

[Prenumerationstjänster](../start/subscriptions.md) | [Sekretesshantering](../start/privacy.md)

+++

+++ Vilka data tas bort när jag bearbetar en borttagningsbegäran?

Campaign tar automatiskt bort alla data som är länkade till ett ämne: mottagarprofil, leverans- och spårningsloggar, anpassade data med ägarskapsrelationer, prenumerationshistorik och webbspårningsdata.

**Så här fungerar det:** Campaign tar bort alla data där länken till mottagaren har `integrity="own"` i schemadefinitionen, vilket garanterar att alla relaterade tabeller tas bort.

Du kan anpassa borttagningsomfånget genom att ändra länkintegriteten i scheman, men rådfråga jurister först. Borttagningen är permanent och kan inte ångras.

[Sekretesshantering](../start/privacy.md) | [Schemalänkar ](../dev/schemas.md)

+++

+++ Påverkar sekretessborttagningar mina leveransrapporter?

Nej. Kampanjrapporter baseras på förberäknade aggregerade mätvärden (totalt antal skickade, öppnade, klickade), inte på direktfrågor i enskilda loggar. När du tar bort enskilda mottagardata ändras inte den historiska aggregeringsstatistiken.

Övergripande leveransstatistik och prestandamått förblir intakta, medan enskilda spårningsloggar och personlig information tas bort. På så sätt kan ni upprätthålla marknadsanalyser samtidigt som ni respekterar de registrerade personernas rättigheter.

[Sekretesshantering](../start/privacy.md) | [Rapporter](../reporting/gs-reporting.md)

+++

+++ Hur förhindrar jag återimport av borttagna data?

Ni måste ta bort data från alla källsystem, inte bara Campaign. Data kommer ofta från externa system (CRM, e-handel, datalager).

**Obligatoriska åtgärder:** Identifiera alla datakällor, ta bort från källsystem, lägg till i uteslutnings-/undertryckslistor, uppdatera importarbetsflöden för att ta hänsyn till borttagningsflaggor och dokumentera processen.

Som Data Controller är du ansvarig för fullständig borttagning av data i hela teknikens ekosystem.

[Sekretesshantering](../start/privacy.md) | [Importera arbetsflöden ](../config/workflows.md)

+++

+++ Kan borttagna användare avanmäla sig igen?

Ja. De registrerade kan anmäla sig igen efter att de har raderats. I Campaign skapas en helt ny mottagarpost utan någon länk till tidigare borttagna data. Profilen börjar med en ren platta.

Kampanjens verifieringskedja registrerar både borttagningshändelsen och skapandet av nya profiler, vilket visar att den nya anmälningen är förenlig och att den nya anmälningen har lämnats fritt efter borttagningen.

[Sekretesshantering](../start/privacy.md) | [Prenumerationer](../start/subscriptions.md)

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
* **[Versioner och uppgraderingar](upgrades.md)** - Läs mer om Campaign-versioner, uppgraderingar och hur du kontrollerar din version
* **[Bästa praxis](delivery-best-practices.md)** - Rekommenderade strategier för vanliga uppgifter

### Tekniska resurser

Detaljerad teknisk dokumentation och resurser för utvecklare.

* **[Kampanj-API:er](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv){target="_blank"}** - fullständig API-referensdokumentation
* **[Campaign GitHub](https://github.com/AdobeDocs/campaign.en)** - Bidra till dokumentation
* **[Teknisk information](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/technotes-home){target="_blank"}** - Detaljerade tekniska artiklar
* **[Kompatibilitetsmatris](compatibility-matrix.md)** - system och versioner som stöds
* **[Vanliga frågor om versioner och uppgraderingar](upgrades.md#upgrades-faq)** - Kontrollera din version och läs mer om uppgraderingar

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

