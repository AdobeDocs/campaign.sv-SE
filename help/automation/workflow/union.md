---
product: campaign
title: Sammanslutning
description: Läs mer om unionens arbetsflödesaktivitet
feature: Workflows, Targeting Activity
exl-id: 4109e198-bf9d-4dd2-92a1-16bbadbe30e8
source-git-commit: 77ec01aaba1e50676bed57f503a9e4e8bb1fe54c
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Sammanslutning{#union}

En **[!UICONTROL Union]** grupperar resultatet av flera inkommande aktiviteter i ett enda mål. Målet skapas med alla erhållna resultat: alla tidigare aktiviteter måste därför avslutas för att unionen ska kunna köras.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Mer information om hur du konfigurerar och använder aktiviteten **[!UICONTROL Union]** finns på [den här sidan](targeting-workflows.md#combining-several-targets--union-).

## Unionsexempel {#union-example}

I följande exempel har resultaten från två frågor kombinerats för att uppdatera listan. De två frågorna har mottagarna som mål. Resultaten är därför baserade på samma tabell.

1. Infoga en aktivitet av typen **[!UICONTROL Union]** direkt efter de två frågorna och före en aktivitet av typen update i listan, och öppna den sedan.
1. Du kan ange en etikett.
1. Välj avstämningsmetoden **[!UICONTROL Keys only]** eftersom populationen som är resultatet av frågor i det här exemplet innehåller konsekventa data.
1. Om du har lagt till ytterligare data för frågorna kan du bestämma dig för att behålla endast de data som delas.
1. Om du vill begränsa storleken på den slutliga fyllningen markerar du alternativet **[!UICONTROL Limit size of generated population]**.

   Ange det slutliga talet genom att ange det maximala antalet mottagare och genom att välja frågan vars population ska prioriteras.

1. Godkänn aktiviteten **[!UICONTROL Union]** och konfigurera aktiviteten [Listuppdatering](list-update.md).
1. Starta arbetsflödet. Antalet resultat visas och listan som definieras i listuppdateringsaktiviteten skapas eller uppdateras. Den här listan innehåller en uppsättning mottagare för båda frågorna eller, i tillämpliga fall, numret som definierades i föregående steg.

   ![](assets/union_example.png)

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar målet som uppstår från unionen. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna, **[!UICONTROL schema]** är schemat för populationen (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.
