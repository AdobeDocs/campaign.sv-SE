---
title: Skicka en kopia av dina meddelanden till en BCC-adress
description: Lär dig hur du aktiverar e-postkopia i Adobe Campaign
feature: Email
role: User
level: Beginner
exl-id: 35702b81-1984-4a62-8f00-c2bc32ab2b42
source-git-commit: 286af4739c33b79c74b3cb7fa90ad167670a4b4c
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

>[!CAUTION]
>
>Av sekretesskäl måste e-post från innehållsförteckningen behandlas av ett arkiveringssystem som kan lagra säkert personligt identifierbar information (PII).

Adobe Campaign hanterar inte själva arkiverade filer. De e-postfiler som motsvarar skickade e-postmeddelanden kan sedan överföras till en fjärrserver, till exempel en SMTP-e-postserver.

Arkiveringsmålet är valfri e-postadress som är osynlig för leveransmottagarna. När BCC-e-postadressen har definierats måste du aktivera det dedikerade alternativet på [leveransmallsnivå](create-templates.md).

>[!NOTE]
>
>Som användare av hanterade molntjänster [kontaktar du Adobe](../start/campaign-faq.md#support){target="_blank"} för att kommunicera e-postadressen för den grundläggande kopian som ska användas för arkivering.

## Aktivera BCC för e-post {#enable-bcc}

Om du vill aktivera Kontroll av webbläsarkompatibilitet för en viss [leveransmall](create-templates.md) följer du stegen nedan:

1. Gå till mappen med leveransmallar i Campaign Explorer. Som standard lagras leveransmallar i mappen **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Redigera leveransmallen för att uppdatera med BCC.
1. Klicka på knappen **[!UICONTROL Properties]**.
1. Markera alternativet **[!UICONTROL Email BCC with enhanced Momentum]** på fliken **[!UICONTROL Delivery]**.

   ![](assets/email-bcc.png)

1. Klicka på **[!UICONTROL Ok]** för att bekräfta.

En kopia av alla skickade meddelanden för varje leverans som baseras på den här mallen skickas till e-postadressen som har konfigurerats för din plattform.

## Skyddsutkast och rekommendationer {#recommendations-bcc}

När du använder BCC för e-post med Adobe Campaign gäller följande skyddsförslag och rekommendationer:

* Du kan bara använda en e-postadress för hemlig kopia.

* Se till att BCC-adressen har tillräcklig mottagningskapacitet för att arkivera alla e-postmeddelanden som skickas.

* E-post-BCC <!--with Enhanced MTA--> levererar till e-postadressen för BCC innan den skickas till mottagarna, vilket kan leda till att BCC-meddelanden skickas trots att de ursprungliga leveranserna kan ha studsat. Mer information om studsar finns i [Förstå leveransfel](delivery-failures.md).

* E-postmeddelanden som skickas till BCC-adressen får inte öppnas och klickas igenom, eftersom dessa aktiviteter beaktas i **[!UICONTROL Total opens]** och **[!UICONTROL Clicks]** från sändningsanalysen, kan orsaka felberäkningar.

<!--Only successfully sent emails are taken in account, bounces are not.-->
