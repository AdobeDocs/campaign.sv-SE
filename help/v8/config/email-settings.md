---
product: Adobe Campaign
title: Inställningar för e-postkanal för kampanj
description: Inställningar för e-postkanal för kampanj
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: 0566d40370a3e14d5205861509f7c1ae8cb4b22d
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 2%

---

# Inställningar för e-postkanal för kampanj

## BCC för e-post

Du kan konfigurera Adobe Campaign att behålla en kopia av e-postmeddelanden som skickas från din plattform.

>[!NOTE]
>Funktionen för e-postkopia är valfri. Kontrollera licensavtalet.

Adobe Campaign hanterar inte själva arkiverade filer. Det gör att du kan skicka meddelanden till en dedikerad adress, varifrån de kan bearbetas och arkiveras i ett externt system.

För att göra detta överförs e-postfiler som motsvarar skickade e-postmeddelanden till en fjärrserver, till exempel en SMTP-e-postserver. Arkiveringsmålet är en e-postadress (osynlig för leveransmottagarna) som du måste ange.

Observera att:

* Du kan bara använda **en** e-postadress för hemlig kopia.

* Det är bara skickad e-post som räknas, studenterna gör det inte.

[!DNL :speech_balloon:] Som användare av hanterade Cloud Services  [kontaktar du ](../start/campaign-faq.md#support) Adobe för att aktivera e-postkopia i Campaign. Du måste ange valfri e-postadress till BCC för det Adobe-team som konfigurerar den åt dig.

När du har konfigurerat BCC för e-post kontrollerar du att funktionen är aktiverad i leveransmallen eller i leveransen via alternativet **BCC för e-post**.

![](assets/email-bcc.png)


**Dokumentation** för närliggande ämnen i Campaign Classic v7:


[!DNL :arrow_upper_right:] [Generera spegelsidan](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#generating-mirror-page){target=&quot;_blank&quot;}

[!DNL :arrow_upper_right:] [Välj e-postformat](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#selecting-message-formats){target=&quot;_blank&quot;}

[!DNL :arrow_upper_right:] [Välj teckenkodning](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#character-encoding){target=&quot;_blank&quot;}

[!DNL :arrow_upper_right:] [Ange studsens e-postadress](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#managing-bounce-emails){target=&quot;_blank&quot;}

[!DNL :arrow_upper_right:] [Använd mallar](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-delivery-templates/about-templates.html) för e-postleverans {target=&quot;_blank&quot;}

[!DNL :arrow_upper_right:] [Förstå leveransfel](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html){target=&quot;_blank&quot;}
