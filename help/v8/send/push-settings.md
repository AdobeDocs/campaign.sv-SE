---
title: Integrera AEP SDK och Campaign
description: Lär dig hur du integrerar Adobe Experience Platform Mobile SDK med din app
feature: Push
role: Admin, Developer
level: Intermediate
exl-id: 1a75f411-3f71-4114-b738-277820dc6138
source-git-commit: a288845e1f092d293d679fa9aaaf6d609de85230
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 4%

---

# Konfigurera kanal för push-meddelanden {#push-notification-configuration}

Om du vill skicka push-meddelanden med Adobe Campaign måste du först konfigurera miljön och appen så som anges på den här sidan. I Adobe Campaign är mobilappskanalen kanalen för att skicka push-meddelanden.

>[!CAUTION]
>
>Vissa viktiga ändringar av tjänsten Android Firebase Cloud Messaging (FCM) kommer att släppas 2024 och kan komma att påverka din Adobe Campaign-implementering. Konfigurationen för prenumerationstjänster för push-meddelanden för Android kan behöva uppdateras för att den här ändringen ska fungera. Du kan redan kontrollera och vidta åtgärder. [Läs mer](../../technotes/upgrades/push-technote.md).

Innan du börjar skicka push-meddelanden med Adobe Campaign måste du se till att det finns konfigurationer och integreringar på mobilappen och för taggar i Adobe Experience Platform. Adobe Experience Platform Mobile SDK erbjuder API:er för integrering på klientsidan för mobiler via Android och iOS-kompatibla SDK:er.

Så här konfigurerar du appen med Adobe Experience Platform Mobile SDK:

1. Kontrollera [förutsättningarna](#before-starting).
1. Ställ in en [mobil taggegenskap](#launch-property) i Adobe Experience Platform Data Collection.
1. Hämta Adobe Experience Platform Mobile SDK enligt informationen [på den här sidan](https://developer.adobe.com/client-sdks/documentation/getting-started/get-the-sdk/){target="_blank"}.
1. (valfritt) Aktivera loggnings- och livscykelstatistik, enligt informationen [på den här sidan](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/){target="_blank"}.
1. (valfritt) Lägg till [Adobe Experience Platform Assurance i din app](https://developer.adobe.com/client-sdks/documentation/getting-started/validate/){target="_blank"} för att validera implementeringen. Lär dig hur du implementerar Adobe Experience Platform Assurance-tillägget [ på den här sidan](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/){target="_blank"}.
1. Konfigurera dina iOS- och Android-mobiltjänster i Adobe Campaign enligt informationen [på den här sidan](#push-service).
1. Installera och konfigurera [Adobe Campaign Extension](#configure-extension) i din mobila egenskap.
1. Följ [dokumentationen för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/){target="_blank"} om du vill konfigurera Adobe Experience Platform Mobile SDK:er i din app.

## Förhandskrav {#before-starting}

### Konfigurera behörigheter {#setup-permissions}

Innan du skapar ett mobilprogram måste du kontrollera att du har eller tilldelar rätt användarbehörigheter för taggar i Adobe Experience Platform. Användarbehörigheter för taggar i Adobe Experience Platform tilldelas användare via Adobe Admin Console. Läs mer i [Tagg-dokumentationen](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=sv-SE){target="_blank"}.

>[!CAUTION]
>
>Push-konfigurationen måste utföras av en expertanvändare. Beroende på din implementeringsmodell och vilka profiler som används i den här implementeringen kan du behöva tilldela en enskild produktprofil den fullständiga behörighetsuppsättningen eller dela behörigheter mellan apputvecklaren och **Adobe Campaign** -administratören.

Följ stegen nedan för att tilldela **Egenskap** och **Företag** behörigheter:

1. Åtkomst till **[!DNL Admin Console]**.
1. Välj **[!UICONTROL Adobe Experience Platform Data Collection]**-kortet på fliken **[!UICONTROL Products]**.
1. Välj en befintlig **[!UICONTROL Product Profile]** eller skapa en ny med knappen **[!UICONTROL New profile]**. Lär dig hur du skapar en ny **[!UICONTROL New profile]** i [Admin Console-dokumentationen](https://experienceleague.adobe.com/docs/experience-platform/access-control/ui/create-profile.html?lang=sv-SE#ui){target="_blank"}.
1. På fliken **[!UICONTROL Permissions]** väljer du **[!UICONTROL Property Rights]**.
1. Klicka på **[!UICONTROL Add all]**. Detta lägger till följande rättigheter i din produktprofil:
   * **[!UICONTROL Approve]**
   * **[!UICONTROL Develop]**
   * **[!UICONTROL Edit Property]**
   * **[!UICONTROL Manage Environments]**
   * **[!UICONTROL Manage Extensions]**
   * **[!UICONTROL Publish]**

   Dessa behörigheter krävs för att installera och publicera Adobe Campaign-tillägget och publicera appegenskapen i **Adobe Experience Platform Mobile SDK**.

1. Välj sedan **[!UICONTROL Company rights]** på den vänstra menyn.
1. Lägg till följande rättigheter:

   * **[!UICONTROL Manage App Configurations]**
   * **[!UICONTROL Manage Properties]**

   Dessa behörigheter krävs för att mobilappsutvecklaren ska kunna ställa in push-autentiseringsuppgifter i **Adobe Experience Platform Data Collection**.

1. Klicka på **[!UICONTROL Save]**.

Följ stegen nedan för att tilldela **[!UICONTROL Product profile]** till användare:

1. Åtkomst till **[!DNL Admin Console]**.
1. Välj **[!UICONTROL Adobe Experience Platform Data Collection]**-kortet på fliken **[!UICONTROL Products]**.
1. Välj din tidigare konfigurerade **[!UICONTROL Product profile]**.
1. Klicka på **[!UICONTROL Add user]** på fliken **[!UICONTROL Users]**.
1. Skriv in användarens namn eller e-postadress och markera användaren. Klicka sedan på **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Om användaren inte redan har skapats i Admin Console läser du [dokumentationen till Lägg till användare](https://helpx.adobe.com/se/enterprise/using/manage-users-individually.html#add-users){target="_blank"}.

### Konfigurera din app {#configure-app}

Den tekniska konfigurationen innefattar nära samarbete mellan apputvecklaren och företagsadministratören. Innan du börjar skicka push-meddelanden med [!DNL Adobe Campaign] måste du definiera inställningar i [!DNL Adobe Experience Platform Data Collection] och integrera din mobilapp med Adobe Experience Platform Mobile SDK:er.

Följ implementeringsstegen som beskrivs i länkarna nedan:

* För **Apple iOS**: Lär dig hur du registrerar din app med APN:er i [Apple-dokumentationen](https://developer.apple.com/documentation/usernotifications/registering_your_app_with_apns){target="_blank"}
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

Genom att konfigurera en mobil egenskap kan utvecklaren eller marknadsföraren av mobilappen konfigurera SDK:n för mobilappen. Du skapar vanligtvis en mobil egenskap för varje mobilprogram som du vill hantera. Lär dig hur du skapar och konfigurerar en mobil egenskap i [dokumentationen för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/create-a-mobile-property/){target="_blank"}.
<!--
To get the SDKs needed for push notification to work you will need the following SDK extensions, for both Android and iOS:

* **[!UICONTROL Mobile Core]** (installed automatically)
* **[!UICONTROL Profile]** (installed automatically)
* **[!UICONTROL Adobe Experience Platform Edge]**
* **[!UICONTROL Adobe Experience Platform Assurance]**, optional but recommended to debug the mobile implementation.
-->

Läs mer om [!DNL Adobe Experience Platform Data Collection]-taggar i [Adobe Experience Platform-dokumentation](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/initial-configuration/configure-tags.html?lang=sv-SE){target="_blank"}.

Öppna den nya taggegenskapen och skapa ett bibliotek när du har skapat den. Så här gör du:

1. Bläddra till **Publiceringsflöde** i den vänstra navigeringen och välj **Lägg till bibliotek**.
1. Ange namnet på biblioteket och välj miljö.
1. Välj **Lägg till alla ändrade resurser** och **Spara och skapa i utveckling**.
1. Ange slutligen det här biblioteket som ditt arbetsbibliotek från knappen **Välj ett arbetsbibliotek** .

## Konfigurera dina mobiltjänster i Campaign {#push-service}

När din mobilapp har konfigurerats i [!DNL Adobe Experience Platform Data Collection] måste du skapa två tjänster (en för iOS-enheter, en för Android-enheter) för att kunna skicka push-meddelanden från **[!DNL Adobe Campaign]**.

Push-meddelanden skickas till appanvändarna via en dedikerad tjänst. När användare installerar din app prenumererar de på den här tjänsten: Adobe Campaign förlitar sig på den här tjänsten för att endast rikta sig till prenumeranterna av din app. I den här tjänsten måste du lägga till dina iOS- och Android-appar som ska skickas på enheter med iOS och Android.

Följ stegen nedan för att skapa en tjänst för att skicka push-meddelanden:

1. Bläddra till fliken **[!UICONTROL Profiles and Targets > Services and Subscriptions]** och klicka på **[!UICONTROL Create]**.

   ![](assets/new-service-push.png){width="800" align="left"}

1. Ange en **[!UICONTROL Label]** och en **[!UICONTROL Internal name]** och välj en **[!UICONTROL Mobile application]**-typ.

   >[!NOTE]
   >
   >Standardmålmappningen för **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i fältet **[!UICONTROL Target mapping]** för tjänsten. Läs mer om målmappningar på [den här sidan](../audiences/target-mappings.md).

1. Använd sedan ikonen **[!UICONTROL Add]** till höger för att definiera de mobilprogram som använder den här tjänsten.

>[!BEGINTABS]

>[!TAB iOS]

Så här skapar du en app för iOS-enheter:

1. Markera **[!UICONTROL Create an iOS application]** och klicka på **[!UICONTROL Next]**.

   ![](assets/new-ios-app.png){width="600" align="left"}

1. Ange namnet på din app i fältet **[!UICONTROL Label]**.
1. (valfritt) Du kan utöka ett push-meddelandeinnehåll med lite **[!UICONTROL Application variables]**. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

   I exemplet nedan läggs variablerna **mediaURl** och **mediaExt** till för att skapa omfattande push-meddelanden och ger sedan programmet den bild som ska visas i meddelandet.

   ![](assets/ios-app-parameters.png){width="600" align="left"}

1. Bläddra till fliken **[!UICONTROL Subscription parameters]** för att definiera mappningen med ett tillägg till schemat **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

1. Bläddra till fliken **[!UICONTROL Sounds]** för att definiera ett ljud som ska spelas upp. Klicka på **[!UICONTROL Add]** och fyll i fältet **[!UICONTROL Internal name]** som måste innehålla namnet på filen som är inbäddad i programmet eller namnet på systemljudet.

1. Klicka på **[!UICONTROL Next]** för att börja konfigurera utvecklingsprogrammet.

1. Integreringsnyckeln är specifik för varje program. Det länkar mobilprogrammet till Adobe Campaign.

   Kontrollera att samma **[!UICONTROL Integration key]** har definierats i Adobe Campaign och i programkoden via SDK.

   Läs mer i [utvecklardokumentationen](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#configuration-keys){target="_blank"}


   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** är helt anpassningsbar med strängvärde, men måste vara exakt densamma som den som anges i SDK.
   >
   > Du kan inte använda samma certifikat för utvecklingsversionen (sandlådan) och produktionsversionen av programmet.

1. Välj ikonen i fältet **[!UICONTROL Application icon]** om du vill anpassa mobilprogrammet i tjänsten.

1. Markera **[!UICONTROL Authentication mode]**. Det finns två lägen:

   * (Rekommenderas) **[!UICONTROL Token-based authentication]**: Fyll i APN-anslutningsinställningarna **[!UICONTROL Key Id]**, **[!UICONTROL Team Id]** och **[!UICONTROL Bundle Id]** och välj sedan ditt p8-certifikat genom att klicka på **[!UICONTROL Enter the private key...]**. Mer information om **[!UICONTROL Token-based authentication]** finns i [Apple-dokumentationen](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Certificate-based authentication]**: Klicka på **[!UICONTROL Enter the certificate...]**, markera din p12-nyckel och ange lösenordet som angavs av utvecklaren av mobilprogrammet. Observera att detta certifikat har ett förfallodatum och måste förnyas årligen. Uppdatera certifikaten innan de upphör att gälla för att undvika avbrott i användandet för dina användare. Certifikaten är giltiga i ett år och du måste uppdatera dem för att kunna fortsätta kommunicera med APN:er.

1. Använd knappen **[!UICONTROL Test the connection]** för att validera konfigurationen.

1. Klicka på **[!UICONTROL Next]** för att börja konfigurera produktionsprogrammet och följ stegen som anges ovan.

1. Klicka på **[!UICONTROL Finish]**.

Ditt iOS-program kan nu användas i Campaign.

>[!TAB Android]

Så här skapar du en app för Android-enheter:

1. Markera **[!UICONTROL Create an Android application]** och klicka på **[!UICONTROL Next]**.

   ![](assets/new-android-app.png){width="600" align="left"}

1. Ange namnet på din app i fältet **[!UICONTROL Label]**.
1. Integreringsnyckeln är specifik för varje program. Det länkar mobilprogrammet till Adobe Campaign.

   Kontrollera att samma **[!UICONTROL Integration key]** har definierats i Adobe Campaign och i programkoden via SDK.

   Läs mer i [utvecklardokumentationen](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#configuration-keys){target="_blank"}


   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** är helt anpassningsbar med strängvärde, men måste vara exakt densamma som den som anges i SDK.
   >

1. Välj ikonen i fältet **[!UICONTROL Application icon]** om du vill anpassa mobilprogrammet i tjänsten.
1. Välj **HTTP v1** i listrutan **[!UICONTROL API version]**.
1. Klicka på länken **[!UICONTROL Load project json file to extract project details...]** för att läsa in JSON-nyckelfilen. Mer information om hur du extraherar JSON-filen finns i [Google Firebase-dokumentationen](https://firebase.google.com/docs/admin/setup#initialize-sdk){target="_blank"}.

   Du kan även ange följande manuellt:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

1. Använd knappen **[!UICONTROL Test the connection]** för att validera konfigurationen.

   >[!CAUTION]
   >
   >Knappen **[!UICONTROL Test connection]** kontrollerar inte om MID-servern (Middle-sourcing) har åtkomst till FCM-servern.

1. (valfritt) Du kan utöka ett push-meddelandeinnehåll med vissa **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka på **[!UICONTROL Finish]** och sedan på **[!UICONTROL Save]**. Ditt Android-program kan nu användas i Campaign.

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | N/A | validate_only |
| meddelandemeddelande | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |


>[!ENDTABS]

## Konfigurera Adobe Campaign Extension i din mobila egenskap {#configure-extension}

**Adobe Campaign Classic-tillägget** för Adobe Experience Platform Mobile SDK:er hanterar push-meddelanden för dina mobilappar och hjälper dig att samla in push-tokens för användare och hantera interaktionsmätning med Adobe Experience Platform-tjänster.

Det här tillägget, som gäller både Campaign Classic v7 och Campaign v8, är förinstallerat i din miljö och måste konfigureras. Så här konfigurerar du tillägget för din mobila taggegenskap:

1. Öppna taggegenskapen som du skapade tidigare.
1. Bläddra till **Tillägg** från den vänstra navigeringen och öppna fliken **Katalog**. Använd sökfältet för att hitta tillägget **Adobe Campaign Classic**.
1. Klicka på knappen **Installera** på Campaign Classic-kortet.
1. Ange inställningar enligt beskrivningen i [dokumentationen för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/){target="_blank"}.

Nu kan du lägga till Campaign i din app, vilket beskrivs i [dokumentationen för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#add-campaign-classic-to-your-app){target="_blank"}.
