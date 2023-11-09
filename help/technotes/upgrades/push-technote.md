---
product: campaign
title: Kommande ändringar i push-meddelandekanalen
description: Kommande ändringar i push-meddelandekanalen
hide: true
hidefromtoc: true
source-git-commit: 11330ed8e79ec256b158747914f178b8b6857a33
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# Kommande ändringar i push-meddelandekanalen {#push-upgrade}

Den här sidan beskriver kommande ändringar av Push Notification Channel via Firebase Cloud Messaging i Adobe Campaign Classic.

Var är viktiga ändringar av tjänsten Firebase Cloud Messaging (FCM) som kan påverka er Adobe Campaign Classic-implementering?

Som en del av Google fortsatta insatser för att förbättra sina tjänster kommer de äldre FCM-API:erna att upphöra i juni 2024 (HTTP-protokollet för Firebase Cloud Messaging: https://firebase.google.com/docs/cloud-messaging/http-server-ref)

Dessa API:er är för närvarande integrerade med Adobe Campaign Classic för att skicka push-meddelanden. Vi förstår att många av våra kunder, precis som du, förlitar sig på dessa tjänster för era marknadsföringskampanjer och kommunikationsbehov, och särskilt för Android-enheter.

## Hur påverkar det dig?

* **HTTP-API-användare (äldre)**: Om någon av dina aktiva push-meddelandekampanjer använder HTTP-API:t (äldre) påverkas din konfiguration direkt av den här ändringen. Vi rekommenderar att du granskar dina aktuella konfigurationer och förbereder dig för migreringen till de nyare API:erna.

* **Goda nyheter för API-användare för HTTP v1**: Om din installation endast använder HTTP v1 API för push-meddelanden för Android är du redan kompatibel och ingen ytterligare åtgärd krävs från din sida.

## Vad gör vi?

* **Övergångsplan**: Vårt team arbetar aktivt med att ta fram en heltäckande övergångsplan. Detta säkerställer att ni vid behov kan uppdatera implementeringen till de nyare FCM-API:erna som redan finns i de senaste versionerna av Adobe Campaign och utan avbrott i era kampanjer.

* **Detaljerade instruktioner**: Vi kommer att tillhandahålla en stegvis guide och andra resurser som underlättar en smidig övergångsprocess.

* **Support**: Vårt kundsupportteam kommer att finnas tillgängligt för att hjälpa dig under den här övergången. Vi kan också vara värd för webbinarier och hjälpmedelsseminarier som täcker de tekniska aspekterna och bästa metoderna för övergången.

## Hur påverkar det dig?

* **Håll dig informerad**: Håll ett öga på inkorgen för mer information från oss, inklusive den detaljerade övergångsplanen.

* **Granska aktuell inställning**: Ta den här tiden till att granska din nuvarande konfiguration och anpassning i Adobe Campaign Classic så att du är redo att göra nödvändiga ändringar om det behövs.

* **Kontakta oss**: Om du har frågor eller funderingar direkt kan du kontakta vårt supportteam.

## Implementeringssteg

Under de närmaste veckorna kommer vi att dela mer information om övergångsplanen för äldre FCM-API:er, inklusive tidslinjer och åtgärdsobjekt. Som du kan vara säker på är vårt främsta mål att göra övergången så smidig som möjligt för dig och ditt team.

Vi uppskattar din verksamhet och tackar för din förståelse för att vi kan anpassa oss till dessa förändringar. Er framgång är vår högsta prioritet, och vi strävar efter att stödja er i varje steg på vägen.

Så du kan förutse ändringen här är de allmänna stegen som behövs för att migrera din push-konfiguration från HTTP (äldre) till FCM HTTPv1 API.

### Builduppgradering

* Campaign Classic: Stöd för HTTPv1 har lagts till i AC7 20.3.1-versionen. Om du använder en tidigare version måste du först uppgradera till den senaste Campaign Classicen.

* Campaign v8: HTTPv1 stöds av alla Campaign v8-utgåvor. Ingen uppgradering behövs.

### Marknadsföring

Konfigurationsändringar kan utföras av kunden/partnern.

1. Först måste du extrahera JSON-filen. Firebase Admin SDK-tjänstens konto-JSON-fil behövs för att mobilprogrammet ska kunna flyttas till HTTPv1. Se detta [page](https://firebase.google.com/docs/admin/setup#initialize-sdk).

1. Navigera till din lista med **Tjänster och prenumerationer**.

1. Hitta alla mobilprogram med HTTP-API-versionen (äldre).

1. För vart och ett av dessa mobilprogram anger du **API-version** till HTTPv1 och följ konfigurationsinstruktionerna i [dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application-android.html).

>[!NOTE]
>
>Övergången till HTTPv1 API kommer att beaktas för nya leveranser. Leveranser som görs om, pågår och används fortfarande med HTTP-API:t (äldre).

### MID-källserver

Inga ändringar krävs.

### Körningsserver i realtid

Du måste kontakta Adobe Campaign support för detta. Migreringsproceduren är densamma som för marknadsföringsservern.

### Android OS- och Android-mobilprogram

Det krävs inga specifika ändringar i koden för Android-mobilprogram och meddelandefunktionen bör inte ändras.

HTTPv1 introducerar dock tre nya nyttolastelement:

| Namn | Standardvärde |
|---|---|
| klibbig | Falskt |
| prioritet | Standard |
| synlighet | Falskt |
| klibbig | Privat |
