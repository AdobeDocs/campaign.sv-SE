---
title: Skicka en kopia av dina meddelanden till en BCC-adress
description: Lär dig hur du aktiverar e-postkopia i Adobe Campaign
feature: Email
role: User
level: Beginner
source-git-commit: 87c971ac6cf4abb6b04d52ce60ac2036055e1e02
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 1%

---


# Skicka en kopia av dina meddelanden till en BCC-adress {#bcc}

<!--
>[!NOTE]
>
>This capability is available starting Campaign v8.3. To check your version, refer to [this section](../start/compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)-->

## Om BCC för e-post {#gs-bcc}

Du kan konfigurera Adobe Campaign att behålla en kopia av e-postmeddelanden som skickas från din plattform. Med det här alternativet kan du skicka meddelanden med en dedikerad BCC-e-postadress (Blind Carbon Copy), varifrån de kan bearbetas och arkiveras i ett externt system.
Adobe Campaign hanterar inte själva arkiverade filer. De e-postfiler som motsvarar skickade e-postmeddelanden kan sedan överföras till en fjärrserver, till exempel en SMTP-e-postserver.

Arkiveringsmålet är valfri e-postadress som är osynlig för leveransmottagarna. När du har definierat e-postadressen för hemlig kopia måste du aktivera det dedikerade alternativet på [leveransmall](create-templates.md) nivå.

![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Service [kontakta Adobe](../start/campaign-faq.md#support){target="_blank"} för att kommunicera e-postadressen för den kontroll av webbläsarkompatibilitet som ska användas för arkivering.

>[!CAUTION]
>
>Av sekretesskäl måste e-post från innehållsförteckningen behandlas av ett arkiveringssystem som kan lagra säkert personligt identifierbar information (PII).


## Aktivera BCC för e-post {#enable-bcc}

Så här aktiverar du BCC för en specifik [leveransmall](create-templates.md)följer du stegen nedan:

1. Gå till mappen med leveransmallar i Campaign Explorer. Som standard lagras leveransmallar i **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** mapp.
1. Redigera leveransmallen för att uppdatera med BCC.
1. Klicka på knappen **[!UICONTROL Properties]**.
1. Från **[!UICONTROL Delivery]** -fliken, kontrollera **[!UICONTROL Email BCC]** alternativ.

   ![](assets/email-bcc.png)

1. Klicka på **[!UICONTROL Ok]** för att bekräfta.

En kopia av alla skickade meddelanden för varje leverans som baseras på den här mallen skickas till e-postadressen som har konfigurerats för din plattform.

## Skyddsutkast och rekommendationer {#recommendations-bcc}

När du använder BCC för e-post med Adobe Campaign gäller följande skyddsförslag och rekommendationer:

* Du kan bara använda en e-postadress för hemlig kopia.

* Se till att BCC-adressen har tillräcklig mottagningskapacitet för att arkivera alla e-postmeddelanden som skickas.

* BCC för e-post <!--with Enhanced MTA--> skickar till e-postadressen till BCC innan den skickas till mottagarna, vilket kan leda till att BCC-meddelanden skickas trots att de ursprungliga leveranserna kan ha studsat. Mer information om studsar finns i [Förstå leveransfel](delivery-failures.md).

* E-postmeddelanden som skickas till BCC-adressen får inte öppnas och klickas igenom, eftersom dessa aktiviteter beaktas i **[!UICONTROL Total opens]** och **[!UICONTROL Clicks]** från sändningsanalysen kan orsaka felberäkningar.

<!--Only successfully sent emails are taken in account, bounces are not.-->
