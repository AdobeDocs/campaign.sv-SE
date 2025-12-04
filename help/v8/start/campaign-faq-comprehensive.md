---
title: Frågor och svar om Campaign v8
description: Få svar på vanliga Adobe Campaign v8-frågor om konfiguration, konfiguration, meddelanden, arbetsflöden med mera
feature: Overview
role: User
level: Beginner
keywords: Vanliga frågor, Campaign v8, frågor, svar, hjälp, support, felsökning
version: Campaign v8
hide: true
hidefromtoc: true
source-git-commit: 3453820bb0eca7847ec55d7e6ea15766a57ab94e
workflow-type: tm+mt
source-wordcount: '10161'
ht-degree: 4%

---

# Vanliga frågor och svar {#faq}

Få snabba svar på de vanligaste frågorna om Adobe Campaign v8. Oavsett om du just har kommit igång eller letar efter avancerad konfigurationshjälp hittar du svar ordnade efter ämne nedan.

**Ny i Campaign?** Börja med [Komma igång](#getting-started) om du vill lära dig grunderna.\
**Behöver du hjälp med versionerna?** Kontrollera [Uppgraderingar](#upgrades) för versionsinformation och uppgraderingsprocesser.\
**Migrerar från v7 eller Standard?** Se [Campaign v8 vs. tidigare versioner &#x200B;](#v7-differences) för skillnader och vägledning om övergångar.\
**Behöver du teknisk hjälp?** Kontrollera [Utvecklare](#developers) och [kampanjinställningar](#settings).\
**Hittar du inte ditt svar?** Besök våra [användarforum](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"} eller [kontakta support](#get-help).

**Tips!** Använd Ctrl+F (Cmd+F i Mac) om du vill söka efter specifika nyckelord på den här sidan. Klicka på en fråga för att utöka svaret.


## Komma igång {#getting-started}

Lär dig grunderna för att börja arbeta med Adobe Campaign v8, från installation och anslutning till att skapa dina första kampanjer.

+++ Vad är Adobe Campaign v8?

Adobe Campaign v8 är en kraftfull automatiseringsplattform för flerkanalsmarknadsföring som hjälper er att skapa, samordna och leverera personaliserade kampanjer i e-post, mobila, sociala och offlinekanaler. Det kombinerar en robust marknadsföringsdatabas, kampanjmotor och interaktionsfunktioner i realtid för att engagera kunderna under hela kundresan.

**Nyckelfunktioner:** Hantering av flerkanalskampanjer, målgruppssegmentering och målgruppsanpassning, automatisering av arbetsflöden, skalanpassning, meddelanden i realtid och i batch, rapportering och analys, integrering med Adobe Experience Cloud.

**Vad gör v8 unik:** Molnbaserad arkitektur (endast Managed Cloud Services), prestanda i företagsklass som drivs av Snowflake-databaser, automatiska uppgraderingar, förbättrad säkerhet och dubbelriktad integrering med Adobe Experience Platform.

**Perfekt för:** Marknadsteam på företag som hanterar komplexa, stora kampanjer i flera kanaler och med flera kontaktytor.

**Relaterade ämnen:**

[Kampanj v8, produktbeskrivning](https://helpx.adobe.com/se/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} | [Nyheter i v8](whats-new.md) | [Guiden Kom igång](get-started.md)

+++

+++ Hur laddar jag ned Campaign?

Du kan hämta installationsprogrammet och klientkonsolen från Adobe Download Center.

Som administratör kan du ladda ned Adobe Campaign via Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html){target="_blank"}.

Läs mer om Distribution Center [på den här sidan](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html){target="_blank"}.

+++

+++ Hur ansluter jag till Campaign v8?

Du måste hämta och installera Campaign-klientkonsolen för att kunna ansluta till Adobe Campaign. [Läs mer](connect.md).

Från och med Campaign v8.6 har du tillgång till användargränssnittet **Campaign-webben** som är tillgängligt via den centrala Adobe Experience Cloud-miljön. Experience Cloud är Adobe integrerade program, produkter och tjänster för digital marknadsföring.

Lär dig hur du ansluter till Adobe Experience Cloud och kommer åt Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui). Läs mer i [Adobe Campaign webbgränssnittsdokumentation](https://experienceleague.adobe.com/en/docs/campaign-web/v8/campaign-web-home){target="_blank"}.


**Relaterade ämnen:**

[Installera klientkonsolen](connect.md) | [Kampanjanvändargränssnitt](campaign-ui.md) | [Användarbehörigheter](gs-permissions.md)

+++

+++ Kan jag ansluta till Campaign v8 med en Adobe ID?

Ja! Tack vare integreringen med IMS (Adobe Identity Management System) ansluter användarna till Adobe Campaign-konsolen med sin Adobe ID. Integreringen ger följande fördelar:

* Samma ID kan användas för alla Experience Cloud-lösningar.
* Anslutningen sparas när Adobe Campaign används med olika integreringar.
* Säkrare policy för lösenordshantering.
* Använda Federated ID-konton (extern ID-leverantör).

[Läs mer](connect.md) om hur du får tillgång till Campaign v8 med en Adobe ID.

+++

+++ Vad är Campaign-användargränssnittskoncept jag bör känna till?

Mer information om grunderna i användargränssnittet i Adobe Campaign finns i [det här avsnittet](campaign-ui.md).

Från och med Campaign v8.6 har du även tillgång till det nya **Campaign-webbgränssnittet** som är tillgängligt via den centrala Adobe Experience Cloud-miljön.

[Läs mer i dokumentationen för Adobe Campaign webbgränssnitt](https://experienceleague.adobe.com/en/docs/campaign-web/v8/campaign-web-home){target="_blank"}.

+++

+++ Hur ställer jag in användarbehörigheter?

Som administratör för Campaign kan du konfigurera behörigheter för användare i organisationen.

Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar:

* Tillgång till vissa funktioner
* Åtkomst till vissa data
* Skapa, ändra och/eller ta bort data

**Relaterade ämnen:**

[Kom igång med behörigheter](gs-permissions.md) | [Hantera användarbehörigheter](manage-permissions.md) | [Lägg till behörigheter i mappar](folder-permissions.md)

+++

+++ Hur väljer jag målgrupp för mina meddelanden?

Campaign erbjuder flera målinriktningsmetoder för att välja rätt målgrupp för era meddelanden:

**Målmetoder:**

* **Frågeredigeraren** - Bygg målgrupper med visuella filter för mottagarattribut, -beteenden eller -demografi
* **Listor** - Använd fördefinierade statiska eller dynamiska mottagarlistor
* **Filimport** - Överför externa mottagarfiler för engångskampanjer
* **Arbetsflöden** - Skapa komplex målningslogik med frågor-, dela- och anrikningsaktiviteter
* **Fördefinierade filter** - Använd färdiga filter (aktiva kunder, prenumeranter, VIP-medlemmar)
* **Segment från Adobe Experience Platform** - utnyttja enhetliga profiler och realtidssegment

Du kan kombinera flera kriterier (plats, inköpshistorik, engagemang) och använda undantag, skärningar eller fackföreningar för att förfina din målgrupp.

**Relaterade ämnen:**

[Definiera målgrupper i Campaign v8](../audiences/gs-audiences.md) | [Frågeredigeraren](query-editor.md) | [Målmappningar](../audiences/target-mappings.md)

+++

+++ Hur skapar och skickar jag ett första e-postmeddelande?

Det är enkelt att skapa ditt första e-postmeddelande i Campaign v8. Du börjar med en mall, väljer målgrupp, utformar ditt innehåll med personalisering, testar det med korrektur och skickar sedan iväg det. Campaign har två gränssnitt för att skapa e-post: den fullständiga **klientkonsolen** för avancerade användare och det moderna **Campaign Web UI** för snabbare och mer intuitiva e-postgenereringar.

**5 nyckelsteg:**

1. **Skapa leverans** - Börja med en e-postmall eller skapa från grunden
2. **Definiera målgrupp** - Välj mottagare med frågor, listor eller arbetsflöden
3. **Designa innehåll** - Använd e-postdesignern för att skapa ditt meddelande med anpassningsfält
4. **Skicka testkorrektur** - Validera återgivning och innehåll mellan enheter och e-postklienter
5. **Analysera och skicka** - Kör leveransanalys för att kontrollera om det finns fel och skicka sedan din e-post

**Relaterade ämnen:**

[E-postdesign och validering](../send/email.md) | [Skapa första leverans](create-message.md) | [Leveransmallar](../send/create-templates.md) | [Anpassa innehåll](../send/personalize.md)

+++

+++ Hur översätter jag ett felmeddelande?

Visas ett felmeddelande på ett främmande språk? Alla felmeddelanden och deras översättning listas på [den här sidan](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=sv){target="_blank"}.

+++

+++ Hur loggar jag ett problem?

Om du vill kontakta Adobe kundsupport ansluter du till [Adobe Admin Console](https://adminconsole.adobe.com/overview){target="_blank"} för att skapa ett ärende eller starta en chattsession.

Kräver enskilda konton med rätt behörigheter. Om du inte kan logga in begär du åtkomst via Experience League. [Läs mer](https://helpx.adobe.com/sv/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}

Du kan även gå med i [Campaign Community](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"} och söka efter svar eller fråga experter.

+++

+++ Vilka system och komponenter är Campaign v8 kompatibelt med?

Du kan hämta en lista över alla system och komponenter som stöds för den senaste versionen av Campaign i [kompatibilitetsmatrisen för Adobe Campaign](compatibility-matrix.md).

+++

+++ Kan jag använda Campaign v8 med andra Adobe-lösningar?

Ja. Campaign v8 kan integreras smidigt med Adobe Experience Cloud lösningar för ett enhetligt ekosystem för marknadsföring.

**Viktiga integreringar:** Adobe Experience Platform (enhetliga profiler, realtidsdata), Adobe Analytics (prestandamätning), Adobe Target (personalisering), Adobe Experience Manager (innehållshantering), Adobe Audience Manager (målgruppssegment).

**Installationsprogram:** Kräver Adobe IMS-autentisering, som konfigurerats automatiskt för hanterade molntjänster i Campaign v8.

**Relaterade ämnen:**

[Adobe Campaign-integreringar](../connect/integration.md) | [Anslut med Adobe ID](connect.md)

+++

+++ Vilka är begränsningarna med Campaign v8?

Campaign v8 har betydande prestandaförbättringar men vissa arkitektoniska skillnader jämfört med Campaign Classic v7, särskilt i samband med FFDA-driftsättningar.

**Viktiga överväganden:**

* **FFDA-arkitektur** - Använder molndatabas (Snowflake) med olika dataåtkomstmönster
* **Datauppdateringar** - Ska utföras i arbetsflöden, inte via direkt databasåtkomst
* **Gruppoptimerad** - Optimerad för gruppåtgärder i stället för högfrekventa individuella uppdateringar
* **Inte tillgängligt i FFDA** - enkäter, Marketing Resource Management (MRM), vissa specifika anslutningar

**Migreringseffekt:** Anpassad kod som använder direkt databasskrivning måste omfaktoriseras. API-integreringar kan behöva anpassas för gruppbearbetning.

Dessa begränsningar utvecklas i takt med att Adobe förbättrar v8. Läs den senaste dokumentationen om du vill se aktuell status.

**Relaterade ämnen:**

[Campaign v7 till v8-migrering](../start/v7-to-v8.md#limitations) | [FFDA-arkitektur](../architecture/enterprise-deployment.md)

+++

+++ Kan jag som Campaign Classic v7-användare migrera till Campaign v8?

Automatisk migrering från en befintlig Campaign Classic v7-miljö är inte tillgänglig än.

Campaign v8 är **endast** tillgänglig som hanterad Cloud Service och kan inte distribueras på en lokal eller hybridmiljö.

Mer information om migreringsprocessen får du av Adobe.

Läs mer i avsnittet [Kampanj v8 jämfört med tidigare versioner](#v7-differences).

+++


## Uppgraderingar {#upgrades}

Lär dig hur du kontrollerar Campaign-versionen, förstår uppgraderingsprocessen och håller dig informerad om nya versioner. Hanterade molntjänster i Campaign v8 hanterar uppgraderingar automatiskt med minimala avbrott.

+++ Vad är min version av Campaign?

Kontrollera [versions- och build-numret](upgrades.md#version) i menyn **Hjälp > Om ...** på klientkonsolen i Campaign.

+++

+++ Hur uppgraderar jag Campaign till den senaste versionen?

Adobe Campaign uppdateras regelbundet. Mindre versioner släpps varje år med nya funktioner, förbättringar och korrigeringar. Dessutom släpper vi regelbundet mindre builder med kumulativa korrigeringar.

Denna regelbundna uppdateringsfrekvens syftar till att få den senaste och bästa informationen i händerna, hålla miljön säker och förbättra din upplevelse av produkten. Därför anser vi att det är viktigt att du kör den senaste versionen av Adobe Campaign.

**Obs!** Som användare av hanterade molntjänster uppgraderas din instans av Adobe med nya versioner.

Läs mer om [Kampanjversioner och uppgraderingar](upgrades.md).

+++

+++ Hur får jag information om releasen av en ny version?

Håll dig informerad om nya Campaign-versioner via dessa kanaler:

* **Adobe-representant** - Kontakta dig direkt när en ny version är tillgänglig
* **Versionsinformation** - Alla versioner och ändringar dokumenteras i [Versionsinformation för kampanj](release-notes.md)
* **Adobe Priority-produktuppdateringar** - [Prenumerera](https://www.adobe.com/se/subscription/priority-product-update.html){target="_blank"} för e-postmeddelanden
* **Campaign Community** - gå med i [diskussioner](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"} för att få tidig uppdatering

Som Managed Cloud Services-användare hanterar Adobe uppgraderingar och koordinerar timing med dig.

**Relaterade ämnen:**

[Versionsinformation](release-notes.md) | [Nyheter](whats-new.md) | [Kampanjversioner och uppgraderingar](upgrades.md)

+++

+++ Varför behöver min organisation en uppgradering?

Uppgradering till den senaste Campaign-versionen är avgörande för säkerhet, prestanda och supportkvalitet.

**Viktiga fördelar:**

* **Förbättrad säkerhet** - Skydd mot sårbarheter, senaste korrigeringar, förbättrat dataskydd
* **Bättre support** - Snabbare problemlösning, åtkomst till felkorrigeringar, prioritetssupport för de senaste versionerna
* **Förbättrade prestanda** - Optimeringar av databaser och arbetsflöden, bättre skalbarhet, mer tillförlitliga åtgärder
* **Nya funktioner** - Senaste funktioner, förbättrade Adobe Experience Cloud-integreringar, moderna gränssnittsförbättringar

Adobe rekommenderar starkt att du kör den senaste versionen. Som Managed Cloud Services-kund utför Adobe uppgraderingar med minimala avbrott.

**Relaterade ämnen:**

[Kampanjversioner och uppgraderingar](upgrades.md) | [Nyheter](whats-new.md) | [Kompatibilitetsmatris](compatibility-matrix.md)

+++

+++ Hur ser uppgraderingen ut och när ligger den?

Som Managed Cloud Services-kund hanterar Adobe hela uppgraderingsprocessen med minimal påverkan på verksamheten.

**Process:**

1. **Meddelande** - Adobe meddelar dig flera veckor i förväg
2. **Planering** - Schemalägg uppgradering vid rätt tidpunkt med din Adobe-representant
3. **Förberedelse** - Adobe förbereder miljö och validerar
4. **Körning** - Adobe uppgraderar infrastrukturen med minimalt driftstopp
5. **Validering** - Adobe-testning efter uppgradering
6. **Uppgradering av klientkonsol** - Du uppgraderar dina klientkonsoler så att de matchar serverversionen

**Ditt ansvar:**

* samordna interna intressenter för timing
* [Uppgradera klientkonsoler](connect.md#upgrade-ac-console) till den nya versionen
* Testa kampanjer och arbetsflöden efter uppgradering
* Rapportera problem till Adobe Support

Adobe utför uppgraderingen av infrastrukturen. Du behöver inte utföra några tekniska åtgärder på servrar.

**Relaterade ämnen:**

[Kampanjversioner och uppgraderingar](upgrades.md) | [Uppgradera klientkonsol](connect.md#upgrade-ac-console) | [Versionsinformation](release-notes.md)

+++


## Kampanj v8 jämfört med tidigare versioner {#v7-differences}

Förstå de viktigaste skillnaderna mellan Campaign v8 och tidigare versioner (Classic v7 och Standard), inklusive arkitektur, driftsättning, migreringsvägar och funktionsändringar. Oavsett om du kommer från Campaign Classic v7 eller Campaign Standard kan du ta reda på vad som är nytt och hur du smidigt kan gå över.


+++ Vilka är de viktigaste skillnaderna mellan Campaign v8 och tidigare versioner?

Campaign v8 bygger på en modern molnbaserad arkitektur med betydande förbättringar:

* **Hanterade molntjänster endast** - Fullständigt hostas av Adobe (inga alternativ för lokal/hybrid)
* **Överlägsen prestanda** - Upp till 20 miljoner åtgärder/timme med FDA-arkitektur (Full Federated Data Access)
* **Nytt Campaign-webbgränssnitt** - Modernt, intuitivt gränssnitt bredvid den klassiska konsolen
* **Automatiska uppgraderingar** - alltid med den senaste versionen utan driftavbrott
* **Förbättrade funktioner** - AI Assistant, omfattande push-meddelanden, uppgraderat SMS, förbättrad integrering med Adobe Experience Cloud

**För användare av Campaign Classic v7:** Lär dig mer om [övergångar från v7 till v8](v7-to-v8.md), inklusive arkitekturändringar, otillgängliga funktioner och migreringsfrågor.

**För Campaign Standard-användare:** Upptäck [övergångsvägen till v8](acs-to-v8.md) och [Campaign Standard migreringsguide](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"}.

**Relaterade ämnen:**

[Nyckelfunktioner för Campaign v8](whats-new.md) | [&#x200B; Campaign v8-arkitektur &#x200B;](../architecture/architecture.md) | [Funktionsmatris](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/capability-matrix){target="_blank"} | [Skyddsritningar och begränsningar](ac-guardrails.md)

+++

+++ Ska jag migrera från Campaign Classic v7 eller Campaign Standard till v8?

Campaign v8 är en strategisk Adobe-plattform som är idealisk för organisationer som behöver kampanjer i stora volymer (20 MB drift/timme), ett modernt webbgränssnitt, molnbaserade fördelar och långsiktig support. Tidigare versioner når slutet av supporten under de närmaste åren.

**Viktiga fördelar:**

* **För Campaign Standard-användare** - välbekant webbgränssnitt, funktionsparitet (dynamisk rapportering, REST API:er, landningssidor), smidig datamigrering
* **För användare av Campaign Classic v7** - Dubbelt gränssnitt (konsol + webb-gränssnitt), bättre prestanda, automatiska uppgraderingar, förbättrad FFDA-arkitektur

**Överväg att migrera om du:**

* Hantera stora datavolymer eller upplev prestandaproblem
* vill minska IT-kostnaderna och infrastrukturhanteringen
* Adobe Experience Cloud/Platform-integrering krävs
* Vill ha framtidssäker teknik med automatiska uppdateringar

**Nästa steg:** Kontakta din Adobe-representant för att utvärdera migreringsberedskapen och åtkomstmigreringsverktygen.

**Relaterade ämnen:**

[Från Campaign Classic v7 till v8](v7-to-v8.md) | [Campaign Standard övergångsguide](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"} | [Funktionsmatris](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/capability-matrix){target="_blank"}

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

+++ Hur migrerar jag min Campaign Classic v7 On-Premise- eller Hybrid-miljö till Adobe Managed Services?

Att migrera till Adobe Managed Services är en strategisk väg från lokalt/hybridv7 till molnet som erbjuder förbättrad skalbarhet, säkerhet och minskade IT-kostnader. Det är ofta en stegsten innan man går över till Campaign v8.

**Nyckelpunkter:**

* Inget automatiserat migreringsverktyg tillgängligt - manuell planering och utförande krävs
* Vi rekommenderar starkt stöd för Adobe Professional Services
* Fördelarna är bland annat molninfrastruktur, automatiska säkerhetspatchar, expertsupport och enklare väg till v8
* Migreringen innefattar noggrann genomgång, miljörevision, datarensning, migrering av faser och produktionsreducering

**Komma igång:** Kontakta din Adobe-representant för att utvärdera din miljö och utveckla en detaljerad migreringsplan med Adobe Professional Services.

Läs mer om [migrering till Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}, inklusive utmaningar, bästa praxis och detaljerad migreringsstrategi.

+++

+++ Vilka är de viktigaste terminologi- och funktionsskillnaderna i Campaign v8?

Campaign v8 har de flesta v7/Standard-funktioner med förbättringar, men vissa termer och funktioner skiljer sig åt. Här följer en sammanfattning av viktiga ändringar.

**Ändringar i nyckelterminologi (Campaign Standard → v8):**

* Anpassade resurser → **Scheman** | Meddelanden → **Leveranser** | Produktanvändare → **Operatorer**
* Säkerhetsgrupper → **Operatorgrupper** | Organisationsenheter → **Mappbehörigheter**

**Uppdateringar för webbgränssnittet för kampanj:**

* Mottagare → **Profiler** | Fröadresser → **Testprofiler** | Leveransanalys → **Leveransförberedelse**
* Listor → **Publiker** | Förhandsgranska e-post → **Simulera innehåll**

**Inte tillgängligt i v8:**

* Lokala/hybriddistributioner (endast hanterade molntjänster)
* Direkt databasåtkomst (använd API:er)
* Manuell infrastrukturhantering (hanterad av Adobe)

**Nya funktioner för Campaign Standard-användare:**

* Dynamisk rapportering, centraliserad profilering, REST API:er, förbättringar av landningssidor, visuella fragment

**Relaterade ämnen:**

[Funktionsmatris](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/capability-matrix){target="_blank"} | [&#x200B; Övergångshandbok för v7 till v8 &#x200B;](v7-to-v8.md) | [Övergång mellan Campaign Standard och v8](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/acs-migration){target="_blank"}

+++


## Profiler och målgrupper {#audiences}

Hitta svar på frågor om att hantera profiler, skapa målgrupper, importera data och målinrikta mottagare för era kampanjer.

+++ Hur skapar man mottagare?

Skapa mottagare manuellt i klientkonsolen för enskilda profiler, importera från filer (CSV/TXT) för att lägga till stora mängder, använda webbformulär för självregistrering eller integrera via API:er från externa system. Använd importarbetsflöden för återkommande datainläsningar.

**Relaterade ämnen:**

[Skapa profiler manuellt](../audiences/create-profiles.md) | [Importera profiler från en fil &#x200B;](../audiences/import-profiles.md) | [Samla in profiler med webbformulär](../audiences/collect-profiles.md)

+++

+++ Hur importerar jag profiler?

Campaign innehåller flera importmetoder: enkel filimport med importguiden, arbetsflödesbaserad import för komplexa omformningar, återkommande importer med schemalagda arbetsflöden från SFTP och API-import för programmatisk integrering.

För filimport förbereder du datafilen (CSV/TXT, UTF-8-kodning), använder importguiden eller arbetsflödet, mappar kolumner till Campaign-fält, definierar uppdaterings-/infogningsregler och testar med ett litet exempel först. Använd arbetsflöden för återkommande importer och tillämpa regler för borttagning av dubbletter.

**Relaterade ämnen:**

[Guiden Importera data](../start/import.md) | [Återkommande importarbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/recurring-import-workflow.html){target="_blank"} | [Datainläsningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"}

+++

+++ Hur skapar jag testprofiler för mina leveranser?

Med testprofiler (dirigerade adresser) kan du rikta in dig på mottagare som inte matchar definierade målinriktningsvillkor, vilket gör att du kan testa leveransen innan du skickar till huvudmålgruppen. Lägg till dem via **[!UICONTROL Seed addresses]** i leveransegenskaperna eller använd mappen **[!UICONTROL Seed addresses]**.

Läs mer om [testprofiler](../audiences/test-profiles.md).

+++

+++ Hur definierar jag målpopulationen för en marknadsföringskampanj?

I Campaign finns flera metoder för målinriktning: skapa frågor med visuella kriterier, rikta befintliga listor eller segment, importera mottagare från externa filer (CSV, TXT) eller tillämpa fördefinierade filter. Du kan kombinera villkor med AND/OR-logik, exkludera specifika populationer, använda kontrollgrupper och dela upp för A/B-testning. Förhandsvisa alltid målpopulationsstorleken innan du skickar.

**Relaterade ämnen:**

[Definiera kampanjmål](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html){target="_blank"} | [Frågeaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"} | [Skapa målgrupper](../audiences/create-audiences.md)

+++

+++ Hur skapar jag en lista med profiler?

En lista är en statisk uppsättning mottagare som ni kan rikta in er på leveranser och återanvända mellan kampanjer.

**Tre metoder:**

* **Manuellt skapande:** Navigera till **[!UICONTROL Profiles and Targets > Lists]** och klicka på **[!UICONTROL Create]**. Lägg till mottagare från en fråga, från ett enskilt val eller från en mapp.

* **Automatisering av arbetsflöden:** Använd aktiviteten **[!UICONTROL List update]** för att skapa och underhålla listor automatiskt utifrån frågeresultat eller importerade data.

* **Under import:** Skapa en lista när du importerar profiler för att spara dem som en återanvändbar grupp.

**Tips!** Använd arbetsflöden för listor som kräver regelbundna uppdateringar och skapa manuellt för engångssegmentering.

**Relaterade ämnen:**

[Skapa målgrupper](../audiences/create-audiences.md) | [Listuppdateringsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/list-update.html){target="_blank"}

+++

+++ Hur kan jag deduplicera en population innan jag skickar ett meddelande?

Använd aktiviteten **[!UICONTROL Deduplication]** i ett arbetsflöde för att ta bort dubblettmottagare före leverans. Placera den mellan dina **[!UICONTROL Query]**- och **[!UICONTROL Delivery]**-aktiviteter och välj sedan ditt dedupliceringsvillkor (vanligtvis e-postadress eller mottagar-ID) och vilken post som ska behållas.

**Tips!** Ta alltid bort dubbletter innan du skickar för att försäkra dig om att alla får ditt meddelande endast en gång.

Läs mer om aktiviteten [Deduplicering](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/deduplication.html){target="_blank"}

+++

+++ Hur identifierar och riktar man sig till dem som prenumererar på ett nyhetsbrev?

Campaign spårar automatiskt nyhetsbrevprenumerationer via informationstjänster. Så här riktar du dig till prenumeranter:

* Använd en **[!UICONTROL Query]**-aktivitet och filtrera **[!UICONTROL Subscriptions]** > välj nyhetsbrevstjänsten
* Ange abonnenter direkt från leveransen genom att välja **[!UICONTROL To > Subscribers of an information service]**
* Skapa prenumerationslistor med arbetsflödesaktiviteten **[!UICONTROL Subscription Services]**

Campaign spårar prenumerations-/prenumerationshistorik och hanterar automatiskt anmälan/avanmälan.

**Relaterade ämnen:**

[Hantera prenumerationer](../start/subscriptions.md) | [Frågeaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}

+++

+++ Vilken är den bästa metoden att utesluta profiler från en målpopulation?

Använd aktiviteten **[!UICONTROL Exclusion]** i ett arbetsflöde för att ta bort oönskade profiler från målet. Placera den efter era målgruppsaktiviteter och definiera vilken population som ska uteslutas.

Läs mer om [Uteslutningsaktiviteten](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/exclusion.html){target="_blank"}

+++

+++ Kan jag använda externa profiler utan att importera dem i Campaign?

Ja, med Campaign v8 kan du arbeta med externa profiler som lagras i en extern databas utan att läsa in dem i Adobe Campaign. [Läs mer](../audiences/external-profiles.md).

+++

## Meddelandedesign {#design}

Lär dig hur du utformar effektiva marknadsföringsmeddelanden i Campaign v8, inklusive e-postmallar, personaliseringstekniker och flerspråkigt innehåll. Designa dina meddelanden i klientkonsolen eller använd det moderna **e-post-Designer** i webbgränssnittet för Campaign för en förbättrad visuell redigeringsupplevelse.

+++ Vilka är de bästa sätten att utforma e-postmeddelanden i Campaign?

Viktiga riktlinjer: se till att designen fungerar mobilt, använd HTML 4.0/XHTML-kompatibel kod med infogad CSS, optimera bilder (under 100 kB) med alternativ text, använd fält för sammanslagning av personalisering, testa mellan e-postklienter innan de skickar samt inkludera en vanlig textversion. Sikta mot en total e-poststorlek på mindre än 500 kB för optimal leverans.

**Relaterade ämnen:**

[Guide för e-postdesign](../send/email.md) | [Bästa tillvägagångssätt vid leverans](delivery-best-practices.md)

+++

+++ Vad är en leveransmall?

En leveransmall är en förkonfigurerad leverans som sparar alla inställningar och parametrar för återanvändning i flera kampanjer. Mallarna innehåller målregler, innehållsdesign, personalisering, tekniska inställningar (avsändare, svar) och typologiregler. Skapa en gång och återanvänd för att bibehålla enhetligheten och snabba upp kampanjskapandet.

Lär dig hur du [skapar leveransmallar](../send/create-templates.md)

+++

+++ Kan jag enkelt importera en befintlig HTML för att skapa ett e-postmeddelande i Campaign?

Ja. Importera HTML-material direkt i content editor, ladda upp filer från datorn eller ladda in från en webbadress. Se till att din HTML använder e-postkompatibel kod (HTML 4.0/XHTML) med intern CSS och lagra bilderna på en offentlig server. Campaign lägger automatiskt till personalisering och spårning till importerade HTML.

**Tips!** Använd **e-post-Designer** i gränssnittet för Campaign-webben, som erbjuder moderna dra-och-släpp-funktioner och inbyggda responsiva mallar, i stället för att importera HTML i Raw-format för att få den bästa e-postdesignupplevelsen.

Lär dig hur du [importerar HTML-innehåll](../send/defining-the-email-content.md)

+++

+++ Hur skapar jag ett prenumerationsbaserat nyhetsbrev i Campaign?

Ja. Använd Campaigns informationstjänster för att hantera prenumerationer på nyhetsbrev. Nyckelfunktioner är automatisk hantering av anmälan/avanmälan, prenumerationsspårning, efterlevnadshantering (GDPR, CAN-SPAM), stöd för flera nyhetsbrev, webbintegrering för registreringsformulär och riktad leverans till prenumeranter.

Lär dig hur du [hanterar prenumerationer](../start/subscriptions.md)

+++

+++ Hur kan jag personalisera meddelanden?

Campaign erbjuder personaliseringsfunktioner för att skapa relevanta, målinriktade meddelanden baserade på mottagardata, beteende och preferenser.

**Personalization-alternativ:**

* **Anpassningsfält** - Infoga mottagardata (t.ex. `"Hello {{firstName}}")`
* **Personaliseringsblock** - Använd fördefinierade eller anpassade innehållsblock
* **Villkorligt innehåll** - Visa annat innehåll baserat på mottagarvillkor
* **Beteendedata** - Utnyttja webbhistorik, inköpsmönster eller engagemangsmått

Testa personaliseringen innan du skickar för att verifiera att kopplingsfält och villkorslogik fungerar korrekt.

**Relaterade ämnen:**

[Personalization-guide](../send/personalize.md) | [Anpassningsfält](../send/personalization-fields.md) | [Villkorligt innehåll](../send/conditions.md)

+++

+++ Hur kan jag personalisera ämnesrader i e-postmeddelanden?

Personaliserade ämnesrader ökar öppningsfrekvensen avsevärt. Med Campaign kan ni dynamiskt infoga mottagardata, använda villkorsstyrd logik och testa varianter för att optimera engagemanget.

**Personalization-tekniker:**

* **Grundläggande fält** - Infoga förnamn, efternamn, plats: `"<%@ firstName %>, exclusive offer for you"`
* **Villkorligt innehåll** - Olika ämnen per segment: `"<% if (recipient.gender == 'F') { %>Special offer just for you<% } else { %>Exclusive deal inside<% } %>"`
* **Dynamiska data** - Inkludera inköpshistorik, förmånspoäng eller kontoinformation
* **Emojis** - Lägg till visuellt tilltalande (testa för e-postklienter först)

**God praxis:** Behåll under 50 tecken, testa personaliseringstoken innan du skickar, använd A/B-testning för att optimera, undvika skräppostutlösare, inkludera värdeförslag eller snabbhet.

**Relaterade ämnen:**

[Anpassningsfält](../send/personalization-fields.md) | [Villkorligt innehåll](../send/conditions.md)

+++

+++ Kan jag skicka flerspråkiga meddelanden?

Ja. Campaign v8 erbjuder flerspråkiga funktioner, där **gränssnittet för Campaign-webben** är det enklaste sättet. Webbgränssnittet har inbyggt flerspråkigt stöd med språkvarianter - lägg till språkvarianter till leveransen så skickar Campaign automatiskt rätt version baserat på mottagarens språk. Finns för e-post, push-meddelanden, SMS och transaktionsmeddelanden.

Viktiga funktioner: automatisk kopiering av innehåll, automatisk språkbaserad sändning, standardspråkreservationer och enkel hantering av varianter.

Klientkonsolen stöder även flerspråkigt innehåll med villkorsstyrt innehåll och arbetsflöden, men kräver mer manuell konfiguration.

**Relaterade ämnen:**

[Flerspråkiga leveranser (webbgränssnitt)](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/multilingual){target="_blank"} | [Villkorligt innehåll (klientkonsol) &#x200B;](../send/conditions.md)

+++

+++ Kan jag lokalisera ett webbformulär?

Ja. Kampanjwebbapplikationer har stöd för flerspråkig lokalisering. Definiera översättningar för alla formulärelement (etiketter, knappar, meddelanden, feltext) med automatisk språkidentifiering som baseras på mottagarprofil eller webbläsarinställningar. Flera språkversioner stöds i ett och samma webbprogram, med återgång till ett standardspråk vid behov.

Läs mer om [Webbprogramslokalisering](../dev/webapps.md)

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

**Relaterade ämnen:**

[Översikt över AI Assistant](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/generative-gs){target="_blank"} | [&#x200B; Användningsexempel för AI-assistenten &#x200B;](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/generative-uc){target="_blank"} | [Märkesjustering](https://experienceleague.adobe.com/en/docs/campaign-web/v8/content/ai-assistant/ai-assistant/brands-score){target="_blank"}

+++

## Testa och skicka meddelanden {#send}

Lär dig de bästa sätten att testa, validera, skicka och spåra era marknadsföringsmeddelanden för att säkerställa att kampanjen kan levereras.

+++ Hur förbättrar man e-postleveransen?

E-postleveransen, som är en viktig del i varje avsändares marknadsföringsprogram, kännetecknas av ständigt föränderliga kriterier och regler. För effektiv navigering i den digitala världen krävs regelbunden anpassning av er e-poststrategi, med hänsyn till viktiga leveranstrender, för att ni ska nå era målgrupper på bästa sätt.

Läs den här guiden om du vill veta mer om [Bästa metoder för slutprodukter](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"}

Lär dig hur du implementerar levererbarhet i Campaign [i den här guiden](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html){target="_blank"}

**Relaterade ämnen:**

[Kom igång med leverans](../send/about-deliverability.md) | [&#x200B; Kontrollera meddelandeinnehåll &#x200B;](../send/control-message-content.md) | [Skärmleverans](../send/monitoring-deliverability.md) | [SpamAssassin](../send/spamassassin.md)

+++

+++ Hur kan jag vara säker på att min leverans skickas utan fel?

**Innan du skickar:** Kör leveransanalys, skicka testkorrektur, granska varningar och verifiera antalet mål.

**Under/efter sändning:** Övervaka kontrollpanel för leverans (skickad, levererad, studsar, fel), kontrollera leveransloggar, spåra lyckade/avhoppsfrekvenser, granska adresser i karantän.

**God praxis:** Konfigurera aviseringar, använd påfyllnader för stora volymer, testa med små volymer först, rensa mottagardatabasen regelbundet, övervaka avsändarens rykte.

**Relaterade ämnen:**

[Spåra och övervaka leveranser](../send/tracking.md) | [Bästa tillvägagångssätt vid leverans](delivery-best-practices.md)

+++

+++ Vad är leveransanalysen?

Leveransanalys är en valideringsfas Kampanjen körs innan den skickas. Den beräknar målpopulationen, validerar innehållet, söker efter fel, tillämpar typologiregler och beräknar leveransvolym.

Campaign genererar loggar med varningar och fel. Fel vid blockleverans och måste åtgärdas. Varningar är rådgivande. Granska alltid analysloggarna innan de skickas.

Läs mer i [Leveransanalysguiden](../send/delivery-analysis.md)

+++

+++ Varför ska jag skapa korrektur?

Korrektur är testmeddelanden som validerar leveransen innan de skickas till huvudmålgruppen. Använd korrektur för att verifiera personalisering, testa innehållsåtergivning mellan e-postklienter, bekräfta länkar och spåra arbete, kontrollera bilder och bilagor och validera mobilrespons.

Korrektur hjälper till att fånga upp fel innan de når tusentals mottagare, aktivera godkännande av intressenter och testa placeringen av inkorgen. Skicka korrektur till flera e-postklienter och enheter och få alltid godkännande före produktionens utskick.

Läs mer i [korrektur- och förhandsvisningsguiden](../send/preview-and-proof.md)

+++

+++ Hur använder man startadresser i Adobe Campaign?

Seed-adresserna läggs automatiskt till i varje leverans för testning, kvalitetssäkring och övervakning, utan att de uppfyller målvillkoren. Användbar för kontinuerlig övervakning, testning av inkorgsplacering, direktreklamvalidering och synlighet för intressenter.

**Viktiga skillnader jämfört med korrektur:**

* **Utdirigerade adresser** - har lagts till automatiskt i produktionsleveranser och räknas som utskicksvolym
* **Korrektur** - Testet skickar före produktion, räkna inte med volymen som används för validering

Hantera dirigerade adresser i **[!UICONTROL Resources > Campaign management > Seed addresses]**. Håll listorna små så att leveransstatistik inte påverkas.

Läs mer i guiden [Avsändningsadresser](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/delivery-control.html){target="_blank"}

+++

+++ Hur kan jag konfigurera en godkännandeprocess innan jag skickar meddelanden?

Campaign tillhandahåller arbetsflöden för godkännande för att säkerställa att meddelandena uppfyller kvalitetsstandarderna innan de skickas. Konfigurera godkännanden för innehåll, mål, extrahering (direktreklam) och budget på kampanj- eller leveransnivå.

**Inställningar:**

Skapa operatorgrupper i **[!UICONTROL Administration > Access management > Operator groups]** och tilldela sedan godkännandegrupper i kampanj- eller leveransegenskaper. Campaign skickar e-postmeddelanden till granskare som kan godkänna, avvisa eller begära ändringar.

**För fristående leveranser (inte i en kampanj):**

Använd **korrektur som godkännandeprocess**. Skicka korrektur till godkännandegruppen för validering och skicka alltid ett nytt bevis efter att ha gjort ändringar för att säkerställa att alla intressenter granskar den senaste versionen.

**Relaterade ämnen:**

[Leveransvalidering](../send/preview-and-proof.md) | [Kampanjgodkännanden](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html){target="_blank"}

+++

+++ Kan jag köra A/B-tester på mina leveranser?

Ja! Med Campaign kan ni köra A/B-tester (kallas även delade tester) för att optimera ämnesrader, innehåll, avsändarnamn, sändningstider och mycket mer genom att jämföra prestanda för olika varianter.

**Vad du kan testa:**

* **Ämnesrader** - Jämför öppna frekvenser mellan olika ämnen
* **Innehållsvariationer** - Testa olika layouter, anrop till åtgärd eller bilder
* **Avsändarinformation** - Testa avsändarens namn eller adresspåverkan
* **Sändningstid** - Identifiera optimala leveransfönster
* **Personalization-strategier** - Jämför personaliserat och generiskt innehåll

**Så här fungerar det:**

1. Skapa leveransen och definiera testvarianter (upp till 3)
2. Dela din målgrupp (vanligtvis 10-20 % för testsegment)
3. Campaign skickar varianter för att testa segment och spåra prestanda
4. Vinnande variant skickar automatiskt till återstående målgrupp (eller du väljer vinnare manuellt)

**Finns i:** Både webbgränssnittet för Campaign och klientkonsolen. Webbgränssnittet är enklare att konfigurera med visuell jämförelse.

**Relaterade ämnen:**

[Leveransanalys](../send/delivery-analysis.md) | [Skicka och spåra leveranser](../send/send.md)

+++

+++ Vad är en typologiregel?

Typologiregler är automatiserade affärslogik som tillämpas under leveransanalysen för att validera och optimera meddelandeutskick. De säkerställer att marknadsföringsprinciperna följs, skyddar slutresultatet och förhindrar att kunderna tröttnar.

**Huvudregeltyper:**

* **Filtreringsregler** - Uteslut mottagare (blocklist, ej prenumererade, i karantän)
* **Tryckregler** - Kontrollera meddelandefrekvensen för att undvika överväldigande mottagare
* **Kapacitetsregler** - Begränsa meddelandevolymen för bearbetningskapacitet eller ISP-begränsningar
* **Kontrollregler** - Kontrollera meddelandets giltighet (ämnesrad, länk för att avbryta prenumerationen, avsändarformat)

Reglerna grupperas i typologier och tillämpas under leveransanalysen. Kampanjen kan utesluta mottagare, blockera leveransen eller generera varningar baserat på reglerna.

Läs mer i [Typologiregelguiden](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html){target="_blank"}

+++

+++ Hur kan jag skicka e-post i påfyllnader?

Ja. Våg som skickar delar upp leveransen i flera batchar som skickas enligt schemalagda intervall. Detta är nödvändigt för stora kampanjer för att balansera serverbelastningen, förhindra strypning av Internet-leverantörer, bygga upp avsändarens anseende med nya IP-adresser och hantera avanmälningar/studsar mellan vågor.

**Konfiguration:**

Aktivera påfyllnadssändning i leveransegenskaperna och definiera antalet påfyllnader (eller batchstorlek), intervallet mellan påfyllnader och vågfördelningen (linjära eller anpassade procentsatser). Campaign delar automatiskt upp målpopulationen och skickar varje våg i tid.

Använd vågor för stora kampanjer, övervaka första vågens prestanda innan du fortsätter och ge tillräckligt med tid mellan vågor för att bearbeta studsar och avanmäla dig.

Lär dig hur du [konfigurerar vågsändning](../send/configure-and-send.md#sending-using-multiple-waves)

+++

+++ Hur schemalägger jag en leverans?

Med Campaign kan ni schemalägga leveranser för framtida sändningar för att optimera sändningstiderna och samordna kampanjer.

**Schemaläggningsalternativ:**

* **Leveransegenskaper** - Skicka omedelbart, schemalägg för ett specifikt datum/tid eller vänta i timmar/dagar
* **Kampanjnivå** - Koordinera alla leveranser i en kampanj
* **Schemaläggaraktivitet för arbetsflöde** - För återkommande leveranser, komplexa mönster och händelseutlösta kampanjer

Campaign har också stöd för optimering av kontaktdatum (bästa sändningstid per mottagare) och anpassning av tidszon (samma lokala tid för alla mottagare).

Lär dig hur du [Schemalägger leverans som skickas](../send/configure-and-send.md#schedule-delivery-sending)

+++

+++ Kan jag lägga till en bilaga i e-postmeddelanden?

Ja. Campaign stöder statiska bilagor (samma fil för alla mottagare) och anpassade bilagor (olika filer per mottagare baserat på profildata). Lägg till bifogade filer i avsnittet **[!UICONTROL Attachments]** i leveransegenskaperna.

**Viktiga överväganden:**

* Behåll bilagor under 1 MB för optimal leverans
* Bifogade filer kan utlösa skräppostfilter; testa noggrant innan de skickas
* Undvik filtyper som ofta blockeras av e-postklienter (.exe, .zip, .js)
* För stora filer bör du använda spårade nedladdningslänkar i stället

Använd säkra filformat (PDF, JPEG, PNG, DOCX) och testa med dirigerade adresser innan produktionen skickas.

Läs mer i guiden [E-postbilagor](../send/email.md#attachments)

+++

+++ Hur konfigurerar jag spårade länkar i en e-postleverans?

Campaign konverterar automatiskt alla URL:er i ditt e-postmeddelande till spårade länkar för att övervaka mottagarnas engagemang. Gå till avsnittet **[!UICONTROL Tracking]** i leveransen för att konfigurera spårningsinställningar för varje länk.

**Konfigurationsalternativ:**

* **Aktivera/inaktivera spårning** - Kontrollspårning per länk
* **Länketiketter** - Lägg till beskrivande namn för rapportering (t.ex. &quot;Shop Now CTA&quot;)
* **Länkkategorier** - Gruppera länkar efter typ för aggregerad analys
* **Spårningstyp** - Spåra klick, öppningar eller båda

Campaign spårar innehållslänkar, länkar till spegelsidor, länkar för att avbryta prenumerationen och kan innehålla en valfri spårningspixel för att öppna e-postmeddelanden. Använd meningsfulla etiketter och kategorier för att förenkla rapporteringen och snabbt identifiera högpresterande innehåll.

**Relaterade ämnen:**

[Länkspårningsguide](../send/tracking.md) | [Följ upp bästa praxis](../send/send.md)

+++

+++ Var kan jag komma åt leverans- och spårningsloggar?

Få åtkomst till leverans- och spårningsloggar direkt från varje kontrollpanel. Klicka på fliken **[!UICONTROL Delivery]** längst ned i klientkonsolen. Navigera till avsnittet **[!UICONTROL Logs]** i webbgränssnittet för Campaign.

**Tillgängliga loggar:**

* **Leveransloggar** - Skickade meddelanden med mottagarinformation och status (skickade, väntande, misslyckades)
* **Spårningsloggar** - Mottagarinteraktioner (öppnas, klickas) med tidsstämplar
* **Uteslutningsloggar** - Uteslutna mottagare med orsaker (karantän, typologiregler, dubbletter)
* **Sändningsloggar** - Slutför sändningshistorik inklusive återförsök och fel

Använd dessa loggar för att felsöka leveransproblem, analysera engagemang och upprätthålla listhygienen.

**Relaterade ämnen:**

[Leveransövervakning](../send/send.md) | [Spårningsguide](../send/tracking.md)

+++

+++ Var kan jag få leveransrapporter?

Campaign innehåller omfattande inbyggda rapporter för att analysera leveransresultat, mottagarnas engagemang och kampanjens effektivitet. Få åtkomst till rapporter från fliken **[!UICONTROL Reports]** i alla leveranser, från kontrollpanelen för kampanjer eller från den globala **[!UICONTROL Reports]**-menyn för analys av olika kampanjer.

**Viktiga rapporter omfattar:**

* **Leveranssammanfattning** - Skicka statistik, öppna, klicka, studsa och avsluta prenumerationer
* **Snabbklickningar** - Visuell heatmap för länkprestanda
* **Spårningsindikatorer** - Genomklickningsfrekvenser och engagemangsmått
* **Ej levererbara** - Studsanalys med felorsaker

Rapporter finns både i klientkonsolen och i webbgränssnittet för Campaign med moderna visualiseringar.

**Relaterade ämnen:**

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

**Relaterade ämnen:**

[Karantänhanteringsguide](../send/quarantines.md) | [Studshantering](../send/delivery-failures.md)

+++

## Arbetsflöden {#workflows}

Upptäck hur du använder arbetsflöden för att automatisera processer, hantera data och samordna komplexa marknadsföringskampanjer i Adobe Campaign.

+++ Vad är ett arbetsflöde?

Med Adobe Campaign följer arbetsflöden för att orkestrera alla processer och uppgifter i olika moduler på programservern. I den omfattande grafiska miljön kan du utforma processer såsom segmentering, kampanjkörning, filhantering och mänskligt deltagande osv. Arbetsflödesmotorn kör och spårar dessa processer.

Du kan till exempel använda ett arbetsflöde för att ladda ned en fil från en server, expandera den och sedan importera poster som finns i databasen i Adobe Campaign.

Ett arbetsflöde kan även innefatta en eller flera operatörer som ska meddelas eller som kan göra val och godkänna processer. På så sätt kan du skapa en leveransinstruktion, tilldela en eller flera operatörer uppgiften att arbeta med innehåll, ange mål och godkänna korrekturer innan leveransen påbörjas.

[Läs mer](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html){target="_blank"} om arbetsflöden. Du kan även läsa om [bästa praxis för arbetsflödet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"}.

**Relaterade ämnen:**

[Kom igång med arbetsflöden](../config/workflows.md) | [Skapa ditt första arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"} | [Användningsexempel för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/about-workflow-use-cases.html){target="_blank"} | [Övervaka arbetsflödeskörning](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}

+++

+++ Kan jag övervaka arbetsflödeskörningen?

Ja. Campaign innehåller flera övervakningsverktyg: kontrollpanel för arbetsflöden (realtidsstatus och fel), arbetsflödesloggar (detaljerade körningsloggar), heatmap (visualisera aktivitet och flaskhalsar), granskningsspår (spåra ändringar) och varningar (meddelanden om fel).

Om du vill övervaka arbetsflödet öppnar du det och klickar på fliken **Loggar**. Misslyckade aktiviteter visas i rött.

**Relaterade ämnen:**

[Övervaka arbetsflödeskörning](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution){target="_blank"} | [Bästa praxis för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}

+++

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

[Skapa ett arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"} | [Arbetsflödesaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/about-activities.html){target="_blank"} | [Bästa praxis för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"} | [Användningsexempel för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/about-workflow-use-cases.html){target="_blank"}

+++

+++ Hur kan jag automatisera återkommande kampanjer?

Använd arbetsflöden med aktiviteten **Schemaläggaren** för att automatisera kampanjer som körs regelbundet, varje dag, vecka, månad eller anpassade intervall. Perfekt för välkomstmeddelanden, födelsedagskalendrar, nyhetsbrev, övergivna påminnelser om varukorgar och regelbunden rapportering.

**Konfigurationsmönster:**

1. **Schemaläggare** - Definiera frekvens (t.ex. &quot;Varje måndag klockan 9)
2. **Fråga** - Välj målgrupp med dynamiska kriterier
3. **Berikning** (valfritt) - Lägg till personaliseringsdata
4. **Leverans** - Konfigurera ditt meddelande (e-post, SMS, push)
5. **Slut** - Arbetsflödet har slutförts och väntar på nästa schemalagda körning

**Vanliga automatiska kampanjer:**

* **Välkomstserie** - Dagligt arbetsflöde för att skicka e-postmeddelanden om introduktion till nya prenumeranter
* **Födelsedag med e-post** - Sök dagligen efter mottagare med födelsedagar, skicka personliga meddelanden
* **Återengagemang** - Veckovis anpassning av inaktiva användare med återvinnande erbjudanden
* **Nyhetsbrev** - Schemalagd innehållsdistribution varje vecka eller månad
* **Åsidosättning av kundvagn** - timarbetsflöde för att identifiera och skicka kundvagnsövergivna

**Tips!** Använd typen **återkommande leverans** i arbetsflöden för att spåra varje körning separat och behålla historikrapportering.

**Relaterade ämnen:**

[Schemaläggaraktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/scheduler.html){target="_blank"} | [Återkommande leveranser](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/sending-a-birthday-email.html){target="_blank"} | [Kampanjautomatisering](https://experienceleague.adobe.com/docs/campaign/automation/home.html){target="_blank"}

+++

+++ Hur importerar jag data i Campaign?

**Metoder:** Importguiden (CSV/TXT för en gång), arbetsflödesbaserad import (**[!UICONTROL Data loading (file)]** aktivitet för komplexa/återkommande importer med omformningar), REST API:er (programmatisk/realtidssynkronisering).

**God praxis:** Testa med små samplingar, använd UTF-8-kodning, mappa fält korrekt, tillämpa borttagning av dubbletter och schemalägg stora importer som inte är toppar.

**Relaterade ämnen:**

[Importera metodtips](../start/import.md) | [Datainläsningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"} | [Återkommande importarbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/recurring-import-workflow.html){target="_blank"}

+++

+++ Hur kan jag säkerställa datakvaliteten under importen?

Datakvalitet är avgörande för att kampanjen ska kunna köras. Dåliga data leder till leveransfel, slöseri med resurser och efterlevnadsrisker. Campaign innehåller verktyg för att validera, rensa och förbättra data under importprocessen.

**Dataverifieringssteg:**

1. **Verifiering före import** - Verifiera filformat, kodning (UTF-8), kolumnmappning, obligatoriska fält finns
2. **Deduplicering** - Använd aktiviteten **[!UICONTROL Deduplication]** för att identifiera och hantera dubbletter via e-post, ID eller anpassade nycklar
3. **Dataanrikning** - Använd aktiviteten **[!UICONTROL Enrichment]** för att lägga till saknade data från befintliga Campaign-tabeller
4. **Formatera standardisering** - Normalisera telefonnummer, e-postadresser, datum, landskoder med JavaScript eller anrikning
5. **Valideringsregler** - Använd begränsningar (giltigt e-postformat, obligatoriska fält, värdeintervall)

**Vanliga problem och korrigeringar:**

* **Teckenkodningsfel** → Använd alltid UTF-8-kodning
* **Felmatchningar i datumformat** → Standardisera till formatet ÅÅÅ-MM-DD
* **Ogiltiga e-postadresser** → Använd verifieringsregler eller JavaScript för att filtrera
* **Duplicera poster** → Inkludera alltid borttagningsaktivitet före uppdateringar
* **Obligatoriska fält saknas** → Ange standardvärden eller avvisa ofullständiga poster

**Bästa praxis:** Skapa en återanvändbar arbetsflödesmall för&quot;datakvalitet&quot; med standardaktiviteter för validering och rensning som du kan tillämpa på alla importer.

**Relaterade ämnen:**

[Guide för datakvalitet](../start/import.md) | [Dedupliceringsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/deduplication.html){target="_blank"} | [Anrikningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}

+++

+++ Vilka är de vanligaste användningsområdena för arbetsflöden i Campaign?

Arbetsflödena automatiserar marknadsföringsprocesserna, bland annat:

**Datahantering:** Importera/läsa in data, rensa, berika, listhantering\
**Kampanjautomatisering:** Välkomstserie, födelsedagskampanjer, återengagemang, övergivna varukorgar\
**Avancerad målinriktning:** A/B-testning, dynamisk segmentering, poängsättning av leads, flerkanalsmarknadsföring\
**Övervakning:** Arbetsflödes-/leveransövervakning, varningar, databasunderhåll\
**Integrering:** CRM-synkronisering, API-integreringar, händelseutlösta arbetsflöden

**Relaterade ämnen:**

[Bibliotek för arbetsflödesanvändning](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/about-workflow-use-cases.html){target="_blank"} | [Skapa ett arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"} | [Bästa praxis för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}

+++

+++ Hur uppdaterar jag Campaign-data med ett arbetsflöde?

Använd aktiviteten **[!UICONTROL Update data]** för satsdatabasåtgärder: Infoga (lägg till nya poster), Uppdatera (ändra befintlig), Infoga eller uppdatera (upsert), Ta bort (ta bort matchande poster).

**Vanliga användningsområden:** Uppdatera profilattribut, synkronisera med externa system, behåll listmedlemskap, rensa/ta bort dubbletter av data, tillämpa bulkstatusändringar.

Konfigurera avstämningsnycklar för korrekt matchning och välj uppdateringsalternativ.

**Relaterade ämnen:**

[Uppdatera dataaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html){target="_blank"} | [Datahanteringsaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/about-action-activities.html){target="_blank"}

+++

+++ Hur kan jag utnyttja datahanteringsfunktionerna?

Datahanteringsaktiviteter möjliggör sofistikerade operationer: anrikning (lägg till data från relaterade tabeller), Delning (segmentpopulationer), borttagning av dubbletter (ta bort dubbletter), Uppdatera data (gruppåtgärder), Ändra dimension (växla målinriktningsdimensioner), Tvärsnitt/Förening/Uteslutning (kombinera/filtrera populationer).

**Vanliga användningsområden:** Förbättra med köp-/beteendedata, segmentera målgrupper, ta bort dubbletter, integrera externa databaser (FDA) och skapa komplexa flertabellsfrågor.

**Relaterade ämnen:**

[Datahanteringsaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/about-targeting-activities.html){target="_blank"} | [Anrikningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}

+++

+++ Kan jag automatisera utskick av personaliserade meddelanden?

Ja. Skapa automatiserade arbetsflöden: Fråga (målgrupp) → Anrikare (lägg till personaliseringsdata) → Dela (valfria segment) → Leverans (personaliserade meddelanden) → Schemaläggare (återkommande körning).

**Personalization:** Använd profildata, beteendedata, villkorsstyrt innehåll och dynamiska värden. Vanliga scenarier: födelsedagskampanjer, övergivna varukorgar, lojalitetsprogram, återfall, händelseutlösta meddelanden.

**Relaterade ämnen:**

[Personalization-guide](../send/personalize.md) | [Användningsexempel för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/send-a-birthday-email.html){target="_blank"}

+++

+++ Hur kan jag dela en målgrupp i delmängder med ett arbetsflöde?

Använd aktiviteten **[!UICONTROL Split]** för att dela upp populationer: Filtreringsvillkor (ålder, plats, VIP-status), Procentfördelning (A/B-testning), Begränsa poster (första N, översta X%), Datagruppering (en delmängd per värde).

**Vanliga användningsområden:** A/B-testning, kanalpreferens, progressiv utrullning, segmentspecifika meddelanden, lastbalansering. Varje delmängd flödar för en separat övergång för olika bearbetning.

**Relaterade ämnen:**

[Delad aktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"} | [Testguide för A/B &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/a-b-testing.html){target="_blank"}

+++

+++ Hur uppdaterar jag mottagardata från en extern fil?

Ja. Arbetsflöde: Datainläsning (fil) → Uppgradering (valfritt) → Avstämning (matchningsnycklar som e-post/ID) → Uppdatera data (uppdatera matchade poster, infoga ny om matchning saknas).

**Vanliga användningsområden:** Uppdatera profilattribut från CRM, uppdatera prenumerationsstatus, synkronisera förmånspunkter, uppdatera inställningar för anmälan/avanmälan.

**God praxis:** Använd unika identifierare, validera data först, testa med exempel och schemalägg regelbundna uppdateringar.

**Relaterade ämnen:**

[Guiden Importera data](../start/import.md) | [Datainläsningsaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"} | [Uppdatera dataaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html){target="_blank"}

+++

+++ Hur kan jag identifiera och inrikta mig på nya mottagare?

Fråga fältet **[!UICONTROL Created date]** om du vill välja mottagare som lagts till inom en viss tidsram.

**Automatiserat välkomstarbetsflöde:** Schemaläggare (kör dagligen) → Fråga (välj nya mottagare) → Deduplicering (valfritt) → Leverans (välkomstmeddelande) → Uppdatera data (markera som &quot;välkomstad&quot;).

**Avancerat:** Använd sammanställningsfunktioner för att dynamiskt identifiera senaste tillägg.

**Relaterade ämnen:**

[Frågeaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"} | [&#x200B; Använda aggregat &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/using-aggregates.html){target="_blank"}

+++

+++ Hur använder jag arbetsflödesaktiviteter?

Fyra aktivitetskategorier:

**Målinriktning:** Fråga, Dela, Ta bort dubbletter, Berikning, Skärningspunkt, Förena, Uteslutning (definiera/förfina målgrupp)\
**Flödeskontroll:** Schemaläggaren, Vänta, Test, Fork, AND-join, OR-join, Jump (hantera logik/timing)\
**Åtgärd:** Leverans, Uppdatera data, Inläsning/extrahering av data, JavaScript-kod (utför åtgärder)\
**Händelse:** Extern signal, filinsamlare, HTTP-överföring (reagerar på utlösare)

Dra från paletten, dubbelklicka för att konfigurera, ansluta till övergångar.

**Relaterade ämnen:**

[Målaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/targeting-activities.html){target="_blank"} | [&#x200B; Flödeskontroll &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/flow-control-activities.html){target="_blank"} | [Åtgärdsaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html){target="_blank"}

+++

+++ Vad är de effektivaste strategierna för arbetsflöden?

**Design:** Rensa namn, lägg till etiketter/beskrivningar, grupprelaterade aktiviteter, dela upp komplexa processer i mindre arbetsflöden\
**Prestanda:** Begränsa frågestorlekar, använd temporära tabeller, schemalägg för låg belastning, undvik alltför stora loopar\
**Felhantering:** Lägg till felsökvägar, konfigurera aviseringar, testa med exempel, granskningsloggar\
**Underhåll:** Arkivera föråldrade arbetsflöden, versionskontroll, begränsa komplexiteten (&lt;20 aktiviteter), använd mallar\
**Säkerhet:** Använd behörigheter, rensa tillfälliga data, använd variabler som inte är hårdkodade

**Relaterade ämnen:**

[Handbok om arbetsflöden för bästa praxis](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"} | [Övervaka arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}

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


**Relaterade ämnen:**

[Ändra språk i webbgränssnittet för kampanj](https://experienceleague.adobe.com/en/docs/campaign-web/v8/start/connect-to-campaign#language-pref){target="_blank"} | [Kom igång med Campaign-klientkonsolen](connect.md)

+++

+++ Vad är Campaign Control Panel och hur kommer jag åt den?

Campaign Control Panel är ett webbaserat administrativt gränssnitt som hjälper Campaign-administratörer att öka effektiviteten genom att hantera inställningar och övervaka användningen i olika Campaign-instanser. Det ger självbetjäningsfunktioner för att hantera viktiga instanskonfigurationer utan att kontakta Adobe Support.

**Nyckelfunktioner:**

* **Underdomänshantering** - Delegera och hantera underdomäner, övervaka SSL-certifikat
* **Lagringsövervakning** - Spåra databasanvändning och förhindra lagringsproblem
* **SFTP-hantering** - Övervaka SFTP-lagring, hantera IP-tillåtelselista och SSH-nycklar
* **Instansinställningar** - Konfigurera IP-tillåtelselista, hantera URL-behörigheter, granska instansinformation
* **Övervakning av aktiva profiler** - Spåra aktiv profilanvändning mot berättiganden
* **Prestandaövervakning** - Övervaka prestanda för databaser och arbetsflöden
* **E-postleverans** - Konfigurera DMARC-, BIMI- och andra autentiseringsposter

**Åtkomstkrav:**

* **Endast administratörsanvändare** - Kontrollpanelen är begränsad till användare med administratörsbehörighet
* **Adobe IMS-autentisering** - Få åtkomst via Adobe Experience Cloud med din Adobe ID
* **Campaign v8 Managed Cloud Services** - endast tillgängligt för värdbaserade instanser

**Ytterligare resurser:**

[Kontrollpanelens dokumentation](https://experienceleague.adobe.com/en/docs/control-panel/using/control-panel-home){target="_blank"} | [Självstudievideor på Kontrollpanelen](https://experienceleague.adobe.com/en/docs/control-panel-learn/tutorials/control-panel-overview){target="_blank"}

+++

+++ Hur gör jag för domändelegering?

En underdomän är en division av domänen som kan användas för att isolera varumärken eller olika typer av trafik (transaktionsmeddelanden, marknadsföringsinformation osv.).

>[!NOTE]
>
>Som användare av hanterade molntjänster kan du kontakta Adobe för att delegera dina underdomäner till Adobe.

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

**Relaterade ämnen:**

[Spåra och övervaka leveranser](../send/tracking.md) | [Konfigurera spårade länkar](../send/tracked-links.md) | [Testspårning](../send/testing-tracking.md)

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

**Relaterade ämnen:**

[Om leveransbarhet i kampanj](../send/about-deliverability.md) | [Guide till bästa praxis för slutprodukter](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"}

+++

+++ Vilka externa databaser kan jag ansluta Campaign till?

Campaign v8 stöder FDA-anslutningar (Federated Data Access) till större företagsdatabassystem (molndatabaser, företagsdatabaser, datalager, big data platforms).

Vilka databasversioner och anslutningskrav som stöds varierar. Kontrollera [kompatibilitetsmatrisen &#x200B;](compatibility-matrix.md) för Campaign v8-versionen för att bekräfta stöd för specifika databaser och se till att FDA-anslutningar licensieras korrekt.

Se [Konfigurera FDA-anslutningar](../connect/fda.md)

+++

+++ Kan Adobe Campaign integreras med CRM-system?

Ja. Campaign tillhandahåller interna CRM-anslutningar för dubbelriktad synkronisering med större CRM-system. Synkroniserar kontaktdata, leads, konton, leveransloggar, spårningsdata och interaktionsstatistik. Stöder schemalagda, manuella och realtidssynkroniseringslägen (via API).

Använd Campaigns CRM-anslutningsassistent för att mappa fält, välja tabeller och schemalägga synkronisering. Kontrollera [kompatibilitetsmatrisen &#x200B;](compatibility-matrix.md) för CRM-versioner som stöds.

**Relaterade ämnen:**

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

Läs mer i [Installera och konfigurera klientkonsolen](connect.md)

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

**Relaterade ämnen:**

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

**Relaterade ämnen:**

[Utöka datamodell](../dev/extend-schema.md) | [&#x200B; Schemastruktur &#x200B;](../dev/schemas.md) | [Bästa praxis för datamodell](../dev/datamodel-best-practices.md)

+++

## Rapportering {#reporting}

Få insikter om Campaigns rapporteringsfunktioner, inklusive inbyggda rapporter, anpassade rapporter och verktyg för dataanalys som kuber.

+++ Hur skapar jag nya rapporter?

Campaign erbjuder flera rapporteringsalternativ beroende på dina behov och din tekniska expertis: inbyggda rapporter, beskrivande analys, anpassade rapporter i klientkonsolen och kuber.

**Rapporteringsalternativ:**

* **Inbyggda rapporter** - Klar att använda leverans-, kampanj- och spårningsrapporter som är tillgängliga på fliken **[!UICONTROL Reports]**
* **Beskrivande analys** - Snabba statistiska rapporter för alla data med ett guidestyrt gränssnitt
* **Anpassade rapporter** - Avancerade rapporter skapade av tekniska användare med rapportredigeraren
* **Kuber** - Multidimensionell datautforskning och pivottabellanalys

**Viktigt!** Kampanjen är utformad för marknadsföringsaktivitetsrapportering, inte som ett specialiserat affärsintelligensverktyg. För komplexa analysbehov kan du överväga att integrera med Adobe Analytics eller särskilda BI-plattformar.

**Relaterade ämnen:**

[Kom igång med rapportering](../reporting/gs-reporting.md) | [Webbgränssnittsrapporter för kampanj &#x200B;](https://experienceleague.adobe.com/en/docs/campaign-web/v8/reports/gs-reports){target="_blank"}

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

Läs mer om [Beskrivande analys](../reporting/built-in-reports.md)

+++

+++ Hur kan jag utforma avancerade rapporter på mina data?

Använd klientkonsolen för att skapa avancerade anpassade rapporter med komplexa analysfunktioner.

På klientkonsolen kan du:

* Bygg komplexa rapporter med SQL-frågor och anpassade beräkningar
* Skapa flersidiga rapporter med diagram, tabeller och pivottabeller
* Designa villkorsstyrd formatering och dynamiskt innehåll
* Få tillgång till den fullständiga Campaign-datamodellen och externa databaser (FDA)

Lär dig hur du [skapar anpassade rapporter (klientkonsol)](../reporting/custom-reports.md)

+++

+++ Vad är en kub och hur kan jag använda den för rapportering?

Kuber är flerdimensionella datastrukturer som gör det möjligt för företagsanvändare att utforska och analysera Campaign-data via pivottabeller utan tekniska kunskaper. Tänk på dem som förkonfigurerade datamodeller som förenklar komplex rapportering. Det här rapportverktyget finns både i klientkonsolen och i webbgränssnittet för Campaign.

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

**Avancerad analys:**

* Få åtkomst till enkätsvar från fliken **[!UICONTROL Responses]** och exportera data
* Använd aktiviteten **[!UICONTROL Survey responses]** i arbetsflöden för att rikta mottagare baserat på deras svar
* Kombinera enkätdata med andra kampanjdata för segmentering och personalisering
* Skapa anpassade rapporter och kuber för flerdimensionell undersökningsanalys

**Relaterade ämnen:**

[Kom igång med enkäter](https://experienceleague.adobe.com/en/docs/campaign-classic/using/online-surveys/about-surveys){target="_blank"} | [Undersökningsrapporter](https://experienceleague.adobe.com/en/docs/campaign-classic/using/online-surveys/publish-track-and-use-collected-data#reports-on-surveys){target="_blank"}

+++

+++ Hur kan jag dela åtkomst till mina rapporter?

Styr rapportens synlighet genom mappbehörigheter och namngivna rättigheter i Campaign.

**Åtkomstkontrollmetoder:**

* **Mappbehörigheter** - Placera rapporter i mappar med lämplig åtkomst för användargrupper
* **Namngivna rättigheter** - Tilldela rättigheter för att visa, skapa eller ändra rapporter
* **Visningskontext** - Definiera var rapporter visas (mappen Rapporter, kampanjflikar, leveransskärmar)

**Inställningar:** Spara rapport i en viss mapp → Konfigurera mappåtkomst för operatorgrupper → Definiera rapportegenskaper och visningssammanhang.

**Relaterade ämnen:**

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

**Relaterade ämnen:**

[Anpassade rapporter](../reporting/custom-reports.md) | [Webbgränssnittsrapporter för kampanj &#x200B;](https://experienceleague.adobe.com/en/docs/campaign-web/v8/reports/gs-reports){target="_blank"}

+++

## Utvecklare {#developers}

Få tillgång till teknisk information för utvecklare, inklusive information om datamodeller, scheman, API:er och anpassningsfunktioner.

+++ Vad är Campaign-datamodellen?

Campaigns datamodell är en schemadriven relationsdatabasstruktur som består av inbyggda tabeller (mottagare, leveranser, kampanjer) som kan utökas för dina affärsbehov.

**Nyckelbegrepp:** Scheman (XML-definitioner), inbyggda tabeller, länkar (relationer), uppräkningar (värdelistor), tillägg (anpassade fält/tabeller).

**Huvudscheman:** Mottagare (`nms:recipient`), leverans (`nms:delivery`), arbetsflöde (`xtk:workflow`), kampanj (`nms:operation`), spårningsloggar.

Det är viktigt att förstå datamodellen för arbetsflöden, frågor, schematillägg och integreringar.

**Relaterade ämnen:**

[Kampanjdatamodell](../dev/datamodel.md) | [Bästa praxis för datamodell](../dev/datamodel-best-practices.md)

+++

+++ Hur arbetar man med Campaign-scheman?

Scheman definierar Campaigns datastruktur i XML-format och anger tabellstruktur, fältegenskaper, relationer, index och åtkomstkontroll.

**Arbeta med scheman:**

* **Visa:** Åtkomst via **[!UICONTROL Administration > Configuration > Data schemas]**
* **Utöka:** Skapa tilläggsscheman (t.ex. `cus:recipient`) för att lägga till anpassade fält utan att ändra huvudscheman
* **Skapa:** Skapa nya tabeller för företagsspecifika data
* **Uppdatera:** Tillämpa ändringar via **[!UICONTROL Tools > Advanced > Update database structure]**

**Vanliga användningsområden:** Lägg till anpassade fält i mottagartabellen, skapa anpassade tabeller, definiera relationer, implementera affärsspecifika modeller.

**Viktigt!** Ändra aldrig inbyggda scheman direkt. Använd alltid tilläggsscheman för uppgraderingskompatibilitet.

**Relaterade ämnen:**

[Kom igång med scheman](../dev/schemas.md) | [Utöka ett schema](../dev/extend-schema.md)

+++

+++ Hur använder man en anpassad mottagartabell?

Använd en anpassad mottagartabell när ni riktar in er på B2B-konton, separata prenumerationsdata, externa system eller flervarumärkesarkitekturer istället för den vanliga mottagartabellen.

**Implementering:** Skapa anpassat schema med obligatoriska fält (e-post, primärnyckel, undantag) → Konfigurera målmappningar → Uppdatera leveransmallar → Anpassa arbetsflöden/frågor.

**Viktiga överväganden:** Måste innehålla obligatoriska leveransfält, arbetsflöden/formulär måste anpassas, testas kritiskt före produktionsmigrering.

**Bästa praxis:** Utöka standardmottagartabellen först. Använd bara anpassade tabeller när det verkligen behövs på grund av komplexiteten.

**Relaterade ämnen:**

[Anpassad mottagartabell](../dev/custom-recipient.md) | [Målmappningar](../audiences/target-mappings.md)

+++

+++ Vilka är de bästa sätten att definiera frågor i Campaign?

Kampanjens frågeredigerare skapar databasfrågor visuellt utan SQL, som används i arbetsflödesaktiviteter, leveransmål, listor, rapporter och filter.

**God praxis:**

* Börja enkelt - bygg stegvis, testa varje steg
* Använd filterdimensioner - återanvänd tabellrelationer
* Optimera prestanda - indexera fält med frågor, undvik komplexa beräkningar
* Återanvänd fördefinierade filter för enhetlighet
* Testa med små prov först
* Dokumentkomplexa frågor

**Vanliga mönster:** Målleveransöppnare, hitta inaktiva kontakter, segmentera efter beteende, exkludera tidigare mottagare.

**Åtkomst:** **[!UICONTROL Tools > Generic query editor]** för ad hoc-sökning.

**Relaterade ämnen:**

[Frågeredigeraren](../start/query-editor.md) | [Frågeaktivitet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}

+++

+++ Hur importerar jag ett datapaket?

Importera paket via **[!UICONTROL Tools > Advanced > Import package]** i klientkonsolen. Paket innehåller kampanjkonfigurationer (scheman, arbetsflöden, typologier) och data för distribution mellan instanser.

**Pakettyper:** Användarpaket (anpassade konfigurationer), plattformspaket (Adobe-tillhandahållet), datapaket (faktiska data).

**Bästa tillvägagångssätt:** Testa i dev först, säkerhetskopiera innan du importerar, exportera från samma/äldre version.

Läs mer i [Arbeta med datapaket](../dev/packages.md)

+++

+++ Var hittar jag listan över API:er för Campaign v8?

Campaign v8 innehåller SOAP API:er (klientkonsolåtgärder), REST API:er (moderna integreringar) och JavaScript API:er (arbetsflödesskript).

**Vanliga användningsområden:** Integrera med CRM/ERP, automatisera kampanjer, synkronisera data, bygga övervakningslösningar, skapa externa gränssnitt.

**Åtkomst:** [API-dokumentation för Campaign v8](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv){target="_blank"}

+++


+++ Hur övervakar jag arbetsflöden från API?

Med kampanj-API:er kan du programmässigt styra arbetsflöden: starta, pausa/återuppta, stoppa, fråga status, hämta loggar, övervaka aktivitetsförloppet.

**API-slutpunkt:** `POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands`

**Kommandon:** `{"method":"start"}`, `{"method":"pause"}`, `{"method":"resume"}`, `{"method":"stop"}`

**Användningsexempel:** Skapa kontrollpaneler för övervakning, implementera automatiska aviseringar, orkestrera från externa schemaläggare, skapa beroenden mellan instanser, generera anpassade rapporter.

**Bästa praxis:** Kombinera API-övervakning med granskningsspår för heltäckande styrning.

Se [Styra arbetsflöden via API](../dev/api/controlling-a-workflow.md)

+++

+++ Hur uppdaterar jag databasstrukturen?

När du har ändrat scheman (lagt till fält, skapat tabeller, ändrat datatyper) ska du uppdatera den fysiska databasstrukturen via **[!UICONTROL Tools > Advanced > Update database structure]** för att tillämpa ändringarna.

**Vid behov:** Lägga till fält, skapa/utöka tabeller, ändra fältegenskaper, lägga till/ta bort länkar, skapa index.

**Viktigt:** Säkerhetskopiera först, testa i dev, planera driftstopp för stora ändringar, koordinera med Adobe support (Managed Cloud Services), observera att vissa ändringar kan orsaka dataförlust.


**Relaterade ämnen:**

[Uppdatera databasstrukturen](../dev/update-database-structure.md) | [Utöka schema](../dev/extend-schema.md)

+++

## Sekretess {#privacy}

Förstå hur Adobe Campaign hjälper er att följa sekretessregler som GDPR och CCPA samt hantera förfrågningar från registrerade personer.

+++ Vilka är de viktigaste sekretessbegreppen i Campaign?

Campaign hjälper er att följa sekretesslagstiftningen (GDPR, CCPA, PDPA, LGPD) genom verktyg för att hantera den registrerades rättigheter, samtycke och datalagring. Viktiga begrepp är sekretessbestämmelser, identifiering av personuppgifter, registrerade rättigheter (åtkomst, radering, mobilitet), samtyckeshantering och regler för datalagring.

Som Data Controller är du ansvarig för att hantera förfrågningar från registrerade, upprätthålla godkännandeposter och säkerställa transparent dataanvändning.

Läs mer om [Integritetshantering](../start/privacy.md)

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

Läs mer om [Integritetshantering](../start/privacy.md)

+++

+++ Hur samlar jag in och hanterar användargodkännande i Campaign?

Giltigt samtycke kräver ett aktivt, specifikt, informerat och återkallbart avtal. Användarna måste vidta explicita åtgärder - inga förkryssade rutor eller tystnad som samtycke. Separata samtycke för olika syften (separat), ge tydliga förklaringar och underhåll poster med tidsstämplar.

**God praxis:** Ange detaljerade alternativ för deltagande, uppdatera regelbundet samtycke, gör det enkelt för dig att komma åt inställningscentren och ramsamtycke som att bygga förtroende.

**Teknisk implementering i Campaign:**

Campaign innehåller prenumerationstjänster, inställningscenter, avanmälningsflaggor och anpassade medgivandefält för spårning av samtycke.

* Utöka mottagarschema för medgivandefält (datum, typ, källa)
* Skapa prenumerationstjänster för varje medgivandetyp
* Bygg webbformulär för inställningscenter
* Använd arbetsflöden för att framtvinga samtycke vid målinriktning
* Underhåll granskningsspår

Kontakta jurister för att kontrollera att implementeringen uppfyller gällande krav.

**Relaterade ämnen:**

[Prenumerationstjänster](../start/subscriptions.md) | [Sekretess och samtycke](../start/privacy.md#consent-retention-roles) | [Sekretesshantering](../start/privacy.md)

+++

+++ Vilka data tas bort när jag bearbetar en borttagningsbegäran?

Campaign tar automatiskt bort alla data som är länkade till ett ämne: mottagarprofil, leverans- och spårningsloggar, anpassade data med ägarskapsrelationer och prenumerationshistorik.

**Så här fungerar det:** Campaign tar bort alla data där länken till mottagaren har `integrity="own"` i schemadefinitionen, vilket garanterar att alla relaterade tabeller tas bort.

Du kan anpassa borttagningsomfånget genom att ändra länkintegriteten i scheman, men rådfråga jurister först. Borttagningen är permanent och kan inte ångras.

**Relaterade ämnen:**

[Sekretesshantering](../start/privacy.md) | [Schemalänkar &#x200B;](../dev/schemas.md)

+++

+++ Påverkar sekretessborttagningar mina leveransrapporter?

Nej. Kampanjrapporter baseras på förberäknade aggregerade mätvärden (totalt antal skickade, öppnade, klickade), inte på direktfrågor i enskilda loggar. När du tar bort enskilda mottagardata ändras inte den historiska aggregeringsstatistiken.

Övergripande leveransstatistik och prestandamått förblir intakta, medan enskilda spårningsloggar och personlig information tas bort. På så sätt kan ni upprätthålla marknadsanalyser samtidigt som ni respekterar de registrerade personernas rättigheter.

**Relaterade ämnen:**

[Sekretesshantering](../start/privacy.md) | [Rapporter](../reporting/gs-reporting.md)

+++

+++ Hur förhindrar jag återimport av borttagna data?

Ni måste ta bort data från alla källsystem, inte bara Campaign. Data kommer ofta från externa system (CRM, e-handel, datalager).

**Obligatoriska åtgärder:** Identifiera alla datakällor, ta bort från källsystem, lägg till i uteslutnings-/undertryckslistor, uppdatera importarbetsflöden för att ta hänsyn till borttagningsflaggor och dokumentera processen.

Som Data Controller är du ansvarig för fullständig borttagning av data i hela teknikens ekosystem.

**Relaterade ämnen:**

[Sekretesshantering](../start/privacy.md) | [Importera arbetsflöden &#x200B;](../config/workflows.md)

+++

+++ Kan borttagna användare avanmäla sig igen?

Ja. De registrerade kan anmäla sig igen efter att de har raderats. I Campaign skapas en helt ny mottagarpost utan någon länk till tidigare borttagna data. Profilen börjar med en ren platta.

Kampanjens verifieringskedja registrerar både borttagningshändelsen och skapandet av nya profiler, vilket visar att den nya anmälningen är förenlig och att den nya anmälningen har lämnats fritt efter borttagningen.

**Relaterade ämnen:**

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

* **[Kampanjsjälvstudiekurser](https://experienceleague.adobe.com/docs/campaign-learn/tutorials/overview.html){target="_blank"}** - Stegvisa videoguider och praktiska självstudiekurser
* **[Nyheter](whats-new.md)** - de senaste funktionerna
* **[Versionsinformation](release-notes.md)** - Aktuell och föregående versionsinformation
* **[Versioner och uppgraderingar](upgrades.md)** - Läs mer om Campaign-versioner, uppgraderingar och hur du kontrollerar din version

### Tekniska resurser

Detaljerad teknisk dokumentation och resurser för utvecklare.

* **[Kampanj-API:er](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv){target="_blank"}** - fullständig API-referensdokumentation
* **[Kompatibilitetsmatris](compatibility-matrix.md)** - system och versioner som stöds
* **[Vanliga frågor om versioner och uppgraderingar](upgrades.md)** - Kontrollera din version och läs mer om uppgraderingar

### Support och tjänster

Få hjälp av Adobe supportteam och hantera instansen.

* **[Adobe Admin Console](https://adminconsole.adobe.com/){target="_blank"}** - Logga supportärenden och hantera användare
* **[Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}** - Kontakta supportteamet
* **[Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv){target="_blank"}** - Hantera inställningarna för Campaign-instansen
* **[Systemstatus](https://status.adobe.com/){target="_blank"}** - Kontrollera status för Adobe-tjänster

### Utbildning och certifiering

Utveckla dina färdigheter med Adobe officiella utbildnings- och certifieringsprogram.

* **[Experience League Hjälp](https://experienceleague.adobe.com/en/browse/campaign/campaign-v8){target="_blank"}** - Hjälpresurser för Campaign v8 (webbgränssnitt och CLient-konsol)
* **[Adobe Digital Learning Services](https://learning.adobe.com/){target="_blank"}** - instruktörsledda och självstudiekurser
* **[Adobe Campaign-certifiering](https://experienceleague.adobe.com/docs/certification/program/overview.html){target="_blank"}** - Verifiera dina kunskaper med professionell certifiering
* **[Experience League utbildningsvägar](https://experienceleague.adobe.com/?lang=en#dashboard/learning){target="_blank"}** - guidade utbildningsresor

### Andra användbara resurser

* **[Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=sv){target="_blank"}** - referens för användare av Classic v7
* **[Webbgränssnittsdokumentation för kampanj](https://experienceleague.adobe.com/en/docs/campaign-web/v8/campaign-web-home){target="_blank"}** - guide för nytt webbgränssnitt
* **[Bästa praxis för slutleverans](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv){target="_blank"}** - Optimera e-postleveransen

