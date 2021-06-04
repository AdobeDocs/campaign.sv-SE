---
product: Adobe Campaign
title: Skicka SMS med Adobe Campaign
description: Kom igång med SMS i Campaign
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: e65750c4e9ebd0367f0430455cac2cc6502ade7e
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 1%

---

# Skapa och skicka SMS

Använd Adobe Campaign för att skicka personaliserade SMS-meddelanden.

[!DNL :arrow_upper_right:] Lär dig hur du kommer igång med SMS-kanal i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-channel.html)

>[!NOTE]
>
>Med Adobe Campaign kan du även skicka push-meddelanden på mobiler via dess **Adobe Campaign Mobile App Channel (NMAC)**-alternativ. Läs mer i [det här avsnittet](push.md).

## Konfigurera SMS-kanal

Om du vill skicka till en mobiltelefon behöver du:

* Ett externt konto som anger en koppling och typ av meddelande.

* En leveransmall där det här externa kontot refereras.

!DNL:arrow_upper_right:] Lär dig konfigurera en SMS-kanal i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up.html?lang=en#sending-messages)

Innan du börjar skicka SMS:

* Kontrollera att mottagarprofilerna innehåller minst en mobiltelefon i profilen.
* Läs igenom Adobe Campaign Classic [Bästa praxis för leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/delivery-best-practices.html?lang=en#sending-messages) som även gäller Campaign v8.

Dessutom måste du känna till SMS-protokollet och inställningarna. Gå igenom anslutningskonfigurationen mellan Adobe Campaign och en SMPP-leverantör i [det här dokumentet](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-protocol.html?lang=en#sending-messages).

## Skapa din första SMS-leverans

1. Om du vill skapa en ny leverans går du till fliken **[!UICONTROL Campaigns]**, klickar på **[!UICONTROL Deliveries]** och klickar på **[!UICONTROL Create]** ovanför listan över befintliga leveranser.

   ![](assets/delivery_step_1.png)

   [!DNL :arrow_upper_right:] Global information om hur du skapar en leverans finns i  [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-about-delivery-creation-steps.html?lang=en#sending-messages).

1. Välj en leveransmall som refererar till det relevanta externa kontot för att skicka SMS-leveranser.

   ![](assets/sms-template-list.png)

   [!DNL :arrow_upper_right:] Lär dig hur du skapar ett SMPP-externt konto i dokumentationen för  [Campaign Classic v7](https://experienceleague.corp.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up.html?lang=en#creating-an-smpp-external-account)

   [!DNL :arrow_upper_right:] Lär dig hur du skapar en leveransmall som kan skickas till mobiler i dokumentationen för  [Campaign Classic v7](https://experienceleague.corp.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up.html?lang=en#changing-the-delivery-template)

1. Identifiera leveransen med en etikett, kod och beskrivning.

1. Klicka på **[!UICONTROL Continue]** för att bekräfta och visa meddelandekonfigurationsfönstret.

1. Ange innehållet i meddelandet i **[!UICONTROL Text content]**-avsnittet i guiden, inklusive anpassningsfält efter behov.

   ![](assets/sms-content.png)

1. Välj målpopulation.

De viktigaste stegen för att skapa och utforma ett SMS finns i Campaign Classic v7-dokumentationen:

* Skapa ett SMS

   [!DNL :arrow_upper_right:] [Lär dig hur du skapar en SMS-leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-create.html?lang=en#sending-messages)

* Designa SMS-innehåll

   [!DNL :arrow_upper_right:] [Lär dig hur du definierar SMS-innehåll](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-create.html?lang=en#defining-the-sms-content)

* Välj publik för ditt e-postmeddelande

   [!DNL :arrow_upper_right:] [Lär dig definiera målpopulationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-defining-the-target-population.html)

[!DNL :bulb:] Stegen för att definiera en målgrupp finns på  [den här sidan](../start/audiences.md).

## Testa ditt SMS

Om du vill visa återgivningen av meddelandet med dess anpassning klickar du på **[!UICONTROL Preview]** och väljer en mottagare.

![](assets/sms-preview.png)

Mer information om hur du skickar ett korrektur finns i följande avsnitt i dokumentationen för Campaign Classic v7:

* Validera en leverans och skicka korrektur
   [!DNL :arrow_upper_right:] [Lär dig viktiga steg för att validera en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html)
* Lägg till dirigerade adresser
   [!DNL :arrow_upper_right:] [Läs mer om dirigeringsadresser](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-seed-addresses/about-seed-addresses.html)

## Skicka och övervaka SMS-leveranser

De viktigaste stegen för att skicka och övervaka ett SMS finns i dokumentationen för Campaign Classic v7:

* Skicka, övervaka och spåra SMS-leveranser

   [!DNL :arrow_upper_right:] [Läs om verktygen för att skicka, övervaka och spåra SMS](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-send.html?lang=en#sending-messages)
* Felsöka SMS-leveranser

   [!DNL :arrow_upper_right:] [Läs mer om felsökning av SMS](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/troubleshooting-sms.html?lang=en#sending-messages)
