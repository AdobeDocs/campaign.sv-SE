---
product: campaign
title: Datainläsning (RDBMS)
description: Läs mer om arbetsflödesaktivitet för datainläsning (RDBMS)
feature: Workflows, Data Management Activity
role: User
exl-id: 2d650573-f630-4aba-bd40-2db88ef1c346
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# Datainläsning (RDBMS){#data-loading-rdbms}



The **[!UICONTROL Data loading (RDBMS)]** Med -aktivitet kan du komma åt den externa databasen direkt och samla in endast de data som krävs för målanpassning.

För att förbättra prestandan rekommenderar vi att du använder frågeaktiviteten (där data i en extern databas kan användas). Mer information finns i [Åtkomst till en extern databas (FDA)](accessing-an-external-database--fda-.md).

Åtgärden är följande:

1. Markera datakällan i listan och ange namnet på tabellen som innehåller de data som ska extraheras.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Namnet på tabellen som anges i motsvarande fält används som mall för datainsamling i den externa databasen. Namnet på den tabell som bearbetas av arbetsflödet kan beräknas eller förmedlas av den inkommande övergången för datainläsningsaktiviteten. Om du vill välja vilken tabell som ska användas klickar du på **[!UICONTROL Advanced..]**. och väljer **[!UICONTROL Specified in the transition]** eller **[!UICONTROL Explicit]** alternativ.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Klicka på **[!UICONTROL Select the columns to extract...]** för att välja vilka data som ska samlas in i databasen.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Du kan definiera ett filter för dessa data. Klicka på **[!UICONTROL Edit query....]** länk.

   De data som samlas in på det här sättet kan användas under hela arbetsflödets livscykel.
