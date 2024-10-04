---
title: Kampanjtransaktionsmeddelanden
description: Kom igång med Transactional Messaging
feature: Transactional Messaging
role: User
level: Beginner, Intermediate
exl-id: 06fdb279-3776-433f-8d27-33d016473dee
source-git-commit: 253f3be945cbfa304fa7342c68f0c73b079e2870
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Kom igång med Transactional Messaging{#send-transactional-messages}

Transactional Messaging (Message Center) är en Campaign-modul som är utformad för att hantera utlösarmeddelanden. Dessa meddelanden genereras från händelser som utlöses från informationssystem och kan vara: faktura, orderbekräftelse, leveransbekräftelse, lösenordsändring, meddelande om otillgänglighet för produkt, kontobesked, skapande av webbkonto osv.

>[!NOTE]
>
>Som användare av hanterade Cloud Service [kontaktar du Adobe](../start/campaign-faq.md#support){target="_blank"} för att konfigurera kampanjtransaktionsmeddelanden i din miljö.

Transaktionsmeddelanden används för att skicka:

* meddelanden, till exempel orderbekräftelser eller lösenordsåterställningar
* ett individuellt svar i realtid på en kunds handling
* icke-marknadsföringsmaterial

Inställningar för transaktionsmeddelanden beskrivs i [det här avsnittet](../config/transactional-msg-settings.md).

Förstå arkitekturen för transaktionsmeddelanden på [den här sidan](../architecture/architecture.md#transac-msg-archi).

## Transactional messaging operating policy policy {#transactional-messaging-operating-principle}

Adobe Campaign Transactional Messaging-modulen integreras i ett informationssystem som returnerar händelser som ska ändras till personaliserade transaktionsmeddelanden. Dessa meddelanden kan skickas individuellt eller gruppvis via e-post, SMS eller push-meddelanden.

Tänk dig att du är ett företag med en webbplats där kunderna kan köpa produkter.

Med Adobe Campaign kan du skicka ett e-postmeddelande till kunder som har lagt till produkter i kundvagnen. När någon av dem lämnar er webbplats utan att gå igenom sina inköp (en extern händelse som utlöser en Campaign-händelse) skickas ett e-postmeddelande om att kunden överger en kundvagn automatiskt till dem (leverans av transaktionsmeddelanden).

De viktigaste stegen för att införa detta är följande:

1. [Skapa en händelsetyp](#create-event-types).
1. [Skapa och utforma meddelandemallen](transactional-template.md#create-message-template). Du måste länka en händelse till ditt meddelande under det här steget.
1. [Testa meddelandet](transactional-template.md#test-message-template).
1. [Publish meddelandemallen](transactional-template.md#publish-message-template).

När du har utformat och publicerat transaktionsmeddelandemallen skickas relevanta data till Campaign via metoderna PushEvent och PushEvents [SOAP ](../send/event-description.md) om en motsvarande händelse aktiveras, och leveransen skickas till målmottagarna.

## Skapa händelsetyper {#create-event-types}

För att vara säker på att varje händelse kan ändras till ett anpassat meddelande måste du först skapa **händelsetyper**.

När [skapar en meddelandemall](#create-message-template) väljer du den typ av händelse som matchar meddelandet som du vill skicka.

>[!CAUTION]
>
>Du måste skapa händelsetyper innan du kan använda dem i meddelandemallar.

Följ stegen nedan för att skapa händelsetyper som ska bearbetas av Adobe Campaign:

1. Bläddra till mappen **[!UICONTROL Administration > Platform > Enumerations]** i Campaign Explorer.
1. Välj uppräkningen **[!UICONTROL Event type]** i listan.
1. Klicka på **[!UICONTROL Add]** om du vill skapa ett uppräkningsvärde. Detta kan vara en orderbekräftelse, lösenordsändring, orderleveransändring osv.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!CAUTION]
   >
   >Varje händelsetyp måste matcha ett värde i uppräkningen **[!UICONTROL Event type]**.

1. När de specificerade listvärdena har skapats loggar du ut och tillbaka till instansen för att det ska gå att skapa.

>[!NOTE]
>
>Läs mer om uppräkningar på [den här sidan](../../v8/config/ui-settings.md#enumerations).

Läs om hur du [skapar och publicerar mallen för transaktionsmeddelanden](transactional-template.md) i nästa steg.
