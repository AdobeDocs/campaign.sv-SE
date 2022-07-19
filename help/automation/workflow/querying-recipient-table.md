---
product: campaign
title: Fråga mottagartabellen
description: Lär dig ställa frågor i mottagartabellen
feature: Query Editor
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# Fråga mottagartabellen {#querying-recipient-table}



I det här exemplet vill vi återskapa namn och e-post för mottagare vars e-postdomän är orange.co.uk och som inte bor i London.

* Vilken tabell ska vi välja?

   mottagartabellen (nms:mottagare)

* Fält som ska markeras som utdatakolumner

   E-post, namn, ort och kontonummer

* Vilka filtervillkor har mottagarna?

   stad- och e-postdomän

* Är en sortering konfigurerad?

   Ja, baserat på **[!UICONTROL Account number]** och **[!UICONTROL Last name]**

Så här skapar du det här exemplet:

1. Klicka **[!UICONTROL Tools > Generic query editor...]** och väljer **Mottagare** (**nms:mottagare**). Klicka sedan på **[!UICONTROL Next]**.
1. Välj: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** och **[!UICONTROL Account number]**. Dessa fält läggs till i **[!UICONTROL Output columns]**. Klicka sedan på **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Sortera kolumnerna så att de visas i rätt ordning. Här vill vi sortera kontonummer i fallande ordning och namn i alfabetisk ordning. Klicka sedan på **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. I **[!UICONTROL Data filtering]** fönster, förfina sökningen: välj **[!UICONTROL Filtering conditions]** och klicka **[!UICONTROL Next]**.
1. The **[!UICONTROL Target element]** I kan du ange filterinställningarna.

   Definiera följande filtervillkor: mottagare med en e-postdomän som är lika med &quot;orange.co.uk&quot;. Välj **E-postdomän (@email)** i **[!UICONTROL Expression]** kolumn, välja **lika med** i **[!UICONTROL Operator]** kolumn och ange&quot;orange.co.uk&quot; i **[!UICONTROL Value]** kolumn.

   ![](assets/query_editor_05.png)

1. Klicka på **[!UICONTROL Distribution of values]** om du vill visa en distribution baserat på e-postdomänen för potentiella kunder. Det finns en procentandel tillgänglig för varje e-postdomän i databasen. Andra domäner än &quot;orange.co.uk&quot; visas tills filtret tillämpas.

   En sammanfattning av frågan visas längst ned i fönstret: **E-postdomän som är lika med &#39;orange.co.uk&#39;**.

1. Klicka på **[!UICONTROL Preview]** för att få en uppfattning om frågeresultatet: Endast e-postdomäner med namnet&quot;orange.co.uk&quot; visas.

   ![](assets/query_editor_nveau_17.png)

1. Vi kommer nu att ändra frågan för att hitta kontakter som inte bor i London.

   Välj **[!UICONTROL City (location/@city)]** i **[!UICONTROL Expression]** kolumn, **[!UICONTROL different from]** som en operator och ange **[!UICONTROL London]** i **[!UICONTROL Value]** kolumn.

   ![](assets/query_editor_08.png)

1. Det här tar dig till **[!UICONTROL Data formatting]** -fönstret. Kontrollera kolumnordningen. Flytta kolumnen&quot;Ort&quot; uppåt under kolumnen&quot;Kontonummer&quot;.

   Avmarkera kolumnen Förnamn om du vill ta bort den från listan.

   ![](assets/query_editor_nveau_15.png)

1. I **[!UICONTROL Data preview]** fönster, klicka **[!UICONTROL Start the preview of the data]**. Den här funktionen beräknar resultatet av frågan.

   The **[!UICONTROL Column results]** -fliken visar frågeresultatet i kolumner.

   Resultatet visar alla mottagare med e-postdomänen&quot;orange.co.uk&quot; som inte bor i London. Kolumnen &quot;Förnamn&quot; visas inte eftersom den avmarkerades under föregående steg. Kontonummer sorteras i fallande ordning.

   ![](assets/query_editor_nveau_12.png)

   The **[!UICONTROL XML result]** -fliken visar resultatet i XML-format.

   ![](assets/query_editor_nveau_13.png)

   The **[!UICONTROL Generated QSL queries]** -fliken visar frågeresultatet i SQL-format.

   ![](assets/query_editor_nveau_14.png)
