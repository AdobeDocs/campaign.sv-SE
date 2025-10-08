---
title: Designfrågor i Campaign v8
description: Lär dig hur du skapar frågor
feature: Query Editor, Data Management
role: User
level: Beginner
version: Campaign v8, Campaign Classic v7
source-git-commit: adea4eb54f3d519802119646bc501aae2ef5f831
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 1%

---

# Query Campaign-databas

Frågor skapas med hjälp av fält i den valda tabellen eller med hjälp av en formel.

Så här skapar du en fråga i Adobe Campaign:

1. [Markera arbetstabellen](#step-1---choose-a-table).
1. [Markera de data som ska extraheras](#step-2---choose-data-to-extract).
1. [Definiera datarorteringsläget](#step-3---sort-data).
1. [Definiera datafiltreringsalternativ](#step-4---filter-data).
1. [Konfigurera dataformatering](#step-5---format-data).
1. [Förhandsgranska resultatet av frågan](#step-6---preview-data).

Alla dessa steg är tillgängliga i [den generiska frågeredigeraren](query-editor.md). När en fråga skapas i en annan kontext kan vissa steg saknas. Mer information om frågor finns i [dokumentationen för aktiviteten i arbetsflödet](../../automation/workflow/query.md).


## Steg 1 - Välj en tabell {#step-1---choose-a-table}

Om du vill fråga Campaign-databasen öppnar du den **[allmänna frågeredigeraren](query-editor.md)** och markerar tabellen som innehåller de data du vill fråga i fönstret **[!UICONTROL Document type]**.

![](assets/query_editor_nveau_21.png)

Om det behövs kan du filtrera data med filterfältet eller knappen **[!UICONTROL Filters]**.

## Steg 2 - Välj data att extrahera {#step-2---choose-data-to-extract}

På skärmen **[!UICONTROL Data to extract]** väljer du de fält som du vill inkludera i utdata. Dessa fält definierar de kolumner som visas i resultaten.

Du kan till exempel välja **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** och **[!UICONTROL City]**. Utdata kommer att struktureras enligt detta val. Om du vill justera kolumnernas inbördes ordning använder du de blå pilarna till höger i fönstret.

![](assets/query_editor_nveau_01.png)

Du kan ändra ett uttryck antingen genom att lägga till en formel eller genom att tillämpa en process på en mängdfunktion. Om du vill redigera ett uttryck klickar du på kolumnfältet **[!UICONTROL Expression]** och väljer sedan **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

Du kan gruppera de data som visas i utdatakolumnerna. Om du vill göra det väljer du **[!UICONTROL Yes]** i kolumnen **[!UICONTROL Group]** i fönstret **[!UICONTROL Data to extract]**. Resultatet sammanställs sedan baserat på den valda grupperingsaxeln. Ett exempel på en fråga som använder gruppering finns i [det här avsnittet](../../automation/workflow/query-delivery-info.md).

![](assets/query_editor_nveau_56.png)

* Med alternativet **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** kan du gruppera resultat och använda villkor för dessa grupper. Den gäller för alla fält i utdatakolumnerna. Du kan till exempel använda den för att gruppera värden från en utdatakolumn och sedan filtrera resultaten så att endast specifik information hämtas, till exempel mottagare mellan 35 och 50 år.

  Mer information om detta finns i [det här avsnittet](../../automation/workflow/query-grouping-management.md).

Alternativet **[!UICONTROL Remove duplicate rows (DISTINCT)]** tar bort identiska rader från utdata (deduplicera). Om du till exempel väljer **Efternamn**, **Förnamn** och **E-post** som utdatakolumner betraktas alla poster med samma värden i alla tre fälten som dubbletter. Endast en instans behålls i resultaten och varje kontakt visas bara en gång.

## Steg 3 - Sortera data {#step-3---sort-data}

I fönstret **[!UICONTROL Sorting]** kan du sortera kolumninnehåll. Använd pilarna för att ändra kolumnordningen:

* I kolumnen **[!UICONTROL Sorting]** kan du sortera och ordna kolumninnehåll från A till Z eller i stigande ordning.
* **[!UICONTROL Descending sort]** ordnar innehållet från Z till A och i fallande ordning. Det här är användbart för att visa postförsäljning, till exempel: de högsta siffrorna visas högst upp i listan.

I det här exemplet sorteras data i stigande ordning baserat på mottagarens ålder.

![](assets/query_editor_nveau_57.png)

## Steg 4 - Filtrera data {#step-4---filter-data}

Med frågeredigeraren kan du filtrera data för att begränsa resultaten. Vilka filter som är tillgängliga beror på tabellen du frågar.

![](assets/query_editor_nveau_09.png)

När du har valt **[!UICONTROL Filtering conditions]** öppnas avsnittet **[!UICONTROL Target elements]**. Här kan du definiera regler för filtrering av data som ska samlas in.

* Om du vill skapa ett nytt filter väljer du de fält, operatorer och värden som behövs för att skapa villkoret. Du kan också kombinera flera villkor, vilket förklaras [på den här sidan](filter-conditions.md).

* Om du vill återanvända ett befintligt filter klickar du på knappen **[!UICONTROL Add]**, markerar **[!UICONTROL Predefined filter]** och väljer det filter du vill använda.

  ![](assets/query_editor_15.png)

Filter som skapats i **[!UICONTROL Generic query editor]** kan återanvändas i andra frågeprogram, och det motsatta värdet är också sant. Om du vill spara ett filter för senare bruk klickar du på ikonen **[!UICONTROL Save]**.

>[!NOTE]
>
>Mer information om hur du skapar och använder filter finns i [Filtreringsalternativ](filter-conditions.md).

Om du vill återställa alla mottagare med engelskspråkighet, som visas i följande exempel, väljer du: &quot;mottagarspråk **lika med** EN&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>Du kan komma åt ett alternativ direkt genom att skriva följande formel i fältet **Värde**: **$(options:OPTION_NAME)**.

Klicka på fliken **[!UICONTROL Preview]** för att visa resultatet av filtreringsvillkoret. I det här fallet visas alla mottagare på engelska med namn, förnamn och e-postadress.

![](assets/query_editor_nveau_98.png)

Användare som är bekanta med SQL-språk kan klicka på **[!UICONTROL Generate SQL query]** för att visa frågan i SQL.

![](assets/query_editor_nveau_99.png)

## Steg 5 - Formatera data {#step-5---format-data}

När begränsningsfiltren har konfigurerats öppnas fönstret **[!UICONTROL Data formatting]**. I det här fönstret kan du ändra ordning på utdatakolumner, omforma data och justera kolumnetikettens skiftläge. Du kan också tillämpa formler på det slutliga resultatet genom att skapa ett beräkningsfält.

>[!NOTE]
>
>Mer information om typerna av beräkningsfält finns i [Skapa beräknade fält](filter-conditions.md#creating-calculated-fields).

Omarkerade kolumner är dolda i förhandsgranskningsfönstret för data.

![](assets/query_editor_nveau_10.png)

I kolumnen **[!UICONTROL Transformation]** kan du ändra en kolumnetikett till versaler eller gemener. Markera kolumnen och klicka i kolumnen **[!UICONTROL Transformation]**. Du kan välja:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Steg 6 - Förhandsgranska data {#step-6---preview-data}

Fönstret **[!UICONTROL Data preview]** anger det sista steget i frågeprocessen. Klicka på **[!UICONTROL Start the preview of the data]** om du vill granska resultatet, som kan visas i kolumner eller XML-format. Öppna fliken **[!UICONTROL Generated SQL queries]** om du vill undersöka den underliggande SQL-frågan. I det här steget kan du verifiera att frågan beter sig som förväntat innan du använder den vidare.

I det här exemplet sorteras data i stigande ordning baserat på mottagarens ålder.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Som för alla listor som är tillgängliga i konsolen visas som standard endast de första 200 raderna i fönstret **[!UICONTROL Data preview]**. Om du vill ändra det här anger du ett nummer i rutan **[!UICONTROL Lines to display]** och klickar på **[!UICONTROL Start the preview of the data]**. [Läs mer](../config/ui-settings.md#manage-and-customize-lists)



**Relaterade ämnen**

* [Aktivitet för arbetsflödesfråga](../../automation/workflow/query.md)
* [Fråga mottagartabellen](../../automation/workflow/querying-recipient-table.md)
* [Filtreringsvillkor](filter-conditions.md)