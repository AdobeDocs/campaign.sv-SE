---
product: campaign
title: Redigera schema
description: Läs mer om arbetsflödesaktiviteten Redigera schema
feature: Workflows, Targeting Activity
role: User, Developer
exl-id: 16fb1aa5-cf99-4461-a1a4-7a68d97e2a74
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# Redigera schema{#edit-schema}



Data kan omformas, normaliseras och, om det behövs, berikas i arbetsflödet med hjälp av aktiviteten **[!UICONTROL Edit schema]**. Det används vanligtvis för att normalisera datastrukturen: du kan ändra namn på utdatakolumnerna eller deras innehåll genom att beräkna medelvärden för ett fält eller en mängd, till exempel.

Den här aktiviteten ändrar inte data i arbetstabellen, utan ändrar bara dess schema, dvs. den logiska vyn av data.

![](assets/wf_manipulation_box.png)

Du kan också skapa kopplingar med andra arbetstabeller via fliken **[!UICONTROL Links]**.

![](assets/wf_manipulation_box_link_tab.png)

I det nedre avsnittet kan du konfigurera listan med föreningsvillkor, dvs. villkoren som används för att stämma av data från de två tabellerna.
