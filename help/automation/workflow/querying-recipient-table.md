---
product: campaign
title: Fråga mottagartabellen
description: Lär dig ställa frågor i mottagartabellen
feature: Query Editor
role: User, Developer
version: Campaign v8, Campaign Classic v7
exl-id: 7f859ce9-7ab8-46e1-8bd6-43aaffe30da2
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 3%

---

# Fråga mottagartabellen {#querying-recipient-table}



I det här exemplet vill vi återskapa namn och e-post för mottagare vars e-postdomän är orange.co.uk och som inte bor i London.

* Vilken tabell ska vi välja?

  Mottagartabellen (nms:recipient)

* Fält som ska markeras som utdatakolumner

  E-post, namn, ort och kontonummer

* Vilka filtervillkor har mottagarna?

  stad- och e-postdomän

* Är en sortering konfigurerad?

  Ja, baserat på **[!UICONTROL Account number]** och **[!UICONTROL Last name]**

Så här skapar du det här exemplet:

1. Klicka på **[!UICONTROL Tools > Generic query editor...]** och välj tabellen **Mottagare** (**nms:recipient**). Klicka sedan på **[!UICONTROL Next]**.
1. Välj: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** och **[!UICONTROL Account number]**. Dessa fält läggs till i **[!UICONTROL Output columns]**. Klicka sedan på **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Sortera kolumnerna så att de visas i rätt ordning. Här vill vi sortera kontonummer i fallande ordning och namn i alfabetisk ordning. Klicka sedan på **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. Förfina sökningen i fönstret **[!UICONTROL Data filtering]**: välj **[!UICONTROL Filtering conditions]** och klicka på **[!UICONTROL Next]**.
1. I fönstret **[!UICONTROL Target element]** kan du ange filterinställningar.

   Definiera följande filtervillkor: mottagare med en e-postdomän som är lika med &quot;orange.co.uk&quot;. Om du vill göra det väljer du **E-postdomän (@email)** i kolumnen **[!UICONTROL Expression]**, väljer **lika med** i kolumnen **[!UICONTROL Operator]** och anger &quot;orange.co.uk&quot; i kolumnen **[!UICONTROL Value]**.

   ![](assets/query_editor_05.png)

1. Om det behövs klickar du på knappen **[!UICONTROL Distribution of values]** för att visa en distribution baserat på e-postdomänen för potentiella kunder. Det finns en procentandel tillgänglig för varje e-postdomän i databasen. Andra domäner än &quot;orange.co.uk&quot; visas tills filtret tillämpas.

   En sammanfattning av frågan visas längst ned i fönstret: **E-postdomänen är lika med orange.co.uk**.

1. Klicka på **[!UICONTROL Preview]** för att få en uppfattning om frågeresultatet: endast&quot;orange.co.uk&quot; e-postdomäner visas.

   ![](assets/query_editor_nveau_17.png)

1. Vi ändrar nu frågan för att hitta kontakter som inte bor i London.

   Markera **[!UICONTROL City (location/@city)]** i kolumnen **[!UICONTROL Expression]**, **[!UICONTROL different from]** som en operator och ange **[!UICONTROL London]** i kolumnen **[!UICONTROL Value]**.

   ![](assets/query_editor_08.png)

1. Du kommer nu till fönstret **[!UICONTROL Data formatting]**. Kontrollera kolumnordningen. Flytta kolumnen&quot;Ort&quot; uppåt under kolumnen&quot;Kontonummer&quot;.

   Avmarkera kolumnen Förnamn om du vill ta bort den från listan.

   ![](assets/query_editor_nveau_15.png)

1. Klicka på **[!UICONTROL Data preview]** i fönstret **[!UICONTROL Start the preview of the data]**. Den här funktionen beräknar resultatet av frågan.

   Fliken **[!UICONTROL Column results]** visar frågeresultatet i kolumner.

   Resultatet visar alla mottagare med e-postdomänen&quot;orange.co.uk&quot; som inte bor i London. Kolumnen &quot;Förnamn&quot; visas inte eftersom den avmarkerades under föregående steg. Kontonummer sorteras i fallande ordning.

   ![](assets/query_editor_nveau_12.png)

   Fliken **[!UICONTROL XML result]** visar resultatet i XML-format.

   ![](assets/query_editor_nveau_13.png)

   Fliken **[!UICONTROL Generated SQL queries]** visar frågeresultatet i SQL-format.

   ![](assets/query_editor_nveau_14.png)
