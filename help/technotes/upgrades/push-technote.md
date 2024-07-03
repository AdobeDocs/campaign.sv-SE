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
source-git-commit: 2e9c9f8e677233b2906f6ebb8f42dd86afe4e111
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 1%

---

# Ändringar i push-meddelandekanalen {#push-upgrade}

Du kan använda Campaign för att skicka push-meddelanden på iOS- och Android-enheter. För att kunna göra detta förlitar sig Campaign på prenumerationstjänster för mobilappar.

Vissa viktiga ändringar av tjänsten Android Firebase Cloud Messaging (FCM) släpps 2024, vilket kan påverka implementeringen av Adobe Campaign. Din prenumerationstjänstkonfiguration för Android push-meddelanden kan behöva uppdateras för att den här ändringen ska fungera.

Dessutom rekommenderar Adobe att du går över till den tokenbaserade anslutningen till APN:er i stället för en certifikatbaserad anslutning, som är säkrare och mer skalbar.

## Tjänsten Google Android Firebase Cloud Messaging (FCM) {#fcm-push-upgrade}

### Vad har ändrats? {#fcm-changes}

Som en del av Google kontinuerliga arbete med att förbättra sina tjänster kommer de äldre FCM-API:erna att upphöra på **22 juli 2024**. Läs mer om HTTP-protokollet för Firebase Cloud Messaging i [Google Firebase-dokumentation](https://firebase.google.com/docs/cloud-messaging/migrate-v1){target="_blank"}.

Adobe Campaign Classic v7 och Adobe Campaign v8 har redan stöd för de senaste API:erna för att skicka push-meddelanden. Vissa gamla implementeringar är dock fortfarande beroende av de äldre API:erna. Dessa implementeringar måste uppdateras.

### Påverkas du? {#fcm-impact}

Om din nuvarande implementering stöder prenumerationstjänster som ansluter till FCM med de äldre API:erna påverkas du. Övergång till de senaste API:erna är obligatoriskt för att undvika att tjänster störs. I så fall kommer Adobe-teamen att kontakta dig.

Om du vill kontrollera om du påverkas kan du filtrera **Tjänster och prenumerationer** enligt filtret nedan:

![](assets/filter-services-fcm.png)


* Om någon av dina aktiva push-meddelandetjänster använder **HTTP (äldre)** API, din konfiguration påverkas direkt av den här ändringen. Du måste granska dina aktuella konfigurationer och gå över till de nyare API:erna som beskrivs nedan.

* Om din installation endast använder **HTTP v1** API för push-meddelanden från Android är du redan kompatibel och du behöver inte vidta några ytterligare åtgärder.

### Hur uppdaterar jag? {#fcm-transition-procedure}

#### Förhandskrav {#fcm-transition-prerequisites}

* För Campaign Classic v7 har stöd för HTTP v1 lagts till i version 20.3.1. Om miljön körs på en äldre version är en förutsättning för övergången till HTTP v1 att du uppgraderar miljön till [senaste Campaign Classicen](https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/latest-release.html){target="_blank"}. För Campaign v8 stöds HTTP v1 av alla versioner och ingen uppgradering behövs.

* Android Firebase Admin SDK-tjänstens konto-JSON-fil behövs för att mobilprogrammet ska kunna flyttas till HTTP v1. Lär dig hur du hämtar den här filen i [Google Firebase-dokumentation](https://firebase.google.com/docs/admin/setup#initialize-sdk){target="_blank"}.

* För Hybrid-, Hosted- och Managed Services-distributioner ska du, utöver övergångsproceduren nedan, kontakta Adobe för att uppdatera körningsservern för realtid (RT). Servern för MID-Source påverkas inte.

* Som Campaign Classic v7-användare på plats måste ni uppgradera både marknadsförings- och Real-Time Execution-servrarna. Servern för MID-Source påverkas inte.

#### Övergångsförfarande {#fcm-transition-steps}

Så här flyttar du miljön till HTTP v1:

1. Bläddra till din lista över **Tjänster och prenumerationer**.
1. Lista alla mobilprogram som använder **HTTP (äldre)** API-version.
1. För vart och ett av dessa mobilprogram anger du **API-version** till **HTTP v1**.
1. Klicka på **[!UICONTROL Load project json file to extract project details...]** för att läsa in JSON-nyckelfilen direkt.

   Du kan även ange följande manuellt:

   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/android-http-v1-config.png)

1. Klicka **[!UICONTROL Test the connection]** för att kontrollera att konfigurationen är korrekt och att marknadsföringsservern har åtkomst till FCM. Observera att när det gäller distributioner via medelkällor **[!UICONTROL Test connection]** kan inte kontrollera om servern har åtkomst till tjänsten Android Firebase Cloud Messaging (FCM).
1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.
1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**.

   Nedan finns FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande. Dessa alternativ är detaljerade [här](#fcm-apps).

   | Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
   |:-:|:-:|:-:|
   | datameddelande | N/A | validate_only |
   | meddelandemeddelande | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

1. När övergången till HTTP v1 är klar måste du uppdatera **leveransmallar** för Android push-meddelanden för att öka antalet batchmeddelanden. Det gör du genom att bläddra till egenskaperna för Android-leveransmallen och i **Leverans** -flik, ange [Batchkvantitet för meddelande](../../v8/send/configure-and-send.md#delivery-batch-quantity) till **256**. Ändringen gäller alla Android leveransmallar som används för Android-leveranser och för alla befintliga Android-leveranser.


>[!NOTE]
>
>När dessa ändringar har tillämpats på alla servrar använder alla nya push-meddelanden som levereras till Android-enheter HTTP v1-API:t. Befintliga push-leveranser som används, pågår och används, använder fortfarande HTTP-API:t (äldre).

### Vilken effekt har mina Android-appar? {#fcm-apps}

Det krävs inga specifika ändringar i Android Mobile-programkoden och meddelandefunktionen bör inte ändras.

Med HTTP v1 kan du dock anpassa push-meddelandena ytterligare med **[!UICONTROL HTTPV1 additional options]**.

![](assets/android-push-additional-options.png)

Du kan:

* Använd **[!UICONTROL Ticker]** för att ange tickningstexten för meddelandet.
* Använd **[!UICONTROL Image]** för att ange bildens URL som ska visas i meddelandet.
* Använd **[!UICONTROL Notification Count]** för att ange antalet nya olästa uppgifter som ska visas direkt på programikonen.
* Ange **[!UICONTROL Sticky]** till false så att meddelandet automatiskt stängs när användaren klickar på det. Om värdet är true visas meddelandet fortfarande även när användaren klickar på det.
* Ange **[!UICONTROL Notification Priority]** nivån på dina meddelanden till standard, minimum, low eller high.
* Ange **[!UICONTROL Visibility]** nivån på dina meddelanden till allmänheten, privat eller hemligt.

Mer information finns på **[!UICONTROL HTTP v1 additional options]** och hur du fyller i dessa fält, se [FCM-dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.



## Apple iOS Push Notification service (APN:er) {#apns-push-upgrade}

### Vad har ändrats? {#ios-changes}

Som Apple rekommenderar bör du skydda kommunikationen med Apple Push Notification-tjänsten (APN:er) genom att använda statslösa autentiseringstoken.

Tokenbaserad autentisering är ett tillståndslöst sätt att kommunicera med APN:er. Tillståndslös kommunikation är snabbare än certifikatbaserad kommunikation eftersom det inte krävs APN:er för att slå upp certifikatet, eller annan information, som är relaterad till din leverantörsserver. Det finns andra fördelar med att använda tokenbaserad autentisering:

* Du kan använda samma token från flera providerservrar.

* Du kan använda en token för att distribuera meddelanden för alla företagets appar.

Läs mer om tokenbaserade anslutningar till APN:er i [Dokumentation för Apple Developer](https://developer.apple.com/documentation/usernotifications/establishing-a-token-based-connection-to-apns){target="_blank"}.

Adobe Campaign Classic v7 och Adobe Campaign v8 har stöd för både tokenbaserade och certifikatbaserade anslutningar. Om implementeringen bygger på en certifikatbaserad anslutning rekommenderar Adobe att du uppdaterar den till en tokenbaserad anslutning.

### Påverkas du? {#ios-impact}

Om den aktuella implementeringen är beroende av certifikatbaserade begäranden om att ansluta till APN:er, påverkas du. Övergång till en tokenbaserad anslutning rekommenderas.

Om du vill kontrollera om du påverkas kan du filtrera **Tjänster och prenumerationer** enligt filtret nedan:

![](assets/filter-services-ios.png)


* Om någon av dina aktiva push-meddelandetjänster använder **Certifikatbaserad autentisering** (.p12) bör dina nuvarande implementeringar granskas och flyttas till en **Tokenbaserad autentisering** läge (.p8) enligt beskrivningen nedan.

* Om din installation endast använder **Tokenbaserad autentisering** för push-meddelanden från iOS är implementeringen redan uppdaterad och ingen ytterligare åtgärd krävs från din sida.

### Hur uppdaterar jag? {#ios-transition-procedure}

#### Förhandskrav {#ios-transition-prerequisites}

* För Campaign Classic v7 har **Tokenbaserad autentisering** Läget har lagts till i version 20.2. Om miljön körs på en äldre version är en förutsättning för den här ändringen att du uppgraderar miljön till [senaste Campaign Classicen](https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/latest-release.html){target="_blank"}. För Campaign v8, **Tokenbaserad autentisering** läge stöds av alla versioner och ingen uppgradering behövs.

* Du behöver en signeringsnyckel för APN:s autentiseringstoken för att generera de tokens som servern använder. Du begär den här nyckeln från ditt Apple-utvecklarkonto, vilket förklaras i [Dokumentation för Apple Developer](https://developer.apple.com/documentation/usernotifications/establishing-a-token-based-connection-to-apns){target="_blank"}.

* För Hybrid-, Hosted- och Managed Services-distributioner ska du, utöver övergångsproceduren nedan, kontakta Adobe för att uppdatera körningsservern för realtid (RT). Servern för MID-Source påverkas inte.

* Som Campaign Classic v7-användare på plats måste ni uppgradera både marknadsförings- och Real-Time Execution-servrarna. Servern för MID-Source påverkas inte.

#### Övergångsförfarande {#ios-transition-steps}

Så här flyttar du dina iOS-mobilprogram till det tokenbaserade autentiseringsläget:

1. Bläddra till din lista över **Tjänster och prenumerationer**.
1. Lista alla mobilprogram som använder **Certifikatbaserad autentisering** mode (.p12).
1. Redigera vart och ett av dessa mobilprogram och gå till **Certifikat/privat nyckel** -fliken.
1. Från **Autentiseringsläge** nedrullningsbar meny, välja **Tokenbaserad autentisering** mode (.p8).
1. Fyll i APN-anslutningsinställningarna **[!UICONTROL Key Id]**, **[!UICONTROL Team Id]** och **[!UICONTROL Bundle Id]** välj sedan ditt p8-certifikat genom att klicka på **[!UICONTROL Enter the private key...]**.

   ![](assets/token-based-certif.png)

1. Klicka **[!UICONTROL Test the connection]** för att kontrollera att konfigurationen är korrekt och att servern har åtkomst till APN:er. Observera att när det gäller distributioner via medelkällor **[!UICONTROL Test connection]** -knappen kan inte kontrollera om servern har åtkomst till APN:er.
1. Klicka **[!UICONTROL Next]** för att börja konfigurera produktionsprogrammet och följa de steg som beskrivs ovan.
1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**.

Ditt iOS-program flyttas nu till det tokenbaserade autentiseringsläget.
