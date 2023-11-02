---
title: Ändra standardmottagartabellen
description: Lär dig använda en anpassad mottagartabell
feature: Custom Resources, Profiles, Configuration
role: User, Developer
level: Intermediate, Experienced
exl-id: 0b71c76b-03d9-4023-84fc-3ecc0df9261b
source-git-commit: f577ee6d303bab9bb07350b60cf0fa6fc9d3a163
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 3%

---

# Använd en anpassad mottagartabell{#gs-ac-custom-recipient}

Adobe Campaign har en inbyggd profiltabell: **nmsRecipient**. Den här tabellen har ett antal fördefinierade fält och tabeller som enkelt kan utökas. Läs mer om tabellen i [den här sidan](datamodel.md#ootb-profiles).

Inbyggt tabelltillägg ger flexibilitet, men det går inte att ta bort vissa oanvända fält eller länkar. Därför kan det vara bra att använda en anpassad mottagartabell när datamodellen skiljer sig avsevärt från den inbyggda mottagartabellstrukturen i Campaign eller om du har ett stort antal profiler.  Den här metoden kräver dock vissa försiktighetsåtgärder när den implementeras.

![](../assets/do-not-localize/book.png) Lär dig hur du konfigurerar instansen att använda en anpassad mottagartabell i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/use-a-custom-recipient-table/about-custom-recipient-table.html){target="_blank"}.