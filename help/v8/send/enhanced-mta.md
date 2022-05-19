---
title: Om Förbättrad MTA i Adobe Campaign
description: Läs mer om omfattningen av och egenskaperna hos utskick av e-post med Adobe Campaign Enhanced MTA
feature: Email
role: Data Engineer
level: Beginner
exl-id: f2c26351-8ed7-498a-ac83-d4c583fb98f3
source-git-commit: 0fa0db62f45097755bebcbf434614c4c835d886a
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 3%

---

# Om den förbättrade MTA-metoden {#sending-with-enhanced-mta}

The **Adobe Campaign Enhanced MTA** (E-postöverföringsagent) tillhandahåller en uppgraderad sändningsinfrastruktur som möjliggör optimal leveransförmåga, renommé, genomströmning, rapportering, studshantering, IP-avkodning och hantering av anslutningsinställningar.

Det är implementerat för alla Campaign v8-kunder för att förbättra skalbarheten, öka leveransgenomströmningen och hjälpa till att skicka fler e-postmeddelanden snabbare. Detta uppnås med nya adaptiva leveransmetoder som ändrar e-postsändningsinställningarna i realtid baserat på feedback från Internetleverantörer.

## Användning och fördelar

**Vad är det förbättrade MTA-avtalet?**

Adobe Campaign använder en MTA (Mail Transfer Agent) som kör SparkPosts kommersiella e-post som MTA anropar **Momentum**.

Momentum är en innovativ MTA-teknik med höga prestanda som inkluderar smartare studshantering och en automatiserad leveransoptimeringsfunktion som hjälper avsändare att uppnå och upprätthålla optimala leveransfrekvenser för inkorgen.

**Vilka är fördelarna?**

* Den förbättrade MTA-metoden möjliggör en kraftig ökning av den totala genomströmningshastigheten och en betydande minskning av mjuka studsar.
* Den använder den senaste MTA-tekniken för att ge dig optimala dataöverföringshastigheter för e-postleveransen.
* Genom att direkt och automatiskt anpassa den till den feedback den får säkerställer den också exaktare och intelligentare e-postleverans med realtidsdata.

## Förbättrade MTA-egenskaper {#enhanced-mta-impacts}

### Studentkvalificering

För **synkron** felmeddelanden vid leveransfel avgör den förbättrade MTA-metoden studstypen och kvalificeringen och skickar tillbaka informationen till Campaign.

Det förbättrade MTA-uttrycket kvalificerar SMTP-studsen och skickar tillbaka den till Campaign i form av en studskod mappad till en Campaign-studsorsak och -kvalificering.

>[!NOTE]
>
>För närvarande **asynkron** studenterna kvalificeras inte av Förbättrat MTA, utan av inMail-processen via **[!UICONTROL Inbound email]** regler. Mer information finns i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#bounce-mail-qualification){target=&quot;_blank&quot;}. <!--Refer to [bounce mail qualification](delivery-failures.md#bounce-mail-qualification)-->

Läs mer om leveransfel i [det här avsnittet](delivery-failures.md).

### Giltighetsperiod

Inställningen för giltighetsperiod i kampanjleveranserna kommer endast att användas av den förbättrade MTA-metoden om den är inställd på **3,5 dagar eller mindre**. Om du definierar ett värde som är högre än 3,5 dagar i Campaign beaktas det inte.

Om giltighetsperioden till exempel är inställd på standardvärdet 5 dagar i Campaign kommer meddelanden med mjuk studsning att hamna i den förbättrade MTA-återförsökskön och provas igen i upp till 3,5 dagar från den dag då meddelandet nådde den förbättrade MTA-gränsen. I så fall används inte det värde som angetts i Campaign.

När ett meddelande har varit i Enhanced MTA-kön i 3,5 dagar och inte kunnat levereras, kommer det att löpa ut och status uppdateras från **[!UICONTROL Sent]** till **[!UICONTROL Failed]** i leveransloggarna.

Mer information om giltighetsperioden finns i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#defining-validity-period){target=&quot;_blank&quot;}.

### Återförsök

Mjuka avhoppsförsök och hur lång tid det tar mellan dem bestäms av den förbättrade MTA-metoden baserat på typ och allvarlighetsgrad för de avhoppssvar som kommer tillbaka från meddelandets e-postdomän.

>[!NOTE]
>
>Inställningarna för nya försök i leveransegenskaperna används inte av Campaign.

Läs mer om återförsök i [det här avsnittet](delivery-failures.md#retries).

### Särskilda MX-regler

MX-regler (Mail eXchanger) är de regler som hanterar kommunikation mellan en sändande server och en mottagande server.

Den utökade MTA har egna MX-regler som gör att den kan anpassa din genomströmning efter domän baserat på ditt eget historiska e-postrykte och på realtidsfeedback från de domäner där du skickar e-post.

### DKIM-signering

DKIM (Domain Keys Identified Mail) är en autentiseringsmetod som används för att identifiera förfalskade avsändaradresser (kallas ofta förfalskning).

I Adobe Campaign signeras DKIM-e-postautentisering av den utökade MTA:n.

Läs mer om DKIM i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication){target=&quot;_blank&quot;}.

## Tjänsten Email Feedback {#email-feedback-service}

Med funktionen för tjänsten för e-postfeedback (EFS) rapporteras status för varje e-postmeddelande korrekt, eftersom feedback hämtas direkt från den förbättrade MTA-agenten (Message Transfer Agent).

När leveransen har startat sker ingen förändring i **[!UICONTROL Success]** procent när meddelandet har skickats från Campaign till det förbättrade MTA-avtalet.

Leveransloggarna visar **[!UICONTROL Taken into account by the service provider]** status för varje måladress.

När meddelandet faktiskt skickas till målprofilerna och när informationen har rapporterats i realtid från Förbättrat MTA visar leveransloggarna **[!UICONTROL Sent]** status för varje adress som tog emot meddelandet. The **[!UICONTROL Success]** procentandelen ökas i enlighet med varje framgångsrik leverans.

När hårda studsmeddelanden rapporteras tillbaka från Förbättrat MTA ändras deras loggstatus från **[!UICONTROL Taken into account by the service provider]** till **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

När meddelanden med mjuk studsning rapporteras tillbaka från Förbättrat MTA ändras inte loggstatusen (**[!UICONTROL Taken into account by the service provider]**): endast [felorsak](delivery-failures.md#delivery-failure-reasons) uppdateras<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. The **[!UICONTROL Success]** procentandelen förblir oförändrad. Mjuka studsmeddelanden provas sedan igen under hela leveransen [giltighetsperiod](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#defining-validity-period){target=&quot;_blank&quot;}:

* Om ett nytt försök lyckas före giltighetsperiodens slut ändras meddelandets status till **[!UICONTROL Sent]** och **[!UICONTROL Success]** procentandelen ökas därefter.

* I annat fall ändras statusen till **[!UICONTROL Failed]**. The **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->procentandelen förblir oförändrad.

>[!NOTE]
>
>Mer information om hårda och mjuka studsar finns i [det här avsnittet](delivery-failures.md#delivery-failure-reasons).
>
>Mer information om återförsök efter ett tillfälligt leveransfel finns i [det här avsnittet](delivery-failures.md#retries).

Tabellen nedan visar hur nyckeltal och sändande loggstatus uppdateras vid varje steg i sändningsprocessen med EFS-funktionen.

| Steg i sändningsprocessen | KPI-sammanfattning | Loggstatus skickas |
|--- |--- |--- |
| Meddelandet har vidarebefordrats från Campaign till det förbättrade MTA-meddelandet | **[!UICONTROL Success]** procentandelen visas inte (börjar vid 0 %) | Tjänsteleverantören har tagit hänsyn till |
| Hårdstudsmeddelanden rapporteras tillbaka från Förbättrad MTA | Ingen ändring i **[!UICONTROL Success]** procent | Misslyckades |
| Mjuka studsmeddelanden rapporteras tillbaka från Förbättrat MTA | Ingen ändring i **[!UICONTROL Success]** procent | Tjänsteleverantören har tagit hänsyn till |
| Mjuka studsmeddelanden - återförsök har slutförts | **[!UICONTROL Success]** procentandelen ökas därefter | Skickat |
| Mjukt studsande meddelanden återförsök misslyckas | Ingen ändring i **[!UICONTROL Success]** procent | Misslyckades |
