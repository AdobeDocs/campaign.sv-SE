---
product: campaign
title: Förbättra data
description: Läs mer om arbetsflödesaktiviteten för anrikning
feature: Workflows, Enrichment Activity
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 3b3fa15f-b16e-42c8-a2e6-03350aee1903
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 0%

---

# Förbättra data{#enriching-data}



## Om att förbättra data {#about-enriching-data}

Det här användningsfallet innehåller information om möjliga användningar av aktiviteten **[!UICONTROL Enrichment]** i ett målarbetsflöde. Mer information om hur du använder aktiviteten **[!UICONTROL Enrichment]** finns i: [Enrichment](enrichment.md).

Ett användningsexempel om hur du kan förbättra en e-postleverans med anpassade datum finns också i [det här avsnittet](email-enrichment-with-custom-date-fields.md).

Kontakterna i marknadsföringsdatabasen får en inbjudan att delta i en tävling via ett webbprogram. Konkurrensresultaten återfås i tabellen **[!UICONTROL Competition results]**. Den här tabellen är länkad till kontakttabellen (**[!UICONTROL Recipients]**). Tabellen **[!UICONTROL Competition results]** innehåller följande fält:

* Konkurrensnamn (@game)
* Utvärderingsnummer (@trial)
* Poäng (@score)

![](assets/uc1_enrich_1.png)

En kontakt som hittas i tabellen **[!UICONTROL Recipients]** kan länkas till flera rader i tabellen **[!UICONTROL Competition results]**. Relationen mellan de här två tabellerna är av typen 1-n. Här är ett exempel på resultatloggarna för en mottagare:

![](assets/uc1_enrich_2.png)

Syftet med detta är att skicka personaliserade leveranser till personer som deltog i den senaste tävlingen beroende på deras högsta poäng. Mottagaren med högsta poäng får första pris, mottagaren med näst högsta poäng får ett tröstpris och alla andra får ett meddelande som önskar dem bättre lycka till nästa gång.

Vi har skapat följande arbetsflöde för målinriktning för att konfigurera det här användningsexemplet:

![](assets/uc1_enrich_3.png)

Så här skapar du arbetsflödet:

1. Två **[!UICONTROL Query]** aktiviteter och en **[!UICONTROL Intersection]**-aktivitet läggs till för nya prenumeranter som gick in sist i tävlingen.
1. Aktiviteten **[!UICONTROL Enrichment]** används för att lägga till data som lagras i tabellen **[!UICONTROL Competition results]**. Fältet **[!UICONTROL Score]** som vår leveranspersonalisering ska ske i läggs till i arbetsflödets arbetsregister.
1. Typaktiviteten **[!UICONTROL Split]** används för att skapa mottagardelmängder baserat på poängvärden.
1. En **[!UICONTROL Delivery]**-aktivitet läggs till för varje delmängd.

## Steg 1: Riktning {#step-1--targeting}

Den första frågan används för målmottagare som lagts till i databasen under de senaste sex månaderna.

![](assets/uc1_enrich_4.png)

Den andra frågan används för att rikta sig till de mottagare som deltog i den senaste tävlingen.

![](assets/uc1_enrich_5.png)

En aktivitet av typen **[!UICONTROL Intersection]** läggs sedan till som mål för de mottagare som lagts till i databasen under de senaste sex månaderna och som gick in i den sista tävlingen.

## Steg 2: Anrikning {#step-2--enrichment}

I det här exemplet får du lära dig hur du anpassar leveranser enligt fältet **[!UICONTROL Score]** som lagras i tabellen **[!UICONTROL Competition results]**. Den här tabellen har en 1:n-typrelation med mottagartabellen. Aktiviteten **[!UICONTROL Enrichment]** används för att lägga till data från en tabell som är länkad till filtreringsdimensionen i arbetsflödets arbetsregister.

1. Välj **[!UICONTROL Add data]**, **[!UICONTROL Data linked to the filtering dimension]** och klicka sedan på **[!UICONTROL Next]** på redigeringsskärmen för anrikningsaktiviteten.

   ![](assets/uc1_enrich_6.png)

1. Välj sedan alternativet **[!UICONTROL Data linked to the filtering dimension]**, markera tabellen **[!UICONTROL Competition results]** och klicka på **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Ange ett ID och en etikett och välj alternativet **[!UICONTROL Limit the line count]** i fältet **[!UICONTROL Data collected]**. I fältet **[!UICONTROL Lines to retrieve]** väljer du 1 som ett värde. För varje mottagare kommer anrikningsaktiviteten att lägga till en rad från tabellen **[!UICONTROL Competition results]** i arbetsflödets arbetsregister. Klicka på **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. I det här exemplet vill vi återfå mottagarens högsta poäng, men bara för den sista tävlingen. Om du vill göra det lägger du till ett filter i fältet **[!UICONTROL Competition name]** för att exkludera alla rader som hör till tidigare tävlingar. Klicka på **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Gå till skärmen **[!UICONTROL Sort]** och klicka på knappen **[!UICONTROL Add]**, markera fältet **[!UICONTROL Score]** och markera kryssrutan i kolumnen **[!UICONTROL descending]** för att sortera objekt i fälten i fallande ordning. **[!UICONTROL Score]** För varje mottagare läggs en rad till i anrikningsaktiviteten som matchar den högsta poängen för det senaste spelet. Klicka på **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. Dubbelklicka på fältet **[!UICONTROL Score]** i fönstret **[!UICONTROL Data to add]**. För varje mottagare läggs bara fältet **[!UICONTROL Score]** till i anrikningsaktiviteten. Klicka på **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Högerklicka på den inkommande övergången för anrikningsaktiviteten och välj **[!UICONTROL Display the target]**. Arbetstabellen innehåller följande data:

![](assets/uc1_enrich_13.png)

Det länkade schemat är:

![](assets/uc1_enrich_15.png)

Förnya den här åtgärden vid utgående övergång av anrikningsaktiviteten. Vi ser att data som är länkade till mottagarpoängen har lagts till. Den högsta poängen för varje mottagare har återställts.

![](assets/uc1_enrich_12.png)

Det matchande schemat har också berikats.

![](assets/uc1_enrich_14.png)

## Steg 3: Dela och leverera {#step-3--split-and-delivery}

Om du vill sortera mottagarna baserat på deras poäng läggs en **[!UICONTROL Split]**-aktivitet till efter anrikningen.

![](assets/uc1_enrich_18.png)

1. En första (**vinnare**) delmängd har definierats så att den innehåller mottagaren med det högsta poängtalet. Det gör du genom att definiera en begränsning av antalet poster, tillämpa en fallande sortering på poängen och begränsa antalet poster till 1.

   ![](assets/uc1_enrich_16.png)

1. Den andra delmängden (**Andra plats**) innehåller mottagaren med det näst högsta poängtalet. Konfigurationen är densamma som för den första delmängden.

   ![](assets/uc1_enrich_17.png)

1. Den tredje delmängden (**losers**) innehåller alla andra mottagare. Gå till fliken **[!UICONTROL General]** och markera kryssrutan **[!UICONTROL Generate complement]** för att ange alla mottagare som inte uppnådde de två högsta poängen som mål.

   ![](assets/uc1_enrich_19.png)

1. Lägg till en **[!UICONTROL Delivery]**-typaktivitet för varje delmängd, med olika leveransmallar för varje.

   ![](assets/uc1_enrich_20.png)
