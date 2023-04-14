---
title: Skicka push-meddelanden med Adobe Campaign
description: Kom igång med push-meddelanden i Campaign
feature: Push
role: Data Engineer
level: Beginner
exl-id: f04c6e0c-f2b9-496a-9697-04ef4c3411ee
source-git-commit: e7c255d30e38c4e17779ef820e8984668ac5d48b
workflow-type: tm+mt
source-wordcount: '1671'
ht-degree: 3%

---

# Skapa och skicka push-meddelanden{#push-notifications-create}

Med mobilappsleveranser kan du skicka meddelanden till iOS- och Android-enheter.

Om du vill skicka push-meddelanden i Adobe Campaign måste du:

1. Integrera SDK med appen. [Läs mer](#push-sdk)
1. Skapa en informationstjänst av mobiltyp för ditt mobilprogram och lägg till iOS- och Android-versionerna av programmet i den tjänsten. [Läs mer](#push-config)
1. Skapa en leverans för både iOS och Android. [Läs mer](#push-create)

## Integrera SDK {#push-sdk}

Om du vill skicka push-meddelanden med Adobe Campaign måste du konfigurera Adobe Campaign-tillägget i användargränssnittet för datainsamling i Adobe Experience Platform Mobile SDK.

Adobe Experience Platform Mobile SDK hjälper er att driva lösningar och tjänster från Adobe Experience Cloud i era mobilappar. SDK-konfigurationen hanteras via användargränssnittet för datainsamling för flexibel konfiguration och utbyggbara, regelbaserade integreringar.

[Läs mer i Adobe Developer-dokumentationen](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.


## Konfigurera appinställningarna i Campaign{#push-config}

Innan du skickar push-meddelanden måste du definiera inställningarna för dina iOS- och Android-appar i Adobe Campaign.

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

   I exemplet nedan visas **mediaURl** och **mediaExt** -variabler läggs till för att skapa omfattande push-meddelanden och ger sedan programmet den bild som ska visas i meddelandet.

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


## Skapa ditt första push-meddelande{#push-create}

I det här avsnittet beskrivs de element som är specifika för leveransen av iOS- och Android-meddelanden.

>[!CAUTION]
>
>När det gäller [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), mobilregistrering är nu **asynkron**. [Läs mer](../architecture/staging.md)

Bläddra till **[!UICONTROL Campaigns]** flik, klicka **[!UICONTROL Deliveries]** och klicka på **[!UICONTROL Create]** ovanför listan över befintliga leveranser.

![](assets/delivery_step_1.png)

>[!BEGINTABS]

>[!TAB iOS]

Så här skickar du meddelanden till iOS-enheter:

1. Välj **[!UICONTROL Deliver on iOS]** leveransmall.

   ![](assets/push_ios_1.png)

1. Om du vill definiera målet för meddelandet klickar du på knappen **[!UICONTROL To]** klicka på **[!UICONTROL Add]**.

   ![](assets/push_ios_2.png)

1. Välj **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, väljer den tjänst som är relevant för ditt mobilprogram och väljer sedan iOS-versionen av programmet.

   ![](assets/push_ios_3.png)

1. Välj **[!UICONTROL Notification type]** mellan **[!UICONTROL General notification (Alert, Sound, Badge)]** eller **[!UICONTROL Silent notification]**.

   ![](assets/push_ios_4.png)

   >[!NOTE]
   >
   >The **Tyst push** I läget kan ett tyst meddelande skickas till ett mobilprogram. Användaren har inte informerats om meddelandets ankomst. Den överförs direkt till programmet.

1. I **[!UICONTROL Title]** anger du etiketten för den titel som du vill ska visas i listan med meddelanden som är tillgängliga från meddelandecentret.

   I det här fältet kan du definiera värdet för **title** -parametern för iOS-meddelandenyttolasten.

1. Du kan lägga till en **[!UICONTROL Subtitle]**, värdet för **underrubrik** -parametern för iOS-meddelandenyttolasten.

1. Ange innehållet i meddelandet i **[!UICONTROL Message content]** i guiden.

1. Från **[!UICONTROL Sound and Badge]** kan du redigera följande alternativ:

   * **[!UICONTROL Clean Badge]**: aktivera det här alternativet för att uppdatera badge-värdet.

   * **[!UICONTROL Value]**: Ange ett tal som ska användas för att visa antalet nya olästa uppgifter direkt på programikonen.

   * **[!UICONTROL Critical alert mode]**: aktivera det här alternativet för att lägga till ljud i meddelandet även om användarens telefon är inställd på fokusläge eller om iPhone är avstängt.

   * **[!UICONTROL Name]**: Välj det ljud som ska spelas upp av mobilterminalen när meddelandet tas emot.

   * **[!UICONTROL Volume]**: ljudvolymen från 0 till 100.

      >[!NOTE]
      > 
      >Ljud måste inkluderas i programmet och definieras när tjänsten skapas.
   ![](assets/push_ios_5.png)

1. Från **[!UICONTROL Application variables]** -fliken, **[!UICONTROL Application variables]** läggs till automatiskt. De gör att du kan definiera meddelandebeteende, till exempel kan du konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. Från **[!UICONTROL Advanced]** kan du redigera följande allmänna alternativ:

   * **[!UICONTROL Mutable content]**: aktivera det här alternativet om du vill tillåta att mobilprogrammet hämtar medieinnehåll.

   * **[!UICONTROL Thread-id]**: identifierare som används för att gruppera relaterade meddelanden tillsammans.

   * **[!UICONTROL Category]**: namnet på ditt kategori-ID som kommer att visa åtgärdsknappar. Dessa meddelanden ger användaren ett snabbare sätt att utföra olika åtgärder som svar på ett meddelande utan att öppna eller navigera i programmet.

   ![](assets/push_ios_6.png)

1. För tidskänsliga meddelanden kan du ange följande alternativ:

   * **[!UICONTROL Target content ID]**: Identifierare som används för att ange vilket programfönster som ska flyttas fram när meddelandet öppnas.

   * **[!UICONTROL Launch image]**: namnet på startbildfilen som ska visas. Om användaren väljer att starta programmet visas den valda bilden i stället för programmets startskärm.

   * **[!UICONTROL Interruption level]**:

      * **[!UICONTROL Active]**: Som standard visas meddelandet omedelbart, skärmen visas och ett ljud kan spelas upp. Meddelanden går inte igenom fokusläget.

      * **[!UICONTROL Passive]**: Systemet lägger till meddelandet i meddelandelistan utan att skärmen eller ljudet ljussätts upp. Meddelanden går inte igenom fokusläget.

      * **[!UICONTROL Time sensitive]** Systemet visar meddelandet omedelbart, lyser upp skärmen, kan spela upp ett ljud och gå igenom fokus-lägen. Den här nivån kräver inget särskilt tillstånd från Apple.

      * **[!UICONTROL Critical]** Systemet visar meddelandet omedelbart, lyser upp skärmen och kringgår avstängningsväxeln eller fokusläget. Observera att den här nivån kräver ett särskilt tillstånd från Apple.
   * **[!UICONTROL Relevance score]**: Ange ett relevansvärde mellan 0 och 100. Systemet använder detta för att sortera meddelandena i meddelandesammanfattningen.

   ![](assets/push_ios_7.png)

1. När meddelandet har konfigurerats klickar du på **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/push-ios-preview.png)


>[!TAB Android]

Så här skickar du meddelanden på Android-enheter:

1. Välj **[!UICONTROL Deliver on Android (android)]** leveransmall.

   ![](assets/push-template-android.png)

1. Om du vill definiera målet för meddelandet klickar du på knappen **[!UICONTROL To]** klicka på **[!UICONTROL Add]**.

   ![](assets/push-android-select-target.png)

1. Välj **[!UICONTROL Subscribers of an Android mobile application]** väljer du den tjänst som är relevant för ditt mobilprogram (i det här fallet Neotrips) och väljer sedan Android-versionen av programmet.

   ![](assets/push-android-subscribers.png)

1. Ange sedan innehållet för meddelandet.

   ![](assets/push-android-content.png)

1. Klicka på **[!UICONTROL Insert emoticon]** om du vill infoga uttryckssymboler i ditt push-meddelande.

1. I **[!UICONTROL Application variables]** anger du värdet för varje variabel. Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. När meddelandet har konfigurerats klickar du på **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   <!--![](assets/push-android-preview.png)-->

>[!ENDTABS]


## Testa, skicka och övervaka dina push-meddelanden

Använd samma process som för andra leveranser när du vill skicka ett korrektur och den slutliga leveransen.

Lär dig hur du validerar en leverans i [den här sidan](preview-and-proof.md).

Lär dig hur du bekräftar och skickar leveransen i [den här sidan](send.md)

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Läs mer om orsaker till leveransfel vid push-meddelanden i [den här sidan](delivery-failures.md#push-error-types).

