---
product: campaign
title: Avancerade parametrar
description: Avancerade parametrar
feature: Workflows, Data Management
role: User, Admin
version: Campaign v8, Campaign Classic v7
exl-id: aafd977e-c8af-426b-904c-8388c9d8e595
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 1%

---

# Avancerade parametrar{#advanced-parameters}



Egenskapsskärmen för en aktivitet har en **[!UICONTROL Advanced]**-flik som gör att du kan definiera ett beteende vid fel, körningsperioden för aktiviteten och som gör att du kan ange ett initieringsskript. Det finns två versioner av den här fliken:

* en förenklad version (till exempel för **[!UICONTROL Start]** och **[!UICONTROL End]** aktiviteter)

  ![](assets/wf-advanced-basic.png)

* en mer detaljerad version (till exempel för aktiviteten **[!UICONTROL Query]**)

  ![](assets/wf-advanced-full.png)

Fälten som ska anges på fliken **[!UICONTROL Advanced]** beskrivs i följande avsnitt.

## Namn {#name}

Det här fältet innehåller aktivitetens interna namn.

## Bild {#image}

I det här fältet kan du ändra bilden som är länkad till en aktivitet. Mer information finns i [Ändra aktivitetsbilder](change-activity-images.md).

## Körning {#execution}

I det här fältet kan du definiera vilken åtgärd som ska utföras när aktiviteten aktiveras. Det finns tre möjliga alternativ:

De här alternativen är vanligtvis markerade i kundvagnen genom att högerklicka på aktiviteten.

* **[!UICONTROL Normal]**: aktiviteten körs som vanligt.
* **[!UICONTROL Do not activate]**: den här aktiviteten och alla följande aktiviteter (i samma gren) körs inte.
* **[!UICONTROL Activate but do not execute]**: den här aktiviteten och alla följande aktiviteter (i samma gren) stoppas automatiskt. Detta kan vara användbart om du vill vara där när aktiviteten startas. Om du vill utföra uppgiften manuellt högerklickar du på aktiviteten och väljer **[!UICONTROL Normal execution]**.

## Tillhörighet {#affinity}

Du kan välja att framtvinga körningen av ett arbetsflöde eller en arbetsflödesaktivitet på en viss dator. För att kunna göra detta måste du definiera en eller flera egenskaper på arbetsflödesnivå eller för den aktuella aktiviteten.


## Max. körningsperiod {#max--execution-period}

I det här fältet kan du ange en varning för när aktiviteten tar för lång tid. Det påverkar inte arbetsflödets funktion. Om uppgiften inte är slutförd innan **[!UICONTROL Max. execution period]** är klar visas en varning för det här arbetsflödet på sidan **[!UICONTROL Instance monitoring]**. Den här sidan nås via fliken **[!UICONTROL Monitoring]** på startsidan.

## Beteende {#behavior}

I det här fältet kan du definiera det beteende som ska användas för asynkrona uppgifter. Det finns två möjliga alternativ:

* **[!UICONTROL Several tasks authorized]**: flera åtgärder kan utföras samtidigt, även om den första inte har slutförts.
* **[!UICONTROL The current task has priority]**: pågående aktiviteter får prioritet. Så länge en uppgift pågår kommer ingen annan åtgärd att utföras.

## Tidszon {#time-zone}

I det här fältet kan du välja aktivitetens tidszon. Mer information om detta: [Hantera tidszoner](managing-time-zones.md).

## Om fel uppstår {#in-case-of-errors}

I det här fältet kan du definiera vilken åtgärd som ska utföras när aktiviteten innehåller fel. Det finns två möjliga alternativ:

* **[!UICONTROL Suspend the process]**: arbetsflödet stoppas automatiskt. Dess status ändras till **[!UICONTROL Failed]**. Starta om arbetsflödet när problemet är löst.
* **[!UICONTROL Ignore]**: den här aktiviteten och alla följande aktiviteter (i samma gren) körs inte. Detta kan vara användbart för återkommande uppgifter. Om grenen har en schemaläggare placerad uppströms startar den som vanligt på nästa körningsdatum.
* **[!UICONTROL Abort on error]**: arbetsflödet stoppas automatiskt och kan inte startas om. Dess status ändras till **[!UICONTROL Failed]**.

## Initieringsskript {#initialization-script}

I det här fältet kan du initiera variabler eller ändra aktivitetsegenskaper. Mer information finns i: [JavaScript-skript och mallar](javascript-scripts-and-templates.md).

## Kommentar {#comment}

Fältet **[!UICONTROL Comment]** är ett kostnadsfritt fält där du kan lägga till en beskrivning.
