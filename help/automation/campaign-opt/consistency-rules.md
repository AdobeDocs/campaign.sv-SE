---
product: campaign
title: Konsekvensregler
description: Konsekvensregler
feature: Typology Rules
exl-id: dcb4ffcf-71e5-48a2-b0f7-42915a599652
source-git-commit: 7f6c394f56d517c0a675e0fd2341bb6ef98044f0
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 4%

---

# Konsekvensregler{#consistency-rules}

Adobe Campaign garanterar enhetlig kommunikation tack vare en uppsättning regler som finns i kampanjtypologier. Syftet är att kontrollera de leveranser som skickas till mottagarna, t.ex. volym, art, relevans osv.

**Kapacitetsregler** kan till exempel undvika att överbelasta plattformen som påverkas av meddelandeleveransen. Specialerbjudanden som innehåller en nedladdningslänk får till exempel inte skickas till för många personer samtidigt för att undvika att servern blir mättad. Telefonkampanjer får inte överskrida uppspelningskapaciteten hos callcenter osv.

## Kontrollkapacitet {#control-capacity}

Innan du levererar meddelanden måste du se till att din organisation har kapacitet (fysisk infrastruktur) att bearbeta leveransen, de svar som leveransen kan generera (inkommande meddelanden) och antalet samtal som ska göras till kontaktprenumeranter (bearbetningskapacitet för callcenter), till exempel.

Skapa typologiregler för **[!UICONTROL Capacity]** om du vill göra det.

I följande exempel skapar vi en typologiregel för en lojalitetskampanj per telefon. Vi begränsar antalet meddelanden till 20 per dag, dvs. den dagliga bearbetningskapaciteten för ett callcenter. När regeln tillämpas på två leveranser kan vi övervaka förbrukningen via loggar.

Så här utformar du en ny kapacitetsregel:

1. Klicka på **[!UICONTROL New]** i mappen **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.
1. Välj en **[!UICONTROL Capacity]**-regeltyp.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Skapa tillgänglighetsraderna på fliken **[!UICONTROL Capacity]**: i vårt exempel är det här tidsperioder under vilka anrop kan göras. Välj en period på 24 timmar och ange 150 i den initiala kvantiteten, vilket innebär att callcentret kan hantera 150 samtal per dag.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Tillgänglighetsraderna är endast avsedda som information. Om du behöver exkludera meddelanden när kapacitetsgränsen nås, se [det här avsnittet](#exclude-messages-when-capacity-limit-reached).

1. Koppla den här regeln till en typologi och referera sedan till typologin i leveransen för att tillämpa den här kapacitetsregeln. Mer information om detta finns i [det här avsnittet](apply-rules.md#apply-a-typology-to-a-delivery).
1. Du kan övervaka förbrukningen från flikarna **[!UICONTROL Consumptions]** och **[!UICONTROL Capacity]**.

   När en regel används i en leverans ger kolumnerna **[!UICONTROL Consumed]** och **[!UICONTROL Remaining]** information om inläsningen, vilket visas nedan:

   ![](assets/campaign_opt_create_capacity_03.png)

   Mer information om detta finns i [det här avsnittet](#monitor-consumption).

## Definiera maximal last {#define-the-maximum-load}

Om du vill definiera den maximala lasten måste du definiera tillgänglighetsrader. Det finns två tillgängliga alternativ: du kan [skapa en eller flera tillgänglighetsrader](#add-availability-lines-one-by-one) manuellt eller skapa tillgänglighetsintervall. Frekvensen för dessa tidsperioder kan automatiseras. [Läs mer](#add-a-set-of-availability-lines).

### Lägg till tillgänglighetsrader en efter en {#add-availability-lines-one-by-one}

Om du vill skapa en tillgänglighetslinje klickar du på knappen **[!UICONTROL Add]** och väljer **[!UICONTROL Add an availability line]**. Ange tillgänglighetsperioden och tillgänglig last.

![](assets/campaign_opt_create_capacity_02.png)

Lägg till så många rader som behövs för att anpassa bearbetningskapaciteten.

### Lägg till en uppsättning tillgänglighetsrader {#add-a-set-of-availability-lines}

Om du vill definiera tillgänglighetsperioder för en viss tid klickar du på knappen **[!UICONTROL Add]** och väljer alternativet **[!UICONTROL Add a set of availability lines]**. Ange en varaktighet för varje tidsperiod och antalet perioder som ska skapas.

Om du vill automatisera hur ofta sidan skapas klickar du på knappen **[!UICONTROL Change]** och definierar tidsplaneringen.

![](assets/campaign_opt_create_capacity_07.png)

Vi kan till exempel definiera ett schema för att skapa tillgänglighetsperioder för alla arbetsdagar med en hastighet på 10 samtal per timme mellan 09.00 och 17.00. Gör så här:

1. Välj typ av intervall och de dagar och timmar som den gäller:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Ange giltighetsdatum:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Kontrollera schemat innan du godkänner det:

   ![](assets/campaign_opt_create_capacity_10.png)

Arbetsflödet **[!UICONTROL Forecasting]** skapar automatiskt alla matchande rader.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>Vi rekommenderar att du skapar tillgänglighetsrader via filimport. På den här fliken kan du visa och kontrollera förbrukningsrader.

## Uteslut meddelanden när kapacitetsgränsen har nåtts {#exclude-messages-when-capacity-limit-reached}

Tillgänglighetsraderna är endast avsedda som information. Om du vill exkludera överflödiga meddelanden markerar du alternativet **[!UICONTROL Exclude from the target messages in excess of capacity]**. Detta förhindrar att kapaciteten överskrids. För samma population som i föregående exempel får förbrukningen och den återstående kapaciteten inte överstiga den ursprungliga kvantiteten:

![](assets/campaign_opt_create_capacity_04.png)

Det högsta antalet meddelanden som kan bearbetas är jämnt fördelat över det definierade tillgänglighetsintervallet. Detta är särskilt relevant för callcenters eftersom deras högsta antal samtal per dag är begränsat. Om det gäller e-postleveranser kan du med alternativet **[!UICONTROL Do not limit instantaneous delivery capacity]** ignorera det här tillgänglighetsintervallet och skicka e-postmeddelanden samtidigt.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>Om det finns en överlagring väljs de sparade meddelandena enligt formeln som definieras i leveransegenskaperna.

![](assets/campaign_opt_create_capacity_06.png)

## Övervaka förbrukning {#monitoring-consumption}

Som standard är kapacitetsreglerna endast avsedda för indikationsändamål. Välj alternativet **[!UICONTROL Exclude messages in excess of capacity from the target]** om du vill förhindra att den definierade inläsningen överskrids. I det här fallet utesluts överflödiga meddelanden automatiskt från leveranser med denna typologiregel.

Visa de värden som visas i kolumnen **[!UICONTROL Consumed]** på fliken **[!UICONTROL Capacity]** i typologiregeln om du vill övervaka förbrukningen.

![](assets/campaign_opt_create_capacity_04.png)

Om du vill visa förbrukningsrader klickar du på fliken **[!UICONTROL Consumptions]** i regeln.
