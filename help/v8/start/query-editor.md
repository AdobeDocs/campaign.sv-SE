---
title: Arbeta med frågeredigeraren
description: Lär dig hur du arbetar med frågeredigeraren
feature: Query Editor, Data Management
role: User
level: Beginner
version: Campaign v8, Campaign Classic v7
source-git-commit: 56d5628312ea3dedf9335dd0933811e4bf66eb97
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# Query Campaign-databas

Frågeverktyget finns på olika nivåer i programmet och kan användas för att definiera målpopulationer, segmentera kunder, extrahera och filtrera spårningsloggar, skapa filter och mycket mer.

Den innehåller en dedikerad assistent - den generiska frågeredigeraren - som du kommer åt på menyn **[!UICONTROL Tools > Generic query editor...]**. Med den här redigeraren kan databasfrågor extrahera, ordna, gruppera och sortera information. Den kan till exempel hämta mottagare som klickat mer än n gånger på en nyhetsbrevslänk under en viss period.

Den generiska frågeredigeraren centraliserar alla frågefunktioner. Det gör det möjligt att skapa och lagra begränsningsfilter, som sedan kan återanvändas i andra sammanhang, till exempel rutan Fråga i ett målarbetsflöde.

![Öppna frågeredigeraren och välj en tabell](assets/query_editor_nveau_21.png)


Steg för att skapa en fråga är detaljerade [på den här sidan](design-queries.md).

<!--
Contexts to use the query editor iin Campaign are listed below:

|Usage|Example|
|  ---  |  ---  |
|**Define a Query activity in a workflow**: Define the criteria to query Campaign database in a workflow. [Learn how to configure the Query activity](../../automation/workflow/query.md)|![Image showing how to configure a query activity in a workflow](../../automation/workflow/assets/query-activity.png){width="200" align="center" zoomable="yes"}|
|**Define audiences**: Specify the population you want to target in your messages, and effortlessly create new audiences tailored to your needs. [Learn how to build audiences](../start/create-message.md#define-the-target-audience)|![Image showing how to access the audience creation interface](../send/sms/assets/audience_to.png){width="200" align="center" zoomable="yes"}|
|**Define audiences**: Specify the population you want to target in your messages or workflows, and effortlessly create new audiences tailored to your needs. [Learn how to build audiences](../audiences/create-audiences.md)|![Image showing how to access the audience creation interface](../audiences/assets/targeting-wf-age-filter.png){width="200" align="center" zoomable="yes"}|
|**Customize workflow activities**: Apply rules within workflow activities, such as **Split** and **Reconciliation**, to align with your specific requirements. [Learn more about workflow activities](../../automation/workflow/activities.md)|![Image showing how to access workflow customization options](assets/access-workflow.png){width="200" align="center" zoomable="yes"}|
|**Predefined filters**: Create predefined filters that serve as shortcuts during various filtering operations, whether you're working with data lists or forming the audience for a delivery. [Learn how to work with predefined filters](../get-started/predefined-filters.md)|![Image showing how to access predefined filters](assets/access-predefined-filter.png){width="200" align="center" zoomable="yes"}|
|**Filter reports data**: Add rules to filter the data displayed in reports. [Learn how to work with reports](../reporting/gs-reports.md)|![Image showing how to filter data in reports](assets/access-reports.png){width="200" align="center" zoomable="yes"}|
|**Customize lists**: Create custom rules to filter the data displayed in lists such as recipients or deliveries lists. [Learn how to filter lists](../get-started/list-filters.md#list-built-in-filters)|![Image showing how to customize list filters](assets/access-lists.png){width="200" align="center" zoomable="yes"}|
|**Build conditional content**: Make email content dynamic by creating conditions that define which content should be displayed to different recipients, ensuring personalized and relevant messaging. [Learn how to build conditional content](../personalization/conditions.md)|![Image showing how to create conditional content](assets/conditional-content.png){width="200" align="center" zoomable="yes"}|
-->

**Relaterade ämnen**

* [Aktivitet för arbetsflödesfråga](../../automation/workflow/query.md)
* [Fråga mottagartabellen](../../automation/workflow/querying-recipient-table.md)
* [Filtreringsvillkor](filter-conditions.md)