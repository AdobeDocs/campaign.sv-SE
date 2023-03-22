---
title: Skicka och övervaka e-postmeddelanden
description: Läs mer om omfattningen och egenskaperna för att skicka e-postmeddelanden med Adobe Campaign
feature: Email
role: Data Engineer
level: Beginner
exl-id: f2c26351-8ed7-498a-ac83-d4c583fb98f3
source-git-commit: 4c79078e32c77499f15906fc81f31ce2b26559d7
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---


# Skicka och övervaka e-postmeddelanden

Kontrollera att du har kört leveransanalysen när leveransen är konfigurerad och klar att skickas. [Läs mer](delivery-analysis.md)

Bekräfta leveransen när du är klar för att starta meddelandeleveransen.

Spåra leveransen från **Leverans** -fliken, tillgänglig via detaljer om leveransen eller via listan över leveranser.

## Övervaka dina e-postmeddelanden

När du har skickat den kontrollerar du leveransstatus på kontrollpanelen och öppnar leveransloggar och rapporter för att bekräfta att meddelandena har skickats korrekt.

![](../assets/do-not-localize/book.png) [Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/track-and-monitor.html){target="_blank"}


## Kampanj-MTA {#mta}

Campaign v8 Mail Transfer Agent (MTA) är en ledande sändningsinfrastruktur som ger optimal leveransbarhet, renommé, dataflöde, rapportering, studshantering, IP-avstämning och hantering av anslutningsinställningar.

Den är tillgänglig för alla kunder med Campaign v8 och garanterar skalbarhet, ett högt leveransflöde och hjälper till att skicka fler e-postmeddelanden snabbare. Detta uppnås med nya adaptiva leveransmetoder som ändrar e-postsändningsinställningarna i realtid baserat på feedback från Internetleverantörer.

### Fördelar

Adobe Campaign använder en MTA (Mail Transfer Agent) som kör SparkPosts kommersiella e-post som MTA anropar **Momentum**.

Momentum är en innovativ MTA-teknik med höga prestanda som inkluderar smartare studshantering och en automatiserad leveransoptimeringsfunktion som hjälper avsändare att uppnå och upprätthålla optimala leveransfrekvenser för inkorgen.

* MTA möjliggör en kraftig ökning av den totala genomströmningshastigheten och en betydande minskning av mjuka studsar.
* Den använder den senaste MTA-tekniken för att ge dig optimala dataöverföringshastigheter för e-postleveransen.
* Genom att direkt och automatiskt anpassa den till den feedback den får säkerställer den också exaktare och intelligentare e-postleverans med realtidsdata.

### Studentkvalificering

För **synkron** felmeddelanden vid leveransfel, MTA avgör studstypen och kvalificeringen och skickar tillbaka informationen till Campaign.

MTA kvalificerar SMTP-studsen och skickar tillbaka kvalificeringen till Campaign i form av en studskod mappad till en Campaign-studsorsak och -kvalificering.

>[!NOTE]
>
>För närvarande **asynkron** studenterna kvalificeras av inMail-processen via **[!UICONTROL Inbound email]** regler.

Läs mer om leveransfel i [det här avsnittet](delivery-failures.md).


### Särskilda MX-regler

MX-regler (Mail eXchanger) är de regler som hanterar kommunikation mellan en sändande server och en mottagande server.

MTA har egna MX-regler som gör det möjligt att anpassa dataflödet per domän baserat på ditt eget historiska e-postrykte och på feedback i realtid från de domäner där du skickar e-post.

### DKIM-signering

DKIM (Domain Keys Identified Mail) är en autentiseringsmetod som används för att identifiera förfalskade avsändaradresser (kallas ofta förfalskning).

I Adobe Campaign utförs DKIM-autentisering via e-post av MTA.

Läs mer om DKIM i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication){target="_blank"}.

## Tjänsten Email Feedback {#email-feedback-service}

Med funktionen för tjänsten för e-postfeedback (EFS) rapporteras status för varje e-postmeddelande korrekt, eftersom feedback hämtas direkt från MTA.

När leveransen har startat sker ingen förändring i **[!UICONTROL Success]** procent när meddelandet har skickats från Campaign till MTA.

Leveransloggarna visar **[!UICONTROL Taken into account by the service provider]** status för varje måladress.

När meddelandet faktiskt levereras till målprofilerna och när informationen har rapporterats i realtid från MTA visar leveransloggarna **[!UICONTROL Sent]** status för varje adress som tog emot meddelandet. The **[!UICONTROL Success]** procentandelen ökas i enlighet med varje framgångsrik leverans.

När hårda studsmeddelanden rapporteras tillbaka från MTA ändras deras loggstatus från **[!UICONTROL Taken into account by the service provider]** till **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

När meddelanden med mjuk studsning rapporteras tillbaka från MTA ändras inte loggstatusen (**[!UICONTROL Taken into account by the service provider]**): endast [felorsak](delivery-failures.md#delivery-failure-reasons) uppdateras<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. The **[!UICONTROL Success]** procentandelen förblir oförändrad. Mjuka studsmeddelanden provas sedan igen under hela leveransen [giltighetsperiod](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#defining-validity-period){target="_blank"}:

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
| Meddelandet har vidarebefordrats från Campaign till MTA | **[!UICONTROL Success]** procentandelen visas inte (börjar vid 0 %) | Tjänsteleverantören har tagit hänsyn till |
| Hårdstudsmeddelanden rapporteras tillbaka från MTA | Ingen ändring i **[!UICONTROL Success]** procent | Misslyckades |
| Momsstudsmeddelanden rapporteras tillbaka från MTA | Ingen ändring i **[!UICONTROL Success]** procent | Tjänsteleverantören har tagit hänsyn till |
| Mjuka studsmeddelanden - återförsök har slutförts | **[!UICONTROL Success]** procentandelen ökas därefter | Skickat |
| Mjukt studsande meddelanden återförsök misslyckas | Ingen ändring i **[!UICONTROL Success]** procent | Misslyckades |
