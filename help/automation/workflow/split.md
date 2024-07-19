---
product: campaign
title: Dela
description: Läs mer om aktiviteten Dela arbetsflöde
feature: Workflows, Targeting Activity
exl-id: bf4935dd-87dc-4c5c-becf-8c4df61805fd
source-git-commit: a5d44321c3d68b9370cfb6e9b1df62435de0dbda
workflow-type: tm+mt
source-wordcount: '1832'
ht-degree: 0%

---

# Dela{#split}

Med en aktivitet av typen **Delad** kan du dela upp ett mål i flera deluppsättningar. Målet har konstruerats med alla mottagna resultat: alla tidigare aktiviteter måste därför ha avslutats för att den här aktiviteten ska kunna utföras.

Denna aktivitet utlöser inte någon union av inkommande populationer. Om flera övergångar markeras i en delad aktivitet rekommenderar vi att du infogar en **[!UICONTROL Union]**-aktivitet framför den.

>[!NOTE]
>
>Det går inte att utföra delade åtgärder för tabeller som har olika källor. Därför måste du lägga till en **berikning**-aktivitet före aktiviteten **Dela**.

* Ett exempel på den delade aktivitet som används finns i [det här avsnittet](targeting-workflows.md#create-subsets-using-the-split-activity).
* Ett exempel som illustrerar hur du använder den delade aktiviteten för att segmentera målet i olika populationer med filtervillkor beskrivs i [det här avsnittet](cross-channel-delivery-workflow.md).
* Ett exempel som visar hur du använder en instansvariabel i en delad aktivitet finns i [det här avsnittet](javascript-scripts-and-templates.md).

Om du vill konfigurera den här aktiviteten definierar du delmängdens innehåll och etikett på fliken **[!UICONTROL Subsets]** och väljer sedan måldimensionen på fliken **[!UICONTROL General]**.

## Skapa delmängder {#create-subsets}

Så här skapar du en delmängd:

1. Klicka på etiketten i det matchande fältet och välj det filter som ska användas.
1. Om du vill filtrera den inkommande populationen väljer du alternativet **[!UICONTROL Add a filtering condition]** och klickar på länken **[!UICONTROL Edit...]**.

   Välj vilken typ av filter som ska användas på data som ska inkluderas i uppsättningen.

   Processen är densamma som för en aktivitet av typen **Query**.

   >[!NOTE]
   >
   >Du kan filtrera data i högst två externa databaser (FDA).

1. Du kan ange maximalt antal poster som ska extraheras från målet för att skapa delmängden. Det gör du genom att markera alternativet **[!UICONTROL Limit the selected records]** och klicka på länken **[!UICONTROL Edit...]**.

   Med en guide kan du välja valläge för poster i den här delmängden. [Läs mer](#limit-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. Om du vill kan du **lägga till andra delmängder** med knappen **[!UICONTROL Add]**.

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >Om alternativet **[!UICONTROL Enable overlapping of output populations]** inte är markerat skapas delmängder i tabbordningen. Använd pilarna i fönstrets övre högra del för att flytta dem. Om den första delmängden återställer 70 % av den ursprungliga populationen kommer nästa delmängd endast att tillämpa sina urvalskriterier på de återstående 30 % och så vidare.

   För varje delmängd som skapas läggs en utgående övergång till i den delade aktiviteten.

   ![](assets/s_user_segmentation_partage_add2.png)

   Du kan välja att generera en enskild utgående övergång (och identifiera uppsättningar med exempelvis segmentkoden): om du vill göra det väljer du alternativet **[!UICONTROL Generate subsets in the same table]** på fliken **[!UICONTROL General]**.

   Om den är klar sparas segmentkoden för varje delmängd automatiskt i en extra kolumn. Den här kolumnen är tillgänglig i personaliseringsfälten på leveransnivå.

## Begränsa antalet delmängdsposter {#limit-the-number-of-subset-records}

Om du inte vill använda hela populationen i en delmängd kan du begränsa antalet poster som den ska innehålla.

1. Markera alternativet **[!UICONTROL Limit the selected records]** i redigeringsfönstret för delmängd och klicka på länken **[!UICONTROL Edit...]**.
1. Välj gränstyp för ditt val:

   * **[!UICONTROL Activate random sampling]**: Det här alternativet tar ett slumpmässigt urval av posterna. Vilken typ av slumpmässigt urval som används beror på databasmotorn.
   * **[!UICONTROL Keep only the first records after sorting]**: Med det här alternativet kan du definiera en begränsning baserat på en eller flera sorteringsordningar. Om du väljer fältet **[!UICONTROL Age]** som sorteringsvillkor och 100 som gräns behålls endast de yngsta 100 mottagarna.
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**: Det här alternativet kombinerar de två föregående alternativen. Du kan definiera en begränsning baserat på en eller flera sorteringsordningar och sedan göra ett slumpmässigt urval på de första posterna om vissa poster har samma värden som de definierade villkoren.

     Om du t.ex. väljer fältet **[!UICONTROL Age]** som sorteringsvillkor och sedan definierar en gräns på 100, men de 2 000 yngsta mottagarna i databasen är alla 18, kommer 100 mottagare att väljas slumpmässigt bland dessa 2 000.

   ![](assets/s_user_segmentation_partage_wz1.png)

1. Om du vill definiera sorteringsvillkor kan du definiera kolumnerna och sorteringsordningen med ett extra steg.

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. Välj sedan metoden för databegränsning.

   ![](assets/s_user_segmentation_partage_wz2.png)

   Det finns flera sätt att göra detta:

   * **[!UICONTROL Size (in %)]**: en procentandel poster. Till exempel extraherar konfigurationen nedan 10 % av den totala populationen.

     Procentandelen gäller den inledande populationen, inte resultatet av aktiviteten.

   * **[!UICONTROL Size (as a % of the segment)]**: en procentandel av posterna som endast relaterar till deluppsättningarna och inte till den ursprungliga populationen.
   * **[!UICONTROL Maximum size]**: maximalt antal poster.
   * **[!UICONTROL By data grouping]**: Du kan ange en gräns för antalet poster beroende på värdena i ett angivet fält i den inkommande populationen. [Läs mer](#limit-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data grouping (in %)]**: Du kan ange en gräns för antalet poster beroende på värdena i ett angivet fält i den inkommande populationen med en procentandel. [Läs mer](#limit-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data distribution]**: Om grupperingsfälten har för många värden eller om du inte vill ange värden igen för varje ny delad aktivitet, kan du konfigurera en **[!UICONTROL By data distribution]**-begränsning (valfri modul för distribuerad marknadsföring) i Adobe Campaign. [Läs mer](#limit-the-number-of-subset-records-per-data-distribution).

1. Klicka på **[!UICONTROL Finish]** för att godkänna urvalskriterierna för posten. Den definierade konfigurationen visas sedan i redigerarens mittersta fönster.

## Begränsa antalet delmängdsposter per datagrupp {#limit-the-number-of-subset-records-by-data-grouping}

Du kan begränsa antalet poster per datagrupp. Denna gräns kan göras med hjälp av ett fast värde eller en procentsats.

Om du till exempel väljer fältet **[!UICONTROL Language]** som ett gruppfält kan du definiera en lista med poster för varje språk.

1. Välj **[!UICONTROL By data grouping]** eller **[!UICONTROL By data grouping (as a %)]** och klicka sedan på **[!UICONTROL Next]** när du har valt datagränsvärdena.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. Markera sedan grupperingsfälten (till exempel fältet **[!UICONTROL Language]**) och klicka på **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. Slutligen anger du tröskelvärden för datagruppering (med hjälp av fasta värden eller procentandelar beroende på den tidigare valda grupperingsmetoden). Om du vill ange samma tröskelvärde för varje värde, till exempel om du vill ange antalet poster för varje språk till 10, väljer du alternativet **[!UICONTROL All data groupings are the same size]**. Om du vill ange en annan gräns för varje värde väljer du alternativet **[!UICONTROL Limitations by grouping value]**. Då kan du välja en annan begränsning för engelska, franska och så vidare.

   ![](assets/s_user_segmentation_partage_wz5.png)

1. Klicka på **[!UICONTROL Finish]** för att godkänna begränsningen och återgå till att redigera delningsaktiviteten.

## Begränsa antalet delmängdsposter per datadistribution {#limit-the-number-of-subset-records-per-data-distribution}

Om grupperingsfälten innehåller för många värden eller om du vill undvika att återställa värden för varje ny delad aktivitet, kan du skapa en begränsning per datadistribution i Adobe Campaign. När du väljer [datagränsvärden](#create-subsets)) väljer du alternativet **[!UICONTROL By data distribution]** och väljer en mall i listrutan. Nedan visas hur du skapar en mall för datadistribution.

Ett exempel på **[!UICONTROL Local approval]**-aktiviteten med en distributionsmall finns på [den här sidan](local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!CAUTION]
>
>Den här funktionen är bara tillgänglig med [tillägget Distributed Marketing](../distributed-marketing/about-distributed-marketing.md). Kontrollera licensavtalet.

Med mallen för datadistribution kan du begränsa antalet poster med hjälp av en lista med grupperingsvärden. Så här skapar du en mall för datadistribution:

1. Om du vill skapa en mall för datadistribution går du till noden **[!UICONTROL Resources > Campaign management > Data distribution]** och klickar på **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. På fliken **[!UICONTROL General]** kan du ange etiketten och körningskontexten för distributionen (måldimension, distributionsfält).

   ![](assets/local_validation_data_distribution_2.png)

   Följande fält måste anges:

   * **[!UICONTROL Label]**: etikett för distributionsmallen.
   * **[!UICONTROL Targeting dimension]**: Ange måldimensionen som datadistributionen ska tillämpas på, till exempel **[!UICONTROL Recipient]**. Det här schemat måste alltid vara kompatibelt med de data som används i målarbetsflödet.
   * **[!UICONTROL Distribution field]**: välj ett fält via måldimensionen. Om du till exempel markerar fältet **[!UICONTROL Email domain]** kommer listan över mottagare att delas upp efter domän.
   * **[!UICONTROL Distribution type]**: välj hur målets begränsningsvärde ska brytas ned på fliken **[!UICONTROL Distribution]**: **[!UICONTROL Percentage]** eller **[!UICONTROL Set]**.
   * **[!UICONTROL Approval storage]**: Om du använder en [lokal godkännandeaktivitet](local-approval.md) i målarbetsflödet anger du det schema som godkännanderesultaten ska lagras i. Du måste ange ett lagringsschema per målschema. Om du använder **[!UICONTROL Recipients]**-målschemat anger du standardlagringsschemat för **[!UICONTROL Local approval of recipients]**.

     Om det finns en enkel begränsning per datagrupp utan lokalt godkännande behöver du inte ange fältet **[!UICONTROL Approvals storage]**.

1. Om du använder en [lokal godkännandeaktivitet](local-approval.md) anger du **[!UICONTROL Advanced settings]** för distributionsmallen:

   ![](assets/local_validation_data_distribution_3.png)

   Följande fält måste anges:

   * **[!UICONTROL Approve targeted messages]**: Markera det här alternativet om du vill att alla mottagare ska vara förmarkerade i listan över mottagare som ska godkännas. Om alternativet inte är markerat markeras ingen mottagare i förväg.

     >[!NOTE]
     >
     >Det här alternativet är markerat som standard.

     ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**: gör att du kan definiera ett uttryck som visar leveransetiketten i returmeddelandet. Standarduttrycket innehåller information om leveransens standardetikett (beräkningssträng). Du kan ändra det här uttrycket.

     ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**: I det här fältet kan du definiera den gruppering som används för att visa mottagare i godkännande- och returmeddelanden.

     ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**: gör att du kan länka ett webbprogram till mottagarlistan. I meddelandet för godkännande och retur kan varje mottagare klickas och länkas till det valda webbprogrammet. I fältet **[!UICONTROL Parameters]** (till exempel **[!UICONTROL recipientId]**) kan du konfigurera den extra parametern som ska användas i URL:en och webbprogrammet.

1. På fliken **[!UICONTROL Breakdown]** kan du definiera listan med distributionsvärden.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**: Ange distributionsvärdena.
   * **[!UICONTROL Percentage / Set]**: Ange postgränsen (fast eller i procent) som är länkad till varje värde.

     Den här kolumnen definieras av fältet **[!UICONTROL Distribution type]** på fliken **[!UICONTROL General]**.

   * **[!UICONTROL Label]**: Ange den etikett som är länkad till varje värde.
   * **[!UICONTROL Group or operator]**: Om du använder en [}lokal godkännanderutaktivitet](local-approval.md) väljer du den operator eller grupp av operatorer som tilldelats varje distributionsvärde.

     Om det finns en enkel begränsning per datagrupp utan lokalt godkännande behöver du inte ange fältet **[!UICONTROL Group or operator]**.

     >[!CAUTION]
     >
     >Kontrollera att operatorerna har tilldelats rätt behörigheter.

## Filtreringsparametrar {#filtering-parameters}

Klicka på fliken **[!UICONTROL General]** för att ange aktivitetsetiketten. Välj mål- och filterdimensionerna för den här delningen. Om det behövs kan du ändra de här dimensionerna för en viss delmängd.

![](assets/s_user_segmentation_partage_general.png)

Markera alternativet **[!UICONTROL Generate complement]** om du vill utnyttja den återstående populationen. Komplementet är det inkommande målet minus kombinationen av delmängderna. En ytterligare utgående övergång läggs sedan till i aktiviteten enligt följande:

![](assets/s_user_segmentation_partage_compl.png)

För att det här alternativet ska fungera på rätt sätt måste inkommande data ha en primärnyckel.

Om data till exempel läses direkt från en extern databas som Netezza (som inte stöder begreppet index) via en **[!UICONTROL Data loading (RDBMS)]**-aktivitet, blir komplementet som skapas av **[!UICONTROL Split]**-aktiviteten felaktigt.

Du kan undvika detta genom att dra och släppa en **[!UICONTROL Enrichment]**-aktivitet precis före **[!UICONTROL Split]**-aktiviteten. I aktiviteten **[!UICONTROL Enrichment]** kontrollerar du **[!UICONTROL Keep all additional data from the main set]** och anger de kolumner som du vill använda för att konfigurera filtren för aktiviteten **[!UICONTROL Split]** i de extra data. Data från den inkommande övergången för aktiviteten **[!UICONTROL Split]** lagras sedan lokalt i en temporär tabell på Adobe Campaign-servern och komplementet kan genereras korrekt.

Med alternativet **[!UICONTROL Enable overlapping of output populations]** kan du hantera populationer som tillhör flera delmängder:

* När rutan inte är markerad ser delningsaktiviteten till att en mottagare inte kan finnas i flera utdataövergångar, även om den uppfyller villkoren för flera delmängder. De kommer att vara i målet för den första fliken med matchande villkor.
* När rutan är markerad kan mottagarna hittas i flera delmängder om de uppfyller filtervillkoren. Adobe Campaign rekommenderar att man använder exklusiva kriterier.

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som är resultatet av uteslutningen. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna, **[!UICONTROL schema]** är schemat för populationen (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Övergången som är associerad med komplementet har samma parametrar.
