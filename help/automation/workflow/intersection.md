---
product: campaign
title: Skärningspunkt
description: Skärningspunkt
feature: Workflows, Targeting Activity
role: User
exl-id: 12777107-5ccc-4f19-9dcd-8f6cade3ee98
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Skärningspunkt{#intersection}



An **Skärningspunkt** Aktivitet av typen -typ skapar ett mål från skärningspunkten för de mottagna målen.

Med en skärningspunkt kan du bara extrahera den population som är gemensam för alla inkommande aktivitetsresultat. Målet skapas med alla mottagna resultat: alla tidigare aktiviteter måste därför avslutas innan skärningspunkten kan utföras. Om du vill konfigurera den här aktiviteten måste du ange en etikett för den samt alternativ för resultatet.

![](assets/s_user_segmentation_inter.png)

Mer information om hur du konfigurerar och använder skärningsaktiviteten finns i [Extrahera leddata (skärning)](targeting-workflows.md#extracting-joint-data--intersection-).

Kontrollera **[!UICONTROL Generate complement]** om du vill bearbeta den återstående populationen. Komplementet ska innehålla en kombination av resultaten av alla inkommande aktiviteter minus skärningspunkten. En ytterligare utgående övergång läggs sedan till i aktiviteten enligt följande:

![](assets/s_user_segmentation_inter_compl.png)

## Exempel på skärning {#intersection-example}

I följande exempel är syftet med skärningen att beräkna mottagarna som är gemensamma för tre enkla frågor för att skapa en lista.

1. Efter tre enkla frågor infogar du en **[!UICONTROL Intersection]** -type-aktivitet.

   I det här exemplet är frågorna avsedda för män, mottagare i Paris och mottagare mellan 18 och 30 år.

1. Konfigurera skärningspunkten. Om du vill göra det väljer du **[!UICONTROL Keys only]** avstämningsmetod eftersom populationerna som är ett resultat av frågorna innehåller konsekventa data.
1. Om du har angett ytterligare data för frågorna kan du välja att behålla endast de som är delade av mottagarna genom att markera den relevanta rutan.
1. Om du vill använda resten av data (vad gäller frågorna men inte deras skärningspunkt), ska du kontrollera **[!UICONTROL Generate complement]** box.
1. Lägg till en aktivitet för listuppdatering efter skärningsresultatet. Du kan också lägga till en listuppdatering till komplementet om du vill använda den här också.
1. Kör arbetsflödet. Här gäller två mottagare för alla tre inmatade frågor samtidigt. Komplementet består av fem mottagare som endast tillämpar en eller två av de tre frågorna.

   Resultatet av överlappningen skickas till den första listuppdateringen. Om du har valt att använda komplementet skickas det också till den andra listuppdateringen.

   ![](assets/intersection_example.png)

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som uppstår från skärningen. **[!UICONTROL tableName]** är namnet på den tabell som registrerar målidentifierarna, **[!UICONTROL schema]** är populationens schema (vanligtvis **[!UICONTROL nms:recipient]**) och **[!UICONTROL recCount]** är antalet element i tabellen.
