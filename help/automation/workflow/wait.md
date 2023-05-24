---
product: campaign
title: Vänta
description: Läs mer om aktiviteten Vänta i arbetsflödet
feature: Workflows
exl-id: a9bcb214-5c87-4b26-804a-22b868905022
source-git-commit: 77ec01aaba1e50676bed57f503a9e4e8bb1fe54c
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# Vänta{#wait}



A **Vänta** Aktiviteten aktiverar övergången efter en tidsfördröjning på var som helst mellan några sekunder och flera månader. En vänteuppgift blockerar inte utförandet av andra uppgifter. arbetsflödet kan köra uppgifter parallellt medan den här uppgiften väntar.

Du kan ange etiketten och vänta med redigeraren, som i exemplet nedan:

![](assets/edit_wait.png)

I **[!UICONTROL Duration]** kan värdet uttryckas i valfri enhet: (enligt operatörens regionala inställningar):

* Om nationella inställningar inte anges: **s** i sekunder, **m** i minuter, **h** i timmar, **d** i dagar, **y** i åratal. Vid tidpunkten för godkännandet konverteras värdet automatiskt till den mest läsbara enheten.

   Standardenheten är dagen (**d**).

* Om de regionala inställningarna till exempel är inställda på &quot;Français&quot;: **s** i sekunder, **mn** i minuter, **h** i timmar, **j** i dagar, **m** för månader, **a** i åratal. Vid tidpunkten för godkännandet konverteras värdet automatiskt till den mest läsbara enheten, som i exemplet ovan **90s** konverterades till **1mn 30s**.

   Standardenheten är dagen (**d**).
