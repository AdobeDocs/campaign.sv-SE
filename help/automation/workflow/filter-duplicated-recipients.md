---
product: campaign
title: Filtrera duplicerade mottagare
description: Lär dig filtrera duplicerade mottagare
feature: Workflows
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# Filtrera duplicerade mottagare {#filtering-duplicated-recipients}



I det här exemplet vill vi filtrera mottagare som visas två gånger eller flera gånger i en leverans för att återskapa duplicerade profiler.

Så här skapar du det här exemplet:

1. Dra och släpp en **[!UICONTROL Query]** i ett arbetsflöde och öppna aktiviteten.
1. Klicka **[!UICONTROL Edit query]** och ange mål- och filterdimensionerna till **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definiera följande filtervillkor för målmottagaren som finns i leveransloggen. Välj **Mottagarens leveranslogg (utsändning)** i **Uttryck** kolumn, välja **finns som** i **Operator** kolumn.

   ![](assets/query_recipients_2.png)

1. Definiera följande filtervillkor för att ange leveransmålet. Välj **[!UICONTROL Internal name]** i kolumnen Uttryck och **[!UICONTROL equal to]** i kolumnen Operator.
1. Lägg till det interna namnet för målleveransen i värdekolumnen.

   ![](assets/query_recipients_3.png)

1. Med **[!UICONTROL AND]** -operatorn, upprepa samma åtgärder för att rikta in sig på andra leveranser.

   ![](assets/query_recipients_4.png)

Din utgående övergång innehåller de dubblettmottagare som är angivna i leveranserna.
