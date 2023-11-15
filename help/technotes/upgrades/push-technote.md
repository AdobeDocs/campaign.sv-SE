---
product: campaign
title: Kommande ändringar i push-meddelandekanalen
description: Kommande ändringar i push-meddelandekanalen
hide: true
hidefromtoc: true
source-git-commit: 5ed6a5c9c458381ef701428aeab146afe4788d58
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 1%

---

# Kommande ändringar i push-meddelandekanalen {#push-upgrade}

Du kan använda Campaign för att skicka push-meddelanden på Android-enheter. För att kunna göra detta förlitar sig Campaign på specifika prenumerationstjänster. Vissa viktiga ändringar av tjänsten Android Firebase Cloud Messaging (FCM) kommer att släppas 2024 och kan påverka din Adobe Campaign-implementering. Din prenumerationstjänstkonfiguration för push-meddelanden för Android kan behöva uppdateras för att den här ändringen ska fungera.

## Vad har ändrats? {#fcm-changes}

Som en del av Google kontinuerliga arbete med att förbättra sina tjänster kommer de äldre FCM-API:erna att upphöra på **20 juni 2024**. Läs mer om HTTP-protokollet för Firebase Cloud Messaging i [Google Firebase-dokumentation](https://firebase.google.com/docs/cloud-messaging/http-server-ref){target="_blank"}.

Adobe Campaign Classic v7 och Adobe Campaign v8 har redan stöd för de senaste API:erna för att skicka push-meddelanden. Vissa gamla implementeringar är dock fortfarande beroende av de äldre API:erna. Dessa implementeringar måste uppdateras.

## Påverkas du? {#fcm-impact}

Om din nuvarande implementering stöder prenumerationstjänster som ansluter till FCM med de äldre API:erna påverkas du. Migrering till de senaste API:erna är obligatoriskt för att undvika eventuella störningar i tjänsten. I så fall kommer Adobe-teamen att kontakta dig.

Om du vill kontrollera om du påverkas kan du filtrera **Tjänster och prenumerationer** enligt filtret nedan:

![](assets/filter-services-fcm.png)


* Om någon av dina aktiva push-meddelandetjänster använder **HTTP (äldre)** API, din konfiguration påverkas direkt av den här ändringen. Du måste granska dina aktuella konfigurationer och migrera till de nyare API:erna enligt beskrivningen nedan.

* Om din installation endast använder **HTTP v1** API för push-meddelanden för Android är du redan kompatibel och ingen ytterligare åtgärd krävs från din sida.

## Hur migrerar jag? {#fcm-migration-procedure}

### Förhandskrav {#fcm-migration-prerequisites}

* För Campaign Classic v7 har stöd för HTTP v1 lagts till i version 20.3.1. Om miljön körs på en äldre version är en förutsättning för migreringen till HTTP v1 att du uppgraderar miljön till [senaste Campaign Classicen](https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/latest-release.html){target="_blank"}. För Campaign v8 stöds HTTP v1 av alla versioner och ingen uppgradering behövs.

* JSON-filen för kontot för Android-administratören för SDK-tjänsten behövs för att mobilprogrammet ska kunna flyttas till HTTP v1. Lär dig hur du hämtar den här filen i [Google Firebase-dokumentation](https://firebase.google.com/docs/admin/setup#initialize-sdk){target="_blank"}.

* För Hybrid-, Hosted- och Managed Services-distributioner ska du, utöver migreringsproceduren nedan, kontakta Adobe för att uppdatera körningsservern för realtid (RT). Servern för MID-Source påverkas inte.

* Som Campaign Classic v7-användare på plats måste ni uppgradera både marknadsförings- och Real-Time Execution-servrarna. Servern för MID-Source påverkas inte.

### Migreringsförfarande {#fcm-migration-steps}

Så här migrerar du miljön till HTTP v1:

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


>[!NOTE]
>
>När dessa ändringar har tillämpats på alla servrar använder alla nya push-meddelanden som levereras till Android-enheter HTTP v1-API:t. Befintliga push-leveranser som används, pågår och används, använder fortfarande HTTP-API:t (äldre).

### Vilken effekt har mina Android-appar? {#fcm-apps}

Det krävs inga specifika ändringar i koden för Android-mobilprogram och meddelandefunktionen bör inte ändras.

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

