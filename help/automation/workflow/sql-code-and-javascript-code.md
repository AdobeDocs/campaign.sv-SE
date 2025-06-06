---
product: campaign
title: SQL-kod och JavaScript-kod
description: Läs mer om arbetsflödesaktiviteter för SQL- och JavaScript-koder
feature: Workflows
Role: User
level: Experienced
version: Campaign v8, Campaign Classic v7
exl-id: 8c385847-a320-4cd9-9048-2bf9daf2ee07
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 7%

---

# SQL-kod och JavaScript-kod{#sql-code-and-javascript-code}



## SQL-kod {#sql-code}

En **[!UICONTROL SQL code]**-aktivitet kör ett SQL-skript. Skriptet är en JST-mall.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

  Redigerarens centrala del innehåller skriptet som ska köras. Skriptet är en JST-mall och kan därför konfigureras enligt arbetsflödeskontexten.

* **[!UICONTROL Processing errors]**

  Se [Bearbetningsfel](monitor-workflow-execution.md#processing-errors).

## JavaScript-kod och avancerad JavaScript-kod {#javascript-code}

**[!UICONTROL JavaScript code]**- och **[!UICONTROL Advanced JavaScript code]**-aktiviteter kör ett JavaScript-skript i ett arbetsflödes kontext. Mer information om skript finns i följande avsnitt:

* [JavaScript-skript och mallar](javascript-scripts-and-templates.md)
* [Exempel på JavaScript-kod i arbetsflöden](javascript-in-workflows.md)

### Körningsfördröjning {#exec-delay}

Från och med version 20.2 har en körningsfördröjning lagts till i aktiviteterna **[!UICONTROL JavaScript code]** och **[!UICONTROL Advanced JavaScript code]**. Som standard får körningsfasen inte överskrida 1 timme. Efter den här fördröjningen avbryts processen med ett felmeddelande och aktivitetskörningen misslyckas.

Du kan ändra den här fördröjningen i fältet **[!UICONTROL Stop execution after]** som är tillgängligt i de här aktiviteterna.

Om du vill ignorera den här gränsen måste du ange värdet till **0**.

### JavaScript code {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: Redigerarens centrala del innehåller skriptet som ska köras.

* **[!UICONTROL Process errors]**: Se [Bearbetningsfel](monitor-workflow-execution.md#processing-errors).

### Advanced JavaScript code {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**: Den första zonen i redigeraren innehåller skriptet som ska köras under det första anropet.
* **[!UICONTROL Next calls]**: Den andra zonen i redigeraren innehåller skriptet som ska köras under nästa anrop.
* **[!UICONTROL Transitions]**: Du kan definiera flera aktivitetsutdataövergångar.
* **[!UICONTROL Schedule]**: På fliken **[!UICONTROL Schedule]** kan du schemalägga när aktiviteten ska utlösas.

Avancerad JavaScript är en beständig uppgift som regelbundet återkallas om den inte har markerats som slutförd. Om du vill avsluta aktiviteten och förhindra framtida återkallningar måste du använda metoden **task.setCompleted()** i avsnittet **[!UICONTROL Next calls]**:

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
