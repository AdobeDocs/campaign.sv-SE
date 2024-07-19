---
product: campaign
title: Arbetsflödets livscykel
description: Läs mer om arbetsflödets livscykel
feature: Workflows
exl-id: 4356b90c-9d7c-49ef-88cd-716b2ccdb7f0
source-git-commit: 7f6c394f56d517c0a675e0fd2341bb6ef98044f0
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 2%

---

# Arbetsflödets livscykel {#workflow-life-cycle}



Arbetsflödescykeln består av tre huvudsteg.

* **Redigeras**

  Detta är den inledande designfasen: När ett nytt arbetsflöde skapas är dess status&quot;Redigeras&quot;. Arbetsflödet hanteras ännu inte av servern och kan ändras utan risk.

* **Startades**

  När den inledande designfasen är klar kan arbetsflödet startas. I den här fasen hanteras instansen av servern och de enskilda åtgärderna körs. Arbetsflödet kan fortfarande ändras med vissa försiktighetsåtgärder.

* **Slutförd**

  Ett arbetsflöde är&quot;Slutfört&quot; när det inte längre finns några pågående uppgifter eller när en operator uttryckligen har stoppat instansen.

Aktiviteterna **Start** och **Delivery** beskrivs exempelvis medan aktiviteten **Approval** blinkar i arbetsflödet nedan.

![](assets/new-workflow-6.png)

Detta innebär att de två första aktiviteterna har slutförts och att godkännande pågår, dvs. det har skapats men ännu inte slutförts.

Tecknen **574 -OK** som visas ovanför övergången efter aktiviteten **Leverans** innebär att leveransförberedelsen har 574 mottagare som mål och att åtgärden har slutförts. Den här informationen, som läggs till i övergångarna när de körs, beräknas av aktiviteterna som bearbetar data.

Arbetsflödet har startats och väntar på att en operator som tillhör gruppen som anges i aktiviteten **Approval** ska fatta ett beslut. Operatorer som tillhör gruppen och som har en e-postadress eller ett mobilnummer meddelas.

Mer information om hur du övervakar arbetsflöden finns i [det här avsnittet](monitor-workflow-execution.md).
