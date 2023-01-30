---
product: campaign
title: Celler
description: Celler
feature: Workflows, Targeting Activity
exl-id: d85645a6-fc15-4c3a-9d67-d4230224e1f7
source-git-commit: 6464e1121b907f44db9c0c3add28b54486ecf834
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 2%

---

# Celler{#cells}

The **[!UICONTROL Cells]** -aktiviteten ger en vy över de olika deluppsättningarna som datakolumner. Den underlättar delmängdsmanipulation och är även utformad för att utnyttja personaliseringsmöjligheterna.

![](assets/wf_split_cells.png)

Den här aktiviteten kan konfigureras för att ange specifika parametrar baserat på användarnas behov. Som standard visas detaljerna för varje delmängd i ett dedikerat fönster via **[!UICONTROL Cells]** och **[!UICONTROL Advanced]** -tabbar.

![](assets/wf_split_cells_with_customization.png)

I exemplet nedan har indataformuläret ändrats: a **[!UICONTROL Data]** -fliken har lagts till för att aktivera associationen för ett erbjudande och en prioritetsnivå för varje delmängd.

![](assets/cells-activity-sample.png)

Följande information har lagts till i arbetsflödesformuläret i **[!UICONTROL Administration > Configurations > Input forms]** nod till Adobe Campaign Explorer:

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

Anpassning av inmatningsformulär i Adobe Campaign är reserverat för expertanvändare.