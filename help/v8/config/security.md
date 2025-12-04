---
title: Bästa praxis för kampanjsäkerhet
description: Kom igång med de effektivaste strategierna för kampanjsäkerhet
feature: Privacy, PI
role: Developer
level: Beginner
exl-id: 1d593c8e-4b32-4902-93a7-7b18cef27cac
version: Campaign v8, Campaign Classic v7
source-git-commit: 3453820bb0eca7847ec55d7e6ea15766a57ab94e
workflow-type: tm+mt
source-wordcount: '2167'
ht-degree: 67%

---

# Bästa praxis för kampanjsäkerhet {#ac-security}

På Adobe tar vi er digitala säkerhet på stort allvar. Säkerhetsrutinerna är djupt integrerade i vår interna programutveckling och våra processer och verktyg för drift och följs noggrant av våra funktionsövergripande team för att förebygga, upptäcka och hantera incidenter på ett snabbt sätt.

Dessutom hjälper vårt samarbete med partners, ledande forskare, säkerhetsforskningsinstitutioner och andra branschorganisationer oss att hålla oss uppdaterade med de senaste hoten och säkerhetsluckorna och vi införlivar regelbundet avancerad säkerhetsteknik i de produkter och tjänster vi erbjuder.

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

* Låt alltid mottagarna godkänna att ta emot meddelanden. För att göra detta ska du fortsätt respektera förfrågningar om borttagning så snabbt som möjligt och verifiera medgivande genom en dubbel anmälningsprocess. Mer information om det här finns i [Skapa ett prenumerationsformulär med dubbel anmälan](https://experienceleague.adobe.com/en/docs/campaign-classic/using/designing-content/web-forms/use-cases-web-forms){target=_blank}.
* Importera inte bedrägliga listor och använd dirigerade adresser för att kontrollera att din klientfil inte används bedrägligt. Mer information om det här finns i [Om dirigerade adresser](https://experienceleague.adobe.com/en/docs/campaign-classic/using/sending-messages/using-seed-addresses/about-seed-addresses){target=_blank}.
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
* **Hantering av rättigheter**: Adobe Campaign ger dig möjligheten att hantera de rättigheter som tilldelats olika operatörer i Campaign via olika färdiga eller anpassade roller. Det här låter dig hantera vilka inom företaget som kan få åtkomst till, ändra eller exportera olika typer av data. Se [Om åtkomsthantering](https://experienceleague.adobe.com/en/docs/campaign-classic/using/installing-campaign-classic/security-privacy/access-management){target=_blank} för mer information.

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
   * Cookien **UUID** (Universal Unique IDentifier) delas mellan Adobe Experience Cloud-lösningar. Den ställs in en gång tills den försvinner från klientwebbläsaren när ett nytt värde skapas. Med den här cookien kan du identifiera de användare som interagerar med Experience Cloud-lösningarna när de besöker en webbplats. Den kan ställas in av en landningssida (för att koppla okända kundaktiviteter till en mottagare) eller av en leverans. Beskrivningen av den här cookien finns på [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html#ec-cookies).
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

<!--
Privacy configuration and hardening is a key element of security optimization. Here are some best practices to follow regarding privacy:

* Protect your customer Personal Information (PI) by using HTTPS instead of HTTP
* Use [PI view restriction](../dev/restrict-pi-view.md) to protect privacy and prevent data from being misused
* Make sure that encrypted passwords are restricted
* Protect the pages that might contain personal information such as mirror pages, web applications, etc.
-->

>[!NOTE]
>
>Som användare av hanterade molntjänster arbetar Adobe med dig för att implementera dessa konfigurationer i din miljö.


## Åtkomsthantering

Åtkomshantering är en viktig del av säkerhetsbehärskningen. Här är några av de bästa sätten:

* Skapa tillräckligt många säkerhetsgrupper
* Kontrollera att alla operatorer har rätt åtkomsträttigheter

Läs mer om behörigheter i [det här avsnittet](../start/gs-permissions.md)

## Riktlinjer för kodning

När du utvecklar i Adobe Campaign (arbetsflöden, Javascript, JSSP osv.) ska du alltid följa dessa riktlinjer:

* **Skript**: Undvik SQL-satser, använd parametriserade funktioner i stället för strängsammanfogning, undvik SQL-injektion genom att lägga till de SQL-funktioner som ska användas i tillåtelselista.

* **Skydda datamodellen**: använd namngivna rättigheter för att begränsa operatoråtgärder, lägg till systemfilter (sysFilter)

* **Lägg till bildtexter i webbprogram**: lägg till bildtexter på dina offentliga landningssidor och prenumerationssidor.

Läs mer i [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/scripting-coding-guidelines.html#installing-campaign-classic){target="_blank"}.


## Personalization

När du lägger till anpassade länkar till ditt innehåll bör du alltid undvika att ha en personalisering i värdnamnsdelen av webbadressen för att undvika eventuella säkerhetsbrister. Följande exempel får aldrig användas i alla URL-attribut &lt;`a href="">` eller `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

## Databegränsning

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


## Åtkomsthantering

Åtkomshantering är en viktig del av säkerhetsbehärskningen. Här är några av de bästa sätten:

* Skapa tillräckligt många säkerhetsgrupper
* Kontrollera att alla operatorer har rätt åtkomsträttigheter

Läs mer om behörigheter i [i det här avsnittet](../start/gs-permissions.md).

## Riktlinjer för kodning

När du utvecklar i Adobe Campaign (arbetsflöden, Javascript, JSSP osv.) ska du alltid följa dessa riktlinjer:

* **Skript**: Undvik SQL-satser, använd parametriserade funktioner i stället för strängsammanfogning, undvik SQL-injektion genom att lägga till de SQL-funktioner som ska användas i tillåtelselista.

* **Skydda datamodellen**: använd namngivna rättigheter för att begränsa operatoråtgärder, lägg till systemfilter (sysFilter)

* **Lägg till bildtexter i webbprogram**: lägg till bildtexter på dina offentliga landningssidor och prenumerationssidor.

Läs mer i [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/scripting-coding-guidelines.html#installing-campaign-classic){target="_blank"}.
