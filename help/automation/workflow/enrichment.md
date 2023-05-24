---
product: campaign
title: Berikning
description: Läs mer om arbetsflödesaktiviteten för anrikning
feature: Workflows, Enrichment Activity, Targeting Activity
exl-id: 23bfabac-62cc-4f86-a739-a34a0e183c31
source-git-commit: 77ec01aaba1e50676bed57f503a9e4e8bb1fe54c
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 2%

---

# Berikning{#enrichment}



The **[!UICONTROL Enrichment]** kan du lägga till information i en profillista och länkar till en befintlig tabell (skapa en ny koppling). Avstämningskriterier med profiler i databasen kan också definieras.

![](assets/enrichment_design.png)

## Definitioner {#definitions}

Om du vill använda anrikningsaktiviteten måste du känna till de olika alternativen som är tillgängliga när du lägger till data.

![](assets/enrichment_edit.png)

The **[!UICONTROL Data linked to the filtering dimension]** ger dig tillgång till

* Filtreringsdimensionens data: åtkomst till arbetstabelldata
* Data länkade till filtreringsdimensionen: åtkomst till data som är länkade till arbetsregistret

![](assets/wf_enrich_linkoptions.png)

The **[!UICONTROL A link]** gör att du kan skapa en join i valfri databastabell.

![](assets/wf_enrich_linkstype.png)

Det finns fyra typer av länkar:

* **[!UICONTROL Define a collection]**: I kan du definiera en länk med en 1-N-kardinalitet mellan tabellerna.
* **[!UICONTROL Define a link whose target is still available]**: I kan du definiera en länk med en 1-1-kardinalitet mellan tabeller. Kopplingsvillkoren måste definieras av en enda post i måltabellen.
* **[!UICONTROL Define a link whose target does not necessarily exist in the base]**: I kan du definiera en länk med 0-1-kardinalitet mellan tabeller. Kopplingsvillkoret måste definieras med 0 eller 1 (max) i måltabellen.

   Det här alternativet är konfigurerat i **[!UICONTROL Simple Join]** som du kommer åt via **[!UICONTROL Edit additional data]** länk till **[!UICONTROL Enrichment]** aktivitet.

* **[!UICONTROL Define a link by searching for a reference among several options]**: den här typen av länk definierar en avstämning mot en unik post. Adobe Campaign skapar en länk till en måltabell genom att lägga till en sekundärnyckel i måltabellen för lagring av en referens till den unika posten.

   Det här alternativet är konfigurerat i **[!UICONTROL Reconciliation and deduplication]** som du kommer åt via **[!UICONTROL Edit additional data]** länk till **[!UICONTROL Enrichment]** aktivitet.

Användningsexempel som beskriver hur anrikningsaktiviteter fungerar i sitt sammanhang finns också i följande avsnitt:

* [E-postberikande med anpassade datumfält](email-enrichment-with-custom-date-fields.md).
* [Berika data](enrich-data.md)
* [Skapa en sammanfattningslista](create-a-summary-list.md)

## Lägga till information {#adding-information}

Använd **[!UICONTROL Enrichment]** aktivitet för att lägga till kolumner i en arbetstabell: den här aktiviteten kan användas som komplement till en frågeaktivitet.

Konfigurationen av ytterligare kolumner finns i [Lägga till data](query.md#adding-data).

The **[!UICONTROL Primary set]** kan du välja ingående övergång: uppgifterna om den här aktivitetens arbetsyta skall berikas.

Klicka på **[!UICONTROL Add data]** och välj vilken typ av data som ska läggas till. Listan över datatyper som erbjuds beror på vilka moduler och alternativ som är installerade på din plattform. I en minimal konfiguration kan du alltid lägga till data som är länkade till filtreringsdimensionen och en länk.

![](assets/enrichment_edit.png)

I exemplet nedan kommer den utgående övergången att berikas med information om åldern på målprofilerna.

![](assets/enrichment_add_data.png)

Högerklicka på anrikningsaktivitetens inkommande övergång för att visa data före anrikningssteget.

![](assets/enrichment_content_before.png)

Arbetstabellen innehåller följande data och det associerade schemat:

![](assets/enrichment_content_before_a.png)

Upprepa den här åtgärden vid anrikningsfasens utdata.

![](assets/enrichment_content_after.png)

Du kan se att data för profilsidor har lagts till:

![](assets/enrichment_content_after_a.png)

Det matchande schemat har också berikats.

## Hantera ytterligare data {#managing-additional-data}

Avmarkera **[!UICONTROL Keep all additional data from the main set]** om du inte vill behålla tidigare definierade ytterligare data. I det här fallet läggs endast de ytterligare kolumner som har valts i anrikningsaktiviteten till i tabellen för utgående arbete. Den ytterligare information som lagts till i aktiviteterna uppströms sparas inte.

![](assets/enrichment_edit_without_additional.png)

Data och schemat vid anrikningsfasutdata blir följande:

![](assets/enrichment_content_after_without_additional.png)

## Skapa en länk {#creating-a-link}

Du kan använda anrikningsaktiviteten för att skapa en länk mellan arbetsdata och Adobe Campaign-databasen: detta blir en lokal länk till arbetsflödet mellan inkommande data.

Om du till exempel läser in data från en fil som innehåller mottagarnas kontonummer, land och e-postadress måste du skapa en länk till landstabellen för att kunna uppdatera informationen i deras profiler.

Gör så här:

1. Samla in och läs in följande filtyp:

   ```
   Account number;Country;Email
   18D65;FRANCE;agnes@gmail.com
   243PP;RUSSIA;paul@gmail.com
   55H87;CROATIA;dave@gmail.com
   56U81;USA;susan@gmail.com
   853PI;ITALY;anna@gmail.com
   890LP;FRANCE;robert@gmail.com
   83TY2;SWITZERLAND;mike@gmail.com
   ```

1. Redigera anrikningsaktiviteten och klicka på **Lägg till data...** om du vill skapa en koppling till tabellen Land.

   ![](assets/enrichment_edit_after_file_box.png)

1. Välj **[!UICONTROL Link definition]** och klicka på **[!UICONTROL Next]** -knappen. Ange vilken typ av länk som ska skapas. I det här exemplet vill vi att filmottagarens land ska stämma överens med ett land i listan över tillgängliga länder i den dedikerade databastabellen. Välj alternativet **[!UICONTROL Define a link by searching for a reference among several options]**. Välj landstabellen i dialogrutan **[!UICONTROL Target schema]** fält.

   ![](assets/enrichment_add_a_link_select_option4.png)

1. Markera sedan de fält som du vill länka källfilsvärdena till i databasen.

   ![](assets/enrichment_add_a_link_select_join.png)

I resultatet av den här anrikningsaktiviteten kommer det tillfälliga schemat att innehålla länken till landstabellen:

![](assets/enrichment_external_link_schema.png)

## Datavstämning {#data-reconciliation}

Anrikningsaktiviteten kan användas för att konfigurera datavstämning, inklusive när data har lästs in i databasen. I det här fallet **[!UICONTROL Reconciliation]** kan du definiera länken mellan data i Adobe Campaign-databasen och data i arbetstabellen.

Välj **[!UICONTROL Identify the targeting document based on work data]** anger du det schema som du vill skapa en länk till och definierar kopplingsvillkoren: för att göra detta väljer du fälten som ska förenas i arbetsdata (**[!UICONTROL Source expression]**) och i målgruppsdimensionen (**[!UICONTROL Destination expression]**).

Du kan använda ett eller flera avstämningskriterier.

![](assets/enrichment_reconciliations_tab_01.png)

Om flera kopplingsvillkor anges måste ALLA verifieras så att data kan länkas ihop.

## Infoga ett erbjudande {#inserting-an-offer-proposition}

Med anrikningsaktiviteten kan du lägga till erbjudanden eller länkar till erbjudanden för mottagare.

Mer information om anrikningsaktiviteten finns i [section](enrichment.md).

Du kan till exempel förbättra data för en mottagarfråga före en leverans.

![](assets/int_enrichment_offer1.png)

När du har konfigurerat frågan (se [section](query.md)):

1. Lägg till och öppna en anrikningsaktivitet.
1. Välj **[!UICONTROL Enrichment]** **[!UICONTROL Add data]** i flik .
1. Välj **[!UICONTROL An offer proposition]** i de typer av data som ska läggas till.

   ![](assets/int_enrichment_offer2.png)

1. Ange en identifierare och en etikett för det förslag som ska läggas till.
1. Ange erbjudandevalet. Det finns två möjliga alternativ:

   * **[!UICONTROL Search for the best offer in a category]**: Markera det här alternativet och ange parametrarna för att ringa in erbjudanden (erbjudandeplats, kategori eller tema, kontaktdatum, antal erbjudanden som ska behållas). Motorn beräknar automatiskt erbjudandena som ska läggas till enligt dessa parametrar. Vi rekommenderar att du fyller i **[!UICONTROL Category]** eller **[!UICONTROL Theme]** i stället för båda samtidigt.

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]**: markera det här alternativet och ange ett erbjudandeutrymme, ett specifikt erbjudande och ett kontaktdatum för att direkt konfigurera det erbjudande du vill lägga till, utan att anropa erbjudandemotorn.

      ![](assets/int_enrichment_offer4.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Se [Flerkanalsleveranser](cross-channel-deliveries.md).

   Antalet tillgängliga offerter för förhandsgranskningen beror på konfigurationen som utförs i anrikningsaktiviteten snarare än eventuell konfiguration som utförs direkt i leveransen.

Om du vill ange erbjudandeförslag kan du även välja att referera en länk till ett erbjudande. Mer information finns i följande avsnitt [Referera till en länk till ett erbjudande](#referencing-a-link-to-an-offer).

## Referera till en länk till ett erbjudande {#referencing-a-link-to-an-offer}

Du kan även referera till en länk till ett erbjudande i en anrikningsaktivitet.

Så här gör du:

1. Välj **[!UICONTROL Add data]** i aktivitetens **[!UICONTROL Enrichment]** -fliken.
1. I fönstret där du väljer vilken typ av data som ska läggas till väljer du **[!UICONTROL A link]**.
1. Välj den typ av länk som du vill etablera samt dess mål. I det här fallet är målet erbjudandeschemat.

   ![](assets/int_enrichment_link1.png)

1. Ange kopplingen mellan inkommande tabelldata i anrikningsaktiviteten (här mottagartabellen) och erbjudandetabellen. Du kan till exempel länka en erbjudandekod till en mottagare.

   ![](assets/int_enrichment_link2.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Se [Flerkanalsleveranser](cross-channel-deliveries.md).

   >[!NOTE]
   >
   >Antalet tillgängliga offerter för förhandsgranskningen beror på konfigurationen som utförs i leveransen.

## Rankning och vikter för erbjudanden {#storing-offer-rankings-and-weights}

Som standard när **berikning** aktiviteten används för att leverera erbjudanden, deras rankningar och deras vikter lagras inte i förslagstabellen.

The **[!UICONTROL Offer engine]** den här informationen lagras som standard i aktiviteten.

Du kan dock lagra den här informationen på följande sätt:

1. Skapa ett anrop till erbjudandemotorn i en anrikningsaktivitet som placerats efter en fråga och före en leveransaktivitet.
1. I aktivitetens huvudfönster väljer du **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Lägg till **[!UICONTROL @rank]** kolumner för rankningen och **[!UICONTROL @weight]** för erbjudandevikten.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Bekräfta tillägget och spara arbetsflödet.

Leveransen lagrar automatiskt rangordningen och vikten av erbjudandena. Den här informationen visas i leveransens **[!UICONTROL Offers]** -fliken.
