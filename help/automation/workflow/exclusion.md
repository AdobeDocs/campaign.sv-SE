---
product: campaign
title: Uteslutning
description: Läs mer om arbetsflödesaktiviteten Uteslutning
feature: Workflows, Targeting Activity
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Uteslutning{#exclusion}



An **Uteslutning** aktivitet av typen -skapar ett mål baserat på ett huvudmål som ett eller flera andra mål extraheras från.

Om du vill konfigurera den här aktiviteten anger du dess etikett och väljer huvudmottagaruppsättningen: kan du skapa resultatet med hjälp av populationen från huvuduppsättningen. Profiler som delas av huvuduppsättningen och minst en av tävlingsaktiviteterna kommer att uteslutas.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Mer information om hur du konfigurerar och använder exkluderingsaktiviteten finns i [Utesluta en population (Uteslutning)](targeting-workflows.md#excluding-a-population--exclusion-).

Kontrollera **[!UICONTROL Generate complement]** om du vill utnyttja den återstående populationen. Komplementet kommer att innehålla den huvudsakliga inkommande populationen minus den utgående populationen. En ytterligare övergång till utdata läggs sedan till i aktiviteten enligt följande:

![](assets/s_user_segmentation_exclu_compl.png)

## Exempel på undantag {#exclusion-examples}

Följande exempel söker efter en lista över mottagare i åldrarna 18 till 30 år, med undantag för personer bosatta i Paris.

1. Infoga och öppna en **[!UICONTROL Exclusion]** Aktivitet av typen -efter två frågor. Den första frågan riktar sig till mottagare som bor i Paris. Den andra frågan riktar sig till 18 till 30 år.
1. Ange huvuduppsättningen. Här är huvudscenen **18-30 år** fråga. Element som hör till den andra uppsättningen tas inte med i slutresultatet.
1. Kontrollera **[!UICONTROL Generate complement]** om du vill utnyttja de data som återstår efter uteslutningen. I detta fall består komplementet av mottagare i åldrarna 18 till 30 år som bor i Paris.
1. Godkänn undantagskonfigurationen och infoga sedan en uppdateringslistaktivitet i resultatet. Du kan också infoga ytterligare en listuppdatering till komplementet där det behövs.
1. Kör arbetsflödet. I det här exemplet består resultatet av mottagare mellan 18 och 30 år, men de som bor i Paris utesluts och skickas till komplementet.

   ![](assets/exclusion_example.png)

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som är resultatet av uteslutningen. **[!UICONTROL tableName]** är namnet på den tabell som registrerar målidentifierarna, **[!UICONTROL schema]** är schemat för populationen (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Övergången som är associerad med komplementet har samma parametrar.
