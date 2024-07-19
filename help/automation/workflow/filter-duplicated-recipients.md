---
product: campaign
title: Filtrera duplicerade mottagare
description: Lär dig filtrera duplicerade mottagare
feature: Workflows
role: User
exl-id: cfa1f45c-e1ac-4055-996c-6e8d041889bb
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# Filtrera duplicerade mottagare {#filtering-duplicated-recipients}



I det här exemplet vill vi filtrera mottagare som visas två gånger eller flera gånger i en leverans för att återskapa duplicerade profiler.

Så här skapar du det här exemplet:

1. Dra och släpp en **[!UICONTROL Query]**-aktivitet i ett arbetsflöde och öppna aktiviteten.
1. Klicka på **[!UICONTROL Edit query]** och ställ in mål- och filtreringsdimensionerna på **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definiera följande filtervillkor för målmottagaren som finns i leveransloggen. Välj **Leveranslogg för mottagare (utsändningslogg)** i kolumnen **Uttryck**. Välj **Finns t.ex.** i kolumnen **Operator**.

   ![](assets/query_recipients_2.png)

1. Definiera följande filtervillkor för att ange leveransmålet. Välj **[!UICONTROL Internal name]** i kolumnen Uttryck och **[!UICONTROL equal to]** i kolumnen Operator.
1. Lägg till det interna namnet för målleveransen i värdekolumnen.

   ![](assets/query_recipients_3.png)

1. Använd en **[!UICONTROL AND]**-operator för att upprepa samma åtgärder för att ange andra leveranser som mål.

   ![](assets/query_recipients_4.png)

Din utgående övergång innehåller de dubblettmottagare som är angivna i leveranserna.
