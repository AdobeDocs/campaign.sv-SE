---
product: Adobe Campaign
title: Skicka push-meddelanden med Adobe Campaign
description: Kom igång med push-meddelanden i Campaign
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: b11b42220dae7d0a878ba102523ee2825d6fb2e2
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

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

[!DNL :arrow_upper_right:] Lär dig hur du skapar dina första push-meddelanden i  [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/creating-notifications.html?lang=en#sending-notifications-on-ios)


>[!CAUTION]
>
>Med Campaign v8-mobilregistrering är nu **asynkron**. [Läs mer](../dev/staging.md)
