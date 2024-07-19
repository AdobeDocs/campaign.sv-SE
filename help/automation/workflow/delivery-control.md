---
product: campaign
title: Leveranskontroll
description: Läs mer om arbetsflödesaktiviteten Leveranskontroll
feature: Workflows
role: User
exl-id: 09fe638d-5e1c-49d1-9196-6300c1e56703
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---

# Leveranskontroll{#delivery-control}



Med en åtgärd av typen **Leveranskontroll** kan du starta, pausa eller stoppa en leverans.

Detta kan vara den leverans som anges i övergången, en leverans som valts uttryckligen eller en leverans som beräknas av ett skript. Mer information finns i [Leverans](delivery.md).

![](assets/edit_diffusion_act.png)

Om du väljer **[!UICONTROL Start]** utför aktiviteten alla steg som krävs för att starta leveransen (målberäkning, förberedelse av innehåll, leverans). Om några av dessa steg redan har utförts av en tidigare arbetsflödesaktivitet, kommer de inte att utföras igen. Om måluppskattningen till exempel redan har utförts av en aktivitet av typen **[!UICONTROL Delivery]** (se [Leverans](delivery.md)), startar aktiviteten **[!UICONTROL Act on the delivery]** de återstående stegen (förberedelse och leverans av innehåll).

Följande alternativ är tillgängliga:

* **[!UICONTROL Generate an outbound transition]**

  Skapar en utgående övergång som ska aktiveras i slutet av körningen. Du kan välja om du vill hämta målet för den utgående leveransen eller inte.

* **[!UICONTROL Processing errors]**

  Se [Bearbetningsfel](monitor-workflow-execution.md#processing-errors).

## Indataparametrar {#input-parameters}

* deliveryId

Leverans-ID, om den valda åtgärden är **[!UICONTROL Specified in the transition]**.
