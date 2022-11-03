---
title: Skapa en kub i Adobe Campaign
description: Lär dig hur du skapar kuber
feature: Reporting
role: Data Engineer
level: Beginner
source-git-commit: 7fc3e5b9f12ca48ef0921e27844ef9fef71ac06b
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 2%

---


# Skapa en kub{#create-a-cube}

## Arbetsytan Kub {#cube-workspace}

Bläddra till **[!UICONTROL Administration > Configuration > Cubes]** från Campaign Explorer.

![](assets/cube-node.png)

Med kuber kan du

* Exportera data direkt i en rapport som utformats i **[!UICONTROL Reports]** på Adobe Campaign.

   Om du vill göra det skapar du en ny rapport och väljer den kub som du vill använda.

   ![](assets/create-new-cube.png)

   Kuber visas som mallar baserade på vilka rapporter skapas. När du har valt en mall klickar du på **[!UICONTROL Create]** för att konfigurera och visa den nya rapporten.

   Du kan anpassa mått, ändra visningsläge eller konfigurera tabellen och sedan visa rapporten med huvudknappen.

   ![](assets/display-cube-table.png)

* Referera till en kub i **[!UICONTROL Query]** rutan för en rapport för att använda sina indikatorer, som visas nedan:

   ![](assets/cube-report-query.png)

* Infoga en pivottabell baserad på en kub på valfri sida i en rapport. Det gör du genom att referera till kuben som ska användas i **[!UICONTROL Data]** pivottabellens flik på den berörda sidan.

   ![](assets/cube-in-a-report.png)

   Mer information finns i [Utforska data i en rapport](cube-tables.md#explore-the-data-in-a-report).


>[!CAUTION]
>
>Administratörsbehörigheter krävs för att skapa kuber.

## Bygg en kub{#cube-create}

Identifiera relevanta dimensioner och mått och skapa dem i kuben innan du börjar skapa en kubrapport.

Så här skapar du en kub:

1. Markera arbetsregistret. [Läs mer](#select-the-work-table).
1. Definiera dimensioner. [Läs mer](#define-dimensions).
1. Definiera mått. [Läs mer](#build-indicators).
1. Skapa aggregat (valfritt). [Läs mer](customize-cubes.md#calculate-and-use-aggregates).

I exemplet nedan lär du dig hur du snabbt skapar en enkel kub i en rapport för att exportera måtten.

### Markera arbetsregistret {#select-the-work-table}

Så här skapar du en kub:

1. Klicka på **[!UICONTROL New]** ovanför listan med kuber.

   ![](assets/create-a-cube.png)

1. Välj det schema som innehåller de element som du vill utforska (kallas även faktchema). I det här exemplet väljer du standardinställningen **Mottagare** tabell.
1. Klicka **[!UICONTROL Save]** så här skapar du kuben: den läggs till i listan med kuber. Nu kan du använda flikarna för att konfigurera den.

1. Klicka på **[!UICONTROL Filter the source data...]** om du vill använda den här kubens beräkningar på data i databasen.

   ![](assets/cube-filter-source.png)

### Definiera dimensioner {#define-dimensions}

När kuben har skapats definierar du dess mått. Dimensioner är de analysaxlar som definieras för varje kub baserat på deras relaterade faktaschema. Detta är de dimensioner som undersöks i analysen, t.ex. tid (år, månad, datum), en produktklassificering (familj, referens osv.), ett populationssegment (per ort, åldersgrupp, status osv.).

Följ stegen nedan för att skapa dimensioner:

1. Bläddra till **[!UICONTROL Dimension]** -fliken i kuben och klicka på **[!UICONTROL Add]** för att skapa en ny dimension.
1. I **[!UICONTROL Expression field]** klickar du på **[!UICONTROL Edit expression]** -ikonen för att markera det fält som innehåller aktuella data.

   ![](assets/cube-add-dimension.png)

1. I det här exemplet väljer vi mottagaren **Ålder**. I det här fältet kan du definiera bindning till gruppsidor och göra det enklare att läsa information. Vi rekommenderar att du använder bindning när det är möjligt att använda flera olika värden.

Om du vill göra det går du till **[!UICONTROL Enable binning]** alternativ. [Läs mer](customize-cubes.md#data-binning).

1. Lägg till en **Datum** typdimension. Här vill vi visa datum då mottagarprofilen skapades. Det gör du genom att klicka **[!UICONTROL Add]** och väljer **[!UICONTROL Creation date]** i mottagartabellen.
Du kan anpassa datumvisningsläget. Om du vill göra det väljer du den hierarki som ska användas och de nivåer som ska genereras:

![](assets/cube-date-dimension.png)

I vårt exempel vill vi bara visa år, månader och dagar. Observera att du inte kan arbeta med veckor och semestrar/månader samtidigt: dessa nivåer är inte kompatibla.

1. Skapa en annan dimension för att analysera data i förhållande till mottagarens ort. Lägg till en ny dimension och välj ort i dialogrutan **[!UICONTROL Location]** noden i mottagarschemat.

Du kan aktivera bindning för att göra det enklare att läsa information och länka värdena till en uppräkning.

Välj uppräkningen i listrutan. Observera att den här uppräkningen måste definieras som **[!UICONTROL Reserved for binning]**.

![](assets/cube-dimension-with-enum.png)

Endast värdena i uppräkningen visas. De andra grupperas under den etikett som definieras i **[!UICONTROL Label of the other values]** fält.

Mer information om detta finns i [det här avsnittet](customize-cubes.md#dynamically-manage-bins).

### Byggindikatorer {#build-indicators}

När dimensionerna har definierats anger du ett beräkningssätt för de värden som ska visas i cellerna.

För att göra detta skapar du indikatorerna i **[!UICONTROL Measures]** -fliken. Skapa så många mått som det finns kolumner att visa i rapporter baserade på den här kuben.

Följ stegen nedan för att skapa indikatorer:

1. Bläddra till **[!UICONTROL Measures]** och klicka på **[!UICONTROL Add]** -knappen.
1. Välj typ av mått och formel som ska användas. I det här exemplet räknar vi antalet kvinnor bland mottagarna. Vår åtgärd baseras på faktchemat och använder **[!UICONTROL Count]** -operator.

   ![](assets/cube-new-measure.png)

   Använd **[!UICONTROL Filter the measure data...]** länk till endast utvalda kvinnor. [Läs mer](customize-cubes.md#define-measures).

   ![](assets/cube-filter-measure-data.png)

1. Ange måttets etikett och spara det.

   ![](assets/cube-save-measure.png)

1. Spara kuben.


Nu kan du skapa en rapport baserad på den här kuben. [Läs mer](cube-tables.md).