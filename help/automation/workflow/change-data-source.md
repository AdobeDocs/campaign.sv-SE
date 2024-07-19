---
title: Ändra datakälla
description: Läs mer om Ändra datakällaktivitet
feature: Workflows, Data Management, Federated Data Access
role: User
exl-id: ca7eca9d-9112-4ea1-9a0c-a24cf6a978e6
source-git-commit: b77c37ab9ba9556fdefc563deac6b55ab0d91dc8
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 2%

---

# Ändra datakälla {#change-data-source}

Använd aktiviteten **[!UICONTROL Change data source]** för att ändra datakällan för en [arbetsflödestabell](use-workflow-data.md#workflow-temporary-work-table). Den här aktiviteten ger större flexibilitet när det gäller att hantera data över olika datakällor, till exempel FDA (Federated Data Access), FDA (Campaign Cloud database) och Campaign Local-databaser.

Arbetsflödet **[!UICONTROL Working table]** används för att hantera och dela data med arbetsflödesaktiviteter.

Som standard skapas **[!UICONTROL Working table]** i samma databas som källan för de data som du vill fråga efter.
När du till exempel hämtar tabellen **[!UICONTROL Recipients]**, som lagras i molndatabasen, skapas en **[!UICONTROL Working table]** i samma molndatabas i arbetsflödet.

Använd en **[!UICONTROL Change Data Source]**-aktivitet om du vill använda en annan datakälla för **[!UICONTROL Working table]**.

Observera, att när du använder aktiviteten **[!UICONTROL Change Data Source]** måste du växla tillbaka till molndatabasen för att fortsätta arbetsflödeskörningen.

>[!IMPORTANT]
>
>Observera att aktiviteterna **[!UICONTROL Change Dimension]** och **[!UICONTROL Change Data source]** inte ska läggas till på en rad. Om du behöver använda båda aktiviteterna i följd måste du ta med en **[!UICONTROL Enrichement]**-aktivitet mellan dem. Detta garanterar att programmet körs på rätt sätt och förhindrar eventuella konflikter och fel.

Om du vill använda aktiviteten **[!UICONTROL Change Data Source]** måste du:

1. Skapa ett arbetsflöde.

1. Fråga dina målmottagare med en **[!UICONTROL Query]**-aktivitet.

   Mer information om aktiviteten **[!UICONTROL Query]** finns på den här [sidan](query.md#create-a-query).

1. Lägg till en **[!UICONTROL Change data source]**-aktivitet.

   ![](assets/change-data-source.png)

1. Redigera din **[!UICONTROL Change data source]**-aktivitet för att välja **[!UICONTROL Default data source]**.

   Arbetstabellen, som innehåller resultatet av din fråga, flyttas sedan till den lokala standarddatabasen för Campaign.

   ![](assets/change-data-source_2.png)

1. Lägg till en **[!UICONTROL JavaScript code]**-aktivitet för att utföra enhetsåtgärder i arbetsregistret.

   Mer information om aktiviteten **[!UICONTROL JavaScript code]** finns på sidan [this](sql-code-and-javascript-code.md#javascript-code).

1. Lägg till ytterligare en **[!UICONTROL Change data source]**-aktivitet för att växla tillbaka till molndatabasen.

1. Redigera den här aktiviteten och välj **[!UICONTROL Active FDA external account]** och motsvarande **[!UICONTROL External database]**-externa konto.

   ![](assets/change-data-source_3.png)

1. Nu kan du starta arbetsflödet.
