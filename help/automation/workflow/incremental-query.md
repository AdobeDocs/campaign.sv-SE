---
product: campaign
title: Inkrementell fråga
description: Läs mer om arbetsflödesaktiviteten Inkrementell fråga
feature: Workflows, Targeting Activity
role: User
exl-id: 3e9f92c3-080f-441b-a15a-2ec9d056d1f9
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 3%

---

# Inkrementell fråga{#incremental-query}



Med en stegvis fråga kan du regelbundet välja ett mål baserat på ett villkor, samtidigt som du utesluter de personer som redan är målinriktade för det här kriteriet.

Populationen som redan är mål lagras i minnet efter arbetsflödesinstans och efter aktivitet, vilket innebär att två arbetsflöden som startas från samma mall inte delar samma logg. Två uppgifter som baseras på samma inkrementella fråga för samma arbetsflödesinstans använder däremot samma logg.

Frågan definieras på samma sätt som för vanliga frågor, men körningen är schemalagd.

**Relaterade ämnen:**

* [Användningsfall: Kvartalsvis listuppdatering med en inkrementell fråga](quarterly-list-update.md)
* [Skapa en fråga](query.md#creating-a-query)

>[!CAUTION]
>
>Om resultatet av en inkrementell fråga är lika med **&#x200B;**&#x200B;under en av dess körningar pausas arbetsflödet tills frågan körs nästa gång. De övergångar och aktiviteter som följer efter den stegvisa frågan bearbetas därför inte före nästa körning.

Så här gör du:

1. Välj alternativet **[!UICONTROL Schedule execution]** på fliken **[!UICONTROL Scheduling & History]**. Aktiviteten förblir aktiv när den har skapats och aktiveras endast vid de tidpunkter som anges i schemat för körning av frågan. Om alternativet är inaktiverat körs frågan omedelbart **och i en gång**.
1. Klicka på knappen **[!UICONTROL Change]**.

   I **[!UICONTROL Schedule editing wizard]**-fönstret kan du konfigurera typen av frekvens, händelseupprepning och händelsegiltighetsperiod.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Klicka på **[!UICONTROL Finish]** om du vill spara schemat.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. I det nedre avsnittet på fliken **[!UICONTROL Scheduling & History]** kan du välja hur många dagar som ska tas med i historiken.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

     Mottagare som redan är målinriktade kan loggas i högst ett antal dagar från den dag då de var målinriktade. Om värdet är noll rensas mottagarna aldrig från loggen.

   * **[!UICONTROL Keep history when starting]**

     Med det här alternativet kan du inte rensa loggen när aktiviteten är aktiverad.

   * **[!UICONTROL SQL table name]**

     Med den här parametern kan du överlagra SQL-standardtabellen som innehåller historikdata.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar den population som frågan riktar sig till. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna, **[!UICONTROL schema]** är schemat för populationen (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.
