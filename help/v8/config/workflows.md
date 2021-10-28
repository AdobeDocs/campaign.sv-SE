---
title: Hantera och automatisera processer med Adobe Campaign arbetsflöden
description: Kom igång med arbetsflöden
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 0be1c5f5-f07d-46dc-bebc-5eb50f466547
source-git-commit: d21dc1adc46121e5c015deed7ddb84ec6a4ec76f
workflow-type: tm+mt
source-wordcount: '1680'
ht-degree: 1%

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

Lär dig utforma arbetsflöden i dessa [end-to-end use case](#end-to-end-uc).

Läs mer om arbetsflöden, användargränssnitt och körning i dokumentationen för Campaign Classic v7:

* [Kom igång med arbetsflöden](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/about-workflows.html?lang=en#automating-with-workflows){target=&quot;_blank&quot;}

* [Bästa arbetsflöden](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/workflow-best-practices.html?lang=sv){target=&quot;_blank&quot;}

* [Inbyggda tekniska arbetsflöden](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/advanced-management/about-technical-workflows.html){target=&quot;_blank&quot;}

* [Körning av arbetsflöden för övervakning](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/monitoring-workflows/monitoring-workflow-execution.html){target=&quot;_blank&quot;}

* [Bygg en målgrupp i ett arbetsflöde för marknadsföringskampanjer](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-target.html?lang=en#building-the-main-target-in-a-workflow){target=&quot;_blank&quot;}

## Arbetsflödesaktiviteter {#wf-activities}

![](../assets/do-not-localize/book.png) Läs mer om tillgängliga arbetsflödesaktiviteter [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/about-activities.html){target=&quot;_blank&quot;}

Arbetsflödesaktiviteter grupperas efter kategori. De fyra aktivitetskategorierna är tillgängliga:

* [Verksamheter som riktar sig till](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/about-targeting-activities.html){target=&quot;_blank&quot;}: Fråga, läslista, berikning, union med mera
* [Flödeskontroll](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/flow-control-activities/about-flow-control-activities.html){target=&quot;_blank&quot;}: Schemaläggare, gaffel, avisering, extern signal med mera
* [Verksamheter](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/action-activities/about-action-activities.html){target=&quot;_blank&quot;}: Flerkanalsleveranser, JavaScript-kod, CRM-aktiviteter, Uppdatera sammanställning med mera
* [Evenemangsaktiviteter](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/action-activities/about-action-activities.html){target=&quot;_blank&quot;}: Filöverföring, webbnedladdning med mera

### Ändra datakällaktivitet {#change-data-source-activity}

The **[!UICONTROL Change data source]** kan du ändra datakällan för ett arbetsflöde **[!UICONTROL Working table]**. Detta ger större flexibilitet att hantera data över olika datakällor, som FDA, FFDA och lokala databaser.

The **[!UICONTROL Working table]** gör att Adobe Campaign arbetsflöde kan hantera data och dela data med arbetsflödesaktiviteter.
Som standard är **[!UICONTROL Working table]** skapas i samma databas som källan för de data som vi frågar efter.

När du till exempel frågar **[!UICONTROL Profiles]** tabellen, som lagras i molndatabasen, skapar du en **[!UICONTROL Working table]** i samma molndatabas.
Om du vill ändra detta kan du lägga till **[!UICONTROL Change Data Source]** aktivitet för att välja en annan datakälla för **[!UICONTROL Working table]**.

Observera att när du använder **[!UICONTROL Change Data Source]** måste du växla tillbaka till molndatabasen för att kunna fortsätta med arbetsflödeskörningen.

Så här använder du **[!UICONTROL Change Data Source]** aktivitet:

1. Skapa ett arbetsflöde.

1. Fråga målmottagarna med en **[!UICONTROL Query]** aktivitet.

   Mer information om **[!UICONTROL Query]** aktivitet, se [Fråga](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/query.html#creating-a-query) i dokumentationen för Campaign Classic V7.

1. Från **[!UICONTROL Targeting]** flik, lägga till **[!UICONTROL Change data source]** och dubbelklicka på den för att välja **[!UICONTROL Default data source]**.

   Arbetstabellen, som innehåller resultatet av frågan, flyttas sedan till PostgreSQL-standarddatabasen.

1. Från **[!UICONTROL Actions]** tabb, dra och släppa **[!UICONTROL JavaScript code]** för att utföra enhetsåtgärder i arbetsregistret.

   Mer information om **[!UICONTROL JavaScript code]** aktivitet, se [JavaScript-kod och avancerad JavaScript-kod](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/action-activities/sql-code-and-javascript-code.html#javascript-code) i dokumentationen för Campaign Classic V7.

1. Lägg till ytterligare **[!UICONTROL Change data source]** aktivitet för att växla tillbaka till molndatabasen.

   Dubbelklicka på aktiviteten och välj **[!UICONTROL Active FDA external account]** därefter motsvarande externt konto.

1. Nu kan du starta arbetsflödet.

## Hantera virtuella lagerställen {#warehouse}

När du har skapat arbetsflödet kan du få tillgång till ytterligare alternativ med **[!UICONTROL Properties]** för ytterligare konfiguration.

![](../assets/do-not-localize/book.png) Läs mer om **Egenskaper för arbetsflöde** in [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/advanced-management/workflow-properties.html?lang=en){target=&quot;_blank&quot;}

Från **[!UICONTROL Execution]** -fliken i arbetsflödets **[!UICONTROL Properties]** kan du länka arbetsflödet till olika lagerställen och optimera hanteringen av arbetsbelastningen. Mer information om **Lagerställen**, se [Snowflake dokumentation](https://docs.snowflake.com/en/user-guide/warehouses-overview.html).

![](assets/warehouse.png)

Beroende på arbetsflödets syfte kan du välja mellan följande tre lagerställen på menyn **[!UICONTROL Warehouse]** nedrullningsbar meny:

* **[!UICONTROL Default]** / **[!UICONTROL Campaign]**: anges som standard när du skapar ett nytt arbetsflöde.

* **[!UICONTROL Import / Export]**: bör ställas in med import- eller exportarbetsflöden för att optimera aktiviteternas prestanda.

* **[!UICONTROL Campaign Burst]**: bör ställas in med kampanj- eller leveransarbetsflöden för att optimera bearbetningstiden för leveranser.

>[!NOTE]
>
>The **[!UICONTROL System]** dist.lager är bara inställt för inbyggda arbetsflöden.

## Ställ in återkommande kampanjer

Designa återkommande arbetsflöde och skapa en ny leveransinstans varje gång arbetsflödet körs. Om ditt arbetsflöde till exempel är utformat för att köras en gång i veckan resulterar det i 52 leveranser efter ett år. Detta innebär också att loggarna separeras av varje leveransinstans.

![](../assets/do-not-localize/book.png) Lär dig hur du skapar en återkommande kampanj i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/setting-up-marketing-campaigns.html?lang=en#recurring-and-periodic-campaigns){target=&quot;_blank&quot;}


## Utnyttja utlösarhändelser

Använd Campaign Transactional Messaging för att automatisera meddelanden som genereras från händelser som triggas av informationssystem. Dessa transaktionsmeddelanden kan t.ex. vara faktura, orderbekräftelse, leveransbekräftelse, lösenordsändring, meddelande om att produkten inte är tillgänglig, kontoutdrag eller skapande av webbkonto. Dessa meddelanden kan skickas individuellt eller i grupp via e-post, SMS eller push-meddelanden.

![](../assets/do-not-localize/glass.png) Läs mer om funktioner för transaktionsmeddelanden i [det här avsnittet](../send/transactional.md).

Koppla upp Adobe Campaign och Adobe Analytics för att ta fram användaråtgärder och skicka i stort sett personaliserade meddelanden i realtid.

![](../assets/do-not-localize/glass.png) Lär dig integrera Campaign med andra lösningar i [det här avsnittet](../start/connect.md)


## Användningsexempel för hela arbetsflödet{#end-to-end-uc}

I det här avsnittet hittar du olika användningsexempel som utnyttjar funktionerna i Campaign-arbetsflöden. De här användningsexemplen är inbyggda i Adobe Campaign Classic v7 och gäller för Adobe Campaign v8.

### Leveranser {#deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

* [A/B-tester](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/a-b-testing/use-case/a-b-testing-use-case.html){target=&quot;_blank&quot;}

   Lär dig hur du jämför två e-postleveranser via ett arbetsflöde för målinriktning. Meddelandet och texten är identiska i båda leveranserna: bara layouten ändras. Målgruppen är uppdelad i tre delar: två testgrupper och den återstående populationen. En annan version av leveransen skickas till varje testgrupp.

* [Skicka ett födelsedagsmeddelande](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/sending-a-birthday-email.html){target=&quot;_blank&quot;}

   I det här användningsexemplet visas hur du planerar att skicka ett återkommande e-postmeddelande till en lista över mottagare på dagen för deras födelsedag.

* [Läser in leveransinnehåll](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/loading-delivery-content.html){target=&quot;_blank&quot;} När leveransinnehållet är tillgängligt i en HTML-fil på en fjärrserver kan du enkelt läsa in det här innehållet i Adobe Campaign-leveranser.

* [Arbetsflöde för flerkanalsleverans](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/cross-channel-delivery-workflow.html){target=&quot;_blank&quot;}

   Lär dig hur du skapar ett arbetsflöde för flerkanalsleverans. Målet är att segmentera en målgrupp från mottagarna av databasen i olika grupper och skicka ett e-postmeddelande till den första gruppen och ett SMS till den andra.

* [E-postberikning med anpassade datumfält](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/email-enrichment-with-custom-date-fields.html){target=&quot;_blank&quot;}

   Lär dig hur du skickar ett e-postmeddelande med anpassade datafält till profiler som firar sina födelsedagar den här månaden. E-postmeddelandet innehåller en kupong som är giltig en vecka före och efter deras födelsedag.

* [Automatisera framtagning, utgåva och publicering av innehåll](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/content-management/automating-via-workflows.html){target=&quot;_blank&quot;}

   Lär dig hur du automatiserar skapandet och leveransen av ett innehållsblock med tillägget för hantering av kampanjinnehåll.


### Övervakning {#monitoring}

<img src="assets/do-not-localize/icon_monitoring.svg" width="60px">

* [Skicka en rapport till en lista](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/monitoring/sending-a-report-to-a-list.html){target=&quot;_blank&quot;}

   Lär dig hur du skapar en månadsinbyggd rapport för spårningsindikatorer i PDF-format och skickar den till en lista över kampanjoperatorer.

* [Övervaka era arbetsflöden](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/monitoring/supervising-workflows.html){target=&quot;_blank&quot;}

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

* [Kvartalslistuppdatering med inkrementell fråga](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/quarterly-list-update.html){target=&quot;_blank&quot;}

   Lär dig hur du använder en stegvis fråga för att automatiskt uppdatera en mottagarlista.

* [Konfigurera ett återkommande importarbetsflöde](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/recurring-import-workflow.html){target=&quot;_blank&quot;}

   Lär dig hur du utformar ett arbetsflöde som kan återanvändas vid import av profiler från en CRM i Adobe Campaign-databasen.

### Målinriktning {#designing-queries}

<img src="assets/do-not-localize/icon_filter.svg" width="60px">

* [Fråga mottagartabellen](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/querying-recipient-table.html){target=&quot;_blank&quot;}

   Lär dig hur du återställer namn och e-post för mottagare vars e-postdomän är orange.co.uk och som inte bor i London.

* [Fråga leveransinformation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/querying-delivery-information.html){target=&quot;_blank&quot;}

   Lär dig hur du definierar frågor om leveransinformation för att hämta profilens beteende.

* [Beräkna aggregat](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/performing-aggregate-computing.html){target=&quot;_blank&quot;}

   Lär dig räkna antalet profiler som bor i London, baserat på kön.

* [Fråga med många-till-många-relation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/designing-queries/querying-using-many-to-many-relationship.html){target=&quot;_blank&quot;}

   Lär dig hur du hittar profiler som inte har kontaktats under de senaste 7 dagarna.

* [Anropa en förekomstvariabel i en fråga](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/advanced-management/javascript-scripts-and-templates.html?lang=en#example){target=&quot;_blank&quot;}

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

