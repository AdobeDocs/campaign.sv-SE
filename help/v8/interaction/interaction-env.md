---
title: Arbeta med Campaign Interaction-miljöer
description: Lär dig hur du skapar miljöer för Campaign Interaction
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 31f38870-1781-4185-9022-d4fd6a31c94a
source-git-commit: 6de5c93453ffa7761cf185dcbb9f1210abd26a0c
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 2%

---

# Arbeta i miljöer{#work-with-environments}

## Live- och designmiljöer{#live-design-environments}

Interaktionen fungerar i två typer av miljöer:

* **[!UICONTROL Design]** erbjuder miljöer som innehåller erbjudanden som redigeras och kan ändras. Dessa erbjudanden har inte gått igenom godkännandecykeln och levereras inte till kontakter.
* **[!UICONTROL Live]** erbjuder miljöer som innehåller godkända erbjudanden när de presenteras för kontakter. Erbjudandena i den här miljön är skrivskyddade.

![](assets/offer_environments_overview_001.png)

Varje **[!UICONTROL Design]** miljön är länkad till en **[!UICONTROL Live]** miljö. När ett erbjudande är klart blir dess innehåll och behörighetskrav föremål för en godkännandecykel. När den här cykeln är slutförd distribueras det aktuella erbjudandet automatiskt till **[!UICONTROL Live]** miljö. Från och med nu finns den tillgänglig för leverans.

Som standard innehåller Campaign en **[!UICONTROL Design]** miljö och **[!UICONTROL Live]** miljö som är länkad till den. Båda miljöerna är förkonfigurerade för att rikta sig till [inbyggd mottagartabell](../dev/datamodel.md#ootb-profiles).

>[!NOTE]
>
>Om du vill ha målmottagartabellen måste du använda målmappningsassistenten för att skapa miljöerna. [Läs mer](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Leveransansvariga kan bara visa **[!UICONTROL Live]** miljö och utnyttja erbjudanden för att leverera dem. Erbjudandehanterarna kan visa och använda **[!UICONTROL Design]** -miljö och visa **[!UICONTROL Live]** miljö. [Läs mer](interaction-operators.md)

## Skapa en miljö för anonyma interaktioner{#create-an-offer-environment}

Som standard innehåller Campaign en inbyggd miljö som är avsedd för mottagartabellen (identifierade erbjudanden). Om du vill ha en annan tabell som anonyma profiler på webbplatsen för inkommande interaktioner måste du uppdatera konfigurationen.

Följ stegen nedan:

1. Bläddra till **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**, högerklicka på den målmappning som du vill använda och välj **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Klicka **[!UICONTROL Next]** väljer du **[!UICONTROL Generate a storage schema for propositions]** och klicka **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Om alternativet redan är markerat avmarkerar du det och markerar det sedan igen.

1. Adobe Campaign skapar två miljöer - **[!UICONTROL Design]** och **[!UICONTROL Live]** - med målinformation från den tidigare aktiverade målmappningen. Miljön är förkonfigurerad med målinformationen.

Om du har aktiverat **[!UICONTROL Visitor]** mappning, **[!UICONTROL Environment dedicated to incoming anonymous interactions]** -rutan markeras automatiskt i miljöns **[!UICONTROL General]** -fliken.

Med det här alternativet kan du aktivera anonyma interaktionsspecifika funktioner, särskilt när du konfigurerar miljön, som innehåller blanksteg. Du kan också konfigurera alternativ som gör att du kan växla från en identifierad miljö till en anonym miljö.

Du kan t.ex. länka en mottagarmiljö till ett tillgängligt utrymme (identifierad kontakt) med ett erbjudandeutrymme som matchar en besökarmiljö (oidentifierad kontakt). På så sätt kommer olika erbjudanden att göras tillgängliga för kontakten beroende på om kontakten identifieras eller inte. Mer information finns i [Skapa erbjudandemellanslag](interaction-offer-spaces.md).

![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Mer information om anonyma interaktioner i en inkommande kanal finns i [Anonyma interaktioner](anonymous-interactions.md).
