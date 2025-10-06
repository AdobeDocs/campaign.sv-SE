---
title: Hantera och automatisera processer med Adobe Campaign arbetsflöden
description: Kom igång med arbetsflöden
feature: Workflows
role: User, Admin
level: Beginner
exl-id: 0be1c5f5-f07d-46dc-bebc-5eb50f466547
source-git-commit: 95c944963feee746a2bb83a85f075134c91059d1
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 3%

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

>[!NOTE]
>
>Adobe Campaign webbgränssnitt har en omdesignad arbetsyta för arbetsflöden som gör att man kan skapa mer dynamiska och personaliserade kundresor. Mer information om arbetsflöden för webbgränssnitt finns i [Adobe Campaign webbgränssnittsdokumentation](https://experienceleague.adobe.com/en/docs/campaign-web/v8/wf/gs-workflows){target=_blank}.


## Arbetsflöden för design och användning {#gs-ac-wf}

Använd Adobe Campaign arbetsflöden för att förbättra hastigheten och skalan på alla delar av era marknadsföringskampanjer, från att skapa segment och förbereda meddelanden till leverans.

Läs mer om arbetsflöden, användargränssnitt och körning på dessa sidor:

* [Kom igång med arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html){target="_blank"}

* [God praxis för arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}

* [Inbyggda tekniska arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html){target="_blank"}

* [Kör arbetsflöden för övervakning](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}

* [Skapa en målgrupp i ett arbetsflöde för marknadsföringskampanjer](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html){target="_blank"}

## Arbetsflödesaktiviteter {#wf-activities}

Läs mer om tillgängliga arbetsflödesaktiviteter i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html){target="_blank"}

Arbetsflödesaktiviteter grupperas efter kategori. De fyra aktivitetskategorierna är tillgängliga:

* [Målaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/targeting-activities.html){target="_blank"}: Fråga, Läslista, Berikning, Förening med mera
* [Flödeskontrollaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/flow-control-activities.html){target="_blank"}: Schemaläggare, gaffel, varning, extern signal med mera
* [Åtgärdsaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html){target="_blank"}: Flerkanalsleveranser, JavaScript-kod, CRM-aktiviteter, Uppdatera sammanställning med mera
* [Händelseaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/event-activities.html){target="_blank"}: Filöverföring, webbnedladdning med mera

<!--
### Change data source activity {#change-data-source-activity}

The **[!UICONTROL Change data source]** activity allows you to change the data source of a workflow **[!UICONTROL Working table]**. This provides more flexibility to manage data across different data sources such as FDA, FFDA and local database.

The **[!UICONTROL Working table]** allows Adobe Campaign workflow to handle data and share data with the workflow activities.
By default, the **[!UICONTROL Working table]** is created in the same database as the source of the data we query on.

For example, when querying the **[!UICONTROL Profiles]** table, stored on the Cloud database, you will create a **[!UICONTROL Working table]** on the same Cloud database.
To change this, you can add the **[!UICONTROL Change Data Source]** activity to choose a different data source for your **[!UICONTROL Working table]**.

Note that when using the **[!UICONTROL Change Data Source]** activity, you will need to switch back to the Cloud database to continue the workflow execution.

To use the **[!UICONTROL Change Data Source]** activity:

1. Create a workflow.

1. Query your targeted recipients with a **[!UICONTROL Query]** activity. 

    For more information on the **[!UICONTROL Query]** activity, refer to [this page](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}.

1. From the **[!UICONTROL Targeting]** tab, add a **[!UICONTROL Change data source]** activity and double-click it to select **[!UICONTROL Default data source]**.
    
    The working table, which contains the result of your query, is then moved to the default PostgreSQL database.

1. From the **[!UICONTROL Actions]** tab, drag and drop a **[!UICONTROL JavaScript code]** activity to perform unitary operations on the working table.

    For more information on the **[!UICONTROL JavaScript code]** activity, refer to [this page](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/sql-code-and-javascript-code.html){target="_blank"}.

1. Add another **[!UICONTROL Change data source]** activity to switch back to the Cloud database. 
    
    Double-click your activity and select **[!UICONTROL Active FDA external account]** then the corresponding external account.

1. You can now start your workflow.
-->

## Hantera virtuella lagerställen {#warehouse}

När du har skapat arbetsflödet kan du få tillgång till ytterligare alternativ med knappen **[!UICONTROL Properties]** för ytterligare konfiguration.

Läs mer om **Arbetsflödesegenskaper** på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/advanced-management/workflow-properties.html){target="_blank"}.

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

Lär dig mer genom användningsexempel som utnyttjar funktioner för Campaign-arbetsflöden [i det här avsnittet](../../automation/workflow/workflow-use-cases.md).
