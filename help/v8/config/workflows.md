---
product: Adobe Campaign
title: Hantera och automatisera processer med Adobe Campaign arbetsflöden
description: Kom igång med arbetsflöden
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 0be1c5f5-f07d-46dc-bebc-5eb50f466547
source-git-commit: c61d8aa8e0a68ccc81a6141782f860daf061bc61
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 0%

---

# Hantera och automatisera processer

Konfigurera Campaign för att utnyttja de kraftfulla funktionerna för automatisering av marknadsföringskampanjer.

Du kan konfigurera:

* Arbetsflöden
* Återkommande kampanjer
* Valideringscykel från början till slut
* Varningar
* Automatisk rapportsändning
* Utlösta händelser

## Arbetsflöden för design och användning{#gs-ac-wf}

Använd Adobe Campaign arbetsflöden för att förbättra hastigheten och skalan på alla delar av era marknadsföringskampanjer, från att skapa segment och förbereda meddelanden till leverans.

Lär dig hur du utformar arbetsflöden i dessa [kompletta användningsfall](#end-to-end-uc).

Läs mer om arbetsflöden, användargränssnitt och körning i dokumentationen för Campaign Classic v7:

↗️ [Kom igång med arbetsflöden](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/about-workflows.html?lang=en#automating-with-workflows){target=&quot;_blank&quot;}
* Arbetsflödesaktiviteter:
   * [Målaktiviteter](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/about-targeting-activities.html){target=&quot;_blank&quot;}: Fråga, läslista, berikning, union med mera
   * [Flödeskontrollaktiviteter](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/flow-control-activities/about-flow-control-activities.html){target=&quot;_blank&quot;}: Schemaläggare, gaffel, avisering, extern signal med mera
   * [Åtgärdsaktiviteter](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/action-activities/about-action-activities.html){target=&quot;_blank&quot;}: Flerkanalsleveranser, JavaScript-kod, CRM-aktiviteter, Uppdatera sammanställning med mera
   * [Händelseaktiviteter](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/action-activities/about-action-activities.html){target=&quot;_blank&quot;}: Filöverföring, webbnedladdning med mera ↗️   [Bygg en målgrupp i ett marknadsföringskampanjarbetsflöde](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-target.html?lang=en#building-the-main-target-in-a-workflow){target=&quot;_blank&quot;} ↗️   [Workflow best practices](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/workflow-best-practices.html){target=&quot;_blank&quot;} ↗️  [inbyggda tekniska arbetsflöden](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/advanced-management/about-technical-workflows.html){target=&quot;_blank&quot;} ↗️ körning [ av ](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/monitoring-workflows/monitoring-workflow-execution.html)Monitor-arbetsflöden{target=&quot;_blank&quot;}


## Ställ in återkommande kampanjer

Designa återkommande arbetsflöde och skapa en ny leveransinstans varje gång arbetsflödet körs. Om ditt arbetsflöde till exempel är utformat för att köras en gång i veckan resulterar det i 52 leveranser efter ett år. Detta innebär också att loggarna separeras av varje leveransinstans.

↗️ Lär dig hur du skapar en återkommande kampanj i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/setting-up-marketing-campaigns.html?lang=en#recurring-and-periodic-campaigns){target=&quot;_blank&quot;}


## Utnyttja utlösarhändelser

Använd Campaign Transactional Messaging för att automatisera meddelanden som genereras från händelser som triggas av informationssystem. Dessa transaktionsmeddelanden kan t.ex. vara faktura, orderbekräftelse, leveransbekräftelse, lösenordsändring, meddelande om att produkten inte är tillgänglig, kontoutdrag eller skapande av webbkonto. Dessa meddelanden kan skickas individuellt eller i grupp via e-post, SMS eller push-meddelanden.

? Läs mer om funktioner för transaktionsmeddelanden i [det här avsnittet](../send/transactional.md).

Koppla upp Adobe Campaign och Adobe Analytics för att ta fram användaråtgärder och skicka i stort sett personaliserade meddelanden i realtid.

? Lär dig hur du integrerar Campaign med andra lösningar i [det här avsnittet](../start/connect.md)


## Användningsexempel för hela arbetsflödet{#end-to-end-uc}

I det här avsnittet hittar du olika användningsexempel som utnyttjar funktionerna i Campaign-arbetsflöden. De här användningsexemplen är inbyggda i Adobe Campaign Classic v7 och gäller för Adobe Campaign v8.

### Leveranser {#deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

* [A/B-testning](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/a-b-testing/use-case/a-b-testing-use-case.html){target=&quot;_blank&quot;}

   Lär dig hur du jämför två e-postleveranser via ett arbetsflöde för målinriktning. Meddelandet och texten är identiska i båda leveranserna: bara layouten ändras. Målgruppen är uppdelad i tre delar: två testgrupper och den återstående populationen. En annan version av leveransen skickas till varje testgrupp.

* [Skicka ett födelsedagsmeddelande](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/sending-a-birthday-email.html){target=&quot;_blank&quot;}

   I det här användningsexemplet visas hur du planerar att skicka ett återkommande e-postmeddelande till en lista över mottagare på dagen för deras födelsedag.

* [Inläsning av leveransinnehåll](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/loading-delivery-content.html){target=&quot;_blank&quot;} När leveransinnehållet är tillgängligt i en HTML-fil på en fjärrserver kan du enkelt läsa in innehållet i Adobe Campaign-leveranser.

* [Arbetsflöde](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/cross-channel-delivery-workflow.html) för flerkanalsleverans{target=&quot;_blank&quot;}

   Lär dig hur du skapar ett arbetsflöde för flerkanalsleverans. Målet är att segmentera en målgrupp från mottagarna av databasen i olika grupper och skicka ett e-postmeddelande till den första gruppen och ett SMS till den andra.

* [E-postanrikning med anpassade datumfält](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/email-enrichment-with-custom-date-fields.html){target=&quot;_blank&quot;}

   Lär dig hur du skickar ett e-postmeddelande med anpassade datafält till profiler som firar sina födelsedagar den här månaden. E-postmeddelandet innehåller en kupong som är giltig en vecka före och efter deras födelsedag.

* [Automatisera skapande, utgåva och publicering](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/content-management/automating-via-workflows.html) av innehåll {target=&quot;_blank&quot;}

   Lär dig hur du automatiserar skapandet och leveransen av ett innehållsblock med tillägget för hantering av kampanjinnehåll.


### Övervakning {#monitoring}

<img src="assets/do-not-localize/icon_monitoring.svg" width="60px">

* [Skicka en rapport till en lista](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/monitoring/sending-a-report-to-a-list.html){target=&quot;_blank&quot;}

   Lär dig hur du skapar en månadsinbyggd rapport för spårningsindikatorer i PDF-format och skickar den till en lista över kampanjoperatörer.

* [Övervaka dina arbetsflöden](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/monitoring/supervising-workflows.html){target=&quot;_blank&quot;}

   Lär dig hur du skapar ett arbetsflöde där du kan övervaka statusen för en uppsättning arbetsflöden som är&quot;pausade&quot;,&quot;stoppade&quot; eller&quot;med fel&quot;.

* [Skicka personaliserade aviseringar till operatorer](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/monitoring/sending-personalized-alerts-to-operators.html){target=&quot;_blank&quot;}

   Lär dig hur du skickar en varning till en operator som ska innehålla namnet på profiler som öppnade ett nyhetsbrev men som inte klickade på länken som det innehåller.

### Datahantering {#management}

<img src="assets/do-not-localize/icon_manage.svg" width="60px">

* [Koordinera datauppdateringar](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/coordinating-data-updates.html){target=&quot;_blank&quot;}

   Lär dig hur du kontrollerar att uppdateringsprocessen har avslutats innan du kör en annan uppdateringsåtgärd. För att göra detta skapar vi en instansvariabel och låter arbetsflödet testa om instansen körs för att bestämma om körningen av arbetsflödet ska fortsätta eller inte och utföra uppdateringen.

* [Skapa en sammanfattningslista](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/creating-a-summary-list.html){target=&quot;_blank&quot;}

   Lär dig hur du skapar ett arbetsflöde där du kan skapa en sammanfattningslista när du har samlat in filer och följt flera förbättringar. Exemplet är baserat på en lista med kontakter som har köpt i en butik.

* [Förbättra data](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/enriching-data.html){target=&quot;_blank&quot;}

   Lär dig hur du skickar personaliserade leveranser till profiler som deltog i den senaste tävlingen beroende på deras resultat.

* [Använd aggregat](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/using-aggregates.html){target=&quot;_blank&quot;}

   Lär dig hur du identifierar de sista mottagarna som har lagts till i databasen.

* [Kvartalsvis uppdatering av en inkrementell fråga](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/quarterly-list-update.html) {target=&quot;_blank&quot;}

   Lär dig hur du använder en stegvis fråga för att automatiskt uppdatera en mottagarlista.

* [Konfigurera ett återkommande importarbetsflöde](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/recurring-import-workflow.html){target=&quot;_blank&quot;}

   Lär dig hur du utformar ett arbetsflöde som kan återanvändas vid import av profiler från en CRM i Adobe Campaign-databasen.

### Målinriktning {#designing-queries}

<img src="assets/do-not-localize/icon_filter.svg" width="60px">

* [Fråga mottagartabellen](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/querying-recipient-table.html){target=&quot;_blank&quot;}

   Lär dig hur du återställer namn och e-post för mottagare vars e-postdomän är orange.co.uk och som inte bor i London.

* [Frågeleveransinformation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/querying-delivery-information.html){target=&quot;_blank&quot;}

   Lär dig hur du definierar frågor om leveransinformation för att hämta profilens beteende.

* [Beräkna aggregat](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/performing-aggregate-computing.html){target=&quot;_blank&quot;}

   Lär dig räkna antalet profiler som bor i London, baserat på kön.

* [Fråga med en många-till-många-relation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/querying-using-many-to-many-relationship.html){target=&quot;_blank&quot;}

   Lär dig hur du hittar profiler som inte har kontaktats under de senaste 7 dagarna.

* [Anropa en förekomstvariabel i en fråga](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/advanced-management/javascript-scripts-and-templates.html?lang=en#example){target=&quot;_blank&quot;}

   Lär dig hur du använder en instansvariabel för att dynamiskt beräkna den delade procentandelen som ska användas på en population.

