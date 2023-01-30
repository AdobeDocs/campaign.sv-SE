---
product: campaign
title: Leveranser över flera kanaler
description: Läs mer om flerkanalsleveranser
feature: Workflows, Channels Activity
exl-id: fedcffcd-cf9b-4c3d-bd25-cb87dda30192
source-git-commit: 6464e1121b907f44db9c0c3add28b54486ecf834
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 4%

---

# Leveranser över flera kanaler{#cross-channel-deliveries}

Flerkanalsleveranser är tillgängliga i **[!UICONTROL Deliveries]** flik för [kampanjarbetsflöde](campaign-workflows.md) verksamhet.

Välj den mall som du vill basera leveransen på och definiera innehållet i mallen.

Du kan ange ett mål för leveransen uppströms arbetsflödet med hjälp av olika målinriktningsaktiviteter.

I exemplet nedan kan du lära dig hur du skapar ett arbetsflöde för att skicka ett e-postmeddelande eller ett SMS för prenumeranter på push-meddelanden, och sedan ett push-meddelande en vecka senare. Så här gör du:

1. Skapa en kampanj.
1. I **[!UICONTROL Targeting and workflows]** fliken med kampanjen, lägg till en **[!UICONTROL Query]** aktivitet.
1. Konfigurera frågan: Välj de mottagare som prenumererar på push-meddelanden som måldimension.

   >[!NOTE]
   >
   >För push-meddelanden använder du **prenumerationsprogram** måldimension.

   ![](assets/cross_channel_delivery_1.png)

1. Lägg till filtervillkoren i frågan. I det här fallet väljer vi mottagare som har ett mobilnummer eller en e-postadress.

   ![](assets/cross_channel_delivery_2.png)

1. Lägg till en **[!UICONTROL Split]** aktiviteter i ditt arbetsflöde för att dela upp mottagare som har ett mobilnummer och de som har en e-postadress.
1. I **[!UICONTROL Delivery]** väljer du en leverans för varje mål.

   Skapa leveransen på samma sätt som med en klassisk leveransguide genom att dubbelklicka på leveransaktiviteten i arbetsflödet.

   ![](assets/cross_channel_delivery_3.png)

1. Lägg till och konfigurera en **[!UICONTROL Wait]** aktivitet för att mottagarna inte ska få för många leveranser samtidigt.
1. Lägg till en **[!UICONTROL Split]** aktiviteter för att dela upp prenumeranter av iOS- eller Android-mobilprogram.

   Välj en tjänst för vart och ett av operativsystemen.

   ![](assets/cross_channel_delivery_4.png)

1. Välj och konfigurera en leverans av mobilapplikationer för vart och ett av operativsystemen.

   ![](assets/cross_channel_delivery_5.png)
