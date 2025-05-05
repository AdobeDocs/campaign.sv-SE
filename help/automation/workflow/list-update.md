---
product: campaign
title: Listuppdatering
description: Listuppdatering
feature: Workflows, Targeting Activity
role: User
exl-id: abb7f777-0b4a-4bf2-bcb6-32264f340a58
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---

# Listuppdatering{#list-update}



En **listuppdateringsaktivitet** lagrar populationen som anges i övergången i en lista över mottagare.

![](assets/s_user_segmentation_update_group.png)

Listan kan väljas från listan med befintliga grupper.

Den kan också skapas med alternativen **[!UICONTROL Create the list if necessary (Computed name)]** och **[!UICONTROL Create the list if necessary (Computed Folder and Name)]**. Med de här alternativen kan du välja vilken etikett du vill använda för att skapa en lista, och senare den mapp som listan ska sparas i. Etiketten kan också genereras automatiskt genom att dynamiska fält eller skript infogas. De olika dynamiska fälten är tillgängliga på snabbmenyn till höger om etiketten.

![](assets/s_user_segmentation_update_list_calc.png)

Om listan redan finns läggs mottagarna till i det befintliga innehållet, såvida du inte markerar alternativet **[!UICONTROL Purge the list if it exists (otherwise add to the list)]**. I det här fallet tas innehållet i listan bort före uppdateringen.

Om du vill att den skapade eller uppdaterade listan ska använda en annan tabell än mottagartabellen markerar du alternativet **[!UICONTROL Create or use a list with its own table]**.

Om du vill använda alternativet måste de specifika tabellerna i fråga ha konfigurerats i din Adobe Campaign-instans.

Om du sparar ett mål i en lista markeras i allmänhet slutet av ett arbetsflöde. Som standard har aktiviteten **[!UICONTROL List update]** därför ingen utgående övergång. Markera alternativet **[!UICONTROL Generate an outbound transition]** om du vill lägga till ett.

![](assets/do-not-localize/how-to-video.png) [Upptäck hur du skapar en lista med mottagare från Utforskaren i en video](#video)

## Exempel: Listuppdatering {#example--list-update}

I följande exempel följer listuppdateringsaktiviteten en fråga som riktar sig till män över 30 som bor i Frankrike. Listan skapas från resultatet av frågan. Den uppdateras sedan varje gång den startas från arbetsflödet. Det kan till exempel användas regelbundet för riktade kampanjerbjudanden.

1. Lägg till en **[!UICONTROL list update activity]** direkt efter en fråga och öppna den sedan för att redigera den.

   Mer information om hur du skapar en fråga i ett arbetsflöde finns i [Fråga](query.md).

1. Du kan välja en etikett för aktiviteten.
1. Välj alternativet **[!UICONTROL Create the list if necessary (Calculated name)]** om du vill visa att listan skapas när det första arbetsflödet har körts och sedan uppdateras med följande körningar.
1. Välj den mapp där du vill spara listan.
1. Ange en etikett för listan. Du kan infoga dynamiska fält för att automatiskt generera namnet från listan. I det här exemplet har listan samma namn som frågan för att enkelt identifiera innehållet.
1. Låt alternativet **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** vara markerat om du vill ta bort mottagare som inte matchar målinriktningsvillkoret och infoga de nya i listan.
1. Låt även alternativet **[!UICONTROL Create or use a list with its own table]** vara markerat.
1. Låt alternativet **[!UICONTROL Generate an outbound transition]** vara avmarkerat.
1. Klicka på **[!UICONTROL Ok]** och starta arbetsflödet.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   Listan med matchande mottagare skapas eller uppdateras.

## Indataparametrar {#input-parameters}

* tableName
* schema

Identifierar populationen som ska sparas i gruppen.

## Utdataparametrar {#output-parameters}

* groupId: Gruppidentifierare.

## Självstudievideo {#video}

I den här videon visas hur du skapar en lista med mottagare från Utforskaren.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

Det finns ytterligare utbildningsvideor för Campaign [här](https://experienceleague.adobe.com/docs/campaign-learn/tutorials/getting-started/introduction-to-adobe-campaign.html?lang=sv-SE){target="_blank"}.