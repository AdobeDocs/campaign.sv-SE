---
product: campaign
title: Uppdatera aggregat
description: Läs mer om aktiviteten Uppdatera aggregerat arbetsflöde
feature: Workflows
role: Data Engineer
level: Beginner
exl-id: 9a213522-bacf-44f9-98a6-caaaf037a0f9
source-git-commit: 77ec01aaba1e50676bed57f503a9e4e8bb1fe54c
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 3%

---

# Uppdatera aggregat{#update-aggregate}

Sammansättningar som definierats i [kuber](../../v8/reporting/gs-cubes.md) för rapportsyften kan uppdateras med en viss aktivitet. En **[!UICONTROL Workflow]**-flik är tillgänglig när aggregeringen konfigureras.

Läs mer om kuber och aggregat i [det här avsnittet](../../v8/reporting/customize-cubes.md#calculate-and-use-aggregates).

Om du vill uppdatera en sammanställning redigerar du aktiviteten **[!UICONTROL Update aggregate]** och väljer den kub och sammanställning som ska uppdateras.

Du kan konfigurera en **fullständig uppdatering** eller en **partiell uppdatering**.

![](assets/update-aggregate-details.png)

Som standard utförs en fullständig uppdatering under varje beräkning. Om du vill aktivera en partiell uppdatering markerar du alternativet och definierar uppdateringsvillkoren.

![](assets/update-aggregate-partial.png)

Ett bra tillvägagångssätt är att lägga till en **[!UICONTROL Scheduler]**-aktivitet för att ställa in frekvensen för beräkningsuppdateringar.
