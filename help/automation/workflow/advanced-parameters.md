---
product: campaign
title: Avancerade parametrar
description: Avancerade parametrar
feature: Workflows, Data Management
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 2%

---

# Avancerade parametrar{#advanced-parameters}



Egenskapsskärmen för en aktivitet har en **[!UICONTROL Advanced]** -flik som gör att du kan definiera ett beteende i händelse av fel, körningsperioden för aktiviteten; och gör att du kan ange ett initieringsskript. Det finns två versioner av den här fliken:

* en förenklad version (för **[!UICONTROL Start]** och **[!UICONTROL End]** aktiviteter, till exempel)

   ![](assets/wf-advanced-basic.png)

* en mer detaljerad version (för **[!UICONTROL Query]** -aktivitet, till exempel)

   ![](assets/wf-advanced-full.png)

Fälten som ska anges i **[!UICONTROL Advanced]** -fliken beskrivs i följande avsnitt.

## Namn {#name}

Det här fältet innehåller aktivitetens interna namn.

## Bild {#image}

I det här fältet kan du ändra bilden som är länkad till en aktivitet. Mer information finns i [Ändra aktivitetsbilder](change-activity-images.md).

## Körning {#execution}

I det här fältet kan du definiera vilken åtgärd som ska utföras när aktiviteten aktiveras. Det finns tre möjliga alternativ:

De här alternativen är vanligtvis markerade i kundvagnen genom att högerklicka på aktiviteten.

* **[!UICONTROL Normal]**: aktiviteten utförs som vanligt.
* **[!UICONTROL Do not activate]**: den här aktiviteten och alla följande uppgifter (i samma gren) körs inte.
* **[!UICONTROL Activate but do not execute]**: den här aktiviteten och alla följande uppgifter (i samma gren) stoppas automatiskt. Detta kan vara användbart om du vill vara där när aktiviteten startas. Om du vill utföra åtgärden manuellt högerklickar du på aktiviteten och väljer **[!UICONTROL Normal execution]**.

## Tillhörighet {#affinity}

Du kan välja att framtvinga körningen av ett arbetsflöde eller en arbetsflödesaktivitet på en viss dator. För att kunna göra detta måste du definiera en eller flera egenskaper på arbetsflödesnivå eller för den aktuella aktiviteten.

Arbetsflödeskonfigurationen för hög tillgänglighet beskrivs här.


## Max. körningsperiod {#max--execution-period}

I det här fältet kan du ange en varning för när aktiviteten tar för lång tid. Det påverkar inte arbetsflödets funktion. Om uppgiften inte är slutförd innan **[!UICONTROL Max. execution period]** är över, **[!UICONTROL Instance monitoring]** visas en varning för det här arbetsflödet. Den här sidan öppnas via **[!UICONTROL Monitoring]** hemsidans flik.

## Beteende {#behavior}

I det här fältet kan du definiera det beteende som ska användas för asynkrona uppgifter. Det finns två möjliga alternativ:

* **[!UICONTROL Several tasks authorized]**: flera åtgärder kan utföras samtidigt, även om den första inte är klar.
* **[!UICONTROL The current task has priority]**: pågående uppgifter får prioritet. Så länge en uppgift pågår kommer ingen annan åtgärd att utföras.

## Tidszon {#time-zone}

I det här fältet kan du välja aktivitetens tidszon. Mer information: [Hantera tidszoner](managing-time-zones.md).

## Vid fel {#in-case-of-errors}

I det här fältet kan du definiera vilken åtgärd som ska utföras när aktiviteten innehåller fel. Det finns två möjliga alternativ:

* **[!UICONTROL Suspend the process]**: arbetsflödet stoppas automatiskt. Dess status ändras till **[!UICONTROL Failed]**. Starta om arbetsflödet när problemet är löst.
* **[!UICONTROL Ignore]**: den här aktiviteten och alla följande åtgärder (i samma gren) körs inte. Detta kan vara användbart för återkommande uppgifter. Om grenen har en schemaläggare placerad uppströms startar den som vanligt på nästa körningsdatum.
* **[!UICONTROL Abort on error]**: arbetsflödet stoppas automatiskt och kan inte startas om. Dess status ändras till **[!UICONTROL Failed]**.

## Initieringsskript {#initialization-script}

I det här fältet kan du initiera variabler eller ändra aktivitetsegenskaper. Mer information finns i: [JavaScript-skript och -mallar](javascript-scripts-and-templates.md).

## Kommentar {#comment}

The **[!UICONTROL Comment]** -fältet är ett kostnadsfritt fält där du kan lägga till en beskrivning.
