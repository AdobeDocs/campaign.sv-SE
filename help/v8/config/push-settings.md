---
title: Integrera AEP SDK och Campaign
description: Lär dig hur du integrerar Adobe Experience Platform SDK för mobiler med din app
version: v8
feature: Push
role: Admin, Developer
level: Intermediate, Experienced
hide: true
hidefromtoc: true
source-git-commit: e3ea361cc486096fe6c19ac469e8a71b636371ac
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 2%

---


# AEP SDK + Campaign: konfigurera push-meddelandekanal {#push-notification-configuration}

Innan du börjar skicka push-meddelanden med Adobe Campaign måste du se till att det finns konfigurationer och integreringar på mobilappen och för taggar i Adobe Experience Platform.... .... ....


## Före start {#before-starting}

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

### Integrera mobilappen med Adobe Experience Platform SDK {#integrate-mobile-app}

Adobe Experience Platform Mobile SDK innehåller API:er för integrering på klientsidan för mobiler via Android och iOS-kompatibla SDK:er. Följ [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/){target="_blank"} om du vill konfigurera med Adobe Experience Platform Mobile SDK i appen.

När allt är klart bör du också ha skapat och konfigurerat en mobil egenskap i [!DNL Adobe Experience Platform Data Collection]. Du skapar vanligtvis en mobil egenskap för varje mobilprogram som du vill hantera. Lär dig hur du skapar och konfigurerar en mobil egenskap i [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/create-a-mobile-property/){target="_blank"}.


## Steg 1: Lägg till push-autentiseringsuppgifter för appar i Adobe Experience Platform Data Collection {#push-credentials}

När du har gett rätt användarbehörigheter måste du nu lägga till dina push-autentiseringsuppgifter för mobilprogrammet i Adobe Experience Platform Data Collection.

Registrering av push-autentiseringsuppgifter krävs för mobilappen för att godkänna att Adobe skickar push-meddelanden åt dig. Se stegen nedan:

1. Från [!DNL Adobe Experience Platform Data Collection], bläddra till **[!UICONTROL App Surfaces]** till vänster.

1. Klicka **[!UICONTROL Create App Surface]** för att skapa en ny konfiguration.

1. Ange **[!UICONTROL Name]** för konfigurationen.

1. Från **[!UICONTROL Mobile Application Configuration]** väljer du operativsystem:

   * **För iOS**

      1. Ange mobilappen **Paket-ID** i **[!UICONTROL App ID (iOS Bundle ID)]** fält. Program-ID:t finns i **Allmänt** fliken för det primära målet i **XCode**.

      1. På **[!UICONTROL Push Credentials]** för att lägga till dina inloggningsuppgifter.

      1. Dra och släpp .p8-filen Apple Push Notification Authentication Key. Den här nyckeln kan hämtas från **Certifikat**, **Identifierare** och **Profiler** sida.

      1. Ange **Nyckel-ID**. Detta är en 10-teckensträng som tilldelas när en p8-autentiseringsnyckel skapas. Den finns under **Tangenter** tabba in **Certifikat**, **Identifierare** och **Profiler** sida.

      1. Ange **Team-ID**. Detta är ett strängvärde som finns under fliken Medlemskap.
   * **För Android**

      1. Ange **[!UICONTROL App ID (Android package name)]**: oftast är paketnamnet program-id:t i din `build.gradle` -fil.

      1. På **[!UICONTROL Push Credentials]** för att lägga till dina inloggningsuppgifter.

      1. Dra och släpp FCM-push-inloggningsuppgifterna. Mer information om hur du hämtar push-autentiseringsuppgifter finns i [Google Documentation](https://firebase.google.com/docs/admin/setup#initialize-sdk){target="_blank"}.



1. Klicka **[!UICONTROL Save]** för att skapa din appkonfiguration.


## Steg 2: Konfigurera en mobil taggegenskap i Adobe Experience Platform Data Collection {#launch-property}

Genom att konfigurera en mobil egenskap kan mobilappsutvecklaren eller -marknadsföraren konfigurera SDK-attribut för mobilen, till exempel timeout för session, [!DNL Adobe Experience Platform] sandlåda som ska användas som mål och **[!UICONTROL Adobe Experience Platform Datasets]** som ska användas för mobil-SDK för att skicka data till.

Mer information och procedurer om hur du skapar en **mobil egenskap** , se de steg som beskrivs i [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/getting-started/create-a-mobile-property/){target="_blank"}.

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


## Steg 3: Konfigurera Adobe Campaign Extension i din mobila egenskap {#configure-extension}

The **Adobe Campaign Classic-tillägg** för Adobe Experience Platform Mobile SDK:er driver push-meddelanden för dina mobilappar och hjälper dig att samla in push-tokens och hantera interaktionsmätning med Adobe Experience Platform tjänster.

Tillägget är förinstallerat i din miljö och måste konfigureras. Så här konfigurerar du tillägget för din mobila taggegenskap:

1. Öppna taggegenskapen som du skapade tidigare.
1. I den vänstra navigeringen bläddrar du till **Tillägg** och öppna **Katalog** -fliken. Använd sökfältet för att hitta **Adobe Campaign Classic** tillägg.
1. På Campaign Classic-kortet klickar du på **Installera** -knappen.
1. Ange inställningar enligt beskrivningen i [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/){target="_blank"}.

Nu kan du lägga till Campaign i din app, vilket beskrivs i  [Dokumentation för Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#add-campaign-classic-to-your-app){target="_blank"}.

## Steg 4: Konfigurera dina mobiltjänster i Campaign{#push-service}

När mobilappen har konfigurerats i [!DNL Adobe Experience Platform Data Collection]måste du skapa två tjänster (en för iOS-enheter, en för Android-enheter) för att kunna skicka push-meddelanden från **[!DNL Adobe Campaign]**.

Lär dig hur du skapar och konfigurerar en tjänst för push-meddelanden i iOS och Android i [det här avsnittet](../send/push.md#push-config).
