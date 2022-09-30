---
title: Anpassa instansen
description: Lär dig hur du anpassar instansen
role: Developer
level: Beginner, Intermediate, Experienced
exl-id: 18000763-5923-48bd-b62d-cccd3c11016d
source-git-commit: 2ce1ef1e935080a66452c31442f745891b9ab9b3
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 6%

---

# Anpassa instansen{#gs-ac-custom}

Lär dig hur **Anpassa Campaign-instansen**.

>[!CAUTION]
>
>Adobe Campaign-anpassning är förbehållet expertanvändare.

## Skapa nya datafält och scheman

Adobe Campaign använder datascheman för att

* Definiera hur dataobjekt i programmet länkas till underliggande databastabeller
* Definiera länkar mellan olika dataobjekt i programmet Campaign
* Definiera och beskriva de enskilda fälten som ingår i varje objekt

Om du till exempel vill lägga till ett fält i en befintlig tabell, som mottagartabellen (nms:mottagare), måste du utöka det schemat.

Två tabelltilläggslägen är tillgängliga:

* Genom gränssnittet med **Nytt fält** assistent

   ![](../assets/do-not-localize/book.png) Lär dig hur du snabbt lägger till ett nytt fält i Campaign i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/new-field-wizard.html?lang=en#configuring-campaign-classic){target=&quot;_blank&quot;}

* Programmerat genom att utöka schemat

   ![](../assets/do-not-localize/glass.png) Lär dig hur du utökar ett befintligt schema i [det här avsnittet](../dev/extend-schema.md).


Du kan också skapa nya tabeller i Campaign-databasen och utöka den inbyggda datamodellen.

Om du vill lägga till en helt ny typ av data som inte finns i körklart läge i Adobe Campaign (till exempel en kontraktstabell) kan du skapa ett anpassat schema direkt. Mer information finns i [det här exemplet](../dev/create-schema.md#example--creating-a-contract-table).

**Relaterade ämnen**

![](../assets/do-not-localize/book.png) Exempel på schemautgåva i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/examples-of-schemas-edition.html?lang=en#configuring-campaign-classic){target=&quot;_blank&quot;}

![](../assets/do-not-localize/book.png) Användningsfall: länka ett fält till en befintlig referenstabell i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/examples-of-schemas-edition.html?lang=en#uc-link){target=&quot;_blank&quot;}


## Ändra indataformulären

Kampanjens indataformulär kan anpassas efter er implementering. Du kan lägga till eller ta bort formulärfält genom att ändra XML-innehållet.

![](../assets/do-not-localize/glass.png) Lär dig hur du ändrar ett befintligt inmatningsformulär eller skapar ett nytt formulär i [det här avsnittet](../dev/forms.md).

## Anpassa kontrollpaneler{#gs-custom-dashboards}

Adobe Campaign gränssnitt använder många webbprogram för att få åtkomst till, hantera och interagera med mottagare, leveranser, kampanjer, lager med mera. De visas i gränssnittet i form av kontrollpaneler med bara en sida.

De färdiga webbprogrammen lagras i noden Administration > Konfiguration > Webbprogram.

![](../assets/do-not-localize/book.png) Lär dig hur du skapar en översiktssida i Campaign i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/use-cases--creating-overviews.html?lang=en#creating-a-single-page-web-application){target=&quot;_blank&quot;}


## Anpassa listor och skapa filter {#gs-lists-and-filters}

### Åtkomst till data från kontrollpaneler

Kampanjlistor innehåller fördefinierade filter som underlättar navigering och datavisning.

![](../assets/do-not-localize/book.png) Läs mer om filtreringsalternativ i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/filtering-data/filtering-options.html?lang=en#about-filtering){target=&quot;_blank&quot;}


### Få åtkomst till data från Utforskaren

När du navigerar i Adobe Campaign Utforskaren-trädet visas data i databasen i listor. Du kan filtrera dessa listor, köra sökningar, lägga till information, filtrera och sortera data.

![](../assets/do-not-localize/book.png) Lär dig hur du konfigurerar listor och sparar en listkonfiguration i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/campaign-workspace/adobe-campaign-ui-lists.html?lang=en#getting-started){target=&quot;_blank&quot;}


Du kan använda filter på de här listorna för att bara visa de data som operatorn behöver. Sedan kan åtgärder utföras på filtrerade data. Med filterkonfigurationen kan du välja data från en lista dynamiskt. Om data ändras uppdateras de filtrerade data.

![](../assets/do-not-localize/book.png) Lär dig filtrera data i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/filtering-data/creating-filters.html?lang=en#typology-of-available-filters){target=&quot;_blank&quot;}
