---
title: Ändra standardmottagartabellen
description: Lär dig använda en anpassad mottagartabell
feature: Custom Resources, Profiles, Configuration
role: User, Developer
level: Intermediate, Experienced
exl-id: 0b71c76b-03d9-4023-84fc-3ecc0df9261b
source-git-commit: be085eaf7e1e7ded5986fdb6100045daba4d88fe
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Använda en anpassad mottagartabell{#gs-ac-custom-recipient}

Adobe Campaign levereras med en inbyggd profiltabell: **nmsRecipient**. Den här tabellen har ett antal fördefinierade fält och tabeller som enkelt kan utökas. Läs mer om tabellen på [den här sidan](datamodel.md#ootb-profiles).

Inbyggt tabelltillägg ger flexibilitet, men det går inte att ta bort vissa oanvända fält eller länkar. Därför kan det vara bra att använda en anpassad mottagartabell när din datamodell skiljer sig avsevärt från den inbyggda mottagartabellstrukturen i Campaign, eller om du har ett stort antal profiler.  Den här metoden kräver dock vissa försiktighetsåtgärder när den implementeras.

Lär dig hur du konfigurerar din instans så att den använder en anpassad mottagartabell i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/use-a-custom-recipient-table/about-custom-recipient-table.html?lang=sv-SE){target="_blank"}.