---
product: campaign
title: Redigera schema
description: Läs mer om arbetsflödesaktiviteten Redigera schema
feature: Workflows, Targeting Activity
exl-id: 16fb1aa5-cf99-4461-a1a4-7a68d97e2a74
source-git-commit: 77ec01aaba1e50676bed57f503a9e4e8bb1fe54c
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# Redigera schema{#edit-schema}



Data kan omformas, normaliseras och vid behov berikas i arbetsflödet med **[!UICONTROL Edit schema]** aktivitet. Det används vanligtvis för att normalisera datastrukturen: Du kan byta namn på utdatakolumnerna eller ändra deras innehåll genom att till exempel beräkna medelvärdena för ett fält eller en mängd.

Den här aktiviteten ändrar inte data i arbetstabellen, utan ändrar bara dess schema, dvs. den logiska vyn av data.

![](assets/wf_manipulation_box.png)

Du kan också skapa kopplingar med andra arbetstabeller via **[!UICONTROL Links]** -fliken.

![](assets/wf_manipulation_box_link_tab.png)

I det nedre avsnittet kan du konfigurera listan med föreningsvillkor, dvs. villkoren som används för att stämma av data från de två tabellerna.
