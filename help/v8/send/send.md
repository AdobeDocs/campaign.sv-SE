---
title: Skicka och övervaka e-postmeddelanden
description: Läs mer om omfattningen och egenskaperna för att skicka e-postmeddelanden med Adobe Campaign
feature: Email
role: Data Engineer
level: Beginner
version: Campaign v8, Campaign Classic v7
exl-id: f2c26351-8ed7-498a-ac83-d4c583fb98f3
source-git-commit: 96f1518f252be7ffa27ba8157b8a090bf4d4510d
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---


# Skicka och övervaka e-postmeddelanden  {#send-and-monitor-emails}

Kontrollera att du har kört leveransanalysen när leveransen är konfigurerad och klar att skickas. [Läs mer](delivery-analysis.md)

Bekräfta leveransen när du är klar för att starta meddelandeleveransen.

Spåra leveransen från fliken **Leverans** som du kommer åt via leveransinformationen eller genom leveranslistan.

## Övervaka dina e-postmeddelanden {#email-monitoring}

Kontrollera leveransstatus på **leveransinstrumentpanelen** och kom åt leveransloggar och rapporter för att bekräfta att meddelandena skickades korrekt.

På kontrollpanelen för leverans kan du kontrollera de bearbetade meddelandena och leveransgranskningsloggarna. Du kan också styra status för meddelandena i leveransloggarna.

>[!NOTE]
>
>Leveransstatus visas inte i realtid. Läs mer om tjänsten för e-postfeedback [i det här avsnittet](#email-feedback-service).

## Kampanj-MTA {#mta}

Campaign v8 Mail Transfer Agent (MTA) är en ledande sändningsinfrastruktur som ger optimal leveransbarhet, renommé, dataflöde, rapportering, studshantering, IP-avstämning och hantering av anslutningsinställningar.

Den är tillgänglig för alla kunder med Campaign v8 och garanterar skalbarhet, ett högt leveransflöde och hjälper till att skicka fler e-postmeddelanden snabbare. Detta uppnås med nya adaptiva leveransmetoder som ändrar e-postsändningsinställningarna i realtid baserat på feedback från Internetleverantörer.

### Fördelar

Adobe Campaign använder en MTA (Mail Transfer Agent) som kör SparkPosts kommersiella e-post MTA som kallas **Momentum**.

Momentum är en innovativ MTA-teknik med höga prestanda som inkluderar smartare studshantering och en automatiserad leveransoptimeringsfunktion som hjälper avsändare att uppnå och upprätthålla optimala leveransfrekvenser för inkorgen.

* MTA möjliggör en kraftig ökning av den totala genomströmningshastigheten och en betydande minskning av mjuka studsar.
* Den använder den senaste MTA-tekniken för att ge dig optimala dataöverföringshastigheter för e-postleveransen.
* Genom att direkt och automatiskt anpassa den till den feedback den får säkerställer den också exaktare och intelligentare e-postleverans med realtidsdata.

### Studentkvalificering

För **synkrona** felmeddelanden vid leveransfel avgör MTA studstypen och kvalificeringen och skickar tillbaka informationen till Campaign.

MTA kvalificerar SMTP-studsen och skickar tillbaka kvalificeringen till Campaign i form av en studskod mappad till en Campaign-studsorsak och -kvalificering.

>[!NOTE]
>
>För närvarande är **asynkrona** studsar kvalificerade av inMail-processen via reglerna **[!UICONTROL Inbound email]**.

Läs mer om leveransfel i [det här avsnittet](delivery-failures.md).


### Särskilda MX-regler

MX-regler (Mail eXchanger) är de regler som hanterar kommunikation mellan en sändande server och en mottagande server.

MTA har egna MX-regler som gör det möjligt att anpassa dataflödet per domän baserat på ditt eget historiska e-postrykte och på feedback i realtid från de domäner där du skickar e-post.

### DKIM-signering

Domain Keys Identified Mail (DKIM) är en autentiseringsmetod som används för att identifiera förfalskade avsändaradresser (kallas ofta förfalskning).

I Adobe Campaign utförs signeringen av DKIM e-postautentisering av MTA.

Läs mer om DKIM i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=sv-SE#authentication){target="_blank"}.

## Tjänsten för e-postfeedback {#email-feedback-service}

Tjänsten för e-postfeedback för Campaign (EFS) rapporterar status för varje e-postleverans som skickas med Adobe Campaign.

När leveransen har startats ändras inte procentandelen **[!UICONTROL Success]** när meddelandet har skickats från Campaign till MTA. Leveransloggarna visar statusen **[!UICONTROL Taken into account by the service provider]** för varje måladress.

När meddelandet levereras till målprofilerna och när den här informationen har rapporterats i realtid från MTA visar leveransloggarna status **[!UICONTROL Sent]** för varje adress som har tagit emot meddelandet. Procentandelen **[!UICONTROL Success]** ökas därefter för varje slutförd leverans.

När hårda studsmeddelanden rapporteras från MTA ändras deras loggstatus från **[!UICONTROL Taken into account by the service provider]** till **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

När meddelanden med mjuk studsning rapporteras tillbaka från MTA ändras inte deras loggstatus (**[!UICONTROL Taken into account by the service provider]**): endast [felorsak](delivery-failures.md#delivery-failure-reasons) uppdateras<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. Procentandelen **[!UICONTROL Success]** ändras inte. Ett nytt försök att studsa meddelanden görs sedan under leveransens [giltighetsperiod](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/communication-channels){target="_blank"}:

* Om ett nytt försök lyckas före giltighetsperiodens slut ändras meddelandets status till **[!UICONTROL Sent]** och procentandelen **[!UICONTROL Success]** ökas i enlighet med detta.

* Annars ändras statusen till **[!UICONTROL Failed]**. Procentandelen **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** --> ändras inte.

>[!NOTE]
>
>Mer information om hårda och mjuka studsar finns i [det här avsnittet](delivery-failures.md#delivery-failure-reasons).
>
>Mer information om återförsök efter ett tillfälligt leveransfel finns i [det här avsnittet](delivery-failures.md#retries).

Tabellen nedan visar hur nyckeltal och sändande loggstatus uppdateras vid varje steg i sändningsprocessen.

| Steg i sändningsprocessen | KPI-sammanfattning | Loggstatus skickas |
|--- |--- |--- |
| Meddelandet har vidarebefordrats från Campaign till MTA | **[!UICONTROL Success]** procent visas inte (startar vid 0 %) | Tjänsteleverantören har tagit hänsyn till |
| Hårdstudsmeddelanden rapporteras tillbaka från MTA | Ingen ändring i procentandelen **[!UICONTROL Success]** | Misslyckades |
| Momsstudsmeddelanden rapporteras tillbaka från MTA | Ingen ändring i procentandelen **[!UICONTROL Success]** | Tjänsteleverantören har tagit hänsyn till |
| Mjuka studsmeddelanden - återförsök har slutförts | Procentandelen **[!UICONTROL Success]** ökas därefter | Skickat |
| Mjukt studsande meddelanden återförsök misslyckas | Ingen ändring i procentandelen **[!UICONTROL Success]** | Misslyckades |
