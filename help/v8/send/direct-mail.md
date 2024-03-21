---
title: Skicka direktreklam med Adobe Campaign
description: Kom igång med direktreklam i Campaign
feature: Direct Mail
role: User
level: Beginner
exl-id: ff2be012-72f3-428d-a973-196fea7ec4ab
source-git-commit: 061197048885a30249bd18af7f8b24cb71def742
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---

# Skapa direktutskicksleveranser

Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen. Du kan sedan dela den här filen med leverantören som levererar meddelanden till målpopulationerna.

Steg för att generera filen är:

1. Skapa leveransen

   Skapa en direktutskick baserat på mallen. Du kan duplicera och konfigurera **[!UICONTROL Deliver by direct mail (paper)]** inbyggd mall.

   Läs mer i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-direct-mail/creating-a-direct-mail-delivery.html){target="_blank"}

1. Definiera målgruppen

   Mottagarprofilerna måste innehålla minst namn och postadresser.

   Postadresser är beräkningsfält. En adress kan som standard innehålla upp till sex rader: den första innehåller förnamnet och efternamnet, de följande raderna innehåller postadressen (väg osv.) och den sista raden innehåller postnumret och ort eller stad. Definitionen av standardfältet för beräknad postadress kan granskas i nms:mottagarschemat.

   En adress anses vara fullständig om fälten för namn, postnummer och ort inte är tomma. Mottagare med ofullständiga adresser utesluts från direktutskick.

   Läs mer i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-defining-the-target-population.html){target="_blank"}

1. Definiera filens innehåll

   Använd extraheringsguiden för att definiera informationen (kolumnerna) som ska exporteras till utdatafilen.

   Läs mer i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-direct-mail/defining-the-direct-mail-content.html){target="_blank"}

1. Validera leveransen

   Kontrollera resultatet av analysen och innehållet i utdatafilen.

   Läs mer i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-direct-mail/validating.html){target="_blank"}

   Extraheringsfilen skapas i samband med en marknadsföringskampanj på extraheringsdatumet. Du kan visa innehållet i den extraherade filen, godkänna den eller ändra formatet och starta extraheringen igen om det behövs. När filen har godkänts kan du skicka e-postmeddelandet till routern. Läs mer i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html)

1. Påbörja leveransen

   När du har validerat extraheringsfilen klickar du på **Bekräfta leverans** Med ett bekräftelsemeddelande kan du starta leveransen.

   Bekräftelsen startar dataextraheringen i den angivna filen.

   När alla godkännanden har beviljats inom ramen för en marknadsföringskampanj skapas extraheringsfilerna via ett särskilt arbetsflöde som, i en standardkonfiguration, startar automatiskt när en direktleverans väntar på extrahering. Läs mer i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html)
