---
product: campaign
title: Uppdatera aggregat
description: Läs mer om aktiviteten Uppdatera aggregerat arbetsflöde
feature: Workflows
role: Data Engineer
level: Beginner
source-git-commit: 8d9b8d3e31362c2d69ec0fc6f16ab375538d7f10
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 3%

---

# Uppdatera aggregat{#update-aggregate}

Aggregat definierade i [kuber](../../v8/reporting/gs-cubes.md) för rapportering kan uppdateras med en viss aktivitet. A **[!UICONTROL Workflow]** -fliken är tillgänglig när du konfigurerar sammanställningen.

Läs mer om kuber och aggregat i [det här avsnittet](../../v8/reporting/customize-cubes.md#calculate-and-use-aggregates).

Om du vill uppdatera en mängd redigerar du **[!UICONTROL Update aggregate]** och välj den kub och den mängd som ska uppdateras.

Du kan konfigurera en **Fullständig uppdatering** eller en **Delvis uppdatering**.

![](assets/update-aggregate-details.png)

Som standard utförs en fullständig uppdatering under varje beräkning. Om du vill aktivera en partiell uppdatering markerar du alternativet och definierar uppdateringsvillkoren.

![](assets/update-aggregate-partial.png)

Ett bra tillvägagångssätt är att lägga till en **[!UICONTROL Scheduler]** aktivitet för att ange frekvensen för uppdateringar av beräkningar.
