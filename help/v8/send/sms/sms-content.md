---
title: SMS definierar innehållet
description: Lär dig hur du konfigurerar innehållet i en SMS-leverans
feature: SMS
role: User
level: Beginner, Intermediate
exl-id: 71d9376c-86e8-41ec-92dc-863455d40c7a
source-git-commit: 70af3bceee67082d6a1bb098e60fd2899dc74600
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# SMS-innehåll {#sms-content}

Så här konfigurerar du innehållet i SMS-leveransen:

1. Ange innehållet i meddelandet i guiden **[!UICONTROL Text content]**

   ![](assets/sms_content.png){zoomable="yes"}

1. Du kan anpassa ditt meddelande genom att infoga anpassningsfält (t.ex. lägga till förnamnet) eller infoga fördefinierade anpassningsblock (t.ex. lägga till hälsningar). Du kan lägga till följande genom att klicka på personaliseringsknappen:

   ![](assets/sms_perso.png){zoomable="yes"}

   När du har klickat på **[!UICONTROL Recipient]** > **[!UICONTROL First name]** får du den här personaliseringen:

   ![](assets/sms_perso_recipient.png){zoomable="yes"}

1. Du kan förhandsgranska leveransen genom att gå till fliken **[!UICONTROL Preview]** och klicka på listrutan **[!UICONTROL Test personalization]** och genom att välja en mottagare i tabellen **[!UICONTROL Recipient]**.

   ![](assets/sms_preview.png){zoomable="yes"}

   Du får en förhandsgranskning av ditt SMS med personaliseringen:

   ![](assets/sms_preview_phone.png){zoomable="yes"}

>[!NOTE]
>
>* SMS-meddelanden är begränsade till en längd på 160 tecken om den latinska 1-teckentabellen (ISO-8859-1) används. Om meddelandet skrivs i Unicode får det inte innehålla fler än 70 tecken. Vissa specialtecken kan påverka meddelandets längd. Mer information om meddelandets längd finns i avsnittet [SMS-teckentranslittation](smpp-external-account.md#smpp-channel-settings).
>
>* När det finns anpassningsfält eller fält för villkorligt innehåll varierar meddelandets storlek från en mottagare till en annan. Meddelandets längd måste utvärderas när personalisering har utförts.
>
>*När du startar analysen kontrolleras meddelandets längd och en varning visas om det skulle uppstå ett spill.

När du har skapat innehållet i leveransen kan du [välja målgrupp](sms-audience.md).