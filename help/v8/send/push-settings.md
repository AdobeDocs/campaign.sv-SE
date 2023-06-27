---
title: Integrera AEP SDK och Campaign
description: Lär dig hur du integrerar Adobe Experience Platform SDK för mobiler med din app
version: v8
feature: Push
role: Admin, Developer
level: Intermediate, Experienced
exl-id: b5a0fe46-f7b4-4be1-abf0-162fc1412886
source-git-commit: d941d9a364ffb2df77ba6726e655ca2916448f89
workflow-type: tm+mt
source-wordcount: '1662'
ht-degree: 3%

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
1. Konfigurera dina iOS- och Android-mobiltjänster i Adobe Campaign enligt [på den här sidan](#push-service).
1. Installera och konfigurera [Adobe Campaign Extension](#configure-extension) i er mobilegendom.
1. Följ [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/){target="_blank"} om du vill konfigurera med Adobe Experience Platform Mobile SDK i appen.

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
<!--
To get the SDKs needed for push notification to work you will need the following SDK extensions, for both Android and iOS:

* **[!UICONTROL Mobile Core]** (installed automatically)
* **[!UICONTROL Profile]** (installed automatically)
* **[!UICONTROL Adobe Experience Platform Edge]**
* **[!UICONTROL Adobe Experience Platform Assurance]**, optional but recommended to debug the mobile implementation.
-->

Läs mer om [!DNL Adobe Experience Platform Data Collection] taggar i [Adobe Experience Platform-dokumentation](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/initial-configuration/configure-tags.html){target="_blank"}.

Öppna den nya taggegenskapen och skapa ett bibliotek när du har skapat den. Så här gör du:

1. Bläddra till **Publiceringsflöde** i den vänstra navigeringen och välj **Lägg till bibliotek**.
1. Ange namnet på biblioteket och välj miljö.
1. Välj **Lägg till alla ändrade resurser** och **Spara och bygg för utveckling**.
1. Äntligen anger du det här biblioteket som ditt arbetsbibliotek från **Välj ett arbetsbibliotek** -knappen.

## Konfigurera dina mobiltjänster i Campaign {#push-service}

När mobilappen har konfigurerats i [!DNL Adobe Experience Platform Data Collection]måste du skapa två tjänster (en för iOS-enheter, en för Android-enheter) för att kunna skicka push-meddelanden från **[!DNL Adobe Campaign]**.

Push-meddelanden skickas till appanvändarna via en dedikerad tjänst. När användarna installerar din app prenumererar de på den här tjänsten: Adobe Campaign förlitar sig på den här tjänsten för att endast rikta sig till appens prenumeranter. I den här tjänsten måste du lägga till dina iOS- och Android-appar som ska skickas på iOS- och Android-enheter.

Följ stegen nedan för att skapa en tjänst för att skicka push-meddelanden:

1. Bläddra till **[!UICONTROL Profiles and Targets > Services and Subscriptions]** och klicka på **[!UICONTROL Create]**.

   ![](assets/new-service-push.png){width="800" align="left"}

1. Ange **[!UICONTROL Label]** och **[!UICONTROL Internal name]** och väljer **[!UICONTROL Mobile application]** typ.

   >[!NOTE]
   >
   >Standardvärdet **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** målmappningen är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i **[!UICONTROL Target mapping]** tjänstens fält. Läs mer om målmappningar i [den här sidan](../audiences/target-mappings.md).

1. Använd sedan **[!UICONTROL Add]** till höger för att definiera de mobilprogram som använder den här tjänsten.

>[!BEGINTABS]

>[!TAB iOS]

Så här skapar du en app för iOS-enheter:

1. Markera **[!UICONTROL Create an iOS application]** och klicka på **[!UICONTROL Next]**.

   ![](assets/new-ios-app.png){width="600" align="left"}

1. Ange namnet på din app i **[!UICONTROL Label]** fält.
1. (valfritt) Du kan förbättra innehållet i ett push-meddelande med **[!UICONTROL Application variables]**. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

   I exemplet nedan är **mediaURl** och **mediaExt** -variabler läggs till för att skapa omfattande push-meddelanden och ger sedan programmet den bild som ska visas i meddelandet.

   ![](assets/ios-app-parameters.png){width="600" align="left"}

1. Bläddra till **[!UICONTROL Subscription parameters]** för att definiera mappningen med ett tillägg till **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema.

1. Bläddra till **[!UICONTROL Sounds]** för att definiera ett ljud som ska spelas upp. Klicka **[!UICONTROL Add]** och fylla **[!UICONTROL Internal name]** fält som måste innehålla namnet på filen som är inbäddad i programmet eller namnet på systemljudet.

1. Klicka **[!UICONTROL Next]** för att börja konfigurera utvecklingsprogrammet.

1. Integreringsnyckeln är specifik för varje program. Det länkar mobilprogrammet till Adobe Campaign.

   Se till att samma **[!UICONTROL Integration key]** definieras i Adobe Campaign och i programkoden via SDK.

   Läs mer i [dokumentation för utvecklare](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#configuration-keys){target="_blank"}


   >[!NOTE]
   >
   > The **[!UICONTROL Integration key]** är helt anpassningsbart med strängvärde, men måste vara exakt densamma som den som anges i SDK:n.
   >
   > Du kan inte använda samma certifikat för utvecklingsversionen (sandlådan) och produktionsversionen av programmet.

1. Välj ikonen på menyn **[!UICONTROL Application icon]** fält för att anpassa mobilapplikationer i din tjänst.

1. Markera **[!UICONTROL Authentication mode]**. Det finns två lägen:

   * (Rekommenderas) **[!UICONTROL Token-based authentication]**: Fyll i APN-anslutningsinställningarna **[!UICONTROL Key Id]**, **[!UICONTROL Team Id]** och **[!UICONTROL Bundle Id]** välj sedan ditt p8-certifikat genom att klicka på **[!UICONTROL Enter the private key...]**. Om du vill ha mer information **[!UICONTROL Token-based authentication]**, se [Apple-dokumentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Certificate-based authentication]**: Klicka **[!UICONTROL Enter the certificate...]**  välj sedan din p12-nyckel och ange lösenordet som angavs av mobilprogramutvecklaren.

   Du kan ändra ditt autentiseringsläge senare i dialogrutan **[!UICONTROL Certificate]** -fliken i ditt mobilprogram.

1. Använd **[!UICONTROL Test the connection]** för att validera konfigurationen.

1. Klicka **[!UICONTROL Next]** för att börja konfigurera produktionsprogrammet och följa de steg som beskrivs ovan.

1. Klicka på **[!UICONTROL Finish]**.

Ditt iOS-program kan nu användas i Campaign.

>[!TAB Android]

Så här skapar du en app för Android-enheter:

1. Markera **[!UICONTROL Create an Android application]** och klicka på **[!UICONTROL Next]**.

   ![](assets/new-android-app.png){width="600" align="left"}

1. Ange namnet på din app i **[!UICONTROL Label]** fält.
1. Integreringsnyckeln är specifik för varje program. Det länkar mobilprogrammet till Adobe Campaign.

   Se till att samma **[!UICONTROL Integration key]** definieras i Adobe Campaign och i programkoden via SDK.

   Läs mer i [dokumentation för utvecklare](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#configuration-keys){target="_blank"}


   >[!NOTE]
   >
   > The **[!UICONTROL Integration key]** är helt anpassningsbart med strängvärde, men måste vara exakt densamma som den som anges i SDK:n.
   >

1. Välj ikonen på menyn **[!UICONTROL Application icon]** fält för att anpassa mobilapplikationer i din tjänst.
1. Välj **HTTP v1** in  **[!UICONTROL API version]** nedrullningsbar lista.
1. Klicka **[!UICONTROL Load project json file to extract project details...]** -länk för att läsa in JSON-nyckelfilen. Mer information om hur du extraherar JSON-filen finns i [Google Firebase-dokumentation](https://firebase.google.com/docs/admin/setup#initialize-sdk){target="_blank"}.

   Du kan även ange följande manuellt:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

1. Använd **[!UICONTROL Test the connection]** för att validera konfigurationen.

   >[!CAUTION]
   >
   >The **[!UICONTROL Test connection]** kontrollerar inte om MID-servern har åtkomst till FCM-servern.

1. (valfritt) Du kan förbättra innehållet i ett push-meddelande med **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Ditt Android-program kan nu användas i Campaign.

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | N/A | validate_only |
| meddelande | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |


>[!ENDTABS]

## Konfigurera Adobe Campaign Extension i din mobila egenskap {#configure-extension}

The **Adobe Campaign Classic-tillägg** för Adobe Experience Platform Mobile SDK:er driver push-meddelanden för dina mobilappar och hjälper dig att samla in push-tokens och hantera interaktionsmätning med Adobe Experience Platform tjänster.

Det här tillägget, som gäller både Campaign Classic v7 och Campaign v8, är förinstallerat i din miljö och måste konfigureras. Så här konfigurerar du tillägget för din mobila taggegenskap:

1. Öppna taggegenskapen som du skapade tidigare.
1. I den vänstra navigeringen bläddrar du till **Tillägg** och öppna **Katalog** -fliken. Använd sökfältet för att hitta **Adobe Campaign Classic** tillägg.
1. På Campaign Classic-kortet klickar du på **Installera** -knappen.
1. Ange inställningar enligt beskrivningen i [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/){target="_blank"}.

Nu kan du lägga till Campaign i din app, vilket beskrivs i  [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#add-campaign-classic-to-your-app){target="_blank"}.
