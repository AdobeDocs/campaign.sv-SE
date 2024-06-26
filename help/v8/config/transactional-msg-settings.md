---
title: Inställningar för kampanjtransaktionsmeddelanden
description: Inställningar för kampanjtransaktionsmeddelanden
feature: Transactional Messaging
role: Admin, Developer
level: Experienced
exl-id: 2899f627-696d-422c-ae49-c1e293b283af
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 4%

---

# Inställningar för transaktionsmeddelanden {#mc-settings}

Transactional Messaging (Message Center) är en Campaign-modul som är avsedd för hantering av utlösta meddelanden. Läs mer om Transactional Messaging i [det här avsnittet](../send/transactional.md).

Förstå arkitekturen för transaktionsmeddelanden i [den här sidan](../architecture/architecture.md#transac-msg-archi).


>[!NOTE]
>
>Som användare av hanterade Cloud Service [kontakta Adobe](../start/campaign-faq.md#support) för att installera och konfigurera Campaign Transactional Messaging i er miljö.

## Definiera behörigheter {#mc-permissions}

Kontakta din Adobe Transition Manager om du vill skapa nya användare för instanser av körning i Message Center som finns i Adobe Cloud. Message Center-användare är specifika operatorer som kräver dedikerad behörighet för att få åtkomst till mappar för &#39;Real time events&#39; (nmsRtEvent).

## Schematillägg  {#mc-schema-ext}

Alla schematillägg som gjorts för scheman som används av [Tekniska arbetsflöden för meddelandecenter](#technical-workflows) på antingen kontroll- eller körningsinstanser måste dupliceras på de andra instanser som används av Adobe Campaign transaktionsmeddelandemodul.

## Skicka push-meddelanden för transaktioner {#mc-transactional-push}

Vid kombination med [Modulen Mobilappskanal](../send/push.md)kan du med transaktionsmeddelanden skicka transaktionsmeddelanden via meddelanden på mobila enheter.

Om du vill skicka push-meddelanden för transaktioner måste du utföra följande konfigurationer:

1. Installera **Mobilappskanal** till kontroll- och körningsinstanserna.

   >[!CAUTION]
   >
   >Kontrollera licensavtalet innan du installerar ett nytt inbyggt Campaign-paket.

1. Replikera **Mobilapplikation** och tillhörande mobilprogram på körningsinstanserna.

Dessutom måste händelsen innehålla följande element:

* ID för den mobila enheten: **registrationId** för Android och **deviceToken** för iOS. Detta ID representerar den adress som meddelandet skickas till.
* Länken till mobilprogrammet eller integreringsnyckeln (**uuid**) som gör att du kan hämta anslutningsinformation som är specifik för programmet.
* Den kanal som meddelandet ska skickas till (**requestedChannel**): 41 för iOS och 42 för Android.
* Alla andra personaliseringsdata.

Nedan visas ett exempel på en händelsekonfiguration som skickar push-meddelanden för transaktioner:

```xml
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation="none" uuid="com.adobe.NeoMiles"/>
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

## Rensa händelser {#purge-events}

Du kan anpassa inställningarna för distributionsguiden för att konfigurera hur länge data ska lagras i databasen.

Händelsetömning utförs automatiskt av **Databasrensning** tekniskt arbetsflöde. Det här arbetsflödet tömmer händelser som tagits emot och lagrats på körningsinstanser och händelser som arkiverats på en kontrollinstans.

Använd pilarna för att ändra inställningarna för tömning av **Händelser** (på en körningsinstans) och **Arkiverade händelser** (på en kontrollinstans).


## Tekniska arbetsflöden {#technical-workflows}

Du måste se till att de tekniska arbetsflödena för dina kontroll- och körningsinstanser har startats innan du distribuerar några transaktionsmeddelandemallar.

Du kommer sedan åt dessa arbetsflöden via **Administration > Produktion > Meddelandecenter** mapp.

### Styra instansarbetsflöden {#control-instance-workflows}

I kontrollinstansen måste du skapa ett arkiveringsarbetsflöde för varje **[!UICONTROL Message Center execution instance]** externt konto. Klicka på **[!UICONTROL Create the archiving workflow]** för att skapa och starta arbetsflödet.

### Arbetsflöden för körningsinstanser {#execution-instance-workflows}

På körningsinstansen/instanserna måste du starta följande tekniska arbetsflöden:

* **[!UICONTROL Processing batch events]** (internt namn: **[!UICONTROL batchEventsProcessing]** ): Med det här arbetsflödet kan du dela upp grupphändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Processing real time events]** (internt namn: **[!UICONTROL rtEventsProcessing]** ): Med det här arbetsflödet kan du dela upp realtidshändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Update event status]** (internt namn: **[!UICONTROL updateEventStatus]** ): Med det här arbetsflödet kan du tilldela en status till händelsen.

  Möjliga händelselägen är:

   * **[!UICONTROL Pending]**: händelsen finns i kön. Ingen meddelandemall har ännu tilldelats den.
   * **[!UICONTROL Pending delivery]**: händelsen finns i kön, en meddelandemall har tilldelats den och bearbetas av leveransen.
   * **[!UICONTROL Sent]**: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.
   * **[!UICONTROL Ignored by the delivery]**: den här statusen kopieras från leveransloggarna. Det betyder att leveransen ignorerats.
   * **[!UICONTROL Delivery failed]**: den här statusen kopieras från leveransloggarna. Det betyder att leveransen misslyckats.
   * **[!UICONTROL Event not taken into account]**: händelsen kunde inte länkas till en meddelandemall. Händelsen kommer inte att bearbetas.
