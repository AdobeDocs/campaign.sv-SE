---
title: Skicka push-meddelanden med Adobe Campaign
description: Kom igång med push-meddelanden i Campaign
feature: Overview
role: Data Engineer
level: Beginner
exl-id: f04c6e0c-f2b9-496a-9697-04ef4c3411ee
source-git-commit: a18141274b4934d45ecc82ce5d872c86e141a96f
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# Skapa och skicka push-meddelanden

Med mobilappsleveranser kan du skicka meddelanden till iOS- och Android-system.

Om du vill skicka push-meddelanden i Adobe Campaign måste du:

1. Konfigurera kampanjmiljön
1. Skapa en informationstjänst av mobiltyp för ditt mobilprogram.
1. Lägg till iOS- och Android-versionerna av programmet i den här tjänsten.
1. Skapa en leverans för både iOS och Android.

![](../assets/do-not-localize/book.png) Lär dig hur du kommer igång med mobilappen i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/about-mobile-app-channel.html){target=&quot;_blank&quot;}

## Integrera Campaign SDK

Campaign SDK underlättar integreringen av mobilapplikationer i Adobe Campaign.

Kompatibla SDK-versioner visas i [Matris för kampanjkompatibilitet](../start/compatibility-matrix.md#MobileSDK).

![](../assets/do-not-localize/glass.png) Lär dig hur du integrerar Campaign Android och iOS SDK med appen i [det här avsnittet](../config/push-config.md)

<!--
### Configure Campaign Extension in Launch

You can integrate Adobe Experience Platorm Launch SDK with Campaign, by leveraging Campaign Classic extension.

![](../assets/do-not-localize/book.png) Learn more in [Adobe Mobile SDK documentation](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaignclassic){target="_blank"}

-->

## Konfigurera appinställningarna i Campaign

Du måste definiera inställningarna för dina iOS- och Android-appar i Adobe Campaign.

![](../assets/do-not-localize/book.png) Riktlinjer för konfiguration av iOS finns i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application.html?lang=en#sending-messages){target=&quot;_blank&quot;}

![](../assets/do-not-localize/book.png) Riktlinjer för konfiguration av Android finns i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application-android.html?lang=en#sending-messages){target=&quot;_blank&quot;}

## Skapa ditt första push-meddelande

I det här avsnittet beskrivs de element som är specifika för leveransen av iOS- och Android-meddelanden.

>[!CAUTION]
>
>Med Campaign v8 är mobilregistrering nu **asynkron**. [Läs mer](../dev/staging.md)

Bläddra till **[!UICONTROL Campaigns]** flik, klicka **[!UICONTROL Deliveries]** och klicka på **[!UICONTROL Create]** ovanför listan över befintliga leveranser.

![](assets/delivery_step_1.png)

![](../assets/do-not-localize/book.png) Global information om hur du skapar en leverans finns i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-about-delivery-creation-steps.html?lang=en#sending-messages){target=&quot;_blank&quot;}

### Skicka meddelanden på iOS {#send-notifications-on-ios}

1. Välj **[!UICONTROL Deliver on iOS]** leveransmall och klicka på **[!UICONTROL Continue]**.

   ![](assets/push-template-ios.png)

1. Om du vill definiera målet för meddelandet klickar du på knappen **[!UICONTROL To]** klicka på **[!UICONTROL Add]**.

   ![](assets/push-ios-select-target.png)

1. Välj **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, väljer den tjänst som är relevant för ditt mobilprogram och väljer sedan iOS-versionen av programmet.

   ![](assets/push-ios-subscribers.png)

1. Välj meddelandetyp: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, **[!UICONTROL Alert and badge]** eller **[!UICONTROL Silent Push]**.

   ![](assets/push-ios-alert.png)

1. I **[!UICONTROL Title]** anger du etiketten för den titel som du vill ska visas i meddelandet.

1. Ange **[!UICONTROL Message]** och **[!UICONTROL Value of the badge]** baserat på den valda meddelandetypen.

1. Du kan också definiera följande element:

   * The **[!UICONTROL Action button]** gör att du kan definiera en etikett för åtgärdsknappen som visas i varningsmeddelanden (**action_loc_key** nyttolastens fält).

   * I **[!UICONTROL Play a sound]** markerar du det ljud som ska spelas upp av mobilterminalen när meddelandet tas emot.

   * I **[!UICONTROL Application variables]** anger du värdet för varje variabel. Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. När meddelandet har konfigurerats klickar du på **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/push-ios-preview.png)


### Skicka meddelanden på Android {#send-notifications-on-android}

1. Välj **[!UICONTROL Deliver on Android (android)]** leveransmall.

   ![](assets/push-template-android.png)

1. Om du vill definiera målet för meddelandet klickar du på knappen **[!UICONTROL To]** klicka på **[!UICONTROL Add]**.

   ![](assets/push-android-select-target.png)

1. Välj **[!UICONTROL Subscribers of an Android mobile application]** väljer du den tjänst som är relevant för ditt mobilprogram (i det här fallet Neotrips) och väljer sedan Android-versionen av programmet.

   ![](assets/push-ios-subscribers.png)

1. Ange sedan innehållet för meddelandet.

   ![](assets/push-android-content.png)

1. Klicka på **[!UICONTROL Insert emoticon]** om du vill infoga uttryckssymboler i ditt push-meddelande.

1. I **[!UICONTROL Application variables]** anger du värdet för varje variabel. Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. När meddelandet har konfigurerats klickar du på **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   <!--![](assets/push-android-preview.png)-->

## Testa, skicka och övervaka dina push-meddelanden

Använd samma process som för e-postleveranser om du vill skicka ett korrektur och den slutliga leveransen. Läs mer i Campaign Classic v7-dokumentationen:

* Validera en leverans och skicka korrektur
   ![](../assets/do-not-localize/book.png) [Lär dig viktiga steg för att validera en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html){target=&quot;_blank&quot;}

* Bekräfta och skicka leveransen
   ![](../assets/do-not-localize/book.png) [Lär dig viktiga steg för att skicka en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html?lang=en){target=&quot;_blank&quot;}

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Läs mer i Campaign Classic v7-dokumentationen:

* Kantlinjer för push-meddelanden
   ![](../assets/do-not-localize/book.png) [Läs mer om karantän för push-meddelanden](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#push-notification-quarantines){target=&quot;_blank&quot;}

* Felsökning
   ![](../assets/do-not-localize/book.png) [Lär dig hur du felsöker push-meddelanden](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/troubleshooting.html?lang=en){target=&quot;_blank&quot;}
