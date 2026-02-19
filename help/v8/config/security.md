---
title: Bästa praxis för kampanjsäkerhet
description: Kom igång med de effektivaste strategierna för kampanjsäkerhet
feature: Privacy, PI
role: Developer
level: Beginner
exl-id: 1d593c8e-4b32-4902-93a7-7b18cef27cac
version: Campaign v8, Campaign Classic v7
source-git-commit: da2274cfd19bb067fcc1e990360093f161d5638a
workflow-type: tm+mt
source-wordcount: '2810'
ht-degree: 52%

---

# Bästa praxis för kampanjsäkerhet {#ac-security}

På Adobe tar vi er digitala säkerhet på stort allvar. Säkerhetsrutinerna är djupt integrerade i vår interna programutveckling och våra processer och verktyg för drift och följs noggrant av våra funktionsövergripande team för att förebygga, upptäcka och hantera incidenter på ett snabbt sätt.

Dessutom hjälper vårt samarbete med partners, ledande forskare, säkerhetsforskningsinstitutioner och andra branschorganisationer oss att hålla oss uppdaterade med de senaste hoten och säkerhetsluckorna och vi införlivar regelbundet avancerad säkerhetsteknik i de produkter och tjänster vi erbjuder.

>[!NOTE]
>
>**Hanterade molntjänster i Campaign v8:** Infrastruktur (nätverk, server, TLS, patchning) hanteras av Adobe. Den här sidan fokuserar på konfiguration på klient- och programnivå som du kontrollerar: åtkomsthantering, autentisering, instansinställningar, dataskydd, kodning och driftspraxis.

## Checklista för säkerhet {#security-checklist}

Använd den här checklistan för att anpassa konfigurationen efter rekommenderade säkra standardinställningar:

* [Åtkomsthantering](#access-management): Skapa säkerhetsgrupper, tilldela lämpliga behörigheter, begränsa administratörsanvändning, en operator per användare, granska regelbundet
* [Autentisering och session](#authentication-and-session): Använd Adobe IMS, stark identitetsprincip, timeout för session
* [Instans- och nätverkssäkerhet](#instance-and-network-security): IP-tillåtelselista, URL-behörigheter, GPG-nycklar via Kontrollpanelen
* [Data- och PII-skydd](#data-and-pii-protection): HTTPS, PII-vybegränsning, begränsa lösenord, skydda känsliga sidor
* [Riktlinjer för kodning](#coding-guidelines): Inga hårdkodade hemligheter, validera indata, parametriserad SQL, captchas
* [Databegränsning](#data-restriction): Begränsa åtkomst till lösenordsfält och hemliga fält i externa konton
* [Drift och efterlevnad](#operational-and-compliance): Jämför med den här baslinjen regelbundet, använd granskningsspår

## Sekretess

För att kunna hantera personuppgifter på ett korrekt sätt bör du arbeta i enlighet med lagstiftningen i den eller de regioner där du bedriver verksamhet. Adobe Campaign funktioner hjälper dig att följa reglerna som anges på [den här sidan](../start/privacy.md)

### Integritet i Adobe Experience Cloud {#experience-cloud-privacy}

Adobe Campaign ingår som en del av Adobe Experience Cloud-lösningarna. Sättet på vilket sekretess hanteras i Campaign följer Experience Clouds allmänna principer som till exempel följande:

* **Vilken information samlas in när Adobe Experience Cloud används**

  Som ett företag som använder Adobe Experience Cloud-lösningar väljer du vilken information som ska samlas in och skickas till ditt Adobe Experience Cloud-konto. Exempel på information som kan samlas in är webbläsaraktivitet, IP-adresser, platsinformation från mobila enheter, kampanjers framgång, artiklar som har köpts eller placerats i en kundvagn osv.

  >[!NOTE]
  >
  >I likhet med alla andra Adobe-produkter samlar Campaign in information om program- och webbplatsanvändare. Se [Adobes integritetspolicy](https://www.adobe.com/se/privacy/policy.html) för mer information.

* **Så används Adobe Experience Cloud för att samla in information**

   * Adobe Experience Cloud-lösningar använder cookies och liknande tekniker såsom webb-beacons (kallas även för taggar eller pixlar) för att göra det möjligt att samla in information. Se [det här avsnittet](#tracking-capabilities) för mer information om cookies och spårningsfunktioner med Adobe Campaign.
   * Du kan också använda Adobe Experience Cloud-tekniker i dina mobilappar. Mer information om hur du skickar mobilleveranser med Campaign finns i [SMS-kanal](../send/sms/sms-channel.md) och Mobilappskanal.

* **Dina användares integritetsinställningar gällande hur du använder Adobe Experience Cloud**

  Adobe ber att du erbjuder dina kunder en integritetspolicy som beskriver:

   * Din bästa praxis gällande integritet i samband med Adobe Experience Cloud
   * Hur användare kan ställa in sina preferenser gällande insamling eller användning av sin information i samband med Adobe Experience Cloud

  >[!NOTE]
  >
  >Liksom för alla Adobe-produkter kan användare i Campaign avanmäla sig från att dela information som samlas in om dem via appar och webbplatser. Mer information finns i [Vanliga frågor och svar om att använda Adobe Experience Cloud](https://www.adobe.com/se/privacy/experience-cloud-usage-info-faq.html).

Se [den här sidan](https://www.adobe.com/se/privacy/marketing-cloud.html) för mer information om integriteten i Adobe Experience Cloud.

## Personuppgifter och personer {#personal-data}

När integritet hanteras är det viktigt att definiera vilka data som ska hanteras med försiktighet och av vem.
* **Personuppgifter** är information som direkt eller indirekt kan identifiera en levande individ.
* **Känsliga personuppgifter** är information om en persons etnicitet, politiska åsikter, religiösa övertygelser, brottsregister, genetiska uppgifter, hälsouppgifter, sexuell läggning, biometriska uppgifter samt medlemskap i fackföreningar.

När ni integrerar Campaign med andra Experience Cloud-lösningar där målgrupper kan överföras från ett system till ett annat, till exempel [Adobe Analytics](../connect/ac-aa.md), [Experience Cloud-målgrupper](../start/shared-audiences.md), Campaign Standard eller med andra lösningar via [CRM Connector](../../automation/workflow/crm-connector.md), måste ni vara extra noga med att skydda personuppgifter.

De [viktigaste föreskrifterna](#privacy-regulations) avser de olika enheter som hanterar data enligt följande:

* Ett **personuppgiftsansvarig** är den myndighet som bestämmer syftet med att samla in, använda och dela personuppgifter och hur det ska göras.

* Ett **personuppgiftsbiträde** är en individ eller part som samlar in, använder eller delar personuppgifter enligt den personuppgiftsansvariges anvisningar.

* En **registrerad** är en levande individ vars personuppgifter samlas in, används eller delas och som direkt eller indirekt kan identifieras genom hänvisning till dessa personuppgifter.

Som företag som samlar in och delar personuppgifter är du den personuppgiftsansvarige, dina kunder är de registrerade och Adobe Campaign fungerar som personuppgiftsbiträde när vi hanterar deras personuppgifter enligt dina anvisningar. Observera att det är ditt ansvar som personuppgiftsansvarige att hantera relationen med de registrerade såsom vid hantering av [förfrågningar om användarens information](#privacy-requests).

### Scenario med användningsfall {#use-case-scenario}

För att illustrera hur personerna i de olika rollerna interagerar följer ett exempel, på hög nivå, av en GDPR-kundupplevelse.

I det här exemplet är kunden i Adobe Campaign ett flygbolag. Det här företaget är **personuppgiftsansvarig** och alla klienter i flygbolaget är **registrerade**. Laura är i det här fallet en kund hos flygbolaget.

Dessa är de olika personerna som används i det här exemplet:

* **Laura** är den **registrerade**. Hon är mottagaren som får meddelanden från flygbolaget. Laura är kanske en person som flyger ofta men kan vid något tillfälle besluta att hon inte vill ha någon personlig reklam eller marknadsföringsmeddelanden från flygbolaget. Hon ber flygbolaget (baserat på deras process) att ta bort sitt nummer som frekvent flygresenär.

* **Anne** är **personuppgiftsansvarig** hos flygbolaget. Hon tar emot Laura begäran, hämtar användbara ID:n som efterfrågas för att identifiera den registrerade och skickar in begäran i Adobe Campaign.

* **Adobe Campaign** är **personuppgiftsbiträdet**.

![](assets/privacy-gdpr-flow.png)

Här följer det allmänna flödet för det här användningsfallet:

1. Den **registrerade** (Laura) skickar en GDPR-begäran till **personuppgiftsansvarige** via e-post, kundtjänsten eller en webbportal.

1. **Personuppgiftsansvarige** (Anne) skickar GDPR-begäran till Campaign via gränssnittet eller ett API.

1. När **personuppgiftsbiträdet** (Adobe Campaign) tar emot informationen utförs åtgärden i GDPR-begäran och ett svar eller bekräftelse skickas till **personuppgiftsansvarige** (Anne).

1. **Personuppgiftsansvarige** (Anne) granskar sedan informationen och skickar tillbaka den till den **registrerade** (Laura).

## Datainsamling {#data-acquisition}

Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du erhåller och övervakar medgivande från dina mottagare.

* Låt alltid mottagarna godkänna att ta emot meddelanden. För att göra detta ska du fortsätt respektera förfrågningar om borttagning så snabbt som möjligt och verifiera medgivande genom en dubbel anmälningsprocess. Mer information om det här finns i [Skapa ett prenumerationsformulär med dubbel anmälan](https://experienceleague.adobe.com/sv/docs/campaign-classic/using/designing-content/web-forms/use-cases-web-forms){target=_blank}.
* Importera inte bedrägliga listor och använd dirigerade adresser för att kontrollera att din klientfil inte används bedrägligt. Mer information om det här finns i [Om dirigerade adresser](https://experienceleague.adobe.com/sv/docs/campaign-classic/using/sending-messages/using-seed-addresses/about-seed-addresses){target=_blank}.
* Genom medgivande och behörighetshantering kan du spåra mottagarnas preferenser och hantera vem inom organisationen som har tillgång till vilka data. Mer information finns i [det här avsnittet](#consent).
* Underlätta och hantera förfrågningar om användarens information från era mottagare. Mer information finns i [det här avsnittet](#privacy-requests).

## Integritetshantering {#privacy-management}

Integritetshantering avser alla processer och verktyg som kan hjälpa er att följa sekretessbestämmelser (GDPR, CCPA, etc.).

Adobe Campaign tillhandahåller olika funktioner för integritetshantering:
* Medgivandehantering, datalagring och användarroller. Se [det här avsnittet](#consent).
* Förfrågningar om användarens information (åtkomsträttigheter och rätt att glömmas). Se [det här avsnittet](#privacy-requests).
* Avanmäl dig från försäljning av personuppgifter (CCPA-specifik).

De viktigaste integritetsfunktionerna i Campaign och ett exempel på vilka personer som berörs, presenteras i [det här avsnittet](https://helpx.adobe.com/se/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).

### Medgivande, lagring och roller {#consent}

Adobe Campaign erbjuder viktiga funktioner som är grundläggande för integriteten:

* **Medgivandehantering**: genom prenumerationshantering kan du hantera mottagarnas preferenser och spåra vilka mottagare som har valt att anmäla sig till vilka typer av prenumerationer. Mer information om det här finns i [Om prenumerationer](../../automation/workflow/subscription-services.md).
* **Datalagring**: alla inbyggda standardiserade loggtabeller har förinställda lagringsperioder vilket i allmänhet begränsar datalagringen till 6 månader eller mindre. Ytterligare lagringsperioder kan ställas in med arbetsflöden. Kontakta Adobes konsulter eller teknikadministratörer för mer information om detta.
* **Hantering av rättigheter**: Adobe Campaign ger dig möjligheten att hantera de rättigheter som tilldelats olika operatörer i Campaign via olika färdiga eller anpassade roller. Det här låter dig hantera vilka inom företaget som kan få åtkomst till, ändra eller exportera olika typer av data. Se [Om åtkomsthantering](https://experienceleague.adobe.com/sv/docs/campaign-classic/using/installing-campaign-classic/security-privacy/access-management){target=_blank} för mer information.

### Förfrågningar om användarens information {#privacy-requests}

Adobe Campaign erbjuder ytterligare funktioner som underlättar din beredskap som personuppgiftsansvarig för vissa förfrågningar om användarens information:

* **Åtkomsträttigheterna** är den registrerades rätt att från personuppgiftsansvarige få bekräftelse på om personuppgifter som rör dem behandlas eller inte, var de befinner dig och varför.

* **Rätten att glömmas** (förfrågan om borttagning) ger den registrerade personen rätten att låta den personuppgiftsansvarige radera sina personuppgifter.

Förfrågningar om **åtkomst** och **radering** visas i [det här avsnittet](../start/privacy.md).

Implementeringsstegen för att skapa de här förfrågningarna finns i [det här avsnittet](../start/privacy.md).

## Spårningsfunktioner {#tracking-capabilities}

### Cookies {#cookies}

Tack vare spårningsfunktionerna i Adobe Campaign kan du spåra vad leveransmottagarna surfar om med hjälp av tre typer av cookies: en sessionscookie och två permanenta cookies.

* En **sessionscookie**: Cookien **nlid** innehåller identifieraren för e-postmeddelandet som skickas till kontakten (**broadlogId**) och identifieraren för meddelandemallen (**deliveryId**). Den läggs till när kontakten klickar på en URL som ingår i ett e-postmeddelande som skickas av Adobe Campaign och låter dig spåra deras beteende på webben. Denna sessionscookie raderas automatiskt när webbläsaren stängs. Kontakten kan konfigurera sin webbläsare så att den inte tillåter cookies.

* Två **permanenta** cookies:
   * Cookien **UUID** (Universal Unique IDentifier) delas mellan Adobe Experience Cloud-lösningar. Den ställs in en gång tills den försvinner från klientwebbläsaren när ett nytt värde skapas. Med den här cookien kan du identifiera de användare som interagerar med Experience Cloud-lösningarna när de besöker en webbplats. Den kan ställas in av en landningssida (för att koppla okända kundaktiviteter till en mottagare) eller av en leverans. Beskrivningen av den här cookien finns på [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=sv-SE#ec-cookies).
   * Cookien **nllastdelid** (som introducerades i Campaign Classic 20.3) är en permanent cookie som innehåller **deliveryId** för den senaste leveransen där användaren klickade på länken. Den här cookien används för att identifiera spårningstabellen som ska användas när sessionscookien saknas.

Föreskrifter som den allmänna dataskyddsförordningen (GDPR) kräver att företag erhåller medgivande från webbplatsanvändare innan de installerar några cookies.

* Popup-fönster bör undvikas eftersom de ofta blockeras av webbläsare.

### Meddelandespårning {#message-tracking}

Med Adobe Campaign kan du spåra skickade e-postmeddelanden och leveransmottagarnas beteende: öppna, klicka på länkar, avsluta prenumerationer osv. Mer information finns i [Om meddelanden](../start/gs-message.md).

Det gör du genom att lägga till spårade länkar i meddelandena för att mäta effekten av leverans och mottagarnas beteende på fliken Spårning på kontrollpanelen för leverans. Spårningsdata tolkas i rapporten för spårningsindikatorer. Mer information om spårning finns på [den här sidan](../send/tracking.md).

### Webbspårning {#web-tracking}

>[!AVAILABILITY]
>
>Webbspårning är inte tillgängligt i Campaign v8. Läs mer om otillgängliga funktioner på [den här sidan](../start/v7-to-v8.md#gs-unavailable-features).

## Skydd av data och PII {#data-and-pii-protection}

Konfiguration och skärpning av sekretess är en viktig del av säkerhetsoptimeringen. Följ dessa standarder:

* **Använd HTTPS för alla slutpunkter** - Kontrollera att alla slutpunkter som används av Campaign (spårning, spegelsida, webbprogram, API:er) hanteras via HTTPS.
* **Begränsa PII-vyn** - Använd [PII-vybegränsning](../dev/restrict-pi-view.md) så att endast behöriga operatorer kan se känsliga fält (t.ex. e-post, telefon) i scheman och på skärmar.
* **Begränsa åtkomsten till krypterade lösenord** - Begränsa åtkomsten till lösenord och hemliga fält i externa konton och andra scheman så att bara administratörer eller en minimal uppsättning operatorer kan visa dem. Se [Databegränsning](#data-restriction) nedan.
* **Skydda känsliga sidor** - Begränsa åtkomsten till spegelsidor, webbprogram och landningssidor som visar eller samlar in PII. Använd operatörs- och mappbehörigheter och, i tillämpliga fall, hämtningar och samtycke.

>[!NOTE]
>
>Som användare av hanterade molntjänster arbetar Adobe med dig för att implementera dessa konfigurationer i din miljö.

## Åtkomsthantering {#access-management}

Åtkomshantering är en viktig del av säkerhetsbehärskningen. Här är de bästa sätten:

* **Skapa tillräckligt många säkerhetsgrupper** - Definiera operatörsgrupper som matchar roller och bara tilldelar de rättigheter som varje roll behöver.
* **Kontrollera att alla operatorer har rätt åtkomsträttigheter** - Använd principen om minst privilegium. Undvik som standard administration eller andra breda rättigheter.
* **Undvik att använda admin-operatorn och undvik att ha för många operatorer i admin-gruppen** - Dela inte det inbyggda administratörskontot. Skapa en operator per fysisk användare för ansvar och revision.
* **En operator per fysisk användare** - Dela inte konton. Skapa en Campaign-operator (Adobe ID) per person så att åtkomsthistorik och loggar kan användas.
* **Begränsa namngivna rättigheter med hög behörighet** - Bevilja **ADMINISTRATION**, **PROGRAM EXECUTION** (createProcess) och **SQL** endast till ett fåtal tillförlitliga operatorer. Dokumentera vem som har dem och varför.
* **Granska åtkomsten regelbundet** - Granska regelbundet Operatorer, Operator-grupper och mappbehörigheter; ta bort eller minska åtkomsten när roller ändras eller personer lämnar.
* **Använd produktprofiler på ett konsekvent sätt** - Föredra att tilldela användare till produktprofiler (operatorgrupper) i Admin Console, håll namnen konsekventa (t.ex. `campaign - <instance> - <group>`). Se [Kom igång med behörigheter](../start/gs-permissions.md).
* **Åtkomst till Kontrollpanelen** - I Campaign v8 kan produktprofiler eller namngivna rättigheter vars namn innehåller admin ge åtkomst till Campaign-kontrollpanelen. Undvik att använda admin i profil- eller gruppnamn om inte dessa användare ska ha åtkomst till Kontrollpanelen.

Läs mer om behörigheter i [det här avsnittet](../start/gs-permissions.md).

## Autentisering och session {#authentication-and-session}

* **Använd Adobe IMS** - Alla användare bör logga in med sin Adobe ID (IMS); förlita sig inte på äldre inloggnings-/lösenord för dagliga operatorer.
* **Förlita dig på en stark identitet- och lösenordspolicy** - Använd Admin Console eller din identitetsleverantör för MFA och lösenordspolicy. Se till att endast behöriga användare tilldelas till produktprofiler för Campaign.
* **Konfigurera sessionstimeout** - Ange en rimlig sessionstimeout och lås skärmen när du lämnar arbetsstationen, om det går att konfigurera (t.ex. klientkonsolen).

## Instans- och nätverkssäkerhet {#instance-and-network-security}

Som produktadministratör för Campaign v8 använder du [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv){target="_blank"} för att hantera säkerhet på instansnivå:

* **IP-tillåtelselista** - Hantera IP-tillåtelselista för instansåtkomst, begränsa till kända nätverk (t.ex. kontor, VPN) och undvik överdrivet breda intervall där det är möjligt.
* **URL-behörigheter** - Begränsa URL-behörigheter till de domäner som instansen behöver anropa (API:er, spårning, externa tjänster) för att minska risken för missbruk av begäran på serversidan.
* **GPG-nycklar** - Om du använder kryptering för filöverföringar eller andra användningsfall hanterar du GPG-nycklar via Kontrollpanelen och roterar dem i enlighet med din säkerhetspolicy.

## Riktlinjer för kodning {#coding-guidelines}

När du utvecklar i Adobe Campaign (arbetsflöden, Javascript, JSSP osv.) ska du alltid följa dessa riktlinjer:

* **Skript** - Försök att undvika rå SQL. Använd parametriserade funktioner i stället för strängsammanfogning. Undvik SQL-injektion genom att bara lägga till de SQL-funktioner du behöver i tillåtelselista.
* **Skydda datamodellen** - Använd namngivna rättigheter för att begränsa operatoråtgärder och lägga till systemfilter (sysFilter).
* **Lägg till hämtningar i webbprogram** - Lägg till hämtningar på offentliga landningssidor och prenumerationssidor.
* **Hårdkoda inte hemligheter** - Hårdkoda inte lösenord, API-nycklar eller token i arbetsflöden, JavaScript eller JSSP; använd externa konton eller säkra konfigurationer.
* **Validera och sanera indata** - Validera och sanera användarindata i webbprogram och arbetsflödesparametrar för att minska riskerna med inmatning och XSS.
* **Använd tillåtelselista för SQL** - När SQL- eller skriptkörning krävs använder du tillåtelselista för tillåtna SQL-funktioner och undviker att skapa frågor från användarindata via strängsammanfogning.

Läs mer i [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/scripting-coding-guidelines.html?lang=sv-SE#installing-campaign-classic){target="_blank"}.


## Personalisering

När du lägger till anpassade länkar till ditt innehåll bör du alltid undvika att ha en personalisering i värdnamnsdelen av webbadressen för att undvika eventuella säkerhetsbrister. Följande exempel får aldrig användas i alla URL-attribut &lt;`a href="">` eller `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

## Databegränsning {#data-restriction}

Du måste se till att de krypterade lösenorden inte är tillgängliga för en autentiserad användare med låg behörighet. Det finns två sätt: begränsa åtkomsten till lösenordsfält enbart eller till hela entiteten.

Med den här begränsningen kan du ta bort lösenordsfält, men låta det externa kontot vara tillgängligt från gränssnittet för alla användare. Läs mer på [den här sidan](../dev/restrict-pi-view.md).

1. Gå in **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.

1. Skapa en ny **[!UICONTROL Extension of a schema]**.

1. Välj **[!UICONTROL External Account]** (extAccount).

1. På den sista skärmen kan du redigera ditt nya srcSchema för att begränsa åtkomsten till alla lösenordsfält:

   Du kan ersätta huvudelementet (`<element name="extAccount" ... >`) med:

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Så din utökade srcSchema kan se ut så här:

   ```
   <...>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   <...> 
   ```

   >[!NOTE]
   >
   >Du kan ersätta `$(loginId) = 0 or $(login) = 'admin'` med `hasNamedRight('admin')` om du vill att alla användare med administratörsbehörighet ska kunna se de här lösenorden.

## Operativ verksamhet och efterlevnad {#operational-and-compliance}

* **Jämför med säker baslinje** - Jämför regelbundet operatörsgrupperna, namngivna rättigheter och mappbehörigheter med rekommendationerna på den här sidan (och, i tillämpliga fall, [Förbättrat säkerhetstillägg](enhanced-security.md)) för att anpassa dem till rekommenderade säkra standardvärden.
* **Använd granskningsspåret** - Använd granskningsspåret för Campaign för att se viktiga ändringar (t.ex. arbetsflöden, leveranser, nyckelkonfiguration). Behåll och granska loggar enligt din efterlevnads- och lagringspolicy.
