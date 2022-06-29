---
title: Katalog för kampanjinteraktionserbjudande
description: Lär dig hur du skapar en erbjudandekatalog
feature: Interaction, Offers
role: Data Engineer
level: Beginner
exl-id: 911096e2-0307-46a8-873c-ee2248b8e3e8
source-git-commit: 8eb92dd1cacc321fc79ac4480a791690fc18511c
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---

# Skapa en erbjudandekatalog

Som en **Erbjudandehanterare**&#x200B;är du ansvarig för att skapa erbjudandekatalogen.

En erbjudandekatalog är kopplad till en befintlig miljö. Erbjudandena i den här katalogen kan bara associeras med de utrymmen som anges i samma miljö.

Innan du skapar dina erbjudanden måste du ange en [miljö](interaction-env.md) som innehåller alla egenskaper (behörighet, begränsningar av mål, presentationsregler) för en uppsättning erbjudanden, sorterade i kategorier, samt en lista över deras space.

## Skapa erbjudandekategorier{#creating-offer-categories}

Erbjudandet är indelat i kategorier/underkategorier. Kategorier skapas i **[!UICONTROL Design]** och driftsättas automatiskt i **[!UICONTROL Live]** miljö (dvs. görs tillgänglig) när de erbjudanden de innehåller godkänns. The **[!UICONTROL Design]** -miljön innehåller en standardkategori för att ta emot alla erbjudanden. Underkategorier kan skapas för att lägga till hierarki i katalogerbjudandena.

För varje kategori kan du definiera **berättigandedatum**, vilket är den period under vilken erbjudandena i kategorin kan presenteras för deras mål. Du kan även justera vikten för en kategori för att prioritera erbjudandepresentationen.

Så här skapar du en ny kategori:

1. Bläddra till **[!UICONTROL Offer catalog]** mapp.

   ![](assets/offer_cat_create_001.png)

1. Högerklicka och välj **[!UICONTROL Create a new "Offer category" folder]** i listrutan.

   ![](assets/offer_cat_create_002.png)

1. Ge kategorin ett nytt namn. Du kan redigera etiketten senare med **[!UICONTROL General]** -fliken.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Upprepa dessa steg om du vill skapa så många kategorier som behövs.

   Därefter kan du, efter behov,

   * Tilldela berättigandedatum från **[!UICONTROL Eligibility]** -fliken.

      ![](assets/offer_cat_create_004.png)

   * **[!UICONTROL Edit query]** för att tillämpa filter på erbjudandemålet.

   * En sammanfattning av reglerna för behörighet.Om du vill visa dem klickar du på **[!UICONTROL Schedule and eligibility rules of the offer]** länk.

## Lägg till en reservkategori

För att se till att alla mottagare får ett erbjudande är det möjligt att systematiskt lägga till en eller flera olika kategorier i rekommendationerna.

Dessa reserverbjudanden måste ha en låg (men inte null) vikt, så att de bara beaktas om inga högre vikterbjudanden är giltiga.

Dessutom får inga presentationsregler tillämpas på dessa erbjudanden för att säkerställa att de alltid ingår i rekommendationerna. Det innebär att om det inte finns något större vikterbjudande får mottagaren minst ett erbjudande från den här kategorin under ett erbjudande.

Följ stegen nedan om du vill inkludera en reservkategori i rekommendationerna:

1. Bläddra till din erbjudandekatalog.
1. Klicka på **[!UICONTROL Eligibility]** och väljer **[!UICONTROL Always include this category in the recommendations]** alternativ.
1. Klicka på **[!UICONTROL Save]**.

   ![](assets/offer_cat_default_001.png)
