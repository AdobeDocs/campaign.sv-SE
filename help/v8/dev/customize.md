---
title: Anpassa instansen
description: Lär dig hur du anpassar instansen
feature: Configuration, Application Settings
role: Developer
level: Intermediate, Experienced
exl-id: 18000763-5923-48bd-b62d-cccd3c11016d
source-git-commit: 061197048885a30249bd18af7f8b24cb71def742
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Anpassa instansen {#gs-ac-custom}

Lär dig hur du **anpassar Campaign-instansen**.

>[!CAUTION]
>
>Adobe Campaign-anpassning är förbehållet expertanvändare.

## Skapa nya datafält och diagram

Adobe Campaign använder datascheman för att

* Definiera hur dataobjekt i programmet kopplas till underliggande databastabeller
* Definiera länkar mellan olika dataobjekt i Campaign-programmet
* Definiera och beskriv de enskilda fälten som ingår i varje objekt

Om du till exempel vill lägga till ett fält i en befintlig tabell, som mottagartabellen (nms:mottagare), måste du utöka det schemat.

Två tabelltilläggslägen är tillgängliga:

* Genom gränssnittet med assistenten **Nytt fält**

  Lär dig hur du snabbt lägger till ett nytt fält i Campaign i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/new-field-wizard.html#configuring-campaign-classic){target="_blank"}

* Programmatiskt genom att utöka schemat. Lär dig att utöka ett befintligt schema i [det här avsnittet](../dev/extend-schema.md).

Du kan också skapa nya tabeller i Campaign-databasen och utöka den inbyggda datamodellen.

Om du vill lägga till en helt ny typ av data som inte finns i körklart läge i Adobe Campaign (till exempel en kontraktstabell) kan du skapa ett anpassat schema direkt. Mer information finns i [det här exemplet](../dev/create-schema.md#example--creating-a-contract-table).

**Relaterade ämnen**

Exempel på schemautgåva i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/examples-of-schemas-edition.html#configuring-campaign-classic){target="_blank"}

Använd skiftläge: länka ett fält till en befintlig referenstabell i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/editing-schemas/examples-of-schemas-edition.html#uc-link){target="_blank"}


## Ändra indataformulären

Kampanjens indataformulär kan anpassas efter er implementering. Du kan lägga till eller ta bort formulärfält genom att ändra XML-innehållet.

Lär dig hur du ändrar ett befintligt indataformulär eller skapar ett nytt formulär i [det här avsnittet](../dev/forms.md).

## Anpassa kontrollpaneler{#gs-custom-dashboards}

Adobe Campaign gränssnitt använder många webbprogram för att få åtkomst till, hantera och interagera med mottagare, leveranser, kampanjer, lager med mera. De visas i gränssnittet i form av kontrollpaneler med bara en sida.

De inbyggda webbprogrammen lagras i mappen **Administration > Konfiguration > Webbprogram** i Utforskaren.

Lär dig hur du skapar en översiktssida i Campaign i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/use-cases--creating-overviews.html#creating-a-single-page-web-application){target="_blank"}


## Anpassa listor och skapa filter {#gs-lists-and-filters}

Kampanjlistor innehåller fördefinierade filter som underlättar navigering och datavisning.

När du navigerar i Adobe Campaign Utforskaren-trädet visas data i databasen i listor. Du kan filtrera dessa listor, köra sökningar, lägga till information, filtrera och sortera data.

Lär dig konfigurera listor och spara en listkonfiguration på [den här sidan](../start/campaign-ui.md).

Du kan använda filter på de här listorna för att bara visa de data som operatorn behöver. Sedan kan åtgärder utföras på filtrerade data. Med filterkonfigurationen kan du välja data från en lista dynamiskt. Om data ändras uppdateras de filtrerade data.

Läs mer om filtreringsalternativ på [den här sidan](../audiences/create-filters.md).
