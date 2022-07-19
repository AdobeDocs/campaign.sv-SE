---
title: Ändra datakälla
description: Läs mer om Ändra datakällaktivitet
feature: Workflows, Data Management, Federated Data Access
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 3%

---

# Ändra datakälla {#change-data-source}

Använd **[!UICONTROL Change data source]** aktivitet för att ändra datakällan för en [arbetsflödestabell](use-workflow-data.md#workflow-temporary-work-table). Den här aktiviteten ger större flexibilitet när det gäller att hantera data över olika datakällor, till exempel FDA (Federated Data Access), FDA (Campaign Cloud database) och Campaign Local-databaser.

Arbetsflödet **[!UICONTROL Working table]** används för att hantera och dela data med arbetsflödesaktiviteter.

Som standard är **[!UICONTROL Working table]** skapas i samma databas som källan för de data som du vill fråga efter.
När du till exempel frågar **[!UICONTROL Recipients]** tabell, som lagras i molndatabasen, skapar arbetsflödet en **[!UICONTROL Working table]** i samma molndatabas.

Använd en **[!UICONTROL Change Data Source]** aktivitet som använder en annan datakälla för **[!UICONTROL Working table]**.

Observera att när du använder **[!UICONTROL Change Data Source]** måste du växla tillbaka till Cloud-databasen för att fortsätta med arbetsflödeskörningen.

Så här använder du **[!UICONTROL Change Data Source]** måste du

1. Skapa ett arbetsflöde.

1. Fråga målmottagarna med en **[!UICONTROL Query]** aktivitet.

   Mer information om **[!UICONTROL Query]** aktivitet, se [page](query.md#create-a-query).

1. Lägg till en **[!UICONTROL Change data source]** aktivitet.

   ![](assets/change-data-source.png)

1. Redigera **[!UICONTROL Change data source]** aktivitet att välja **[!UICONTROL Default data source]**.

   Arbetstabellen, som innehåller resultatet av din fråga, flyttas sedan till den lokala standarddatabasen för Campaign.

   ![](assets/change-data-source_2.png)

1. Lägg till en **[!UICONTROL JavaScript code]** för att utföra enhetsåtgärder i arbetsregistret.

   Mer information om **[!UICONTROL JavaScript code]** aktivitet, se [den här sidan](sql-code-and-javascript-code.md#javascript-code).

1. Lägg till ytterligare **[!UICONTROL Change data source]** aktivitet för att växla tillbaka till molndatabasen.

1. Redigera den här aktiviteten och välj **[!UICONTROL Active FDA external account]** och motsvarande **[!UICONTROL External database]** externt konto.

   ![](assets/change-data-source_3.png)

1. Nu kan du starta arbetsflödet.
