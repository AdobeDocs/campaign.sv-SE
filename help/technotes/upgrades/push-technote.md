---
product: campaign
title: Kommande ändringar i push-meddelandekanalen
description: Kommande ändringar i push-meddelandekanalen
feature: Push
role: Admin
level: Experienced
badge-v7: label="v7" type="Informative" tooltip="Gäller även Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller Campaign v8"
exl-id: 45ac6f8f-eb2a-4599-a930-1c1fcaa3095b
source-git-commit: a9aa9cb508ca1f5cdcd59e61b5be029e3de1a82f
workflow-type: tm+mt
source-wordcount: '1665'
ht-degree: 1%

---

# Ändringar i push-meddelandekanalen {#push-upgrade}

Du kan använda Campaign för att skicka push-meddelanden på iOS- och Android-enheter. För att kunna göra detta förlitar sig Campaign på prenumerationstjänster för mobilappar.

Vissa viktiga ändringar av tjänsten Android Firebase Cloud Messaging (FCM) släpps 2024, vilket kan påverka implementeringen av Adobe Campaign. Din prenumerationstjänstkonfiguration för Android push-meddelanden kan behöva uppdateras för att den här ändringen ska fungera.

Dessutom rekommenderar Adobe att du går över till den tokenbaserade anslutningen till APN:er i stället för en certifikatbaserad anslutning, som är säkrare och mer skalbar.

## Tjänsten Google Android Firebase Cloud Messaging (FCM) {#fcm-push-upgrade}

### Vad har ändrats? {#fcm-changes}

Som en del av Google kontinuerliga arbete med att förbättra sina tjänster kommer de äldre FCM-API:erna att upphöra den **22 juli 2024**. Läs mer om HTTP-protokollet för meddelanden i Firebase Cloud i [Google Firebase-dokumentationen](https://firebase.google.com/docs/cloud-messaging/migrate-v1){target="_blank"}.

Adobe Campaign Classic v7 och Adobe Campaign v8 har redan stöd för de senaste API:erna för att skicka push-meddelanden. Vissa gamla implementeringar är dock fortfarande beroende av de äldre API:erna. Dessa implementeringar måste uppdateras.

### Påverkas du? {#fcm-impact}

Om din nuvarande implementering stöder prenumerationstjänster som ansluter till FCM med de äldre API:erna påverkas du. Övergång till de senaste API:erna är obligatoriskt för att undvika att tjänster störs. I så fall kommer Adobe-teamen att kontakta dig.

Om du vill kontrollera om du påverkas kan du filtrera dina **tjänster och prenumerationer** enligt filtret nedan:

![](assets/filter-services-fcm.png)


* Om någon av dina aktiva push-meddelandetjänster använder API:t **HTTP (äldre)** påverkas din konfiguration direkt av den här ändringen. Du måste granska dina aktuella konfigurationer och gå över till de nyare API:erna som beskrivs nedan.

* Om din installation enbart använder **HTTP v1** API för push-meddelanden från Android är du redan kompatibel och du behöver inte vidta några ytterligare åtgärder.

### Hur uppdaterar jag? {#fcm-transition-procedure}

#### Förhandskrav {#fcm-transition-prerequisites}

* Android Firebase Admin SDK-tjänstens konto-JSON-fil behövs för att mobilprogrammet ska kunna flyttas till HTTP v1. Lär dig hur du hämtar den här filen i [Google Firebase-dokumentationen](https://firebase.google.com/docs/admin/setup#initialize-sdk){target="_blank"}.

* För Campaign Classic v7 har stöd för HTTP v1 lagts till i version 20.3.1. Om miljön körs på en äldre version är en förutsättning för övergången till HTTP v1 att du uppgraderar miljön till den [senaste Campaign Classicen](https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/latest-release.html){target="_blank"}. För Campaign v8 stöds HTTP v1 av alla versioner och ingen uppgradering behövs.

* Som Campaign Classic v7-användare på plats måste ni uppgradera både marknadsförings- och Real-Time Execution-servrarna.

* För Hybrid-, Hosted- och Managed-Cloud Service ska du, utöver övergångsproceduren nedan, kontakta Adobe för att uppdatera Real-Time-körningsservern (RT).

* Om det externa Android-kontot för routning:

   * Som en Campaign Classic v7-användare på plats eller hybridanvändare kontrollerar du att ditt externa Android-routningskonto är konfigurerat med `androidPushConnectorV2.js`. Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/en/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application-android#configuring-external-account-android){target="_blank"}.

   * För Hybrid-, Hosted- och Managed-Cloud Service-distributioner måste du även ansluta till kundtjänstteamet på Adobe för att verifiera att `androidPushConnectorV2.js (nms)`-anslutningen har valts i Android routningsexterna konto för MID-källservern.

#### Övergångsförfarande {#fcm-transition-steps}

Så här flyttar du miljön till HTTP v1:

1. Bläddra till din lista över **tjänster och prenumerationer**.
1. Visa alla mobilprogram som använder API-versionen **HTTP (äldre)**.
1. För vart och ett av dessa mobilprogram ställer du in **API-version** på **HTTP v1**.
1. Klicka på länken **[!UICONTROL Load project json file to extract project details...]** om du vill läsa in JSON-nyckelfilen direkt.

   Du kan även ange följande manuellt:

   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/android-http-v1-config.png)

1. Klicka på **[!UICONTROL Test the connection]** om du vill kontrollera att konfigurationen är korrekt och att marknadsföringsservern har åtkomst till FCM. Observera att knappen **[!UICONTROL Test connection]** inte kan kontrollera om servern har åtkomst till tjänsten Android Firebase Cloud Messaging (FCM) för distributioner med medelhög källkod.
1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med vissa **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.
1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**.

   Nedan finns FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande. De här alternativen är detaljerade [här](#fcm-apps).

   | Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
   |:-:|:-:|:-:|
   | datameddelande | N/A | validate_only |
   | meddelandemeddelande | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |


>[!NOTE]
>
>När dessa ändringar har tillämpats på alla servrar använder alla **nya** push-meddelanden som levereras till Android-enheter HTTP v1-API:t. Befintliga push-leveranser som används, pågår och används, använder fortfarande HTTP-API:t (äldre). Lär dig hur du uppdaterar dem i avsnittet nedan.

#### Uppdatera befintliga mallar {#fcm-transition-update}

När övergången till HTTP v1 är klar måste du uppdatera dina **leveransmallar** för Android push-meddelanden för att öka antalet batchmeddelanden. Det gör du genom att bläddra till egenskaperna för din Android-leveransmall och ange [Antal meddelandebatchar](../../v8/send/configure-and-send.md#delivery-batch-quantity) till **256** på fliken **Leverans**. Använd ändringen på alla leveransmallar som används för dina Android-leveranser och på alla befintliga Android-leveranser.

Du kan även uppdatera befintliga mallar för leveranser och leveranser som skapats före uppgraderingen till en version som stöder HTTP v1. Så här gör du:

* Som Managed Cloud Services eller Hosted customer kontaktar du Adobe för att uppdatera Android leveransmallar.

* För lokala miljöer hämtar du skriptet `fcm-httpv1-migration.js` och kör det enligt instruktionerna nedan.

  Hämta [fcm-httpv1-migration.zip](assets/do-not-localize/fcm-httpv1-migration-js.zip).

  >[!CAUTION]
  >
  >Skriptet måste köras på din lokala Marketing-instans.


  +++Steg för att uppdatera befintliga leveranser och mallar (endast lokalt)

  Så här korrigerar du alla mallar för leveranser och leveranser som skapats före uppgraderingen till en version som stöder HTTP v1:

   1. Exportera dina befintliga leveranser och leveransmallar i ett paket för att kunna återställa dem om ett oväntat problem skulle uppstå under patchningen.
   1. Kör följande kommando i Posgresql:

      ```sql
      pg_dump -Fp -f /sftp/<db_name>-nmsdelivery-before_rd_script.sql -t nmsdelivery -d <db_name>
      ```

   1. Som standard är skriptet i `dryrun`-läge, kan du starta det i det läget för att kontrollera om någon leverans behöver korrigeras.

      Kommando

      ```sql
      nlserver javascript -instance:<instance_name> -file fcm-httpv1-migration.js 
      ```

      Utdata

      ```sql
      ...
      HH:MM:SS >   Processing delivery (id:123456,  label:'Deliver on Android - New', name:'DM1234')
      HH:MM:SS >   Dry run: Would update androidCheckParams for delivery (id:123456,  label:'Deliver on Android - New', name:'DM1234')
      HH:MM:SS >   Processing delivery (id:567890,  label:'Deliver on Android - New', name:'DM5678')
      HH:MM:SS >   Dry run: Would update androidCheckParams for delivery (id:567890,  label:'Deliver on Android - New', name:'DM5678')
      ...
      HH:MM:SS >   Summary (XYZ processed deliverie(s) or delivery template(s)):
      HH:MM:SS >>  - X had not patchable androidCheckParams formula!
      HH:MM:SS >   - Y had androidCheckParams formula patched.
      HH:MM:SS >   - Z ignored as alreading having androidCheckParams formula patched.
      ```

      >[!NOTE]
      >
      >Leveranserna `not patchable` måste uppdateras manuellt. Deras ID finns i loggen.

   1. Kör skriptet i körningsläge på följande sätt för att uppdatera leveranser:

      ```sql
      nlserver javascript -instance:<instance_name> -file fcm-httpv1-migration.js -arg:run
      ```

  +++

### Vilken effekt har mina Android-appar? {#fcm-apps}

Det krävs inga specifika ändringar i Android Mobile-programkoden och meddelandefunktionen bör inte ändras.

Med HTTP v1 kan du dock anpassa ditt push-meddelande ytterligare med **[!UICONTROL HTTPV1 additional options]**.

![](assets/android-push-additional-options.png)

Du kan:

* Använd fältet **[!UICONTROL Ticker]** för att ange tickningstexten för meddelandet.
* Använd fältet **[!UICONTROL Image]** för att ange bildens URL som ska visas i meddelandet.
* Använd fältet **[!UICONTROL Notification Count]** för att ange antalet nya olästa uppgifter som ska visas direkt på programikonen.
* Ställ in alternativet **[!UICONTROL Sticky]** på false så att meddelandet automatiskt stängs när användaren klickar på det. Om värdet är true visas meddelandet fortfarande även när användaren klickar på det.
* Ange **[!UICONTROL Notification Priority]**-nivån för ditt meddelande till standard, minimum, low eller high.
* Ange **[!UICONTROL Visibility]**-nivån för ditt meddelande som offentlig, privat eller hemlig.

Mer information om **[!UICONTROL HTTP v1 additional options]** och hur du fyller i fälten finns i [FCM-dokumentationen](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.



## Apple iOS Push Notification service (APN:er) {#apns-push-upgrade}

### Vad har ändrats? {#ios-changes}

Som Apple rekommenderar bör du skydda kommunikationen med Apple Push Notification-tjänsten (APN:er) genom att använda statslösa autentiseringstoken.

Tokenbaserad autentisering är ett tillståndslöst sätt att kommunicera med APN:er. Tillståndslös kommunikation är snabbare än certifikatbaserad kommunikation eftersom det inte krävs APN:er för att slå upp certifikatet, eller annan information, som är relaterad till din leverantörsserver. Det finns andra fördelar med att använda tokenbaserad autentisering:

* Du kan använda samma token från flera providerservrar.

* Du kan använda en token för att distribuera meddelanden för alla företagets appar.

Läs mer om tokenbaserade anslutningar till APN:er i [dokumentationen för Apple Developer](https://developer.apple.com/documentation/usernotifications/establishing-a-token-based-connection-to-apns){target="_blank"}.

Adobe Campaign Classic v7 och Adobe Campaign v8 har stöd för både tokenbaserade och certifikatbaserade anslutningar. Om implementeringen bygger på en certifikatbaserad anslutning rekommenderar Adobe att du uppdaterar den till en tokenbaserad anslutning.

### Påverkas du? {#ios-impact}

Om den aktuella implementeringen är beroende av certifikatbaserade begäranden om att ansluta till APN:er, påverkas du. Övergång till en tokenbaserad anslutning rekommenderas.

Om du vill kontrollera om du påverkas kan du filtrera dina **tjänster och prenumerationer** enligt filtret nedan:

![](assets/filter-services-ios.png)


* Om någon av dina aktiva push-meddelandetjänster använder läget **Certifikatbaserad autentisering** (.p12) bör dina aktuella implementeringar granskas och flyttas till ett **tokenbaserat autentiseringsläge** (.p8) enligt beskrivningen nedan.

* Om din installation enbart använder **tokenbaserat autentiseringsläge** för push-meddelanden från iOS är din implementering redan uppdaterad och du behöver inte vidta några ytterligare åtgärder.

### Hur uppdaterar jag? {#ios-transition-procedure}

#### Förhandskrav {#ios-transition-prerequisites}

* För Campaign Classic v7 har stöd för **tokenbaserad autentisering** lagts till i version 20.2. Om miljön körs på en äldre version är en förutsättning för den här ändringen att du uppgraderar miljön till den [senaste Campaign Classicen](https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/latest-release.html){target="_blank"}. För Campaign v8 stöds **tokenbaserat autentiseringsläge** av alla versioner och ingen uppgradering behövs.

* Du behöver en signeringsnyckel för APN:s autentiseringstoken för att generera de tokens som servern använder. Du begär den här nyckeln från ditt Apple-utvecklarkonto, vilket förklaras i [Apple Developer-dokumentationen](https://developer.apple.com/documentation/usernotifications/establishing-a-token-based-connection-to-apns){target="_blank"}.

* För Hybrid-, Hosted- och Managed Services-distributioner ska du, utöver övergångsproceduren nedan, kontakta Adobe för att uppdatera körningsservern för realtid (RT). Servern för MID-Source påverkas inte.

* Som Campaign Classic v7-användare på plats måste ni uppgradera både marknadsförings- och Real-Time Execution-servrarna. Servern för MID-Source påverkas inte.

#### Övergångsförfarande {#ios-transition-steps}

Så här flyttar du dina iOS-mobilprogram till det tokenbaserade autentiseringsläget:

1. Bläddra till din lista över **tjänster och prenumerationer**.
1. Visa alla mobilprogram som använder **certifikatbaserad autentisering** (.p12).
1. Redigera vart och ett av dessa mobilprogram och bläddra till fliken **Certifikat/privat nyckel**.
1. I listrutan **Autentiseringsläge** väljer du **tokenbaserad autentisering** (.p8).
1. Fyll i APN-anslutningsinställningarna **[!UICONTROL Key Id]**, **[!UICONTROL Team Id]** och **[!UICONTROL Bundle Id]** och välj sedan ditt p8-certifikat genom att klicka på **[!UICONTROL Enter the private key...]**.

   ![](assets/token-based-certif.png)

1. Klicka på **[!UICONTROL Test the connection]** för att kontrollera att konfigurationen är korrekt och att servern har åtkomst till APN:er. Observera att knappen **[!UICONTROL Test connection]** inte kan kontrollera om servern har åtkomst till APN:er för MID-Source-distributioner.
1. Klicka på **[!UICONTROL Next]** för att börja konfigurera produktionsprogrammet och följ stegen som anges ovan.
1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**.

Ditt iOS-program flyttas nu till det tokenbaserade autentiseringsläget.
