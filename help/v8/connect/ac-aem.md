---
title: Arbeta med Campaign och Adobe Experience Manager
description: Lär dig arbeta med Campaign och Adobe Experience Manager
feature: Experience Manager Integration
role: Admin, User
level: Beginner
exl-id: e83893f7-a8be-48a3-a7a6-aced7b4d4f69
source-git-commit: 4f9183c7f1d12feb255a0050da423647f0fce85e
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Arbeta med Campaign och Adobe Experience Manager {#ac-aem}

Tack vare integrationen mellan Adobe Campaign och Adobe Experience Manager kan ni hantera innehållet i era e-postleveranser och era formulär direkt i Adobe Experience Manager.

[Upptäck hur du redigerar din Adobe Experience Manager som Cloud Service-innehåll i Campaign-webbgränssnittet](https://experienceleague.adobe.com/docs/campaign-web/v8/integrations/aem-content.html){target="_blank"}.

[Läs mer om Adobe Experience Manager i det här dokumentet](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/campaignonpremise.html#aem-and-adobe-campaign-integration-workflow){target="_blank"}.


>[!NOTE]
>
>Som hanterad molntjänstanvändare [kontaktar du Adobe](../start/campaign-faq.md#support) för att integrera Adobe Experience Manager med Campaign.

## Importera innehåll från Adobe Experience Manager {#integrating-with-aem}

Den här integreringen kan till exempel användas för att skapa ett nyhetsbrev i Adobe Experience Manager som sedan används i Adobe Campaign som en del av en e-postkampanj.

**Från Adobe Experience Manager:**

1. Navigera till [!DNL Adobe Experience Manager]-författarinstansen och klicka på Adobe Experience längst upp till vänster på sidan. Välj **[!UICONTROL Sites]** på menyn.

   ![](assets/aem_authoring_1.png)

1. Åtkomst till **[!UICONTROL Campaigns > Name of your brand (here we.Shopping) > Main Area > Email]**.

1. Klicka på **[!UICONTROL Create]** och välj **[!UICONTROL Page]** i listrutan.

   ![](assets/aem_authoring_2.png)

1. Välj mallen **[!UICONTROL Adobe Campaign Email]** och ge nyhetsbrevet ett namn.

1. När du har skapat sidan går du till menyn **[!UICONTROL Page information]** och klickar på **[!UICONTROL Open Properties]**.

   ![](assets/aem_authoring_3.png)

1. Anpassa e-postinnehållet genom att lägga till komponenter, till exempel anpassningsfält från Adobe Campaign. Läs mer i [Adobe Experience Manager-dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/authoring/aem-adobe-campaign/campaign.html#editing-email-content){target="_blank"}.

1. När e-postmeddelandet är klart går du till menyn **[!UICONTROL Page information]** och klickar på **[!UICONTROL Start workflow]**.

   ![](assets/aem_authoring_4.png)

1. I den första listrutan väljer du **[!UICONTROL Approve Adobe Campaign]** som arbetsflödesmodell och klickar på **[!UICONTROL Start workflow]**.

   ![](assets/aem_authoring_5.png)

1. En ansvarsfriskrivning visas högst upp på sidan med datumet `This page is subject to the workflow Approve for Adobe Campaign`. Klicka på **[!UICONTROL Complete]** bredvid ansvarsfriskrivningen för att bekräfta granskningen och klicka på **[!UICONTROL Ok]**.

1. Klicka på **[!UICONTROL Complete]** igen och välj **[!UICONTROL Newsletter approval]** i listrutan **[!UICONTROL Next Step]**.

   ![](assets/aem_authoring_6.png)

Nyhetsbrevet är nu klart och synkroniserat i Adobe Campaign.

**Från Adobe Campaign:**

1. Klicka på **[!UICONTROL Deliveries]** och sedan **[!UICONTROL Create]** på fliken **[!UICONTROL Campaigns]**.

1. Välj mallen **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** i listrutan **[!UICONTROL Delivery template]**.

   ![](assets/aem_authoring_7.png)

1. Lägg till en **[!UICONTROL Label]** i leveransen och klicka på **[!UICONTROL Continue]**.

1. Klicka på **[!UICONTROL Synchronize]** för att komma åt dina AEM-leveranser.

   Om knappen inte visas i gränssnittet går du till knappen **[!UICONTROL Properties]** och öppnar fliken **[!UICONTROL Advanced]**. Kontrollera att fältet **[!UICONTROL Content editing mode]** är konfigurerat till **[!UICONTROL AEM]** och ange din AEM-instansinformation i fältet **[!UICONTROL AEM account]**.

   ![](assets/aem_authoring_8.png)

1. Markera den AEM-leverans som tidigare skapats i [!DNL Adobe Experience Manager] och bekräfta genom att klicka på **[!UICONTROL Ok]**.

   ![](assets/aem_authoring_11.png)

1. Klicka på knappen **[!UICONTROL Refresh content]** när du har ändrat din AEM-leverans.

   ![](assets/aem_authoring_12.png)

1. Klicka på **[!UICONTROL Desynchronize]** om du vill ta bort länken mellan Experience Manager och Campaign.

Din e-post kan nu skickas till din målgrupp.

## Importera resurser från Adobe Experience Manager Assets bibliotek {#assets-library}

Du kan också infoga resurser direkt från [!DNL Adobe Experience Manager Assets Library] när du redigerar ett e-postmeddelande eller en landningssida i Adobe Campaign. Den här funktionen beskrivs i [Adobe Experience Manager Assets-dokumentationen](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/managing/manage-assets.html){target="_blank"}.

**Från Adobe Experience Manager:**

1. Navigera till [!DNL Adobe Experience Manager]-författarinstansen och klicka på Adobe Experience längst upp till vänster på sidan. Välj **[!UICONTROL Assets]** `>` **[!UICONTROL Files]** på menyn.

   ![](assets/aem_assets_1.png)

1. Klicka på **Skapa** och sedan på **Filer** för att importera resursen till ditt **Adobe Experience Manager Assets-bibliotek**. Läs mer i [Adobe Experience Manager-dokumentationen](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/managing/manage-assets.html#uploading-assets){target="_blank"}.

   ![](assets/aem_assets_2.png)

1. Byt namn på resursen om det behövs och välj **Överför**.

Resursen har nu överförts till ditt **Adobe Experience Manager Assets-bibliotek**.

**Från Adobe Campaign:**

1. Skapa en ny leverans i Adobe Campaign genom att gå till fliken **Kampanjer**, klicka på **Leveranser** och klicka på knappen **Skapa** ovanför listan över befintliga leveranser.

   ![](assets/aem_assets_3.png)

1. Välj en **leveransmall** och ge sedan leveransen ett namn.

1. Definiera och anpassa meddelandeinnehållet. [Läs mer](../send/email.md)

1. Om du vill använda ditt **Adobe Experience Manager Assets-bibliotek** öppnar du **[!UICONTROL Properties]** för din AEM-leverans och väljer fliken **[!UICONTROL Advanced]** .

   Välj ditt **AEM-konto** och aktivera alternativet **[!UICONTROL Use above AEM instance as shared asset library]**.

   ![](assets/aem_authoring_9.png)

1. Gå till menyn **[!UICONTROL Select a shared asset]** från ikonen **Bild** .

   ![](assets/aem_assets_4.png)

1. I urvalsfönstret väljer du en bild i ditt **Adobe Experience Manager Assets-bibliotek** och sedan **Välj**.

   ![](assets/aem_assets_5.png)

Din mediefil överförs nu till din e-postleverans. Nu kan du ange målgruppen, bekräfta leveransen och fortsätta skicka den.
