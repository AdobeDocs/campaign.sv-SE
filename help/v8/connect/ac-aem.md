---
title: Arbeta med Campaign och Adobe Experience Manager
description: Lär dig arbeta med Campaign och Adobe Experience Manager
feature: Experience Manager Integration
role: Admin, User
level: Beginner
exl-id: e83893f7-a8be-48a3-a7a6-aced7b4d4f69
source-git-commit: 92fe7c41047aafd26cca70a547025a3eff73e398
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Arbeta med Campaign och Adobe Experience Manager {#ac-aem}

Tack vare integrationen mellan Adobe Campaign och Adobe Experience Manager kan ni hantera innehållet i era e-postleveranser och era formulär direkt i Adobe Experience Manager. Du kan antingen importera **Adobe Experience Manager** innehåll i Campaign eller koppla samman **Adobe Experience Manager som molntjänst** så att du kan redigera innehållet direkt i webbgränssnittet.

![](../assets/do-not-localize/book.png) [Upptäck hur du kan redigera din Adobe Experience Manager som Cloud Service i webbgränssnittet för Campaign](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/email/content/integrations/aem-content.html?lang=en)

![](../assets/do-not-localize/book.png) [Läs mer om Adobe Experience Manager i det här dokumentet](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/campaignonpremise.html#aem-and-adobe-campaign-integration-workflow)

## Skapa med Adobe Experience Manager {#integrating-with-aem}

![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Service [kontakta Adobe](../start/campaign-faq.md#support) för att integrera Adobe Experience Manager med Campaign.

Den här integreringen kan till exempel användas för att skapa ett nyhetsbrev i Adobe Experience Manager som sedan används i Adobe Campaign som en del av en e-postkampanj.

**Från Adobe Experience Manager:**

1. Navigera till [!DNL Adobe Experience Manager] författarinstans och klicka på Adobe Experience i det övre vänstra hörnet på sidan. Välj **[!UICONTROL Sites]** på menyn.

   ![](assets/aem_authoring_1.png)

1. Åtkomst **[!UICONTROL Campaigns > Name of your brand (here we.Shopping) > Main Area > Email]**.

1. Klicka **[!UICONTROL Create]** och markera **[!UICONTROL Page]** i listrutan.

   ![](assets/aem_authoring_2.png)

1. Välj **[!UICONTROL Adobe Campaign Email]** mall och ge nyhetsbrevet ett namn.

1. När du har skapat sidan öppnar du **[!UICONTROL Page information]** meny och klicka **[!UICONTROL Open Properties]**.

   ![](assets/aem_authoring_3.png)

1. Anpassa e-postinnehållet genom att lägga till komponenter, till exempel anpassningsfält från Adobe Campaign. [Läs mer](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/authoring/aem-adobe-campaign/campaign.html?lang=en#editing-email-content)

1. När e-postmeddelandet är klart går du till **[!UICONTROL Page information]** meny och klicka **[!UICONTROL Start workflow]**.

   ![](assets/aem_authoring_4.png)

1. I den första listrutan väljer du **[!UICONTROL Approve Adobe Campaign]** som arbetsflödesmodell och klicka **[!UICONTROL Start workflow]**.

   ![](assets/aem_authoring_5.png)

1. En ansvarsfriskrivning visas högst upp på sidan med följande information: `This page is subject to the workflow Approve for Adobe Campaign`. Klicka **[!UICONTROL Complete]** bredvid ansvarsfriskrivningen för att bekräfta granskningen och klicka på **[!UICONTROL Ok]**.

1. Klicka **[!UICONTROL Complete]** igen och välj **[!UICONTROL Newsletter approval]** i **[!UICONTROL Next Step]** nedrullningsbar meny.

   ![](assets/aem_authoring_6.png)

Nyhetsbrevet är nu klart och synkroniserat i Adobe Campaign.

**Från Adobe Campaign:**

1. Från **[!UICONTROL Campaigns]** flik, klicka **[!UICONTROL Deliveries]** sedan **[!UICONTROL Create]**.

1. Välj **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** mall från **[!UICONTROL Delivery template]** listruta.

   ![](assets/aem_authoring_7.png)

1. Lägg till en **[!UICONTROL Label]** till leveransen och klicka **[!UICONTROL Continue]**.

1. Klicka **[!UICONTROL Synchronize]** för att få tillgång till era AEM.

   Om knappen inte visas i gränssnittet går du till **[!UICONTROL Properties]** och få åtkomst till **[!UICONTROL Advanced]** -fliken. Se till att **[!UICONTROL Content editing mode]** fältet är konfigurerat till **[!UICONTROL AEM]** och ange AEM i **[!UICONTROL AEM account]** fält.

   ![](assets/aem_authoring_8.png)

1. Välj den AEM leveransen som skapades i [!DNL Adobe Experience Manager] och bekräfta genom att klicka **[!UICONTROL Ok]**.

1. Klicka på **[!UICONTROL Refresh content]** när AEM ändras.

Din e-post kan nu skickas till din målgrupp.

## Importera resurser från Adobe Experience Manager Assets bibliotek {#assets-library}

Du kan även infoga resurser direkt från [!DNL Adobe Experience Manager Assets Library] när du redigerar ett e-postmeddelande eller en landningssida i Adobe Campaign. Den här funktionen beskrivs i [Adobe Experience Manager Assets-dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/managing/manage-assets.html?lang=en).

1. Överför dina resurser i dina **Adobe Experience Manager Assets Library**. [Mer information](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/managing/manage-assets.html?lang=en#uploading-assets)

1. Skapa en ny leverans i Adobe Campaign genom att gå till **Kampanjer** flik, klicka **Leveranser** och klicka på **Skapa** ovanför listan över befintliga leveranser.

1. Välj en **Leveransmall** och namnge sedan leveransen.

1. Definiera och anpassa meddelandeinnehållet. [Läs mer](../send/email.md)

1. Använd **Adobe Experience Manager Assets-bibliotek**, få åtkomst till **[!UICONTROL Properties]** AEM och välj **[!UICONTROL Advanced]** -fliken. Aktivera **[!UICONTROL Use above AEM instance as shared asset library]** alternativ.

   ![](assets/aem_authoring_9.png)

1. Från **Bild** -ikonen, visa **[!UICONTROL Select a shared asset]** -menyn.

   ![](assets/aem_authoring_10.png)

1. I urvalsfönstret väljer du en bild från **Adobe Experience Manager Assets-bibliotek**, och bekräfta sedan.

E-postleveransen är klar. Nu kan du ange målgruppen, bekräfta leveransen och fortsätta skicka den.
