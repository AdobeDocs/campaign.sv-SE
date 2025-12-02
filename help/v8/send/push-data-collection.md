---
title: Skicka push-meddelanden med Adobe Campaign
description: Kom igång med push-meddelanden i Campaign
feature: Push
role: Data Engineer
level: Intermediate
badge: label="Begränsad tillgänglighet" type="Informative"
exl-id: 0f22b17c-ed01-4add-8300-8689b8a9f963
source-git-commit: 11a9f17bc5c1ec8388de294395a6d7b7a5e8a7e6
workflow-type: tm+mt
source-wordcount: '1353'
ht-degree: 2%

---

# Ändrad konfiguration för push-meddelanden {#push-notifications-config}

Campaign v8.5 introducerar vår senaste tjänst för push-meddelanden, som bygger på ett robust ramverk som bygger på modern spetsteknik. Den här tjänsten är utformad för att låsa upp nya nivåer av skalbarhet, så att dina meddelanden kan nå en större publik med smidig effektivitet. Med vår förbättrade infrastruktur och våra optimerade processer kan ni förvänta er större skalbarhet och tillförlitlighet, så att ni kan engagera och kommunicera med era mobilappsanvändare som aldrig förr.

>[!AVAILABILITY]
>
> Den här funktionen är exklusivt tillgänglig för nya kunder från och med Campaign v8.5 och progressivt introducerad till en uppsättning utvalda kunder. Om miljön etablerades före juni 2023 gäller den här sidan inte dig och du måste följa de procedurer som beskrivs [på den här sidan](push-settings.md).

I samband med den här uppdaterade implementeringen kan du skicka push-meddelanden i Adobe Campaign på följande sätt:

1. [Skapa en appyta i Adobe Experience Platform Data Collection](#create-app-surface)

1. [Konfigurera programinställningarna i Adobe Campaign](#push-config-campaign)

1. [Skapa och konfigurera en mobil egenskap i Adobe Experience Platform Data Collection](#create-mobile-property)

1. [Lägg till Adobe Adobe Experience Platform Assurance-tillägg](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/){target="_blank"} (rekommenderas)

1. [Lägg till Campaign Classic i ditt mobilprogram](#campaign-mobile-ap)

1. [Skapa för både iOS och Android](##push-create)

>[!NOTE]
>
> Äldre FCM och APNS p12 stöds inte i datainsamling.

## Skapa en appyta i Adobe Experience Platform Data Collection {#create-app-surface}

Du måste lägga till push-autentiseringsuppgifter för ditt mobilprogram i [!DNL Adobe Experience Platform Data Collection].

Registrering av push-autentiseringsuppgifter krävs för mobilappen för att godkänna att Adobe skickar push-meddelanden åt dig. Se stegen nedan:

1. I [!DNL Adobe Experience Platform Data Collection] väljer du fliken **[!UICONTROL App Surfaces]** på den vänstra panelen.

1. Klicka på **[!UICONTROL Create App Surface]** om du vill skapa en ny konfiguration.

   ![](assets/push-config-1.png)

1. Ange **[!UICONTROL Name]** som konfiguration.

1. Välj operativsystemet från **[!UICONTROL Mobile Application Configuration]**:

>[!BEGINTABS]

>[!TAB iOS]

![](assets/push-config-2.png)

1. Ange mobilappens **paket-ID** i fältet **[!UICONTROL App ID (iOS Bundle ID)]**.

   Program-ID:t finns på fliken **Allmänt** för det primära målet i **XCode** för ditt Apple-utvecklarkonto.

1. Aktivera **[!UICONTROL Push Credentials]** om du vill lägga till dina autentiseringsuppgifter.

1. Dra och släpp .p8-filen Apple Push Notification Authentication Key.

   Den här nyckeln kan hämtas från sidan **Certifikat**, **Identifierare** och **Profiler** på ditt Apple-utvecklarkonto.

1. Ange **nyckel-ID**. Detta är en 10-teckensträng som tilldelas när en p8-autentiseringsnyckel skapas.

       Den finns på fliken **Keys** i sidan **Certificates**, **Identifiers** och **Profiles** på ditt Apple-utvecklarkonto.
   
1. Ange **Team-ID**. Detta är ett strängvärde som finns under fliken **Medlemskap**.

1. Klicka på **[!UICONTROL Save]** om du vill skapa appkonfigurationen.

>[!TAB Android]

![](assets/push-config-3.png)

1. Ange **[!UICONTROL App ID (Android package name)]**. Paketnamnet är vanligtvis program-ID:t i din `build.gradle`-fil.

1. Växla **[!UICONTROL Push Credentials]** om du vill lägga till dina autentiseringsuppgifter.

1. Dra och släpp FCM-push-inloggningsuppgifterna. Mer information om hur du hämtar push-autentiseringsuppgifter finns i [Google-dokumentationen](https://firebase.google.com/docs/admin/setup#initialize-sdk){target="_blank"}.

1. Klicka på **[!UICONTROL Save]** om du vill skapa appkonfigurationen.

>[!ENDTABS]

## Konfigurera programinställningarna i Adobe Campaign{#push-config-campaign}

### Skapa en tjänst {#create-service}

Innan du skickar push-meddelanden måste du definiera inställningarna för dina iOS- och Android-appar i Adobe Campaign.

Push-meddelanden skickas till appanvändarna via en dedikerad tjänst. När användare installerar din app prenumererar de på den här tjänsten: Adobe Campaign förlitar sig på den här tjänsten för att endast rikta sig till prenumeranterna av din app. I den här tjänsten måste du lägga till dina iOS- och Android-appar som ska skickas på enheter med iOS och Android.

Följ stegen nedan för att skapa en tjänst för att skicka push-meddelanden:

1. Bläddra till fliken **[!UICONTROL Profiles and Targets > Services and Subscriptions]** och klicka på **[!UICONTROL Create]**.

   ![](assets/push-config-4.png){width="800" align="left"}

1. Ange en **[!UICONTROL Label]** och en **[!UICONTROL Internal name]** och välj en **[!UICONTROL Mobile application]**-typ.

   >[!NOTE]
   >
   >Standardmålmappningen **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i fältet **[!UICONTROL Target mapping]** för tjänsten. Läs mer om målmappningar på [den här sidan](../audiences/target-mappings.md).

1. Använd sedan ikonen **[!UICONTROL Add]** till höger för att definiera de mobilprogram som använder den här tjänsten.

   ![](assets/push-config-5.png)

### Skapa ett mobilprogram {#create-sapp}

När du har skapat tjänsten måste du nu definiera de mobilprogram som ska använda den här tjänsten.

>[!BEGINTABS]

>[!TAB iOS]

Så här skapar du en app för iOS-enheter:

1. Klicka på **[!UICONTROL Add]** och välj sedan **[!UICONTROL Create an iOS application]** från din tjänst. Klicka på **[!UICONTROL Next]**.

   ![](assets/push-config-6.png)

1. I fönstret **[!UICONTROL Launch app configurations list]** väljer du appytan som tidigare skapats i det här avsnittet. Klicka på **[!UICONTROL Next]**.

   ![](assets/push-config-7.png)

1. (valfritt) Du kan utöka ett push-meddelandeinnehåll med lite **[!UICONTROL Application variables]**. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

   I exemplet nedan läggs variablerna **mediaURl** och **mediaExt** till för att skapa omfattande push-meddelanden och ger sedan programmet den bild som ska visas i meddelandet.

   ![](assets/push-config-8.png)

1. Bläddra till fliken **[!UICONTROL Subscription parameters]** för att definiera mappningen med ett tillägg till schemat **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

1. Bläddra till fliken **[!UICONTROL Sounds]** för att definiera ett ljud som ska spelas upp. Klicka på **[!UICONTROL Add]** och fyll i fältet **[!UICONTROL Internal name]** som måste innehålla namnet på filen som är inbäddad i programmet eller namnet på systemljudet.

1. Klicka på **[!UICONTROL Next]** för att börja konfigurera utvecklingsprogrammet.

1. **[!UICONTROL Integration key]** är specifikt för varje program. Det länkar mobilprogrammet till Adobe Campaign och kommer att användas när Campaign-tillägget konfigureras.

   Kontrollera att samma **[!UICONTROL Integration key]** har definierats i Adobe Campaign och i programkoden via SDK.

   Läs mer i [utvecklardokumentationen](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#configuration-keys){target="_blank"}


   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** är helt anpassningsbar med strängvärde, men måste vara exakt densamma som den som anges i SDK.
   >
   > Du kan inte använda samma certifikat för utvecklingsversionen (sandlådan) och produktionsversionen av programmet.

   ![](assets/push-config-9.png)

1. Välj ikonen i fältet **[!UICONTROL Application icon]** om du vill anpassa mobilprogrammet i tjänsten.

1. Klicka på **[!UICONTROL Next]** för att börja konfigurera produktionsprogrammet och följ stegen som anges ovan. Observera att du inte kan använda samma **[!UICONTROL Integration key]** för utvecklingsversionen (sandlådan) och produktionsversionen av programmet.

1. Klicka på **[!UICONTROL Finish]**.

Ditt iOS-program kan nu användas i Campaign.

>[!TAB Android]

Så här skapar du en app för Android-enheter:

1. Klicka på **[!UICONTROL Add]** och välj sedan **[!UICONTROL Create an Android application]** från din tjänst. Klicka på **[!UICONTROL Next]**.

   ![](assets/push-config-10.png)

1. I fönstret **[!UICONTROL Launch app configurations list]** väljer du appytan som skapas i det här avsnittet och klickar på **[!UICONTROL Next]**.

   ![](assets/push-config-11.png)

1. Integreringsnyckeln är specifik för varje program. Det länkar mobilprogrammet till Adobe Campaign och kommer att användas när Campaign-tillägget konfigureras.

   Kontrollera att samma **[!UICONTROL Integration key]** har definierats i Adobe Campaign och i programkoden via SDK.

   Läs mer i [utvecklardokumentationen](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#configuration-keys){target="_blank"}

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** är helt anpassningsbar med strängvärde, men måste vara exakt densamma som den som anges i SDK.

   ![](assets/push-config-12.png)

1. Välj ikonen i fältet **[!UICONTROL Application icon]** om du vill anpassa mobilprogrammet i tjänsten.

1. (valfritt) Du kan utöka ett push-meddelandeinnehåll med vissa **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Bläddra till fliken **[!UICONTROL Subscription parameters]** för att definiera mappningen med ett tillägg till schemat **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**.

Ditt Android-program kan nu användas i Campaign.

>[!ENDTABS]

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | N/A | validate_only |
| meddelandemeddelande | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

## Konfigurera en mobil egenskap i Adobe Experience Platform Data Collection {#create-mobile-property}

1. Gå till Taggar-menyn från startsidan för Datainsamling.

1. Klicka på **[!UICONTROL New Property]**.

   ![](assets/push-config-13.png)

1. Ange ett namn för egenskapen och välj **[!UICONTROL Mobile]** som plattform.

   ![](assets/push-config-14.png)

1. Klicka på **[!UICONTROL Save]** för att skapa den mobila egenskapen.

1. Få åtkomst till din nya mobila egenskap.

1. Gå till menyn **[!UICONTROL Extensions]** och sedan till fliken **[!UICONTROL Catalog]** från kontrollpanelen för mobila egenskaper.

   ![](assets/push-config-15.png)

1. Installera tillägget **[!DNL Adobe Campaign Classic]**. [Läs mer om Campaign-tillägget](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#configure-campaign-classic-extension)

   ![](assets/push-config-16.png)

1. Fyll i instansinformationen:

   * **[!UICONTROL Registration endpoint]** eller **[!UICONTROL Tracking endpoint]** URL:er finns på menyn **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]** i Campaign.
   * **[!UICONTROL Integration keys]** finns i den mobilapp som konfigurerats i [det här avsnittet](#create-app).

   ![](assets/push-config-17.png)

1. Klicka på **[!UICONTROL Save]**.

1. Du måste nu publicera konfigurationen från menyn **[!UICONTROL Publishing flow]**. [Läs mer](https://developer.adobe.com/client-sdks/documentation/getting-started/create-a-mobile-property/#publish-the-configuration)

Din mobila egenskap synkroniseras nu automatiskt med det tekniska arbetsflödet för **[!UICONTROL Adobe Experience Platform Data Collection]**. [Läs mer](../../automation/workflow/technical-workflows.md#list-technical-workflows)

## Lägg till Campaign Classic i ditt mobilprogram {#campaign-mobile-app}

Mobil-SDK:et i Adobe Experience Platform hjälper dig att driva lösningar och tjänster från Adobe Experience Cloud i dina mobilappar. SDK-konfigurationen hanteras via användargränssnittet för datainsamling för flexibel konfiguration och utbyggbara, regelbaserade integreringar.

[Läs mer i Adobe Developer-dokumentationen](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic/#add-campaign-classic-to-your-app){target="_blank"}.

## Skapa ett push-meddelande{#push-create}

När du har konfigurerat ditt mobilprogram i datainsamling kan du nu skapa och skicka push-meddelanden i Adobe Campaign.

Se [den här sidan](push.md#push-create) för detaljerade element som är specifika för leveransen av iOS- och Android-meddelanden.
