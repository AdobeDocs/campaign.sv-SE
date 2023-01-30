---
product: campaign
title: Hantera tidszoner
description: Hantera tidszoner
feature: Workflows
exl-id: 04b7638d-55dd-4317-b605-5d618ef014ba
source-git-commit: 6464e1121b907f44db9c0c3add28b54486ecf834
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---

# Hantera tidszoner{#managing-time-zones}

Med Adobe Campaign kan du hantera tidsförskjutningar mellan olika länder som berörs av samma instans. Den använda konfigurationen konfigureras när instansen skapas.

I ett arbetsflöde kan du anpassa scheman för aktivitetskörning och länka en specifik tidszon till en aktivitet eller till hela arbetsflödet. Den här konfigurationen kan vara användbar vid import av filen eller inom ramen för leveransplanering.

## Körningsplanering {#execution-scheduling}

Du kan schemalägga körningen av uppgifter med hjälp av schemaläggaren (se [Schemaläggare](scheduler.md)). Du kan också använda de schemaläggningsalternativ som är tillgängliga i aktiviteterna som erbjuder den här funktionen. Dessa aktiviteter erbjuder **[!UICONTROL Schedule]** tab: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**, osv.

För alla schemalagda aktiviteter, dvs. alla aktiviteter med schemaläggningsalternativ, kan du välja vilken tidszon som ska användas. Tidszonen väljs via **[!UICONTROL Advanced]** flik för den berörda aktiviteten:

![](assets/wf-timezone-in-a-box.png)

Möjliga värden är:

* Tidszon för server

   Använder tidszonen för Adobe Campaign-programservern.

* Användarens tidszon

   Använder tidszonen för den Adobe Campaign-operator som kör arbetsflödet.

* Tidszon för databas

   Använder tidszonen för databasservern som används.

* Särskilda tidszoner

   Använder den markerade tidszonen.

Om **[!UICONTROL By default]** värdet är markerat används arbetsflödets tidszon eller, i annat fall, programserverns tidszon.

## Länka en tidszon till en aktivitet {#linking-a-time-zone-to-an-activity}

The **[!UICONTROL Advanced]** -fliken i arbetsflödesaktiviteterna där du kan välja dess tidszon. Även om arbetsflödenas tidszon för det mesta räcker, kan det vara nödvändigt att överlagra den om och om igen för en viss aktivitet, till exempel dataimport, för att länka datum till rätt tidszon.
