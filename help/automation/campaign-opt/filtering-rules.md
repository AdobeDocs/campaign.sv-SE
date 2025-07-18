---
product: campaign
title: Konfigurera filtreringsregler
description: Lär dig konfigurera filtreringsregler
feature: Typology Rules
exl-id: 17507cdf-211f-4fa2-abb9-33d4f6dc47bb
source-git-commit: 1fb93efac4fee4965213f8b42f518f2c10638e20
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---

# Filtreringsregler{#filtering-rules}

Använd filtreringsregler för att välja meddelanden som ska exkluderas baserat på kriterier som definierats i en fråga. Dessa regler är kopplade till en målinriktningsdimension.

Filtreringsregler kan länkas till andra typer av regler (kontroll, tryck osv.) i typologier, eller grupperas i en dedikerad **filtreringstypologi**. [Läs mer](#create-and-use-a-filtering-typology).

## Skapa en filtreringsregel {#create-a-filtering-rule}

Du kan t.ex. filtrera nyhetsbrevets prenumeranter för att förhindra att kommunikationen skickas till mottagare som är minderåriga.

Så här definierar du filtret:

1. Bläddra till mappen **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** i Campaign-exporteraren och klicka på ikonen **Nytt** för att skapa en typologiregel.
1. Skapa en typologiregel för **[!UICONTROL Filtering]** som gäller för alla kanaler.

   ![](assets/campaign_opt_create_filter_01.png)

1. På fliken **Filter** ändrar du standardmåldimensionen till **Prenumerationer** (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Skapa filtret med länken **[!UICONTROL Edit the query from the targeting dimension...]**.

   ![](assets/campaign_opt_create_filter_03.png)

1. Filtrera på mottagarsidan och spara filtreringsvillkoret.

   ![](assets/campaign_opt_create_filter_03b.png)

1. Länka den här regeln från fliken **Typologier** till en kampanjtypologi och spara den.

   ![](assets/campaign_opt_create_filter_04.png)

När den här regeln används i en leverans, exkluderas underåriga prenumeranter automatiskt. Ett specifikt meddelande indikerar när regeln tillämpas:

![](assets/campaign_opt_create_filter_05.png)

## Villkora en filtreringsregel {#condition-a-filtering-rule}

Du kan begränsa programfältet för filtreringsregeln baserat på den länkade leverans- eller leveransdispositionen.

Det gör du genom att gå till fliken **[!UICONTROL General]** i typologiregeln, välja den typ av begränsning som ska användas och skapa filtret.
<!--
![](assets/campaign_opt_create_filter_06.png)
-->


I det här fallet gäller att även om regeln är länkad till alla leveranser, kommer den endast att tillämpas på dem som matchar kriterierna för det definierade filtret.

>[!NOTE]
>
>Typologier och filtreringsregler kan användas i ett arbetsflöde i aktiviteten **[!UICONTROL Delivery outline]**. [Läs mer](../workflow/delivery-outline.md).

## Skapa och använda en filtertypologi {#create-and-use-a-filtering-typology}

Du kan skapa **[!UICONTROL Filtering]**-typologier: de innehåller bara filtreringsregler.

![](assets/campaign_opt_create_typo_filtering.png)

Dessa specifika typologier kan länkas till en leverans när målet har valts: klicka på länken **[!UICONTROL To]** i leveransguiden och klicka sedan på fliken **[!UICONTROL Exclusions]**.

![](assets/campaign_opt_apply_typo_filtering.png)

Välj sedan den filtreringstyp som ska användas för leveransen. Om du vill göra det klickar du på knappen **[!UICONTROL Add]** och väljer de typologier som ska användas.

Du kan också länka filtreringsregler direkt via den här fliken utan att gruppera dem i en typologi. Använd fönstrets nedre del för att göra detta.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>Endast typologier och filtreringsregler är tillgängliga i urvalsfönstret.
>
>Dessa konfigurationer kan definieras i leveransmallen som automatiskt tillämpas på alla nya leveranser som skapas med hjälp av mallen.
>

## Undantagsregler för standardleverans {#default-deliverability-exclusion-rules}

Två filtreringsregler är tillgängliga som standard: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) och **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Under e-postanalysen jämför dessa regler mottagarnas e-postadresser med de förbjudna adresserna eller domännamnen i en krypterad global undertryckningslista som hanteras i leveransinstansen. Om det finns en matchning skickas inte meddelandet till den mottagaren.

Detta för att undvika att läggas till i blockeringslista på grund av skadlig aktivitet, särskilt användning av en svampfälla. Om du till exempel använder en svällning för att prenumerera via ett av dina webbformulär, skickas ett bekräftelsemeddelande via e-post till den svällningen, vilket gör att din adress automatiskt läggs till i blockeringslista.

>[!NOTE]
>
>Adresserna och domännamnen som finns i den globala undertryckningslistan är dolda. Endast antalet uteslutna mottagare anges i leveransanalysloggarna.
