---
title: Inställningar för e-postkanal för kampanj
description: Inställningar för e-postkanal för kampanj
feature: Email
role: User
level: Intermediate, Experienced
exl-id: e4e3fb49-9942-4e2d-a020-557d1ac5dcdc
source-git-commit: edb099b3e882d857752af76798012ccd1c5a99be
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 4%

---

# Inställningar för e-postkanal för kampanj

## BCC för e-post {#email-bcc}

<!--
>[!NOTE]
>
>This capability is available starting Campaign v8.3. To check your version, refer to [this section](../start/compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)-->

Du kan konfigurera Adobe Campaign att behålla en kopia av e-postmeddelanden som skickas från din plattform.

Adobe Campaign hanterar inte själva arkiverade filer. Det gör att du kan skicka de meddelanden du vill till en dedikerad e-postadress för hemlig kopia (BCC), varifrån de kan bearbetas och arkiveras i ett externt system. De e-postfiler som motsvarar skickade e-postmeddelanden kan sedan överföras till en fjärrserver, till exempel en SMTP-e-postserver.

>[!CAUTION]
>
>Av sekretesskäl måste e-post från innehållsförteckningen behandlas av ett arkiveringssystem som kan lagra säkert personligt identifierbar information (PII).

Arkiveringsmålet är valfri e-postadress som är osynlig för leveransmottagarna.

![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Services [kontakta Adobe](../start/campaign-faq.md#support){target="_blank"} för att kommunicera e-postadressen för den kontroll av webbläsarkompatibilitet som ska användas för arkivering.

När BCC-e-postadressen har definierats måste du aktivera det dedikerade alternativet på leveransnivån.

>[!CAUTION]
>
>När du skapar en ny leverans- eller leveransmall **[!UICONTROL Email BCC]** är inte aktiverat som standard. Du måste aktivera det manuellt i mallen för e-postleverans eller leverans.


Följ stegen nedan för att göra detta:

1. Gå till **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]**, eller **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Välj leverans eller duplicera den färdiga produkten **[!UICONTROL Email delivery]** väljer du sedan den duplicerade mallen.
1. Klicka på knappen **[!UICONTROL Properties]**.
1. Klicka på fliken **[!UICONTROL Delivery]**.  
1. Markera alternativet **[!UICONTROL Email BCC]**.

   ![](assets/email-bcc.png)

1. Välj **[!UICONTROL Ok]**.

En kopia av alla skickade meddelanden för varje leverans som baseras på den här mallen skickas till den konfigurerade e-postadressen för hemlig kopia.

Observera följande särdrag och rekommendationer:

* Du kan bara använda en e-postadress för hemlig kopia.

* Se till att BCC-adressen har tillräcklig mottagningskapacitet för att arkivera alla e-postmeddelanden som skickas.

* BCC för e-post <!--with Enhanced MTA--> skickar till e-postadressen till BCC innan den skickas till mottagarna, vilket kan leda till att BCC-meddelanden skickas trots att de ursprungliga leveranserna kan ha studsat. Mer information om studsar finns i [Förstå leveransfel](../send/delivery-failures.md).

* Om e-postmeddelanden som skickas till BCC-adressen öppnas och klickas igenom, kommer detta att beaktas i **[!UICONTROL Total opens]** och **[!UICONTROL Clicks]** från sändningsanalysen, vilket kan orsaka några felberäkningar.

<!--Only successfully sent emails are taken in account, bounces are not.-->

**Läs mer i dokumentationen för Campaign Classic v7**

* [Välj e-postformat](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#selecting-message-formats){target="_blank"}

* [Välj teckenkodning](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#character-encoding){target="_blank"}

* [Ange studsens e-postadress](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/email-parameters.html#managing-bounce-emails){target="_blank"}

* [Använd mallar för e-postleverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-delivery-templates/about-templates.html){target="_blank"}

* [Förstå leveransfel](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html){target="_blank"}
