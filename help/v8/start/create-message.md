---
title: Kom igång med meddelanden
description: Kom igång med meddelanden
feature: Email, Push, SMS, Direct Mail, Cross Channel Orchestration
role: User
level: Beginner
exl-id: 6cf8a929-637e-4e51-9160-5980ca727efb
source-git-commit: 4c79078e32c77499f15906fc81f31ce2b26559d7
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 4%

---

# Kom igång med meddelanden{#gs-ac-audiences}

Med Adobe Campaign kan ni skicka flerkanalskampanjer, inklusive e-post, SMS, push-meddelanden och direktreklam, och mäta hur effektiva de är med hjälp av olika dedikerade rapporter. Dessa meddelanden är utformade och skickas genom leveranser och kan anpassas för varje mottagare.

De viktigaste funktionerna är målinriktning, definition och personalisering av meddelanden, genomförande av kommunikation och tillhörande verksamhetsrapporter. Den huvudsakliga funktionella åtkomstpunkten är leveransassistenten. Den här åtkomstpunkten leder till flera funktioner som täcks av Adobe Campaign.

Lär dig viktiga steg för att skapa en leverans i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-about-delivery-creation-steps.html).

Adobe Campaign v8 har följande leveranskanaler:

* **E-postkanal**: Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen. Läs mer i [den här sidan](../send/email.md).

* **Direktpostkanal**: Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen.  Läs mer i [den här sidan](../send/direct-mail.md)

* **Mobilkanal**: leveranser i mobilkanaler gör att du kan skicka personaliserat SMS till målpopulationen.  Läs mer i [den här sidan](../send/sms.md)

* **Mobil programkanal**: mobilappsleveranser gör att du kan skicka meddelanden till iOS- och Android-system.  Läs mer i [den här sidan](../send/push.md)

<!--
* **LINE channel**: LINE deliveries let you send messages on LINE, an instant messaging application available on all smartphones. Learn more in [this page](../send/line.md)
-->

## Välj hur du vill skicka meddelanden{#gs-send-msg}

När meddelandet har skapats och dess innehåll har utformats och testats kan du välja hur du vill skicka det. Campaign erbjuder en uppsättning funktioner för att:

* Skicka meddelanden manuellt till huvudmålet

   ![](assets/send-email.png)

   Lär dig hur du skickar meddelanden i [det här avsnittet](../send/send.md)

* Skicka meddelanden som är kopplade till en [marknadsföringskampanj](campaigns.md)

   ![](assets/deliveries-in-a-campaign.png)

   Lär dig hur du skickar meddelanden i samband med en kampanj i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html)

* Skicka meddelanden via [arbetsflöde](../config/workflows.md)

   ![](assets/send-in-a-wf.png)

   Lär dig automatisera e-postleveranser i [den här sidan](../../automation/workflow/delivery.md)

* [Utlösarmeddelanden](../send/transactional.md) från en händelse

* Schemalägg meddelanden

   ![](assets/schedule-send.png)

[Användningsfall: läs om schemat och skicka födelsedag via e-post](../../automation/workflow/send-a-birthday-email.md)


## Lägg till personalisering{#personalization}

Meddelanden från Adobe Campaign kan personaliseras på olika sätt. [Läs mer om personaliseringsfunktioner](../send/personalize.md)

Du kan:

* Infoga dynamiska personaliseringsfält. [Läs mer](../send/personalization-fields.md)
* Infoga fördefinierade personaliseringsblock. [Läs mer](../send/personalization-blocks.md)
* Skapa villkorsstyrt innehåll. [Läs mer](../send/conditions.md)

## Skicka transaktionsmeddelanden{#gs-transac-messages}

Transactional messaging (Message Center) är den Campaign-modul som är avsedd för hantering av utlösarmeddelanden.

![](../assets/do-not-localize/glass.png) Läs mer om funktioner för transaktionsmeddelanden i [det här avsnittet](../architecture/architecture.md#transac-msg-archi)

![](../assets/do-not-localize/glass.png) Steg för att konfigurera och skicka transaktionsmeddelanden beskrivs i [den här sidan](../send/transactional.md)

![](../assets/do-not-localize/book.png) Upptäck den här funktionen i ett heltäckande användningsfall i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/transactional-email-with-attachments.html){target="_blank"}

## Loggar för leverans och spårning{#gs-tracking-logs}

Att övervaka era leveranser efter att de har skickats är ett viktigt steg för att se till att era marknadsföringskampanjer är effektiva och når ut till era kunder. Du kan övervaka efter att du har skickat en leverans samt förstå hur leveransfel och karantäner hanteras.

![](../assets/do-not-localize/book.png) Lär dig hur du övervakar leveranser i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html#sending-messages){target="_blank"}

