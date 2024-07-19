---
title: Hantera och automatisera processer med Adobe Campaign arbetsflöden
description: Kom igång med arbetsflöden
feature: Workflows
role: User, Admin
level: Beginner
exl-id: 0be1c5f5-f07d-46dc-bebc-5eb50f466547
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# Kom igång med arbetsflöden{#gs-with-workflows}

Konfigurera Campaign för att utnyttja de kraftfulla funktionerna för automatisering av marknadsföringskampanjer.

Du kan konfigurera:

* Arbetsflöden
* Återkommande kampanjer
* Valideringscykel från början till slut
* Varningar
* Automatisk rapportsändning
* Utlösta händelser

## Arbetsflöden för design och användning {#gs-ac-wf}

Använd Adobe Campaign arbetsflöden för att förbättra hastigheten och skalan på alla delar av era marknadsföringskampanjer, från att skapa segment och förbereda meddelanden till leverans.

Lär dig hur du utformar arbetsflöden i dessa [kompletta användningsfall](#end-to-end-uc).

Läs mer om arbetsflöden, användargränssnitt och körning på dessa sidor:

* [Kom igång med arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html){target="_blank"}

* [Bästa praxis för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}

* [Inbyggda tekniska arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html){target="_blank"}

* [Körning av arbetsflöden för övervakning](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}

* [Skapa en målgrupp i ett arbetsflöde för marknadsföringskampanjer](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html){target="_blank"}

## Arbetsflödesaktiviteter {#wf-activities}

Läs mer om tillgängliga arbetsflödesaktiviteter i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html){target="_blank"}

Arbetsflödesaktiviteter grupperas efter kategori. De fyra aktivitetskategorierna är tillgängliga:

* [Målaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/targeting-activities.html){target="_blank"}: Fråga, Läslista, Berikning, Förening med mera
* [Flödeskontrollaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/flow-control-activities.html){target="_blank"}: Schemaläggare, gaffel, varning, extern signal med mera
* [Åtgärdsaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html){target="_blank"}: Flerkanalsleveranser, JavaScript-kod, CRM-aktiviteter, Uppdatera sammanställning med mera
* [Händelseaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/event-activities.html){target="_blank"}: Filöverföring, webbnedladdning med mera

### Ändra datakällaktivitet {#change-data-source-activity}

Med aktiviteten **[!UICONTROL Change data source]** kan du ändra datakällan för arbetsflödet **[!UICONTROL Working table]**. Detta ger större flexibilitet att hantera data över olika datakällor, som FDA, FFDA och lokala databaser.

**[!UICONTROL Working table]** tillåter Adobe Campaign-arbetsflöde att hantera data och dela data med arbetsflödesaktiviteter.
Som standard skapas **[!UICONTROL Working table]** i samma databas som källan för de data vi söker efter.

Om du till exempel frågar i tabellen **[!UICONTROL Profiles]**, som lagras i molndatabasen, skapar du en **[!UICONTROL Working table]** i samma molndatabas.
Om du vill ändra detta kan du lägga till aktiviteten **[!UICONTROL Change Data Source]** och välja en annan datakälla för **[!UICONTROL Working table]**.

Observera att när du använder aktiviteten **[!UICONTROL Change Data Source]** måste du växla tillbaka till molndatabasen för att kunna fortsätta med arbetsflödeskörningen.

Så här använder du aktiviteten **[!UICONTROL Change Data Source]**:

1. Skapa ett arbetsflöde.

1. Fråga dina målmottagare med en **[!UICONTROL Query]**-aktivitet.

   Mer information om aktiviteten **[!UICONTROL Query]** finns på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}.

1. Lägg till en **[!UICONTROL Change data source]**-aktivitet på fliken **[!UICONTROL Targeting]** och dubbelklicka på den för att välja **[!UICONTROL Default data source]**.

   Arbetstabellen, som innehåller resultatet av frågan, flyttas sedan till PostgreSQL-standarddatabasen.

1. Dra och släpp en **[!UICONTROL JavaScript code]**-aktivitet från fliken **[!UICONTROL Actions]** för att utföra enhetsåtgärder i arbetstabellen.

   Mer information om aktiviteten **[!UICONTROL JavaScript code]** finns på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/sql-code-and-javascript-code.html){target="_blank"}.

1. Lägg till ytterligare en **[!UICONTROL Change data source]**-aktivitet för att växla tillbaka till molndatabasen.

   Dubbelklicka på din aktivitet och välj **[!UICONTROL Active FDA external account]** och sedan motsvarande externt konto.

1. Nu kan du starta arbetsflödet.

## Hantera virtuella lagerställen {#warehouse}

När du har skapat arbetsflödet kan du få tillgång till ytterligare alternativ med knappen **[!UICONTROL Properties]** för ytterligare konfiguration.

Läs mer om **Arbetsflödesegenskaper** i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/advanced-management/workflow-properties.html){target="_blank"}.

På fliken **[!UICONTROL Execution]** i arbetsflödets **[!UICONTROL Properties]** kan du välja att länka arbetsflödet till olika lagerställen och optimera arbetsbelastningshanteringen. Mer information om **lagerställen** finns i [Snowflake-dokumentationen](https://docs.snowflake.com/en/user-guide/warehouses-overview.html){target="_blank"}.

![](assets/warehouse.png)

Beroende på arbetsflödets syfte kan du välja mellan följande tre lagerställen i listrutan **[!UICONTROL Warehouse]**:

* **[!UICONTROL Default]** / **[!UICONTROL Campaign]**: anges som standard när ett nytt arbetsflöde skapas.

* **[!UICONTROL Import / Export]**: bör anges med import- eller exportarbetsflöden för att optimera aktiviteternas prestanda.

* **[!UICONTROL Campaign Burst]**: ska anges med kampanj- eller leveransarbetsflöden för att optimera bearbetningstiden för leveranser.

>[!NOTE]
>
>Lagerstället **[!UICONTROL System]** har bara angetts för inbyggda arbetsflöden.

## Ställ in återkommande kampanjer

Designa återkommande arbetsflöde och skapa en ny leveransinstans varje gång arbetsflödet körs. Om ditt arbetsflöde till exempel är utformat för att köras en gång i veckan resulterar det i 52 leveranser efter ett år. Detta innebär också att loggarna separeras av varje leveransinstans.

Lär dig hur du skapar en återkommande kampanj på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/recurring-periodic-campaigns.html){target="_blank"}.


## Utnyttja utlösarhändelser

Använd Campaign Transactional Messaging för att automatisera meddelanden som genereras från händelser som triggas av informationssystem. Dessa transaktionsmeddelanden kan t.ex. vara faktura, orderbekräftelse, leveransbekräftelse, lösenordsändring, meddelande om att produkten inte är tillgänglig, kontoutdrag eller skapande av webbkonto. Dessa meddelanden kan skickas individuellt eller i grupp via e-post, SMS eller push-meddelanden.

Läs mer om funktioner för transaktionsmeddelanden i [det här avsnittet](../send/transactional.md).

Koppla upp Adobe Campaign och Adobe Analytics för att ta fram användaråtgärder och skicka i stort sett personaliserade meddelanden i realtid.

Lär dig hur du integrerar Campaign med andra lösningar i [det här avsnittet](../start/connect.md)


## Användningsexempel för hela arbetsflödet{#end-to-end-uc}

I det här avsnittet hittar du olika användningsexempel som utnyttjar funktionerna i Campaign-arbetsflöden.

### Leveranser {#deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">


* [Skicka ett födelsedagsmeddelande](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/send-a-birthday-email.html){target="_blank"}

  I det här användningsexemplet visas hur du planerar att skicka ett återkommande e-postmeddelande till en lista över mottagare på deras födelsedag.

* [Läs in leveransinnehåll](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/load-delivery-content.html){target="_blank"}
När ditt leveransinnehåll är tillgängligt i en HTML-fil på en fjärrserver kan du enkelt läsa in det i Adobe Campaign-leveranser.

* [Arbetsflöde för flerkanalsleverans](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/cross-channel-delivery-workflow.html){target="_blank"}
Lär dig hur du skapar ett arbetsflöde för flerkanalsleverans. Målet är att segmentera en målgrupp från mottagarna av databasen i olika grupper och skicka ett e-postmeddelande till den första gruppen och ett SMS till den andra.

* [E-postanrikning med anpassade datumfält](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/email-enrichment-with-custom-date-fields.html){target="_blank"}
Lär dig hur du skickar ett e-postmeddelande med anpassade datafält till profiler som firar sina födelsedagar den här månaden. E-postmeddelandet innehåller en kupong som är giltig en vecka före och efter deras födelsedag.

Och dessa sidor finns i dokumentationen för Campaign v7:

* [Automatisera skapande, utgåva och publicering av innehåll](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/content-management/automating-via-workflows.html){target="_blank"}
Lär dig hur du automatiserar skapandet och leveransen av ett innehållsblock med tillägget för hantering av kampanjinnehåll.

* [A/B-testning](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/a-b-testing/use-case/a-b-testing-use-case.html){target="_blank"}
Lär dig hur du jämför två e-postleveranser via ett arbetsflöde för målinriktning. Meddelandet och texten är identiska i båda leveranser: endast layouten ändras. Målpopulationen är uppdelad i tre: två testgrupper och den återstående populationen. En annan version av leveransen skickas till varje testgrupp.

### Övervakning {#monitoring}

<img src="assets/do-not-localize/icon_monitoring.svg" width="60px">

* [Skicka en rapport till en lista](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/monitoring/send-a-report-to-a-list.html){target="_blank"}
Lär dig hur du skapar en månadsinbyggd rapport för spårningsindikatorer i PDF-format och skickar den till en lista över kampanjoperatorer.

* [Övervaka dina arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/monitoring/workflow-supervision.html){target="_blank"}
Lär dig hur du skapar ett arbetsflöde där du kan övervaka statusen för en uppsättning arbetsflöden som är&quot;pausade&quot;,&quot;stoppade&quot; eller&quot;med fel&quot;.

* [Skicka personaliserade aviseringar till operatorer](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/monitoring/send-alerts-to-operators.html){target="_blank"}
Lär dig hur du skickar en varning till en operator som ska innehålla namnet på profiler som öppnade ett nyhetsbrev men som inte klickade på länken som det innehåller.

### Datahantering {#management}

<img src="assets/do-not-localize/icon_manage.svg" width="60px">

* [Koordinera datauppdateringar](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/coordinate-data-updates.html){target="_blank"}
Lär dig hur du kontrollerar att uppdateringsprocessen har avslutats innan du kör en annan uppdateringsåtgärd. För att göra detta skapar vi en instansvariabel och låter arbetsflödet testa om instansen körs för att bestämma om körningen av arbetsflödet ska fortsätta och uppdateringen utföras.

* [Skapa en sammanfattningslista](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/create-a-summary-list.html){target="_blank"}
Lär dig hur du skapar ett arbetsflöde där du kan skapa en sammanfattningslista när du har samlat in filer och följt flera förbättringar. Exemplet är baserat på en lista med kontakter som har köpt i en butik.

* [Förbättra data](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/enrich-data.html){target="_blank"}
Lär dig hur du skickar personaliserade leveranser till profiler som deltog i den senaste tävlingen beroende på deras resultat.

* [Använd aggregat](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/using-aggregates.html){target="_blank"}
Lär dig hur du identifierar de sista mottagarna som har lagts till i databasen.

* [Kvartalsvis listuppdatering med en inkrementell fråga](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/designing-queries/quarterly-list-update.html){target="_blank"}
Lär dig hur du använder en stegvis fråga för att automatiskt uppdatera en mottagarlista.

* [Konfigurera ett återkommande importarbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/recurring-import-workflow.html){target="_blank"}
Lär dig hur du utformar ett arbetsflöde som kan återanvändas vid import av profiler från en CRM i Adobe Campaign-databasen.

### Målinriktning {#designing-queries}

<img src="assets/do-not-localize/icon_filter.svg" width="60px">

* [Fråga mottagartabellen](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/designing-queries/querying-recipient-table.html){target="_blank"}
Lär dig hur du återställer namn och e-post för mottagare vars e-postdomän är orange.co.uk och som inte bor i London.

* [Fråga efter leveransinformation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/designing-queries/query-delivery-info.html){target="_blank"}
Lär dig hur du definierar frågor om leveransinformation för att hämta profilens beteende.

* [Beräkna aggregat](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/designing-queries/compute-aggregates.html){target="_blank"}
Lär dig räkna antalet profiler som bor i London, baserat på kön.

* [Fråga med många-till-många-relation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/designing-queries/query-many-to-many-relationship.html){target="_blank"}
Lär dig hur du hittar profiler som inte har kontaktats under de senaste 7 dagarna.

* [Anropa en instansvariabel i en fråga](https://experienceleague.adobe.com/docs/campaign/automation/workflows/advanced-management/javascript-scripts-and-templates.html){target="_blank"}
Lär dig hur du använder en instansvariabel för att dynamiskt beräkna den delade procentandelen som ska användas på en population.

<!--
### Change data source activity {#data-source-uc}

The **[!UICONTROL Change data source]** activity allows you to change the data source of a workflow **[!UICONTROL Working table]**. 

In this use case, learn how to use the **[!UICONTROL Change data source]** activity to perform unitary operations to insert or update information to the recipient table.

![](assets/wf_data_source_uc.png)

1. Create a workflow and add a **[!UICONTROL Start]** activity.

1. Query your targeted recipients from the NmsRecipient table with a **[!UICONTROL Query]** activity. 

    For more information on the **[!UICONTROL Query]** activity, refer to the [Query](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/query.html#creating-a-query) page in Campaign Classic V7 documentation.

1. 

1. From the **[!UICONTROL Targeting]** tab, add a **[!UICONTROL Change data source]** activity and double-click it to select **[!UICONTROL Default data source]**.
    
    The working table, which contains the result of your query, is then moved to the default PostgreSQL database.

1. From the **[!UICONTROL Actions]** tab, drag and drop a **[!UICONTROL JavaScript code]** activity to perform unitary operations on the working table.

1. Add another **[!UICONTROL Change data source]** activity to revert back to the Cloud database. 
    
    Double-click your activity and select **[!UICONTROL Active FDA external account]** then the corresponding external account.

1. Add an **[!UICONTROL End]** activity and start your workflow.
-->

