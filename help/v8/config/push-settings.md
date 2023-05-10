---
title: Integrera AEP SDK och Campaign
description: Lär dig hur du integrerar Adobe Experience Platform SDK för mobiler med din app
version: v8
feature: Push
role: Admin, Developer
level: Intermediate, Experienced
hide: true
hidefromtoc: true
source-git-commit: 3bef6d2544a86bf1d5efa4868b82ec59c7e36484
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 2%

---


# AEP SDK + Campaign: konfigurera push-meddelandekanal {#push-notification-configuration}

Innan du börjar skicka push-meddelanden med Adobe Campaign måste du se till att det finns konfigurationer och integreringar på mobilappen och för taggar i Adobe Experience Platform.

Adobe Experience Platform Mobile SDK innehåller API:er för integrering på klientsidan för mobiler via Android och iOS-kompatibla SDK:er.

Så här konfigurerar du appen med Adobe Experience Platform Mobile SDK:

1. Kontrollera [krav](#before-starting).
1. Konfigurera en [mobil tagg, egenskap](#launch-property) i Adobe Experience Platform Data Collection.
1. Få en mer detaljerad beskrivning av Adobe Experience Platform Mobile SDK [på den här sidan](https://developer.adobe.com/client-sdks/documentation/getting-started/get-the-sdk/){target="_blank"}.
1. (valfritt) Aktivera loggnings- och livscykelstatistik, som detaljerad [på den här sidan](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/){target="_blank"}.
1. (valfritt) Lägg till [Adobe Experience Platform Assurance för din app](https://developer.adobe.com/client-sdks/documentation/getting-started/validate/){target="_blank"} to validate your implementation. Learn how to implement Adobe Experience Platform Assurance extension [in this page](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/){target="_blank"}.
1. Följ [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/){target="_blank"} om du vill konfigurera med Adobe Experience Platform Mobile SDK i appen.
1. Installera och konfigurera [Adobe Campaign Extension](#configure-extension) i er mobilegendom.
1. Konfigurera dina iOS- och Android-mobiltjänster i Adobe Campaign enligt [på den här sidan](../send/push.md#push-config).


## Förhandskrav {#before-starting}

### Konfigurera behörigheter {#setup-permissions}

Innan du skapar ett mobilprogram måste du kontrollera att du har eller tilldelar rätt användarbehörigheter för taggar i Adobe Experience Platform. Användarbehörigheter för taggar i Adobe Experience Platform tilldelas användare via Adobe Admin Console. Läs mer i [Dokumentation för taggar](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html){target="_blank"}.

>[!CAUTION]
>
>Push-konfigurationen måste utföras av en expertanvändare. Beroende på din implementeringsmodell och vilka profiler som används i den här implementeringen kan du behöva tilldela en enskild produktprofil den fullständiga behörighetsuppsättningen eller dela behörigheter mellan apputvecklaren och **Adobe Campaign** administratör.

Tilldela **Egenskap** och **Företag** gör du så här:

1. Öppna **[!DNL Admin Console]**.
1. Från **[!UICONTROL Products]** väljer du **[!UICONTROL Adobe Experience Platform Data Collection]** kort.
1. Välj en befintlig **[!UICONTROL Product Profile]** eller skapa en ny med **[!UICONTROL New profile]** -knappen. Lär dig skapa en ny **[!UICONTROL New profile]** i [Dokumentation till Admin Console](https://experienceleague.adobe.com/docs/experience-platform/access-control/ui/create-profile.html#ui){target="_blank"}.
1. På fliken **[!UICONTROL Permissions]** väljer du **[!UICONTROL Property Rights]**.
1. Klicka på **[!UICONTROL Add all]**. Detta lägger till följande rättigheter i din produktprofil:
   * **[!UICONTROL Approve]**
   * **[!UICONTROL Develop]**
   * **[!UICONTROL Edit Property]**
   * **[!UICONTROL Manage Environments]**
   * **[!UICONTROL Manage Extensions]**
   * **[!UICONTROL Publish]**

   Dessa behörigheter krävs för att installera och publicera Adobe Campaign-tillägget och publicera appegenskapen i **Adobe Experience Platform Mobile SDK**.

1. Välj sedan **[!UICONTROL Company rights]** i den vänstra menyn.
1. Lägg till följande rättigheter:

   * **[!UICONTROL Manage App Configurations]**
   * **[!UICONTROL Manage Properties]**

   Dessa behörigheter krävs för att mobilappsutvecklaren ska kunna ställa in push-autentiseringsuppgifter i **Adobe Experience Platform Data Collection**.

1. Klicka på **[!UICONTROL Save]**.

Om du vill tilldela **[!UICONTROL Product profile]** för användarna, följ stegen nedan:

1. Öppna **[!DNL Admin Console]**.
1. Från **[!UICONTROL Products]** väljer du **[!UICONTROL Adobe Experience Platform Data Collection]** kort.
1. Välj din tidigare konfigurerade **[!UICONTROL Product profile]**.
1. Klicka på **[!UICONTROL Add user]** på fliken **[!UICONTROL Users]**.
1. Skriv in användarens namn eller e-postadress och markera användaren. Klicka sedan på **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Om användaren inte redan har skapats i Admin Console går du till [Lägga till användardokumentation](https://helpx.adobe.com/enterprise/using/manage-users-individually.html#add-users){target="_blank"}.

### Konfigurera din app {#configure-app}

Den tekniska konfigurationen innefattar nära samarbete mellan apputvecklaren och företagsadministratören. Innan du skickar push-meddelanden med [!DNL Adobe Campaign]måste du definiera inställningar i [!DNL Adobe Experience Platform Data Collection] och integrera mobilappen med Adobe Experience Platform Mobile SDK:er.

Följ implementeringsstegen som beskrivs i länkarna nedan:

* För **Apple iOS**: Lär dig hur du registrerar din app med APN:er i [Apple Documentation](https://developer.apple.com/documentation/usernotifications/registering_your_app_with_apns){target="_blank"}
* För **Google Android**: Lär dig hur du konfigurerar en Firebase Cloud Messaging-klientapp på Android i [Google Documentation](https://firebase.google.com/docs/cloud-messaging/android/client){target="_blank"}

<!--
## Add your app push credentials in Adobe Experience Platform Data Collection {#push-credentials}

After granting the correct user permissions, you now need to add your mobile application push credentials in Adobe Experience Platform Data Collection. 

The mobile app push credential registration is required to authorize Adobe to send push notifications on your behalf. Refer to the steps detailed below:

1. From [!DNL Adobe Experience Platform Data Collection], browse to **[!UICONTROL App Surfaces]** in the left rail.

1. Click **[!UICONTROL Create App Surface]** to create a new configuration.

1. Enter a **[!UICONTROL Name]** for the configuration.

1. From **[!UICONTROL Mobile Application Configuration]**, select the system and enter settings.

    * **For iOS**

        1. Enter the mobile app **Bundle Id** in the **[!UICONTROL App ID (iOS Bundle ID)]** field. The app Bundle ID can be found in the **General** tab of the primary target in **XCode**.
        
        1. Switched on the **[!UICONTROL Push Credentials]** button to add your credentials.
        
        1. Drag and drop your .p8 Apple Push Notification Authentication Key file. This key can be acquired from the **Certificates**, **Identifiers** and **Profiles** page.

        1. Provide the **Key ID**. This is a 10 character string assigned during the creation of p8 auth key. It can be found under **Keys** tab in **Certificates**, **Identifiers** and **Profiles** page.
        
        1. Provide the **Team ID**. This is a string value which can be found under the Membership tab.

    * **For Android**

        1. Provide the **[!UICONTROL App ID (Android package name)]**: usually the package name is the app id in your `build.gradle` file.

        1. Switched on the **[!UICONTROL Push Credentials]** button to add your credentials.

        1. Drag and drop the FCM push credentials. For more details on how to get the push credentials refer to [Google Documentation](https://firebase.google.com/docs/admin/setup#initialize-sdk){target="_blank"}.
    

1. Click **[!UICONTROL Save]** to create your app configuration.
-->

## Konfigurera en mobil taggegenskap i Adobe Experience Platform Data Collection {#launch-property}

Genom att konfigurera en mobil egenskap kan utvecklaren eller marknadsföraren av mobilappen konfigurera SDK:n för mobilappen. Du skapar vanligtvis en mobil egenskap för varje mobilprogram som du vill hantera. Lär dig hur du skapar och konfigurerar en mobil egenskap i [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/create-a-mobile-property/){target="_blank"}.

För att de SDK:er som behövs för att push-meddelanden ska fungera behöver du följande SDK-tillägg för både Android och iOS:

* **[!UICONTROL Mobile Core]** (installeras automatiskt)
* **[!UICONTROL Profile]** (installeras automatiskt)
* **[!UICONTROL Adobe Experience Platform Edge]**
* **[!UICONTROL Adobe Experience Platform Assurance]**, valfritt men rekommenderas för felsökning av mobilimplementeringen.

Läs mer om [!DNL Adobe Experience Platform Data Collection] taggar i [Adobe Experience Platform-dokumentation](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/initial-configuration/configure-tags.html){target="_blank"}.

Öppna den nya taggegenskapen och skapa ett bibliotek när du har skapat den. Så här gör du:

1. Bläddra till **Publiceringsflöde** i den vänstra navigeringen och välj **Lägg till bibliotek**.
1. Ange namnet på biblioteket och välj miljö.
1. Välj **Lägg till alla ändrade resurser** och **Spara och bygg för utveckling**.
1. Äntligen anger du det här biblioteket som ditt arbetsbibliotek från **Välj ett arbetsbibliotek** -knappen.


## Konfigurera Adobe Campaign Extension i din mobila egenskap {#configure-extension}

The **Adobe Campaign Classic-tillägg** för Adobe Experience Platform Mobile SDK:er driver push-meddelanden för dina mobilappar och hjälper dig att samla in push-tokens och hantera interaktionsmätning med Adobe Experience Platform tjänster.

Tillägget är förinstallerat i din miljö och måste konfigureras. Så här konfigurerar du tillägget för din mobila taggegenskap:

1. Öppna taggegenskapen som du skapade tidigare.
1. I den vänstra navigeringen bläddrar du till **Tillägg** och öppna **Katalog** -fliken. Använd sökfältet för att hitta **Adobe Campaign Classic** tillägg.
1. På Campaign Classic-kortet klickar du på **Installera** -knappen.
1. Ange inställningar enligt beskrivningen i [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/){target="_blank"}.

Nu kan du lägga till Campaign i din app, vilket beskrivs i  [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#add-campaign-classic-to-your-app){target="_blank"}.

## Konfigurera dina mobiltjänster i Campaign{#push-service}

När mobilappen har konfigurerats i [!DNL Adobe Experience Platform Data Collection]måste du skapa två tjänster (en för iOS-enheter, en för Android-enheter) för att kunna skicka push-meddelanden från **[!DNL Adobe Campaign]**.

Lär dig hur du skapar och konfigurerar en tjänst för push-meddelanden i iOS och Android i [det här avsnittet](../send/push.md#push-config).
