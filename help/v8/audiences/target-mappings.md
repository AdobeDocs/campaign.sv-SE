---
title: Arbeta med målmappningar
description: Lär dig hur du använder och skapar målmappningar
feature: Audiences, Profiles
role: User, Developer
level: Beginner, Intermediate
exl-id: 5256fc15-1878-4064-9c75-7876a3826b83
source-git-commit: db27abf860b0744a4120166c68e2cc2ae8a3d172
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Arbeta med målmappningar{#gs-target-mappings}

Som standard har mallar för e-post och SMS-leverans som mål **[!UICONTROL Recipients]**. Målmappningen använder därför fälten i **nms:mottagare** tabell.

Standardmålmappningen för push-meddelanden är **Prenumerationsprogram (nms:appSubscriptionRcp)**, som är länkad till mottagartabellen.

Du kan använda andra målmappningar för leveranser eller skapa en ny målmappning.

## Inbyggda målmappningar {#ootb-mappings}

Adobe Campaign innehåller följande inbyggda målmappningar:

| Namn | Använd | Schema |
|---|---|---|
| Mottagare | Leverera till mottagare (inbyggd mottagartabell) | nms:mottagare |
| Besökare | Ge besökare vars profiler har samlats in via hänskjutning (viral marketing) för ex. | mns:besökare |
| Prenumerationer | Leverera till mottagare som prenumererar på en informationstjänst som ett nyhetsbrev | nms:prenumeration |
| Prenumerationer på besökare | Skicka till besökare som prenumererar på en informationstjänst | nms:visitorSub |
| Operatorer | Leverera till Adobe Campaign | nms:operator |
| Extern fil | Leverera via en fil som innehåller all information som behövs för leveransen | Inget länkat schema, inget mål har angetts |

## Skapa en målmappning {#new-mapping}

Du kan också skapa en målmappning. Du kan behöva lägga till en anpassad målmappning, till exempel om:

* du använder en anpassad mottagartabell,
* Du konfigurerar en filtreringsdimension som skiljer sig från den inbyggda måldimensionen på målmappningsskärmen.

Läs mer om anpassade mottagartabeller i [den här sidan](../dev/custom-recipient.md).

Guiden Skapa målmappning för Adobe Campaign hjälper dig att skapa alla scheman som behövs för att du ska kunna använda din anpassade målmappning.

1. Bläddra till **[!UICONTROL Administration]** `>` **[!UICONTROL Campaign Management]** `>` **[!UICONTROL Target mappings]** från Adobe Campaign Explorer.

1. Skapa en ny målmappning och välj ditt anpassade schema som måldimension.

   ![](assets/new-target-mapping.png)


1. Ange fälten där profilinformationen lagras: efternamn, förnamn, e-postadress, adress osv.

   ![](assets/wf_new_mapping_define_join.png)

1. Ange parametrarna för informationslagring, inklusive suffixet för tilläggsscheman för att de ska vara enkla att identifiera.

   ![](assets/wf_new_mapping_define_names.png)

   Du kan välja om du vill lagra undantag (**excludelog**), med meddelanden (**broadlog**) eller i en separat tabell.

   Du kan också välja om du vill hantera spårning för den här leveransmappningen (**trackinglog**).

1. Välj sedan de tillägg som ska beaktas. Tilläggstypen beror på dina Campaign-inställningar och tillägg.

   ![](assets/wf_new_mapping_define_extensions.png)

   Klicka på **[!UICONTROL Save]** knapp för att starta framtagning av leveransmappning: alla länkade tabeller skapas automatiskt baserat på de valda parametrarna.
