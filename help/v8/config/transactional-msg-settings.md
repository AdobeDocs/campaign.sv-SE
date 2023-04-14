---
title: Inställningar för kampanjtransaktionsmeddelanden
description: Inställningar för kampanjtransaktionsmeddelanden
feature: Transactional Messaging
role: Admin, Developer
level: Intermediate, Experienced
exl-id: 2899f627-696d-422c-ae49-c1e293b283af
source-git-commit: c61f03252c7cae72ba0426d6edcb839950267c0a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Inställningar för transaktionsmeddelanden

![](../assets/do-not-localize/speech.png) Som användare av hanterade Cloud Services [kontakta Adobe](../start/campaign-faq.md#support) för att installera och konfigurera Campaign Transactional Messaging i er miljö.

![](../assets/do-not-localize/glass.png) Funktionerna för transaktionsmeddelanden beskrivs i [det här avsnittet](../send/transactional.md).

![](../assets/do-not-localize/glass.png) Förstå arkitekturen för transaktionsmeddelanden i [den här sidan](../architecture/architecture.md#transac-msg-archi).

## Definiera behörigheter

Om du vill skapa nya användare för instanser av körning i Message Center på Adobe Cloud måste du kontakta Adobe kundtjänst. Meddelandecenteranvändare är specifika operatorer som kräver dedikerad behörighet för att få åtkomst till mappar för&quot;realtidshändelser&quot; (nmsRtEvent).

## Schematillägg

Alla schematillägg som gjorts för scheman som används av **Tekniska arbetsflöden för meddelandecenter** på antingen kontroll- eller körningsinstanser måste dupliceras på de andra instanser som används av Adobe Campaign transaktionsmeddelandemodul.

![](../assets/do-not-localize/book.png) Läs mer om Tekniska arbetsflöden i Message Center i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/configure-transactional-messaging/additional-configurations.html#technical-workflows)

## Skicka push-meddelanden för transaktioner

I kombination med mobilappskanalmodulen kan du med transaktionsmeddelanden skicka transaktionsmeddelanden via meddelanden på mobila enheter.

![](../assets/do-not-localize/book.png) Mobilappskanalen finns i [det här avsnittet](../send/push.md).

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

## Övervaka gränsvärden {#monitor-thresholds}

Du kan konfigurera varningströskeln (orange) och varningströskeln (röd) för de indikatorer som visas i **Tjänstnivå för meddelandecenter** och **Bearbetningstid för meddelandecenter** rapporter.

Följ stegen nedan för att göra detta:

1. Öppna distributionsguiden på **körningsinstans** och bläddra till **[!UICONTROL Message Center]** sida.
1. Använd pilarna för att ändra tröskelvärdena.


## Rensa händelser {#purge-events}

Du kan anpassa inställningarna för distributionsguiden för att konfigurera hur länge data ska lagras i databasen.

Rensa händelser utförs automatiskt av **Databasrensning** tekniskt arbetsflöde. Det här arbetsflödet tömmer händelser som tagits emot och lagrats på körningsinstanser och händelser som arkiverats på en kontrollinstans.

Använd pilarna för att ändra inställningarna för tömning av **Händelser** (på en körningsinstans) och **Arkiverade händelser** (på en kontrollinstans).


## Tekniska arbetsflöden {#technical-workflows}

Du måste se till att de tekniska arbetsflödena för dina kontroll- och körningsinstanser har startats innan du distribuerar några transaktionsmeddelandemallar.

Du kommer sedan åt dessa arbetsflöden via **Administration > Produktion > Meddelandecenter** mapp.

### Styra instansarbetsflöden {#control-instance-workflows}

I kontrollinstansen måste du skapa ett arkiveringsarbetsflöde för varje **[!UICONTROL Message Center execution instance]** externt konto. Klicka på **[!UICONTROL Create the archiving workflow]** för att skapa och starta arbetsflödet.

### Arbetsflöden för körningsinstanser {#execution-instance-workflows}

På körningsinstansen/instanserna måste du starta följande tekniska arbetsflöden:

* **[!UICONTROL Processing batch events]** (internt namn: **[!UICONTROL batchEventsProcessing]** ): Med det här arbetsflödet kan du dela upp grupphändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Processing real time events]** (internt namn: **[!UICONTROL rtEventsProcessing]** ): Med det här arbetsflödet kan du bryta ned realtidshändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Update event status]** (internt namn: **[!UICONTROL updateEventStatus]** ): det här arbetsflödet gör att du kan tilldela en status till händelsen.

   Möjliga händelselägen är:

   * **[!UICONTROL Pending]**: händelsen finns i kön. Ingen meddelandemall har ännu tilldelats den.
   * **[!UICONTROL Pending delivery]**: Om händelsen finns i kön har en meddelandemall tilldelats den och bearbetas av leveransen.
   * **[!UICONTROL Sent]**: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.
   * **[!UICONTROL Ignored by the delivery]**: den här statusen kopieras från leveransloggarna. Det betyder att leveransen ignorerats.
   * **[!UICONTROL Delivery failed]**: den här statusen kopieras från leveransloggarna. Det betyder att leveransen misslyckats.
   * **[!UICONTROL Event not taken into account]**: händelsen kunde inte länkas till en meddelandemall. Händelsen kommer inte att bearbetas.
