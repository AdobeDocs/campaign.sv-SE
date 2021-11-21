---
product: campaign
title: Presentera erbjudanden för anonyma profiler (inkommande interaktion)
description: Lär dig presentera erbjudanden för anonyma profiler
exl-id: b7a04360-f8c6-4c69-9594-2b44d3f819b7
source-git-commit: 00a88cf9217faf32070a3cd34a2c1ae5243d9a6e
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Anonyma interaktioner{#anonymous-interactions}

## Miljö för anonyma interaktioner {#environment-for-anonymous-interactions}

Som standard, Campaign **Interaktion** -modulen innehåller en förkonfigurerad miljö för den inbyggda mottagartabellen (identifierade erbjudanden). Om du behöver ange en annan tabell som mål, en besökstabell för anonyma erbjudanden eller en anpassad mottagartabell som exempel, måste du använda guiden för målmappning för att skapa miljön. [Läs mer om miljöer](interaction-env.md).

När du skapar en anonym miljö via guiden för att skapa mappningar **[!UICONTROL Environment dedicated to incoming anonymous interactions]** -rutan markeras automatiskt i miljöns **[!UICONTROL General]** -fliken.

The **[!UICONTROL Targeting dimension]** slutförs automatiskt. Som standard länkas den till besökstabellen.

The **[!UICONTROL Visitor folder]** visas. Det fylls automatiskt i för att länka till **[!UICONTROL Visitors]** mapp. I det här fältet kan du välja var besökarprofiler ska sparas.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Om du vill filtrera flera typer av besökare, till exempel om anonyma erbjudanden presenteras för ett eller flera varumärken, måste du skapa en miljö för varje varumärke och en **[!UICONTROL Visitors]** typmapp för varje miljö.

## Erbjud katalog för anonyma interaktioner {#offer-catalog-for-anonymous-interactions}

På samma sätt som utgående interaktioner ordnas inkommande interaktioner i en erbjudandekatalog som består av kategorier och erbjudanden.

Om du vill skapa kategorier och utrymmen använder du samma process som för identifierade besökare. Se [Skapa en erbjudandekategori](interaction-offer-catalog.md#creating-offer-categories) och [Skapa en erbjudandemiljö](interaction-env.md#creating-an-offer-environment)).

## Anonyma besökare {#anonymous-visitors}

Anonyma besökare kan bli föremål för en process för identifiering av cookies när de ansluter. Den här implicita igenkänningen baseras på besökarens webbläsarhistorik.

Under det här steget görs en jämförelse mellan de data som har återställts av cookies och de i din databas. I vissa fall identifieras besökare (de identifieras sedan implicit), i andra fall identifieras de inte (och förblir därför anonyma).

Om du vill köra den här analysen kontrollerar du **[!UICONTROL Implicitly identify the individual based on their browser history]** alternativ.

![](assets/identification_anonymous_visitors.png)

## Bearbetar oidentifierade anonyma besökare {#processing-unidentified-anonymous-visitors}

Om ingen anonym besökare identifieras efter analysen kan du lagra deras data i ett givet utrymme. På så sätt kan du föreslå erbjudanden som är särskilt avsedda för den här typen av besökare, och som matchar de angivna typologireglerna.

Om det inte finns något element som gör att du kan identifiera en kontakt, eller om du inte vill föreslå ett identifierat erbjudande till en kontakt som kan identifieras implicit, kan du välja att göra en reservlösning i en anonym miljö.

Om du vill göra det går du till **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** anger du sedan den miljö som är dedikerad till de oidentifierade besökarna i **[!UICONTROL Linked anonymous space]** när du anger ett erbjudandeutrymme.

![](assets/anonymous_to_anonymous_environment.png)
