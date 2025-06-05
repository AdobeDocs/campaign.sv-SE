---
product: campaign
title: Erbjudanden per cell
description: Erbjudanden per cell
feature: Workflows, Targeting Activity, Interaction
role: User
version: Campaign v8, Campaign Classic v7
exl-id: e2216dfd-1ef8-4747-b716-576fd6498fa6
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 7%

---

# Erbjudanden per cell{#offers-by-cell}



Med aktiviteten **[!UICONTROL Offers by cell]** kan du distribuera den inkommande populationen (från en fråga till exempel) till flera segment och ange ett erbjudande som ska visas för vart och ett av dessa segment.

Den här aktiviteten kan bara användas med **Interaktion**. Läs mer om erbjudandehantering i [det här avsnittet](../../v8/interaction/interaction.md).

Så här gör du:

1. Lägg till aktiviteten **[!UICONTROL Offers by cell]** när du har angett målpopulationen och öppna den sedan.
1. På fliken **[!UICONTROL General]** väljer du det erbjudandeutrymme som du vill visa erbjudandena på.
1. På fliken **[!UICONTROL Cells]** anger du de olika delmängderna med knappen **[!UICONTROL Add]**:

   * Ange delmängdsfyllningen med de tillgängliga filtrerings- och begränsningsreglerna.
   * Välj sedan det erbjudande som du vill presentera för undergruppen. De erbjudanden som är tillgängliga är sådana som är berättigade till det erbjudandeutrymme som valdes i föregående steg.

     ![](assets/int_offer_per_cell1.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Se [Flerkanalsleveranser](cross-channel-deliveries.md).
