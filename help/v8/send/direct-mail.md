---
title: Skicka direktreklam med Adobe Campaign
description: Kom igång med direktreklam i Campaign
feature: Direct Mail
role: Data Engineer
level: Beginner
exl-id: ff2be012-72f3-428d-a973-196fea7ec4ab
source-git-commit: 0a55d947a7646aab64ab2f9d0d09a6f930db576e
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# Skapa direktutskicksleveranser

Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen. Du kan sedan dela den här filen med leverantören som levererar meddelanden till målpopulationerna.

Steg för att generera filen är:

1. Skapa leveransen

   Skapa en direktutskick baserat på mallen. Du kan duplicera och konfigurera **[!UICONTROL Deliver by direct mail (paper)]** inbyggd mall.

   ![](../assets/do-not-localize/book.png) Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-direct-mail/creating-a-direct-mail-delivery.html){target=&quot;_blank&quot;}

1. Definiera målgruppen

   Mottagarprofilerna måste innehålla minst namn och postadresser.

   Postadresser är beräkningsfält. En adress kan som standard innehålla upp till sex rader: den första innehåller förnamnet och efternamnet, de följande raderna innehåller postadressen (väg etc.) och den sista raden innehåller postnumret och ort eller stad.

   En adress anses vara fullständig om fälten för namn, postnummer och ort inte är tomma.

   ![](../assets/do-not-localize/book.png) Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-defining-the-target-population.html){target=&quot;_blank&quot;}

1. Definiera filens innehåll

   Använd extraheringsguiden för att definiera informationen (kolumnerna) som ska exporteras till utdatafilen.

   ![](../assets/do-not-localize/book.png) Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-direct-mail/defining-the-direct-mail-content.html){target=&quot;_blank&quot;}

1. Validera leveransen

   Kontrollera resultatet av analysen och innehållet i utdatafilen.

   ![](../assets/do-not-localize/book.png) Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-direct-mail/validating.html){target=&quot;_blank&quot;}

   Extraheringsfilen skapas i samband med en marknadsföringskampanj på extraheringsdatumet. Du kan visa innehållet i den extraherade filen, godkänna den eller ändra formatet och starta extraheringen igen om det behövs. När filen har godkänts kan du skicka e-postmeddelandet till routern. Läs mer i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html)

1. Starta leveransen

   När du har validerat extraheringsfilen klickar du på **Bekräfta leverans** Med ett bekräftelsemeddelande kan du starta leveransen.

   Bekräftelsen startar dataextraheringen i den angivna filen.

   När alla godkännanden har beviljats inom ramen för en marknadsföringskampanj skapas extraheringsfilerna via ett särskilt arbetsflöde som, i en standardkonfiguration, startar automatiskt när en direktleverans väntar på extrahering. Läs mer i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html)
