---
product: campaign
title: Skapa en sammanfattningslista
description: Skapa en sammanfattningslista
feature: Workflows, Data Management
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 86dee66a-357a-4927-916e-51cde6c006d5
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 1%

---

# Skapa en sammanfattningslista{#creating-a-summary-list}

I det här exemplet beskrivs hur du skapar ett arbetsflöde som du kan skapa en sammanfattningslista genom att samla in filer och följa flera förbättringar. Exemplet är baserat på en lista med kontakter som har köpt i en butik.

![](assets/uc2_enrich_overview.png)

Följande datastruktur används:

![](assets/uc2_enrich_data.png)

Syftet är att

* Använda de olika alternativen för anrikningsaktiviteten
* Uppdatera data i databasen efter en avstämning
* Så här skapar du en global&quot;vy&quot; av data som berikats

Om du vill skapa en sammanfattningslista måste du följa dessa steg:

1. Samla in och läsa in en inköpsfil i arbetsflödets arbetsregister
1. Förbättra importerade data genom att skapa en länk till en referenstabell
1. Uppdaterar tabellen&quot;Inköp&quot; med data som berikats
1. Förbättra&quot;Kontaktdata&quot; med en sammanställd beräkning från tabellen&quot;Inköp&quot;
1. Skapa en sammanfattningslista

## Steg 1: Läs in filen och stämma av importerade data {#step-1--loading-the-file-and-reconciling-the-imported-data}

De data som ska läsas in är&quot;Inköpsrelaterade&quot; data i följande format:

```
Product Name;Product price;Store
Computer;2000;London 3
Tablet;600;Cambridge
Computer;2000;London 5
Computer;2000;London 8
Tablet;600;Cambridge
Phone;500;London 5
```

Dessa data finns i textfilen&quot;Purchases.txt&quot;.

1. Lägg till aktiviteterna **Filinsamlaren** och **Datainläsning (fil)** i arbetsflödet.

   Med aktiviteten **Filinsamlare** kan du samla in och skicka filer från och till Adobe Campaign-servern.

   Med aktiviteten **Datainläsning(fil)** kan du utöka arbetsflödets arbetsregister med insamlade data. Mer information om den här aktiviteten finns på [den här sidan](data-loading-file.md).

1. Konfigurera aktiviteten **Filinsamlare** för att samla in textfiler (&#42;.txt) från den valda katalogen.

   ![](assets/uc2_enrich_collecteur.png)

   Med aktiviteten **Filinsamlaren** kan du hantera frånvaron av en fil i källkatalogen. Det gör du genom att kontrollera alternativet **[!UICONTROL Process file nonexistence]**. I det här arbetsflödet har en **Wait**-aktivitet lagts till för att försöka med en annan filsamling om den saknas i katalogen vid tidpunkten för samlingen.

1. Konfigurera aktiviteten **Datainläsning (fil)** med en exempelfil med samma format som de data som ska importeras.

   ![](assets/uc2_enrich_chargement1.png)

   Klicka på länken **[!UICONTROL Click here to change the file format...]** om du vill byta namn på kolumnerna med hjälp av de interna namnen och etiketterna i tabellen&quot;Inköp&quot;.

   ![](assets/uc2_enrich_chargement2.png)

När data har importerats utförs en anrikning genom att en länk skapas till en referenstabell som matchar schemat&quot;Lagrar&quot;.

Lägg till anrikningsaktiviteten och konfigurera den enligt följande:

1. Välj huvuduppsättningen med data från aktiviteten **Datainläsning(fil)**.

   ![](assets/uc2_enrich_enrich1.png)

1. Klicka på **[!UICONTROL Add data]** och välj sedan alternativet **[!UICONTROL A link]**.

   ![](assets/uc2_enrich_enrich2.png)

1. Välj alternativet **[!UICONTROL Define a collection]**.
1. Välj schemat&quot;Lagrar&quot; som mål.

   ![](assets/uc2_enrich_enrich3.png)

Mer information om de olika typerna av länkar finns i [Förbättra och ändra data](targeting-workflows.md#enrich-and-modify-data).

I följande fönster måste du skapa ett kopplingsvillkor genom att välja källfältet (i huvuduppsättningen) och målfältet (som tillhör schemat &quot;Stores&quot;) för att konfigurera datavstämningen.

![](assets/uc2_enrich_enrich4.png)

Nu när länken skapas ska vi lägga till en kolumn i arbetsflödets arbetsregister från schemat&quot;Stores&quot;: fältet&quot;ZipCode Reference&quot;.

1. Öppna anrikningsaktiviteten.
1. Klicka på **[!UICONTROL Edit additional data]**.
1. Lägg till fältet ZipCode Reference i **[!UICONTROL Output columns]**.

![](assets/uc2_enrich_enrich5.png)

Informationen i arbetsflödets arbetsregister efter denna berikning är följande:

![](assets/uc2_enrich_population1.png)

## Steg 2: Skriv inhämtade data i tabellen&quot;Inköp&quot; {#step-2--writing-enriched-data-to-the--purchases--table}

I det här steget beskrivs hur du skriver importerade och berikade data till tabellen&quot;Inköp&quot;. För att göra detta måste vi använda en **Uppdatera data**-aktivitet.

En avstämning mellan data i arbetsflödets arbetstabell och måldimensionen **Inköp** måste utföras innan data i tabellen **Inköp** uppdateras.

1. Klicka på fliken **[!UICONTROL Reconciliation]** i anrikningsaktiviteten.
1. Välj måldimensionen, inköpsschemat i det här fallet.
1. Välj ett Source-uttryck för data i arbetsflödestabellen (fältet&quot;storeName&quot; i det här fallet).
1. Välj ett måluttryck för data i tabellen&quot;Inköp&quot; (&quot;lagenamn&quot; i det här fallet).
1. Markera alternativet **[!UICONTROL Keep unreconciled data coming from the work table]**.

![](assets/uc2_enrich_reconciliation.png)

I aktiviteten **Uppdatera data** behövs följande konfiguration:

1. Välj alternativet **[!UICONTROL Insert or update]** i fältet **[!UICONTROL Operation type]** för att undvika att skapa nya poster varje gång filen samlas in.
1. Välj värdet **[!UICONTROL By directly using the targeting dimension]** för alternativet **[!UICONTROL Record identification]**.
1. Välj inköpsschemat som **[!UICONTROL Document type]**.
1. Ange listan med fält som ska uppdateras. I kolumnen **[!UICONTROL Destination]** kan du definiera fälten i schemat Inköp. I kolumnen **[!UICONTROL Expression]** kan du markera de fält i arbetstabellen som ska utföra en mappning.
1. Klicka på alternativet **[!UICONTROL Generate an outbound transition]**.


## Steg 3: Berika kontaktdata {#step-3--enriching--contact--data-}

Schemat&quot;Kontakter&quot; är fysiskt länkat till schemat&quot;Inköp&quot;. Det innebär att du kan använda ett annat alternativ för alternativet &quot;Anrikning&quot;: lägga till data som är länkade till filtreringsdimensionen.

Syftet med den andra anrikningen är att skapa en sammanställning av inköpsschemat för att beräkna det totala antalet inköp för varje identifierad kontakt.

1. Lägg till en aktivitet av typen **query** som gör att du kan återställa alla **kontakter** som är lagrade.
1. Lägg till en **fördjupningsaktivitet** och välj sedan den huvuduppsättning som är resultatet av föregående fråga.
1. Klicka på Lägg till **[!UICONTROL Data]**.
1. Klicka på alternativet **[!UICONTROL Data linked to the targeting dimension]**.
1. Klicka på alternativet **[!UICONTROL Data linked to the filtering dimension]** i fönstret **[!UICONTROL Select fields to add]**.
1. Markera noden **[!UICONTROL Purchases]** och klicka sedan på **[!UICONTROL Next]**.

   ![](assets/uc2_enrich_enrich9.png)

1. Ändra fältet **[!UICONTROL Collected data]** genom att välja alternativet **[!UICONTROL Aggregates]**.

   ![](assets/uc2_enrich_enrich10.png)

1. Klicka på **[!UICONTROL Next]**.
1. Lägg till följande uttryck för att beräkna inköpsvolymen för varje kontakt: &quot;Sum(@prodprice)&quot;.

   ![](assets/uc2_enrich_enrich6.png)

Om du vill förbereda sammanfattningslistan måste du lägga till fält från fälten&quot;Inköp&quot; och från den första anrikningen: fältet&quot;ZipCode Reference&quot;.

1. Klicka på länken **[!UICONTROL Edit additional data...]** i anrikningsaktiviteten.
1. Lägg till fälten&quot;Butiksnamn&quot; och&quot;Inköp/Postnummerreferens&quot;.

   ![](assets/uc2_enrich_enrich7.png)

1. Klicka på fliken **[!UICONTROL Properties]**.
1. Ändra den andra länken så att bara en rad skapas.

## Steg 4: Skapa och lägg till i en sammanfattningslista {#step-4--creating-and-adding-to-a-summary-list}

Det sista steget är att skriva alla data som berikats till en lista.

1. Lägg till en **listuppdateringsaktivitet** i arbetsflödet. Denna verksamhet måste vara kopplad till den utgående övergången för den andra anrikningsaktiviteten.
1. Välj alternativet **[!UICONTROL Create the list if necessary (Calculated name)]**.
1. Välj ett värde för det beräknade namnet. Etiketten som valts för listan är aktuellt datum: &lt;%= formatDate(new Date(), &quot;%2D/%2M/%2Y&quot;) %>.

När arbetsflödet är klart kommer listan att innehålla:

* en förteckning över kontakter,
* a &quot;Total purchasing&quot; column,
* en&quot;Store name&quot;-kolumn,
* en kolumn av typen&quot;Postnr&quot; angiven för alla butiker som finns i butiksreferensschemat.

![](assets/uc2_enrich_listfinal.png)
