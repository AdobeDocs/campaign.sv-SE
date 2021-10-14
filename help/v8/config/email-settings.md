---
title: Inställningar för e-postkanal för kampanj
description: Inställningar för e-postkanal för kampanj
feature: Overview
role: Data Engineer
level: Beginner
exl-id: e4e3fb49-9942-4e2d-a020-557d1ac5dcdc
source-git-commit: 63b53fb6a7c6ecbfc981c93a723b6758b5736acf
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

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

![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Services  [kontaktar du ](../start/campaign-faq.md#support) Adobe för att aktivera e-postkopia i Campaign. Du måste ange valfri e-postadress till BCC för det Adobe-team som konfigurerar den åt dig.

När du har konfigurerat BCC för e-post kontrollerar du att funktionen är aktiverad i leveransmallen eller i leveransen via alternativet **BCC för e-post**.

![](assets/email-bcc.png)


**Dokumentation** för närliggande ämnen i Campaign Classic v7:


* [Generera spegelsidan](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#generating-mirror-page){target=&quot;_blank&quot;}

* [Välj e-postformat](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#selecting-message-formats){target=&quot;_blank&quot;}

* [Välj teckenkodning](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#character-encoding){target=&quot;_blank&quot;}

* [Ange studsens e-postadress](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#managing-bounce-emails){target=&quot;_blank&quot;}

* [Använd mallar](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-delivery-templates/about-templates.html) för e-postleverans {target=&quot;_blank&quot;}

* [Förstå leveransfel](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html){target=&quot;_blank&quot;}
