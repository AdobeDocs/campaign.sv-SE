---
product: Adobe Campaign
title: Skicka push-meddelanden med Adobe Campaign
description: Kom igång med push-meddelanden i Campaign
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: c6f1cfdec3d05a81f8885cc73b370723024f858f
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Skapa och skicka push-meddelanden

Med mobilappsleveranser kan du skicka meddelanden till iOS- och Android-system.

Om du vill skicka push-meddelanden i Adobe Campaign måste du:

1. Konfigurera kampanjmiljön
1. Skapa en informationstjänst av mobiltyp för ditt mobilprogram.
1. Lägg till iOS- och Android-versionerna av programmet i den här tjänsten.
1. Skapa en leverans för både iOS och Android.

[!DNL :arrow_upper_right:] Läs om hur du kommer igång med mobilappar i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/about-mobile-app-channel.html)

## Integrera med Adobe SDK

### Integrera Campaign SDK

Campaign SDK underlättar integreringen av mobilapplikationer i Adobe Campaign.

[!DNL :arrow_upper_right:] Lär dig hur du integrerar Campaign SDK med din app i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en#loading-campaign-sdk)

### Konfigurera Campaign Extension i Launch

Ni kan integrera Adobe Experience Platform Launch SDK med Campaign genom att utnyttja tillägget Campaign Classic.

[!DNL :arrow_upper_right:] Läs mer i dokumentationen för  [Adobe Mobile SDK](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaignclassic)

## Konfigurera appinställningarna i Campaign

Du måste definiera dina inställningar för iOS- och Android-appar i Adobe Campaign.

[!DNL :arrow_upper_right:] Riktlinjer för konfiguration av iOS finns i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application.html?lang=en#sending-messages)

[!DNL :arrow_upper_right:] Riktlinjer för konfiguration av Android finns i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application-android.html?lang=en#sending-messages)

## Skapa ditt första push-meddelande

I det här avsnittet beskrivs de element som är specifika för leveransen av iOS- och Android-meddelanden.

[!DNL :arrow_upper_right:] Alla steg för att skapa push-meddelanden finns i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/creating-notifications.html?lang=en#sending-notifications-on-ios)

>[!CAUTION]
>
>Med Campaign v8 är mobilregistreringen nu **asynkron**. [Läs mer](../dev/staging.md)

Om du vill skapa en ny leverans går du till fliken **[!UICONTROL Campaigns]**, klickar på **[!UICONTROL Deliveries]** och klickar på **[!UICONTROL Create]** ovanför listan över befintliga leveranser.

![](assets/delivery_step_1.png)

### Skicka meddelanden på iOS {#sending-notifications-on-ios}

1. Välj leveransmallen **[!UICONTROL Deliver on iOS]** och klicka på **[!UICONTROL Continue]**.

   ![](assets/push-template-ios.png)

1. Om du vill definiera målet för meddelandet klickar du på länken **[!UICONTROL To]** och sedan på **[!UICONTROL Add]**.

   ![](assets/push-ios-select-target.png)

1. Välj **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, välj den tjänst som är relevant för ditt mobilprogram och välj sedan iOS-versionen av programmet.

   ![](assets/push-ios-subscribers.png)

1. Välj meddelandetyp: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, **[!UICONTROL Alert and badge]** eller **[!UICONTROL Silent Push]**.

   ![](assets/push-ios-alert.png)

1. I fältet **[!UICONTROL Title]** anger du etiketten för titeln som du vill ska visas i meddelandet.

1. Ange **[!UICONTROL Message]** och **[!UICONTROL Value of the badge]** baserat på den valda meddelandetypen.

1. Med **[!UICONTROL Action button]** kan du definiera en etikett för åtgärdsknappen som visas i varningsmeddelanden (**action_loc_key** fält för nyttolasten).

1. I fältet **[!UICONTROL Play a sound]** väljer du det ljud som ska spelas upp av mobilterminalen när meddelandet tas emot.

1. I fältet **[!UICONTROL Application variables]** anger du värdet för varje variabel. Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. När meddelandet har konfigurerats klickar du på fliken **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/push-ios-preview.png)

### Skicka meddelanden på Android {#sending-notifications-on-android}

1. Välj leveransmallen **[!UICONTROL Deliver on Android (android)]**.

   ![](assets/push-template-android.png)

1. Om du vill definiera målet för meddelandet klickar du på länken **[!UICONTROL To]** och sedan på **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_android_2.png)

1. Välj **[!UICONTROL Subscribers of an Android mobile application]**, välj den tjänst som är relevant för ditt mobilprogram (Neotrips, i det här fallet) och välj sedan Android-versionen av programmet.

   ![](assets/push-android-select-target.png)

1. Ange sedan innehållet för meddelandet.

   ![](assets/push-android-content.png)

1. Klicka på ikonen **[!UICONTROL Insert emoticon]** för att infoga uttryckssymboler i push-meddelandet.

1. I fältet **[!UICONTROL Application variables]** anger du värdet för varje variabel. Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. När meddelandet har konfigurerats klickar du på fliken **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/push-android-preview.png)

## Testa, skicka och övervaka dina push-meddelanden

Använd samma process som för e-postleveranser om du vill skicka ett korrektur och den slutliga leveransen.

När du har skickat meddelanden kan du övervaka och spåra dina leveranser.