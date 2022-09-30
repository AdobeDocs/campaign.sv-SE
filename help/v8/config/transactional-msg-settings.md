---
title: Inställningar för kampanjtransaktionsmeddelanden
description: Inställningar för kampanjtransaktionsmeddelanden
feature: Transactional Messaging
role: Admin, Developer
level: Intermediate, Experienced
exl-id: 2899f627-696d-422c-ae49-c1e293b283af
source-git-commit: 2ce1ef1e935080a66452c31442f745891b9ab9b3
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Inställningar för transaktionsmeddelanden

![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Services [kontakta Adobe](../start/campaign-faq.md#support) för att installera och konfigurera Campaign Transactional Messaging i er miljö.

![](../assets/do-not-localize/glass.png) Funktionerna för transaktionsmeddelanden beskrivs i [det här avsnittet](../send/transactional.md).

![](../assets/do-not-localize/glass.png) Förstå arkitekturen för transaktionsmeddelanden i [den här sidan](../architecture/architecture.md).

## Definiera behörigheter

Om du vill skapa nya användare för instanser av körning i Message Center på Adobe Cloud måste du kontakta Adobe kundtjänst. Meddelandecenteranvändare är specifika operatorer som kräver dedikerad behörighet för att få åtkomst till mappar för&quot;realtidshändelser&quot; (nmsRtEvent).

## Schematillägg

Alla schematillägg som gjorts för scheman som används av **Tekniska arbetsflöden för meddelandecenter** på antingen kontroll- eller körningsinstanser måste dupliceras på de andra instanser som används av Adobe Campaign transaktionsmeddelandemodul.

![](../assets/do-not-localize/book.png) Läs mer om Tekniska arbetsflöden i Message Center i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/configure-transactional-messaging/additional-configurations.html#technical-workflows)

## Skicka push-meddelanden för transaktioner

I kombination med mobilappskanalmodulen kan du med transaktionsmeddelanden skicka transaktionsmeddelanden via meddelanden på mobila enheter.

![](../assets/do-not-localize/book.png) Mobilappskanalen finns i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/about-mobile-app-channel.html?lang=en#sending-messages).

Om du vill skicka push-meddelanden för transaktioner måste du utföra följande konfigurationer:

1. Installera **Mobilappskanal** till kontroll- och körningsinstanserna.

   >[!CAUTION]
   >
   >Kontrollera licensavtalet innan du installerar ett nytt inbyggt Campaign-paket.

1. Replikera **Mobilapplikation** och tillhörande mobilprogram på körningsinstanserna.

För att Campaign ska kunna skicka transaktionspush-meddelanden måste händelsen innehålla följande element:

* ID för den mobila enheten: **registrationId** för Android och **deviceToken** för iOS. Detta ID representerar den adress som meddelandet ska skickas till.
* Länken till mobilprogrammet eller integreringsnyckeln (**uuid**) som gör att du kan hämta anslutningsinformation som är specifik för programmet.
* Den kanal som meddelandet skickas till (**requestedChannel**): 41 för iOS och 42 för Android.
* Andra data som kan användas för personalisering.

Här är ett exempel på en händelse som innehåller den här informationen:

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
