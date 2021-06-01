---
product: Adobe Campaign
title: Kampanjinteraktionsoperatorer
description: Skapa operatorer för erbjudandehantering
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: 5363950db5092bc7e0a72a0823db1132a17dda33
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 1%

---

# Live- och designmiljöer{#live-design-environments}

Interaktionen fungerar i två typer av miljöer:

* **[!UICONTROL Design]** erbjuder miljöer som innehåller erbjudanden som redigeras och kan ändras. Dessa erbjudanden har inte gått igenom godkännandecykeln och levereras inte till kontakter.
* **[!UICONTROL Live]** erbjuder miljöer som innehåller godkända erbjudanden när de presenteras för kontakter. Erbjudandena i den här miljön är skrivskyddade.

![](assets/offer_environments_overview_001.png)

Varje **[!UICONTROL Design]**-miljö är länkad till en **[!UICONTROL Live]**-miljö. När ett erbjudande är klart blir dess innehåll och behörighetskrav föremål för en godkännandecykel. När den här cykeln är slutförd distribueras det aktuella erbjudandet automatiskt till **[!UICONTROL Live]**-miljön. Från och med nu finns den tillgänglig för leverans.

Som standard har Campaign en **[!UICONTROL Design]**-miljö och en **[!UICONTROL Live]**-miljö länkad till den. Båda miljöerna är förkonfigurerade för den inbyggda mottagartabellen [](../dev/datamodel.md#ootb-profiles) som mål.

>[!NOTE]
>
>Om du vill ha målmottagartabellen måste du använda målmappningsassistenten för att skapa miljöerna. [Läs mer](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Leveransansvariga kan bara visa **[!UICONTROL Live]**-miljön och utnyttja erbjudanden för att leverera dem. Erbjudandehanterare kan visa och använda **[!UICONTROL Design]**-miljön och visa **[!UICONTROL Live]**-miljön. [Läs mer](interaction-operators.md).

## Skapa en erbjudandemiljö {#creating-an-offer-environment}

Som standard innehåller Campaign en inbyggd miljö som är avsedd för mottagartabellen (identifierade erbjudanden). Följ stegen nedan om du vill skapa en måltabell:

1. Bläddra till **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**, högerklicka på den målmappning som du vill använda och välj **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Klicka på **[!UICONTROL Next]**, markera alternativet **[!UICONTROL Generate a storage schema for propositions]** och klicka på **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Om alternativet redan är markerat avmarkerar du det och markerar det sedan igen.

1. Adobe Campaign skapar två miljöer - **[!UICONTROL Design]** och **[!UICONTROL Live]** - med målinformation från den tidigare aktiverade målmappningen. Miljön är förkonfigurerad med målinformationen.
