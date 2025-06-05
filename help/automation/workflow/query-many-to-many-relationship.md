---
product: campaign
title: Fråga med många-till-många-relation
description: Lär dig hur du utför frågor med hjälp av en många-till-många-relation
feature: Query Editor
role: User, Data Engineer
version: Campaign v8, Campaign Classic v7
exl-id: c320054d-7f67-4b12-aaa7-785945bf0c18
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Fråga med många-till-många-relation {#querying-using-a-many-to-many-relationship}



I det här exemplet vill vi återställa mottagare som inte har kontaktats under de senaste 7 dagarna. Frågan gäller alla leveranser.

I det här exemplet visas även hur du konfigurerar ett filter som är relaterat till valet av ett samlingselement (eller en orange nod). Samlingselement är tillgängliga i fönstret **[!UICONTROL Field to select]**.

* Vilken tabell måste markeras?

  Mottagartabellen (**nms:mottagare**)

* Fält som ska markeras för utdatakolumnen

  Primär nyckel, efternamn, förnamn och e-postadress

* Baserat på vilka kriterier är den information som filtreras

  Baserat på leveransloggarna för mottagare som går tillbaka 7 dagar före idag

Använd följande steg:

1. Öppna den allmänna frågeredigeraren och markera mottagartabellen **[!UICONTROL (nms:recipient)]**.
1. I fönstret **[!UICONTROL Data to extract]** väljer du **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** och **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Sortera namnen i bokstavsordning i sorteringsfönstret.

   ![](assets/query_editor_nveau_34.png)

1. Välj **[!UICONTROL Filtering conditions]** i fönstret **[!UICONTROL Data filtering]**.
1. I fönstret **[!UICONTROL Target element]** innebär filtreringsvillkoret för att extrahera profiler utan spårningslogg de senaste 7 dagarna två steg. Elementet som du måste markera är en många-till-många-länk.

   * Börja med att markera samlingselementet **[!UICONTROL Recipient delivery logs (broadlog)]** (orange nod) för den första **[!UICONTROL Value]**-kolumnen.

     ![](assets/query_editor_nveau_67.png)

     Välj operatorn **[!UICONTROL do not exist as]**. Du behöver inte välja ett andra värde på den här raden.

   * Innehållet i det andra filtervillkoret beror på det första. Här visas fältet **[!UICONTROL Event date]** direkt i tabellen **[!UICONTROL Recipient delivery logs]** eftersom det finns en länk till tabellen.

     ![](assets/query_editor_nveau_36.png)

     Välj **[!UICONTROL Event date]** med operatorn **[!UICONTROL greater than or equal to]**. Välj värdet **[!UICONTROL DaysAgo (7)]**. Det gör du genom att klicka på **[!UICONTROL Edit expression]** i fältet **[!UICONTROL Value]**. I fönstret **[!UICONTROL Formula type]** väljer du **[!UICONTROL Process on dates]** och **[!UICONTROL Current date minus n days]** och ger&quot;7&quot; som ett värde.

     ![](assets/query_editor_nveau_37.png)

     Filtervillkoret har konfigurerats.

     ![](assets/query_editor_nveau_38.png)

1. I fönstret **[!UICONTROL Data formatting]** växlar du efternamn till versaler. Klicka på raden **[!UICONTROL Last name]** i kolumnen **[!UICONTROL Transformation]** och välj **[!UICONTROL Switch to upper case]** i listrutan.

   ![](assets/query_editor_nveau_39.png)

1. Använd funktionen **[!UICONTROL Add a calculated field]** för att infoga en kolumn i dataförhandsvisningsfönstret.

   I det här exemplet lägger du till ett beräkningsfält med förnamn och efternamn på mottagarna i en enda kolumn. Klicka på funktionen **[!UICONTROL Add a calculated field]**. I fönstret **[!UICONTROL Export calculated field definition]** anger du en etikett och ett internt namn och väljer typen **[!UICONTROL JavaScript Expression]**. Ange sedan följande uttryck:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Klicka på **[!UICONTROL OK]**. Fönstret **[!UICONTROL Data formatting]** har konfigurerats.

   Mer information om hur du lägger till beräkningsfält finns i det här avsnittet.

1. Resultatet visas i fönstret **[!UICONTROL Data preview]**. Mottagare som inte har kontaktats de senaste 7 dagarna visas i alfabetisk ordning. Namnen visas med stora bokstäver och kolumnen med för- och efternamn har skapats.

   ![](assets/query_editor_nveau_41.png)
