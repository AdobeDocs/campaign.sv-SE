---
product: campaign
title: Fråga med grupperingshantering
description: Lär dig hur du utför frågor med hjälp av grupperingshantering
feature: Query Editor
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 4%

---

# Fråga med grupperingshantering {#querying-using-grouping-management}



I det här exemplet vill vi köra en fråga för att hitta alla e-postdomäner som är riktade över 30 gånger under tidigare leveranser.

* Vilken tabell måste markeras?

   mottagartabellen (nms:mottagare)

* Fält som ska markeras i utdatakolumner?

   E-postdomän och primärnyckel (med antal)

* Datagruppering?

   Baserat på e-postdomän med ett antal primärnycklar över 30. Denna operation genomförs med **[!UICONTROL Group by + Having]** alternativ. **[!UICONTROL Group by + Having]** I kan du gruppera data (&quot;gruppera efter&quot;) och göra en markering av grupperade data (&quot;ha&quot;).

Så här skapar du det här exemplet:

1. Öppna **[!UICONTROL Generic query editor]** och välj mottagartabellen (**nms:mottagare**).

   ![](assets/query_editor_02.png)

1. I **[!UICONTROL Data to extract]** väljer du **[!UICONTROL Email domain]** och **[!UICONTROL Primary key]** fält. Räkna med **[!UICONTROL Primary key]** fält.

   Mer information om antalet primärnycklar finns i .

1. Kontrollera **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** box.

   ![](assets/query_editor_nveau_29.png)

1. I **[!UICONTROL Sorting]** -fönster, sortera e-postdomäner i fallande ordning. Om du vill göra det markerar du **[!UICONTROL Yes]** i **[!UICONTROL Descending sort]** kolumn. Klicka på **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. I **[!UICONTROL Data filtering]** väljer du **[!UICONTROL Filtering conditions]**. Gå till **[!UICONTROL Target elements]** fönster och klicka **[!UICONTROL Next]**.
1. I **[!UICONTROL Data grouping]** väljer du **[!UICONTROL Email domain]** genom att klicka **[!UICONTROL Add]**.

   Det här fönstret för datagruppering visas bara om **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) har markerats.

   ![](assets/query_editor_blocklist_04.png)

1. I **[!UICONTROL Grouping condition]** anger du ett primärnyckelantal som är större än 30 eftersom vi bara vill att e-postdomäner som är avsedda mer än 30 gånger ska returneras som resultat.

   Det här fönstret visas när **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** kryssrutan har markerats: Det är här grupperingsresultatet filtreras (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. I **[!UICONTROL Data formatting]** fönster, klicka **[!UICONTROL Next]**: ingen formatering behövs här.
1. Klicka på **[!UICONTROL Launch data preview]**: Här returneras tre olika e-postdomäner som är riktade över 30 gånger.

   ![](assets/query_editor_blocklist_06.png)
