---
title: Arbeta med målmappningar
description: Lär dig använda och skapa målmappningar
feature: Audiences, Profiles
role: User, Developer
level: Beginner, Intermediate
exl-id: 5256fc15-1878-4064-9c75-7876a3826b83
source-git-commit: 4c787abbf9b13c08263e602930bc532d73e08a5a
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Arbeta med målmappningar{#gs-target-mappings}

Som standard är e-post- och SMS-leveransmallar avsedda för **[!UICONTROL Recipients]**. Målmappningen använder därför fälten i tabellen **nms:receive**.

För push-meddelanden är standardmålmappningen **Subscriber applications (nms:appSubscriptionRcp)**, som är länkad till mottagartabellen.

Du kan använda andra målmappningar för leveranser eller skapa en ny målmappning.

## Inbyggda målmappningar {#ootb-mappings}

Adobe Campaign innehåller följande inbyggda målmappningar:

| Namn | Använd för | Schema |
|---|---|---|
| Mottagare | Leverera till mottagare (inbyggd mottagartabell) | nms:mottagare |
| Besökare | Leverera till besökare vars profiler har samlats in via hänskjutning (viral marketing) för ex. | mns:besökare |
| Prenumerationer | Leverera till mottagare som prenumererar på en informationstjänst som ett nyhetsbrev | nms:prenumeration |
| Prenumerationer på besökare | Skicka till besökare som prenumererar på en informationstjänst | nms:visitorSub |
| Operatorer | Leverera till Adobe Campaign | nms:operator |
| Extern fil | Leverera via en fil som innehåller all information som behövs för leveransen | Inget länkat schema, inget mål har angetts |
| Prenumerationsprogram | Leverera till mottagare som prenumererar på ett program | nms:appSubscriptionRcp |


## Skapa en målmappning {#new-mapping}

Du kan också skapa en målmappning. Du kan behöva lägga till en anpassad målmappning om:

* du använder en anpassad mottagartabell,
* Du konfigurerar en filtreringsdimension som skiljer sig från den inbyggda måldimensionen på målmappningsskärmen.

Läs mer om anpassade mottagartabeller på [den här sidan](../dev/custom-recipient.md).

Guiden Skapa målmappning för Adobe Campaign hjälper dig att skapa alla scheman som behövs för att du ska kunna använda din anpassade målmappning.

1. Bläddra till **[!UICONTROL Administration]** `>` **[!UICONTROL Campaign Management]** `>` **[!UICONTROL Target mappings]** från Adobe Campaign Explorer.

1. Skapa en ny målmappning och välj ditt anpassade schema som måldimension.

   ![](assets/new-target-mapping.png)


1. Ange fälten där profilinformationen lagras: efternamn, förnamn, e-postadress, etc.

   ![](assets/wf_new_mapping_define_join.png)

1. Ange parametrarna för informationslagring, inklusive suffixet för tilläggsscheman för att de ska vara enkla att identifiera.

   ![](assets/wf_new_mapping_define_names.png)

   Du kan välja om du vill lagra undantag (**excludelog**), med meddelanden (**broadlog**) eller i en separat tabell.

   Du kan också välja om du vill hantera spårning för den här leveransmappningen (**spårningslogg**).

1. Välj sedan de tillägg som ska beaktas. Tilläggstypen beror på dina Campaign-inställningar och tillägg.

   ![](assets/wf_new_mapping_define_extensions.png)

   Klicka på knappen **[!UICONTROL Save]** för att starta skapandet av leveransmappningen: alla länkade tabeller skapas automatiskt baserat på de valda parametrarna.
