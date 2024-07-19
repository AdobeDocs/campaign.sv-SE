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



En **Wait**-aktivitet aktiverar övergången efter en tidsfördröjning på mellan några sekunder och flera månader. En vänteuppgift blockerar inte körningen av andra uppgifter. Arbetsflödet kan köra uppgifter parallellt medan den här uppgiften väntar.

Du kan ange etiketten och vänta med redigeraren, som i exemplet nedan:

![](assets/edit_wait.png)

I fältet **[!UICONTROL Duration]** kan värdet uttryckas i valfri enhet: (enligt operatorns nationella inställningar):

* Om nationella inställningar inte anges: **s** för sekunder, **m** för minuter, **h** för timmar, **d** för dagar, **y** för år. Vid tidpunkten för godkännandet konverteras värdet automatiskt till den mest läsbara enheten.

  Standardenheten är dagen (**d**).

* Om de regionala inställningarna till exempel är inställda på Français: **s** för sekunder, **mn** för minuter, **h** för timmar, **j** för dagar, **m** för månader, **a** för år. Vid tidpunkten för godkännandet konverteras värdet automatiskt till den mest läsbara enheten, som i exemplet ovan konverterades **90s** till **1mn 30s**.

  Standardenheten är dagen (**d**).
