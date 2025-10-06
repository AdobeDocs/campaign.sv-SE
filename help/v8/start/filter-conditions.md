---
title: Designfrågor i Campaign v8
description: Lär dig hur du skapar frågor
feature: Query Editor
role: User
level: Beginner
version: Campaign v8, Campaign Classic v7
source-git-commit: 95c944963feee746a2bb83a85f075134c91059d1
workflow-type: tm+mt
source-wordcount: '3323'
ht-degree: 33%

---


# Definiera filtervillkor{#filter-conditions}

Om du vill utforma frågan måste du välja filtervillkoren i frågeredigeraren. Tillgängliga funktioner och användningsexempel finns på den här sidan.

## Välj operator {#choose-operator}

Inom filtervillkoren måste du länka samman två värden med hjälp av en operator.

![](assets/query_editor_nveau_96.png)

Nedan finns en lista över tillgängliga operatorer:

<table> 
 <thead> 
  <tr> 
   <th> Operatör<br /> </th> 
   <th> Syfte<br /> </th> 
   <th> Exempel<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Equal to</span> <br /> </td> 
   <td> Returnerar ett resultat som är identiskt med de data som anges i den andra värdekolumnen.<br /> </td> 
   <td> <strong>Efternamnet (@lastName) är lika med 'Jones'</strong>, returnerar bara mottagare vars efternamn är Jones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Greater than</span> <br /> </td> 
   <td> Returnerar ett värde som är större än det angivna värdet.<br /> </td> 
   <td> <strong>Ålder (@age) större än 50</strong>, returnerar alla värden större än 50, dvs. 51, 52 osv.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Less than</span> <br /> </td> 
   <td> Returnerar ett värde som är mindre än det angivna värdet.<br /> </td> 
   <td> <strong>Skapad (@created) före 'DaysAgo(100)'</strong>, returnerar alla mottagare som skapats för mindre än 100 dagar sedan.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Greater than or equal to</span> <br /> </td> 
   <td> Returnerar alla värden som är lika med eller större än det angivna värdet.<br /> </td> 
   <td> <strong>Ålder (@age) som är större än eller lika med 30</strong> returnerar alla mottagare som är 30 år eller äldre.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Less than or equal to</span> <br /> </td> 
   <td> Returnerar alla värden som är lika med eller lägre än det angivna värdet.<br /> </td> 
   <td> <strong>Ålder (@age) mindre än eller lika med '60'</strong>, returnerar alla mottagare som är 60 år eller yngre.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Inte lika med</span> <br /> </td> 
   <td> Returnerar alla värden som inte är identiska med det angivna värdet.<br /> </td> 
   <td> <strong>Språket (@language) är lika med "English"</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Börjar med</span> <br /> </td> 
   <td> Returnerar resultatet med början på det angivna värdet.<br /> </td> 
   <td> <strong>Kontonr (@account) börjar med 32010.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Börjar inte med </span> <br /> </td> 
   <td> Returnerar resultat som inte börjar med det angivna värdet <br /> </td> 
   <td> <strong>Kontonumret (@account) börjar inte med </strong><br />. </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Contains</span> <br /> </td> 
   <td> Returnerar resultaten som innehåller minst det angivna värdet.<br /> </td> 
   <td> <strong>E-postdomänen (@domain) innehåller mail</strong>, returnerar alla domännamn som innehåller mail. Domänen gmail.com returneras alltså också.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Innehåller inte </span> <br /> </td> 
   <td> Returnerar resultat som inte innehåller det angivna värdet.<br /> </td> 
   <td> <strong>E-postdomänen (@domain) innehåller inte 'vo'</strong>. I det här fallet returneras inte domännamn som innehåller "vo". Domännamnet voila.fr visas inte i resultatet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Like</span> <br /> </td> 
   <td> <span class="uicontrol">Like</span> är mycket lik operatören <span class="uicontrol">Contains</span>. Du kan infoga ett <span class="uicontrol">%</span> jokertecken i värdet.<br /> </td> 
   <td> <strong>Efternamn (@lastName) som Jon%s</strong>. Här används jokertecknet som joker för att hitta namnet Jones om operatorn hade glömt den saknade bokstaven mellan n och s.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Not like</span> <br /> </td> 
   <td> liknar <span class="uicontrol">Gilla</span> . Du kan inte återställa det angivna värdet. Även här måste det angivna värdet innehålla jokertecknet <span class="uicontrol">%</span>.<br /> </td> 
   <td> <strong>Efternamnet (@lastName) är inte som Smi%h</strong>. Här returneras inte mottagare vars efternamn är Smi%h.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is empty</span> <br /> </td> 
   <td> I det här fallet matchar resultatet vi söker efter ett tomt värde i den andra värdekolumnen.<br /> </td> 
   <td> <strong>Mobilen (@mobilePhone) är tom</strong> returnerar alla mottagare som inte har något mobilnummer.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Är inte tom</span> <br /> </td> 
   <td> Fungerar i motsatt riktning till operatorn <span class="uicontrol">Är tom</span>. Du behöver inte ange data i den andra värdekolumnen.<br /> </td> 
   <td> <strong>E-post (@email) är inte tom</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ingår i </span> <br /> </td> 
   <td> Returnerar resultat som ingår i de angivna värdena. Dessa värden måste avgränsas med kommatecken.<br /> </td> 
   <td> <strong>Födelsedatum (@bornDate) ingår i </strong> (12/10/1979, 12/10/1984), returnerar de mottagare som är födda mellan dessa datum. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ingår inte i </span> <br /> </td> 
   <td> Fungerar som operatorn <span class="uicontrol">Ingår i</span>. Här vill vi exkludera mottagare baserat på de angivna värdena.<br /> </td> 
   <td> <strong>Födelsedatum (@BirthDate) ingår inte i </strong> (12/10/1979, 12/10/1984). Till skillnad från i föregående exempel returneras inte mottagare som fötts inom dessa datum.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## ANVÄND OCH, ELLER, UTOM {#using-and--or--except}

För frågor som använder flera filtervillkor måste du definiera länkar mellan villkoren. Det finns tre möjliga länkar:

* **[!UICONTROL And]** låter dig kombinera två filtreringsvillkor,
* **[!UICONTROL Or]** låter dig erbjuda ett alternativ,
* Med **[!UICONTROL Except]** kan du definiera ett undantag.

Klicka på **[!UICONTROL And]** (erbjuds som standard) och välj i listrutan.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**: lägger till ett villkor och aktiverar överfiltrering.
* **[!UICONTROL Or]**: lägger till ett villkor och aktiverar överfiltrering.

  I följande exempel kan du söka efter mottagare vars e-postdomän innehåller &quot;orange.co.uk&quot; ELLER vars postkod börjar med &quot;NW&quot;.

  ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**: Om du har två filter och den första inte returnerar något värde, skapar den här typen av länk ett undantag.

  I följande exempel vill vi returnera mottagare vars e-postdomän innehåller &quot;orange.co.uk&quot; EXCEPT om mottagarens efternamn är &quot;Smith&quot;.

  ![](assets/query_condition_modif_03.png)

I det här exemplet visas ett filter som gör att du kan visa: mottagare som antingen talar spanska, ELLER är kvinnor med mobilnummer, ELLER mottagare utan kontonummer och vars företagsnamn börjar med bokstaven&quot;N&quot;.

![](assets/query_editor_nveau_31.png)

## Prioritera villkor {#prioritizing-conditions}

I det här avsnittet beskrivs hur du prioriterar villkor tack vare de blå pilarna i verktygsfältet.

* Med pilen till höger kan du lägga till en nivå med parenteser i filtret.
* Med pilen som pekar åt vänster kan du ta bort en vald parentesnivå från filtret.

  ![](assets/query_condition_modif_04.png)

* Med de lodräta pilarna kan du flytta ett villkor och på så sätt ändra deras körningssekvens.

I det här exemplet visas hur du använder pilen för att ta bort en parentesnivå. Starta från följande filtreringsvillkor: **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

Placera markören på filtervillkoret **[!UICONTROL Gender (@gender) equal to Male]** och klicka på pilen **[!UICONTROL Remove a parenthesis level]**.

![](assets/query_editor_nveau_32.png)

Villkoret **[!UICONTROL Gender (@gender) equal to Male]** har tagits bort ur parentesen. Den har flyttat till samma nivå som villkoret&quot;City equal to London&quot;. De här villkoren är sammankopplade (**[!UICONTROL And]**).

## Välj data som ska extraheras {#selecting-data-to-extract}

De tillgängliga fälten varierar mellan olika tabeller. Alla fält lagras i en huvudnod som kallas **[!UICONTROL Main element]**. I följande exempel finns de tillgängliga fälten i mottagartabellen. Fält visas alltid i bokstavsordning.

Det markerade fältets detaljrikedom visas längst ned i fönstret. Fältet **[!UICONTROL Email domain]** är till exempel ett **[!UICONTROL Calculated SQL field]** och dess tillägg är **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Använd verktyget **[!UICONTROL Search]** för att hitta ett tillgängligt fält.

Dubbelklicka på ett tillgängligt fält för att lägga till det i utdatakolumnerna. I slutet av frågan skapar varje markerat fält en kolumn i fönstret **[!UICONTROL Data preview]**.

![](assets/query_editor_nveau_01.png)

Avancerade fält visas inte som standard. Klicka på **[!UICONTROL Display advanced fields]** längst ned till höger i de tillgängliga fälten för att visa allt. Klicka en gång till för att återgå till den tidigare vyn.

I mottagartabellen är de avancerade fälten till exempel **Boolean 1**, **[!UICONTROL Boolean 2]**, **[!UICONTROL Boolean 3]**, **[!UICONTROL Foreign key of "Folder" link]**.

I följande exempel visas de avancerade fälten i mottagartabellen.

![](assets/query_editor_nveau_53.png)

De olika kategorierna av fält:

<table> 
 <thead> 
  <tr> 
   <th> Ikon<br /> </th> 
   <th> Beskrivning<br /> </th> 
   <th> Exempel <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> Enkelt fält <br /> </td> 
   <td> E-post, kön osv.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> Primärnyckel. Det här SQL-fältet är ett sätt att identifiera en post i en tabell.<br /> </td> 
   <td> Identifierarmottagare är primära nycklar och identifierare är unika per definition.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Sekundärnyckel. Används som en länk till en annan tabell.<br /> </td> 
   <td> Mottagarens sekundärnyckel, tjänstens externa nyckel osv.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Beräknat fält. Den här typen av fält beräknas på begäran med värdena i databasen.<br /> </td> 
   <td> Ålder, e-postdomän osv.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> Fält som innehåller långa texter.<br /> </td> 
   <td> Kommentar, fullständig adress osv.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> Indexerat SQL-fält. <br /> </td> 
   <td> Fullständigt namn, ISO-kod osv. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Länka till en tabell och ett samlingselement:

<table> 
 <thead> 
  <tr> 
   <th> Ikon<br /> </th> 
   <th> Beskrivning<br /> </th> 
   <th> Exempel<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> Länkar till en tabell i synnerhet. Dessa sammanfaller med 1-1-typassociationer. En förekomst av källtabellen kan bara sammanfalla med en förekomst av måltabellen. Till exempel kan bara en mottagare länkas till ett land.<br /> </td> 
   <td> Mapp, delstat, land osv. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Samlingselement i en viss tabell. Dessa sammanfaller med 1-N-typassociationer. En källtabellförekomst kan sammanfalla med flera förekomster av måltabellen, men en förekomst av måltabellen kan sammanfalla med endast en förekomst av källtabellen. En mottagare kan till exempel prenumerera på 'n'-prenumerationsbrev.<br /> </td> 
   <td> Prenumerationer, listor, undantagsloggar osv.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Använd knappen **[!UICONTROL Add]** (ovanför sidikonfältet) för att lägga till en utdatakolumn där vi vill redigera uttrycket. Mer information om hur du redigerar ett uttryck finns i [det här avsnittet](#building-expressions).
>* Ta bort en utdatakolumn genom att klicka på den röda x (**Ta bort**).
>* Ändra ordningen på utdatakolumnerna med hjälp av pilarna.
>* **[!UICONTROL Distribution of values]** fungerar som ett sätt att visa fördelningen av värdena för det valda fältet (t.ex. distributioner som är kopplade till mottagarorter, mottagarspråk osv.).

## Skapa beräknade fält {#creating-calculated-fields}

Om det behövs lägger du till en kolumn under dataformatering. Ett beräkningsfält lägger till en kolumn i dataförhandsvisningsavsnittet. Klicka på **[!UICONTROL Add a calculated field]**.

![](assets/query_editor_nveau_43.png)

Det finns fyra typer av beräknade fält:

* **[!UICONTROL Fixed string]**: gör att du kan lägga till en teckensträng.

  ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**: Värdet för beräkningsfältet kombinerar en teckensträng och JavaScript-direktiv.

  ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**: Värdet för beräkningsfältet är resultatet av en JavaScript-funktionsutvärdering. Det returnerade värdet kan skrivas in (tal, datum osv.).

  ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**: Med den här typen av fält kan du använda/ändra innehållet i en av utdatakolumnerna i en ny kolumn.

  Det går att använda källvärdet för en kolumn och ge den ett målvärde. Det här målvärdet visas i den nya utdatakolumnen.

  Ett exempel på hur du lägger till den beräknade fälttypen **[!UICONTROL Enumerations]** finns i [det här avsnittet](../../workflow/using/adding-enumeration-type-calculated-field.md).

  ![](assets/query_editor_nveau_63.png)

  Beräkningsfältet av typen **[!UICONTROL Enumerations]** kan innehålla fyra villkor:

   * **[!UICONTROL Keep the source value]** återställer källvärdet till målet utan att ändra det.
   * Med **[!UICONTROL Use the following value]** kan du ange ett standardmålvärde för icke-definierade källvärden.
   * **[!UICONTROL Generate a warning and continue]** varnar användaren om att källvärdet inte kan ändras.
   * **[!UICONTROL Generate an error and reject the line]** förhindrar att raden beräknas och importeras.

Klicka på **[!UICONTROL Detail of calculated field]** om du vill visa detaljerna för det infogade fältet.

Klicka på krysset **[!UICONTROL Remove the calculated field]** om du vill ta bort det här beräknade fältet.

![](assets/query_editor_nveau_58.png)

## Skapa uttryck {#building-expressions}

Med uttrycksredigeringsverktyget kan du beräkna aggregeringar, generera funktioner eller redigera en formel med hjälp av ett uttryck.

I följande exempel visas hur du kör ett antal på en primärnyckel.

Använd följande steg:

1. Klicka på **[!UICONTROL Add]** i fönstret **[!UICONTROL Data to extract]**. I fönstret **[!UICONTROL Formula type]** väljer du en typ av formel att ange uttrycket för.

   Det finns flera typer av formler: **[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**.

   Välj **[!UICONTROL Process on an aggregate function]** och **[!UICONTROL Count]**. Klicka på **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_54.png)

1. Primärnyckeln beräknas.

   ![](assets/query_editor_nveau_88.png)

Här är en detaljerad vy över de alternativ som är tillgängliga i fönstret **[!UICONTROL Formula types]**:

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** låter dig återgå till fönstret **[!UICONTROL Field to select]**.
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. Här är några exempel på användning av ballast:

   * Med **[!UICONTROL Count]** kan du köra ett primärnyckelantal.
   * Med **[!UICONTROL Sum]** kan du lägga till alla inköp som gjorts av en kund under ett år.
   * Med **[!UICONTROL Maximum value]** kan du hitta de kunder som har köpt de mest&quot;n&quot;-produkterna.
   * Med **[!UICONTROL Minimum value]** kan du sortera bland kunder och hitta de som senast har prenumererat på ett erbjudande.
   * **[!UICONTROL Average]**. Med den här funktionen kan du beräkna medelåldern för mottagarna.

     I rutan **[!UICONTROL Distinct]** kan du återställa unika värden och värden som inte är noll i en kolumn. Du kan till exempel återställa alla en mottagares spårningsloggar och dessa spårningsloggar ändras till värdet 1 eftersom alla gäller samma mottagare.

1. **[!UICONTROL Expression]** öppnar fönstret **[!UICONTROL Edit the expression]**. Detta gör att du kan identifiera telefonnummer med för många siffror, vilket sannolikt är indatafel.

   ![](assets/query_editor_nveau_71.png)

   En lista över alla tillgängliga funktioner finns i [Lista över funktioner](#list-of-functions).

## Lista över funktioner {#list-of-functions}

Om du väljer en **[!UICONTROL Expression]**-typformel kommer du till fönstret&quot;redigera uttrycket&quot;. Olika funktionskategorier kan kopplas till de tillgängliga fälten: **[!UICONTROL Aggregates]**, **[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Windowing function]** och **[!UICONTROL Others]**.

Uttrycksredigeraren ser ut så här:

![](assets/s_ncs_user_filter_define_expression.png)

Här kan du markera fält i databastabellerna och lägga till avancerade funktioner. Följande funktioner är tillgängliga:

**Aggregat**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Medel</strong><br /> </td> 
   <td> Returnerar medelvärdet för en taltypskolumn <br /> </td> 
   <td> Avg(&lt;värde&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Antal</strong><br /> </td> 
   <td> Räknar värden som inte är null i en kolumn <br /> </td> 
   <td> Count(&lt;värde&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Räknar returnerade värden (alla fält)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Motskild</strong><br /> </td> 
   <td> Räknar distinkta icke-null-värden för en kolumn <br /> </td> 
   <td> Countdistans(&lt;värde&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Returnerar det maximala värdet för en tal-, sträng- eller datumtypskolumn <br /> </td> 
   <td> Max(&lt;värde&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Returnerar det minsta värdet för en tal-, sträng- eller datumtypskolumn <br /> </td> 
   <td> Min(&lt;värde&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Returnerar standardavvikelsen för ett tal, en sträng eller en datumkolumn <br /> </td> 
   <td> StdDev(&lt;värde&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Summa</strong><br /> </td> 
   <td> Returnerar summan av värdena för en tal-, sträng- eller datumtypskolumn <br /> </td> 
   <td> Sum(&lt;värde&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**Sträng**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> Anger om alla parametrar inte är null och inte tomma<br /> </td> 
   <td> AllNonNull2(&lt;sträng&gt;, &lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> Anger om alla parametrar inte är null och inte tomma<br /> </td> 
   <td> AllNonNull3(&lt;sträng&gt;, &lt;sträng&gt;, &lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> Returnerar ASCII-värdet för det första tecknet i strängen.<br /> </td> 
   <td> Ascii(&lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> Returnerar tecknet som motsvarar ASCII-koden "n"<br /> </td> 
   <td> Char(&lt;tal&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Returnerar positionen för sträng 2 i sträng 1.<br /> </td> 
   <td> Charindex(&lt;sträng&gt;, &lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Returnerar den n:e raden (från 1 till n) i strängen<br /> </td> 
   <td> GetLine(&lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Returnerar den tredje parametern om de två första parametrarna är lika. Om inte returneras den sista parametern <br /> </td> 
   <td> IfEquals(&lt;sträng&gt;, &lt;sträng&gt;, &lt;sträng&gt;, &lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Anger om PM:et som skickas som en parameter är null<br /> </td> 
   <td> IsMemoNull(&lt;PM&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> Sammanfogar de strängar som skickas som parametrar. Lägger till blanksteg mellan strängarna om det behövs.<br /> </td> 
   <td> JuxtWords(&lt;sträng&gt;, &lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> Sammanfogar de strängar som skickas som parametrar. Lägger till blanksteg mellan strängarna om det behövs <br /> </td> 
   <td> JuxtWords3(&lt;sträng&gt;, &lt;sträng&gt;, &lt;sträng&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> Returnerar den slutförda strängen till vänster<br /> </td> 
   <td> LPad(&lt;sträng&gt;, &lt;tal&gt;, &lt;tecken&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> Returnerar de första n tecknen i strängen<br /> </td> 
   <td> Left(&lt;sträng&gt;, &lt;tal&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> Returnerar längden på strängen <br /> </td> 
   <td> Length(&lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> Returnerar strängen i gemener<br /> </td> 
   <td> Lower(&lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Tar bort blanksteg till vänster om strängen<br /> </td> 
   <td> Ltrim(&lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Returnerar en hexadecimal representation av MD5-nyckeln för en sträng<br /> </td> 
   <td> Md5Digest(&lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>PMContains</strong><br /> </td> 
   <td> Anger om PM:et innehåller den sträng som skickas som en parameter<br /> </td> 
   <td> MemoContains(&lt;PM&gt;, &lt;sträng&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Returnerar den slutförda strängen till höger<br /> </td> 
   <td> RPad(&lt;sträng&gt;, &lt;tal&gt;, &lt;tecken&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> Returnerar de sista n tecknen i strängen<br /> </td> 
   <td> Right(&lt;sträng&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Tar bort blanksteg till höger om strängen<br /> </td> 
   <td> Rtrim(&lt;sträng&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> Returnerar strängen med den första bokstaven i varje ord med versaler<br /> </td> 
   <td> Smart(&lt;sträng&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> Extraherar delsträngen från tecken n1 i strängen och med längden n2<br /> </td> 
   <td> Substring(&lt;sträng&gt;, &lt;offset&gt;, &lt;längd&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Konverterar talet till en sträng<br /> </td> 
   <td> ToString(&lt;tal&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> Returnerar strängen med versaler<br /> </td> 
   <td> Upper(&lt;sträng&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Returnerar sekundärnyckeln för en länk som skickas som en parameter om de andra två parametrarna är lika<br /> </td> 
   <td> VirtualLink(&lt;tal&gt;, &lt;tal&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Returnerar sekundärnyckeln (text) för en länk som skickas som en parameter om de andra två parametrarna är lika<br /> </td> 
   <td> VirtualLinkStr(&lt;sträng&gt;, &lt;tal&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Returnerar strängstorleken <br /> </td> 
   <td> dataLength(&lt;sträng&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Datum**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> Lägger till ett antal dagar till ett datum<br /> </td> 
   <td> AddDays(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Lägger till ett antal timmar till ett datum<br /> </td> 
   <td> AddHours(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Lägger till ett antal minuter till ett datum<br /> </td> 
   <td> AddMinutes(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Lägger till ett antal månader till ett datum<br /> </td> 
   <td> AddMonths(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Lägger till ett antal sekunder till ett datum<br /> </td> 
   <td> AddSeconds(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> Lägger till ett antal år till ett datum<br /> </td> 
   <td> AddYears(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Returnerar endast datumet (med tiden 00:00)*<br /> </td> 
   <td> DateOnly(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> Returnerar talet som representerar dagen på datumet<br /> </td> 
   <td> Day(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Returnerar antalet dagar i året för datumet <br /> </td> 
   <td> DayOfYear(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Returnerar det datum som motsvarar aktuellt datum minus n dagar <br /> </td> 
   <td> DaysAgo(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Returnerar det datum (heltal åååmmdd) som motsvarar det aktuella datumet minus n dagar <br /> </td> 
   <td> DaysAgoInt(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Antal dagar mellan två datum<br /> </td> 
   <td> DaysDiff(&lt;slutdatum&gt;, &lt;startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Returnerar åldern i dagar för ett datum<br /> </td> 
   <td> DaysOld(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Returnerar serverns aktuella systemdatum<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> Returnerar timmen för datumet<br /> </td> 
   <td> Hour(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Returnerar antalet timmar mellan två datum<br /> </td> 
   <td> HoursDiff(&lt;slutdatum&gt;, &lt;startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> Returnerar minuterna av datumet<br /> </td> 
   <td> Minute(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Returnerar antalet minuter mellan två datum<br /> </td> 
   <td> MinutesDiff(&lt;slutdatum&gt;, &lt;startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> Returnerar talet som representerar månaden för datumet<br /> </td> 
   <td> Month(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Returnerar det datum som motsvarar aktuellt datum minus n månader<br /> </td> 
   <td> MonthsAgo(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Returnerar antalet månader mellan två datum<br /> </td> 
   <td> MonthsDiff(&lt;slutdatum&gt;, &lt;startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Returnerar åldern i månader för ett datum<br /> </td> 
   <td> MonthsOld(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> Returnerar sekunder för datumet<br /> </td> 
   <td> Second(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Returnerar antalet sekunder mellan två datum<br /> </td> 
   <td> SecondsDiff(&lt;slutdatum&gt;, &lt;startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> Subtraherar ett antal dagar från ett datum<br /> </td> 
   <td> SubDays(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Subtraherar ett antal timmar från ett datum<br /> </td> 
   <td> SubHours(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Subtraherar ett antal minuter från ett datum<br /> </td> 
   <td> SubMinutes(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> Subtraherar ett antal månader från ett datum<br /> </td> 
   <td> SubMonths(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Subtraherar ett antal sekunder från ett datum<br /> </td> 
   <td> SubSeconds(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> Subtraherar ett antal år från ett datum<br /> </td> 
   <td> SubYears(&lt;datum&gt;, &lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Konverterar ett datum + tid som ett datum<br /> </td> 
   <td> ToDate(&lt;datum + tid&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Konverterar en sträng till ett datum + tid<br /> </td> 
   <td> ToDateTime(&lt;sträng&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Avrundar ett datum + tid till närmaste sekund<br /> </td> 
   <td> TruncDate(@lastModified, &lt;antal sekunder&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Avrundar ett datum + tid till en viss precision, uttryckt i sekunder<br /> </td> 
   <td> TruncDateTZ(&lt;datum&gt;, &lt;antal sekunder&gt;, &lt;tidszon&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Avrundar ett datum till kvartal<br /> </td> 
   <td> TruncQuarter(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Avrundar tidsdelen upp till närmaste sekund<br /> </td> 
   <td> TruncTim(e&lt;datum&gt;, &lt;antal sekunder&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Avrundar ett datum till veckan<br /> </td> 
   <td> TruncWeek(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Avrundar ett datum + tid till 1 januari under året<br /> </td> 
   <td> TruncYear(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Returnerar talet som representerar dagen i veckan på datumet<br /> </td> 
   <td> WeekDay(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> Returnerar talet som representerar datumåret<br /> </td> 
   <td> Year(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> Returnerar talet som representerar året och månaden på datumet<br /> </td> 
   <td> YearAndMonth(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> Returnerar antalet år mellan de två datumen<br /> </td> 
   <td> YearsDiff(&lt;slutdatum&gt;, &lt;startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> Returnerar åldern i år för ett datum<br /> </td> 
   <td> YearsOld(&lt;datum&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Observera att funktionen **Dateonly** tar hänsyn till serverns tidszon, inte till operatorns.

**Numeriskt**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> Returnerar det absoluta värdet av ett tal<br /> </td> 
   <td> Abs(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Returnerar det lägsta heltalet som är större än eller lika med ett tal<br /> </td> 
   <td> Ceil(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Returnerar det största heltalet större än eller lika med ett tal <br /> </td> 
   <td> Floor(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> Returnerar det största av två tal<br /> </td> 
   <td> Greatest(&lt;tal 1&gt;, &lt;tal 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> Returnerar det minsta av två tal<br /> </td> 
   <td> Minst(&lt;tal 1&gt;, &lt;tal 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Returnerar resten av heltalsdivisionen av n1 med n2<br /> </td> 
   <td> Mod(&lt;tal 1&gt;, &lt;tal 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Procent</strong><br /> </td> 
   <td> Returnerar förhållandet mellan två tal uttryckta i procent<br /> </td> 
   <td> Procent(&lt;tal 1&gt;, &lt;tal 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> Returnerar det slumpmässiga värdet<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> Avrundar ett tal till n decimaler<br /> </td> 
   <td> Round(&lt;tal&gt;, &lt;antal decimaler&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> Returnerar talets tecken<br /> </td> 
   <td> Sign(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Konverterar ett heltal till ett flyttal<br /> </td> 
   <td> ToDouble(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Konverterar ett flyttal till ett 64-bitars heltal<br /> </td> 
   <td> ToInt64(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Konverterar ett flyttal till ett heltal<br /> </td> 
   <td> ToInteger(&lt;tal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Trunkerar n1 till n2 decimaler<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. Valuta

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> Konverterar ett belopp i en källvaluta till ett belopp i målvalutan <br /> </td> 
   <td> ConvertCurrency(&lt;belopp&gt;, &lt;källvaluta&gt;, &lt;målvaluta&gt;, &lt;konverteringsdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> Formaterar det belopp som visas baserat på de valda valutainställningarna <br /> </td> 
   <td> FormatCurrency(&lt;belopp&gt;, &lt;valuta&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Geomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Avstånd</strong><br /> </td> 
   <td> Returnerar avståndet mellan två punkter som definieras av deras longitud och latitud, uttryckt i grader.<br /> </td> 
   <td> Distance(&lt;longitud A&gt;, &lt;latitud A&gt;, &lt;longitud B&gt;, &lt;latitud B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Övriga**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Returnerar värdet 1 om villkoret är sant. Annars returneras värdet 2.<br /> </td> 
   <td> Case(When(&lt;villkor&gt;, &lt;värde 1&gt;), Else(&lt;värde 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Tar bort flaggan i värdet<br /> </td> 
   <td> ClearBit(&lt;identifierare&gt;, &lt;flagga&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Returnerar värde 2 om värde 1 är noll eller null, annars returneras värde 1<br /> </td> 
   <td> Coalesce(&lt;värde 1&gt;, &lt;värde 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Returnerar värde 3 om värde 1 = värde 2. Om inte returnerar värde 4.<br /> </td> 
   <td> Decode(&lt;värde 1&gt;, &lt;värde 2&gt;, &lt;värde 3&gt;, &lt;värde 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Returnerar värde 1 (kan endast användas som en parameter för case-funktionen)<br /> </td> 
   <td> Else(&lt;värde 1&gt;, &lt;värde 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Extraherar domänen från en e-postadress<br /> </td> 
   <td> GetEmailDomain(&lt;värde&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Hämtar URL:en för spegelsidservern<br /> </td> 
   <td> GetMirrorURL(&lt;värde&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Returnerar värdet 1 om uttrycket är true. Om inte returneras värdet 2<br /> </td> 
   <td> Iif(&lt;villkor&gt;, &lt;värde 1&gt;, &lt;värde 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Anger om flaggan är i värdet<br /> </td> 
   <td> IsBitSet(&lt;identifierare&gt;, &lt;flagga&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Returnerar värdet 2 om strängen 1 är tom, annars returneras värdet 3<br /> </td> 
   <td> IsEmptyString(&lt;värde 1&gt;, &lt;värde 2&gt;, &lt;värde 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Returnerar den tomma strängen om argumentet är NULL<br /> </td> 
   <td> NoNull(&lt;värde&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Returnerar radnumret<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Tvingar flaggan i värdet<br /> </td> 
   <td> SetBit(&lt;identifierare&gt;, &lt;flagga&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Konverterar ett tal till ett booleskt värde<br /> </td> 
   <td> ToBoolean(&lt;tal&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> Returnerar värdet 1 om uttrycket är true. Annars returnerar den värde 2 (kan bara användas som en parameter för fallfunktionen)<br /> </td> 
   <td> When(&lt;tillstånd&gt;, &lt;värde 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Fönsterfunktioner**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> Tillämpar en fallande sortering<br /> </td> 
   <td> Desc(&lt;värde 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Sorterar resultatet i partitionen<br /> </td> 
   <td> OrderBy(&lt;värde 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Partitionerar resultatet av en fråga i en tabell<br /> </td> 
   <td> PartitionBy(&lt;värde 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Genererar ett radnummer baserat på tabellpartitionen och en sorteringssekvens.<br /> </td> 
   <td> RowNum(PartitionBy(&lt;värde 1&gt;), OrderBy(&lt;värde 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>
