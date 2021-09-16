---
title: Skicka SMS med Adobe Campaign
description: Kom igång med SMS i Campaign
feature: Overview
role: Data Engineer
level: Beginner
exl-id: e2e2922a-2058-4588-b1b5-6997f29ee663
source-git-commit: f071fc227dac6d72873744ba56eb0b4b676de5dd
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---

# Skapa och skicka SMS

Använd Adobe Campaign för att skicka personaliserade SMS-meddelanden.

↗️ Lär dig hur du kommer igång med SMS-kanal i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-channel.html){target=&quot;_blank&quot;}

>[!NOTE]
>
>Med Adobe Campaign kan du även skicka push-meddelanden på mobiler via dess **Adobe Campaign Mobile App Channel (NMAC)**-alternativ. Läs mer i [det här avsnittet](push.md).

## Konfigurera SMS-kanal

Om du vill skicka till en mobiltelefon behöver du:

* Ett externt konto som anger en koppling och typ av meddelande.

* En leveransmall där det här externa kontot refereras.

↗️ Lär dig konfigurera en SMS-kanal i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up.html?lang=en#sending-messages){target=&quot;_blank&quot;}

Innan du börjar skicka SMS:

* Kontrollera att mottagarprofilerna innehåller minst en mobiltelefon i profilen.
* Läs igenom Adobe Campaign Classic [Bästa praxis för leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/delivery-best-practices.html?lang=en#sending-messages){target=&quot;_blank&quot;} som även gäller Campaign v8.

Dessutom måste du känna till SMS-protokollet och inställningarna. Gå igenom anslutningsinställningarna mellan Adobe Campaign och en SMPP-leverantör i [det här dokumentet](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-protocol.html?lang=en#sending-messages){target=&quot;_blank&quot;}.

## Skapa din första SMS-leverans

1. Om du vill skapa en ny leverans går du till fliken **[!UICONTROL Campaigns]**, klickar på **[!UICONTROL Deliveries]** och klickar på **[!UICONTROL Create]** ovanför listan över befintliga leveranser.

   ![](assets/delivery_step_1.png)

   ↗️ Global information om hur du skapar en leverans finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-about-delivery-creation-steps.html?lang=en#sending-messages){target=&quot;_blank&quot;}.

1. Välj en leveransmall som refererar till det relevanta externa kontot för att skicka SMS-leveranser.

   ![](assets/sms-template-list.png)

   ↗️ Lär dig hur du skapar ett externt SMPP-konto i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up.html?lang=en#creating-an-smpp-external-account){target=&quot;_blank&quot;}

   ↗️ Lär dig hur du skapar en leveransmall som ska skickas till mobiler i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up.html?lang=en#changing-the-delivery-template){target=&quot;_blank&quot;}

1. Identifiera leveransen med en etikett, kod och beskrivning.

1. Klicka på **[!UICONTROL Continue]** för att bekräfta och visa meddelandekonfigurationsfönstret.

1. Ange innehållet i meddelandet i **[!UICONTROL Text content]**-avsnittet i guiden, inklusive anpassningsfält efter behov.

   ![](assets/sms-content.png)

1. Välj målpopulation.

De viktigaste stegen för att skapa och utforma ett SMS finns i Campaign Classic v7-dokumentationen:

* Skapa ett SMS

   ↗️ [Lär dig hur du skapar en SMS-leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-create.html?lang=en#sending-messages){target=&quot;_blank&quot;}

* Designa SMS-innehåll

   ↗️ [Lär dig hur du definierar SMS-innehållet](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-create.html?lang=en#defining-the-sms-content){target=&quot;_blank&quot;}

* Välj publik för ditt e-postmeddelande

   ↗️ [Lär dig definiera målpopulationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-defining-the-target-population.html){target=&quot;_blank&quot;}

? Stegen för att definiera en målgrupp finns på [den här sidan](../start/audiences.md).

## Testa ditt SMS

Om du vill visa återgivningen av meddelandet med dess anpassning klickar du på **[!UICONTROL Preview]** och väljer en mottagare.

![](assets/sms-preview.png)

Mer information om hur du skickar ett korrektur finns i följande avsnitt i dokumentationen för Campaign Classic v7:

* Validera en leverans och skicka korrektur
↗️ [Lär dig viktiga steg för att validera en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html){target=&quot;_blank&quot;}
* Lägg till dirigerade adresser
↗️ [Lär dig mer om dirigerade adresser](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-seed-addresses/about-seed-addresses.html){target=&quot;_blank&quot;}

## Skicka och övervaka SMS-leveranser

De viktigaste stegen för att skicka och övervaka ett SMS finns i dokumentationen för Campaign Classic v7:

* Skicka, övervaka och spåra SMS-leveranser

   ↗️ [Lär dig mer om verktygen för att skicka, övervaka och spåra SMS](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-send.html?lang=en#sending-messages){target=&quot;_blank&quot;}

* Felsöka SMS-leveranser

   ↗️ [Lär dig mer om SMS-felsökning](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/troubleshooting-sms.html?lang=en#sending-messages){target=&quot;_blank&quot;}
