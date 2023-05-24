---
product: campaign
title: Sammanslutning
description: Läs mer om unionens arbetsflödesaktivitet
feature: Workflows, Targeting Activity
exl-id: 4109e198-bf9d-4dd2-92a1-16bbadbe30e8
source-git-commit: 77ec01aaba1e50676bed57f503a9e4e8bb1fe54c
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 1%

---

# Sammanslutning{#union}

A **[!UICONTROL Union]** grupperar resultatet av flera inkommande aktiviteter i ett enda mål. Målet skapas med alla mottagna resultat: Alla tidigare aktiviteter måste därför avslutas för att unionen ska kunna genomföras.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Mer information om hur du konfigurerar och använder **[!UICONTROL Union]** aktivitet, se [den här sidan](targeting-workflows.md#combining-several-targets--union-).

## Unionsexempel {#union-example}

I följande exempel har resultaten från två frågor kombinerats för att uppdatera listan. De två frågorna har mottagarna som mål. Resultaten är därför baserade på samma tabell.

1. Infoga en **[!UICONTROL Union]** -type-aktivitet direkt efter de två frågorna och innan en aktivitet av typen update i listan startar du den.
1. Du kan ange en etikett.
1. Välj **[!UICONTROL Keys only]** avstämningsmetod eftersom populationen som är ett resultat av frågor i det här exemplet innehåller konsekventa data.
1. Om du har lagt till ytterligare data för frågorna kan du bestämma dig för att bara behålla de data som delas.
1. Om du vill begränsa storleken på den slutliga populationen kontrollerar du **[!UICONTROL Limit size of generated population]** alternativ.

   Ange det slutliga talet genom att ange det maximala antalet mottagare och genom att välja frågan vars population ska prioriteras.

1. Godkänn **[!UICONTROL Union]** aktiviteten och konfigurera sedan [Listuppdatering](list-update.md) aktivitet.
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

Den här uppsättningen med tre värden identifierar målet som uppstår från unionen. **[!UICONTROL tableName]** är namnet på den tabell som registrerar målidentifierarna, **[!UICONTROL schema]** är schemat för populationen (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.
