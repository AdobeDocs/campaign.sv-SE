---
product: campaign
title: Presentera ett erbjudande (inkommande interaktion)
description: Lär dig presentera det bästa erbjudandet med Campaign Interaction Module
feature: Interaction, Offers
role: User, Admin
exl-id: d0137fa7-3d04-4205-b49c-46973e45a5b8
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 4%

---

# Presentera det bästa erbjudandet{#interaction-present-offers}

Erbjudanden kan visas på olika erbjudandeplatser med hjälp av [en ingående eller utgående kanal](interaction-architecture.md#interaction-types). I det här kapitlet beskrivs några specifika funktioner för inkommande kanaler.

![](assets/inbound-interactions.png)

För att ett erbjudande ska kunna väljas ut av erbjudandemotorn måste det godkännas och vara tillgängligt i en live-miljö.

Mer information finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/managing-offers/managing-an-offer-catalog/approving-and-activating-an-offer.html?lang=sv-SE#approving-offer-content){target="_blank"}.

I kontexten för en inkommande kontakt kan användaren som bläddrar på sidan identifieras av webbplatsen eller inte. Erbjudandemotorn erbjuder olika erbjudanden för identifierade profiler och för anonyma profiler.

Innan du kan presentera erbjudanden på en inkommande kanal måste du konfigurera offertmotorsamtalet där du vill att erbjudandena ska presenteras. I de flesta fall för inkommande interaktion är detta webbsidan.

>[!NOTE]
>
>För inkommande interaktioner måste du konfigurera erbjudandemotorn så att den kan presentera och uppdatera ett eller flera erbjudanden.
>
>Du måste också aktivera enhetsläge på dina erbjudanden. Mer information finns på [den här sidan](interaction-offer-spaces.md).
