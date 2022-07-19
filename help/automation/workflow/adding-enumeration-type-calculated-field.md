---
product: campaign
title: Lägg till ett beräkningsfält av uppräkningstyp
description: Lär dig hur du lägger till ett beräkningsfält av typen Uppräkning
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Lägg till ett beräkningsfält av uppräkningstyp {#adding-an-enumeration-type-calculated-field}



Här vill vi skapa en fråga med en **[!UICONTROL Enumerations]** skriv beräkningsfält. Det här fältet genererar ytterligare en kolumn i förhandsgranskningsfönstret för data. Den här kolumnen anger de numeriska värden som returneras som resultat för varje mottagare (0, 1 och 2). Varje värde i den nya kolumnen tilldelas ett kön: &quot;Man&quot; för &quot;1&quot;, &quot;kvinna&quot; för &quot;2&quot; eller &quot;Inte angivet&quot; om värdet är lika med &quot;0&quot;.

* Vilken tabell måste markeras?

   mottagartabellen (nms:mottagare)

* Fält som ska markeras i utdatakolumnen?

   Efternamn, förnamn, kön

* Vilka villkor som informationen ska filtreras baserat på?

   Mottagarspråket

Använd följande steg:

1. Öppna den allmänna frågeredigeraren och välj mottagartabellen (**[!UICONTROL nms:recipient]**).
1. I **[!UICONTROL Data to extract]** fönster, markera **[!UICONTROL Last name]**, **[!UICONTROL First name]** och **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. I **[!UICONTROL Sorting]** fönster, klicka **[!UICONTROL Next]**: ingen sortering behövs för det här exemplet.
1. I **[!UICONTROL Data filtering]** väljer du **[!UICONTROL Filtering conditions]**.
1. I **[!UICONTROL Target element]** anger du ett filtervillkor för att samla in mottagare som talar engelska.

   ![](assets/query_editor_nveau_74.png)

1. I **[!UICONTROL Data formatting]** fönster, klicka **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Gå till **[!UICONTROL Type]** fönstret **[!UICONTROL Export calculated field definition]** fönster och markera **[!UICONTROL Enumerations]**.

   Definiera den kolumn som det nya beräkningsfältet ska referera till. Om du vill göra det väljer du **[!UICONTROL Gender]** i den nedrullningsbara menyn i **[!UICONTROL Source column]** fält: målvärdena sammanfaller med **[!UICONTROL Gender]** kolumn.

   ![](assets/query_editor_nveau_76.png)

   Definiera **Källa** och **Mål** värden: målvärdet gör frågeresultatet lättare att läsa. Frågan ska returnera mottagarens kön och resultatet blir antingen 0, 1 eller 2.

   Klicka på **[!UICONTROL Add]** i **[!UICONTROL List of enumeration values]**:

   * I **[!UICONTROL Source]** anger du källvärdet för varje kön (0,1,2) på en ny rad.
   * I **[!UICONTROL Destination]** anger du värden: &quot;Ej angivet&quot; för rad &quot;0&quot;, &quot;Man&quot; för rad &quot;1&quot; och &quot;Kvinna&quot; för rad &quot;2&quot;.

   Välj **[!UICONTROL Keep the source value]** funktion.

   Klicka **[!UICONTROL OK]** för att godkänna beräkningsfältet.

   ![](assets/query_editor_nveau_77.png)

1. I **[!UICONTROL Data formatting]** fönster, klicka **[!UICONTROL Next]**.
1. I förhandsgranskningsfönstret **[!UICONTROL start the preview of the data]**.

   Den extra kolumnen definierar kön för 0, 1 och 2:

   * 0 för &quot;Ej angivet&quot;
   * 1 för &quot;Male&quot;
   * 2 för &quot;Kvinna&quot;

   ![](assets/query_editor_nveau_78.png)

   Om du t.ex. inte anger kön &quot;2&quot; i **[!UICONTROL List of enumeration values]** och **[!UICONTROL Generate a warning and continue]** funktionen i **[!UICONTROL In other cases]** fältet är markerat visas en varningslogg. Den här loggen anger att kön &quot;2&quot; (kvinna) inte har angetts. Den visas i **[!UICONTROL Logs generated during export]** i förhandsgranskningsfönstret.

   ![](assets/query_editor_nveau_79.png)

   Låt oss ta ett exempel till och säga att uppräkningsvärdet &quot;2&quot; inte anges. Välj **[!UICONTROL Generate an error and reject the line]** funktion: alla mottagare av kön&quot;2&quot; kommer att orsaka avvikelser och annan information på raden (för- och efternamn, osv.) exporteras inte. En fellogg visas i **[!UICONTROL Logs generated during export]** i förhandsgranskningsfönstret. Den här loggen anger att uppräkningsvärdet &quot;2&quot; inte har angetts.

   ![](assets/query_editor_nveau_80.png)
