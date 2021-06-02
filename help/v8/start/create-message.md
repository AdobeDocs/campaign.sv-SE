---
product: Adobe Campaign
title: Kom igång med meddelanden
description: Kom igång med meddelanden
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 6cf8a929-637e-4e51-9160-5980ca727efb
source-git-commit: 41ea85bc3c616ed7cdd0718ff3368aab971a5352
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 4%

---

# Kom igång med meddelanden{#gs-ac-audiences}

Med Adobe Campaign kan ni skicka flerkanalskampanjer, inklusive e-post, SMS, push-meddelanden och direktreklam, och mäta hur effektiva de är med hjälp av olika dedikerade rapporter. Dessa meddelanden är utformade och skickas genom leveranser och kan anpassas för varje mottagare.

De viktigaste funktionerna är målinriktning, definition och personalisering av meddelanden, genomförande av kommunikation och tillhörande verksamhetsrapporter. Den huvudsakliga funktionella åtkomstpunkten är leveransassistenten. Den här åtkomstpunkten leder till flera funktioner som täcks av Adobe Campaign.

Lär dig hur du skapar en leverans i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-about-delivery-creation-steps.html).

Adobe Campaign v8 har följande leveranskanaler:

* **E-postkanal**: Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen. Läs mer i [den här sidan](../send/email.md).

* **Direktpostkanal**: Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen.  Läs mer i [den här sidan](../send/direct-mail.md)

* **Mobilkanal**: leveranser i mobilkanaler gör att du kan skicka personaliserat SMS till målpopulationen.  Läs mer i [den här sidan](../send/sms.md)

* **Mobil programkanal**: mobilappsleveranser gör att du kan skicka meddelanden till iOS- och Android-system.  Läs mer i [den här sidan](../send/push.md)

<!--
* **LINE channel**: LINE deliveries let you send messages on LINE, an instant messaging application available on all smartphones. Learn more in [this page](../send/line.md)
-->

## Välj hur du vill skicka meddelanden

När meddelandet har skapats och dess innehåll har utformats och testats kan du välja hur du vill skicka det. Campaign erbjuder en uppsättning funktioner för att:

* Skicka meddelanden manuellt till huvudmålet
   [!DNL :arrow_upper_right:] [Lär dig hur du skickar meddelanden](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-messages.html)
* Skicka meddelanden som är kopplade till en [marknadsföringskampanj](campaigns.md)
   [!DNL :arrow_upper_right:] [Lär dig hur du skickar meddelanden i samband med en kampanj](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-deliveries.html).
* Skicka meddelanden via ett [arbetsflöde](../config/workflows.md)
   [!DNL :arrow_upper_right:] [Lär dig automatisera e-postleveranser](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/action-activities/delivery.html)
* [Utlös ](../send/transactional.md) meddelanden från en händelse
   [!DNL :arrow_upper_right:] [Användningsfall: lära dig hur du skickar ett transaktionsmejl med en bifogad fil](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/use-case/transactional-email-with-attachments.html)
* Schemalägg meddelanden
   [!DNL :arrow_upper_right:] [Användningsfall: läs om schemat och skicka födelsedag via e-post](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/sending-a-birthday-email.html?)


## Lägg till personalisering

Meddelanden från Adobe Campaign kan personaliseras på olika sätt.

Du kan:

* Infoga dynamiska personaliseringsfält.
   [!DNL :arrow_upper_right:] Lär dig hur du använder personaliseringsfält i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/personalizing-deliveries/personalization-fields.html)
* Infoga fördefinierade personaliseringsblock.
   [!DNL :arrow_upper_right:] Lär dig vad som är ett personaliseringsblock och hur du använder det i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/personalizing-deliveries/personalization-blocks.html)
* Skapa villkorsstyrt innehåll.
   [!DNL :arrow_upper_right:] Lär dig hur du infogar villkorsstyrt innehåll i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/personalizing-deliveries/conditional-content.html)

## Skicka transaktionsmeddelanden

Transactional messaging (Message Center) är den Campaign-modul som är avsedd för hantering av utlösarmeddelanden.

[!DNL :bulb:] Läs mer om funktioner för transaktionsmeddelanden i  [det här avsnittet](../dev/architecture.md#transac-msg-archi)

[!DNL :bulb:] Steg för att konfigurera och skicka transaktionsmeddelanden finns på  [den här sidan](../send/transactional.md)

[!DNL :arrow_upper_right:] Upptäck den här funktionen i ett heltäckande användningsfall i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/use-case/transactional-email-with-attachments.html?lang=en#transactional-messaging)

## Loggar för leverans och spårning

Att övervaka era leveranser efter att de har skickats är ett viktigt steg för att se till att era marknadsföringskampanjer är effektiva och når ut till era kunder. Du kan övervaka efter att du har skickat en leverans samt förstå hur leveransfel och karantäner hanteras.

[!DNL :arrow_upper_right:] [Lär dig hur du övervakar leveranser i det här avsnittet](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=en#sending-messages)


**Relaterade ämnen**

[!DNL :arrow_upper_right:]  [Bästa praxis för leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/delivery-best-practices.html)

[!DNL :arrow_upper_right:]  [Testa och skicka ett e-postmeddelande](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-messages.html)

[!DNL :arrow_upper_right:]  [Skicka korrektur](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html)
