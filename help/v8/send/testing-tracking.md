---
title: Testa meddelandespårning
description: Lär dig hur du testar meddelandespårning innan du skickar leveranser
feature: Monitoring
role: User
level: Beginner
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: edbe7ab49a628436dfb4d27ae17122917d7371e9
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Testa meddelandespårning {#testing-tracking}

Innan du skickar materialet till hela målgruppen är det viktigt att du testar spårningsfunktionen för att se till att alla länkar fungerar korrekt och att spårningsdata samlas in korrekt. Denna verifieringsprocess hjälper er att identifiera och åtgärda eventuella spårningsproblem innan kampanjen publiceras, vilket förhindrar potentiella problem med länkomdirigering, spårning av pixelinläsning eller datainsamling.

Med testspårning kan du:

* Kontrollera att alla länkar i meddelandet är korrekt spårade och omdirigerade
* Bekräfta att spegelsidans länk fungerar och spåras
* Se till att pixelspårning läses in korrekt för öppen spårning
* Kontrollera att personaliserade parametrar i URL:er fångas in korrekt
* Verifiera att det tekniska arbetsflödet för spårning behandlar data korrekt

Du kan testa spårning på spegelsidor, e-postloggar och länkar genom att följa stegen nedan:

## Steg 1: Skapa en testleverans {#create-test-delivery}

1. Skapa en ny e-postleverans som ska användas för testning. [Lär dig skapa en leverans](../start/create-message.md)
1. Designa ditt e-postinnehåll med länkar som du vill spåra. [Lär dig mer om design av e-postinnehåll](defining-the-email-content.md)
1. Lägg till ett anpassat sidblock i e-postinnehållet. [Läs om personaliseringsblock](personalization-blocks.md)

   ![](assets/mirror-page-insert.png)

1. Ange den användare som ska ta emot e-postmeddelandet. Eftersom den här användaren måste öppna e-postmeddelandet och klicka på de länkar det innehåller måste du markera en testmottagaradress som du kontrollerar. [Läs om testprofiler](../audiences/test-profiles.md)

## Steg 2: Skicka testleveransen {#send-test}

1. Kontrollera att spårning är aktiverat i leveransinställningarna:
   * Öppna **[!UICONTROL Properties]** av leveransen
   * Gå till avsnittet **[!UICONTROL Tracking & Images]**
   * Kontrollera att **[!UICONTROL Activate tracking]** är markerad
   * Kontrollera att **[!UICONTROL Opens tracking]** är markerad om du vill spåra öppningar

   ![](assets/s_ncs_user_email_del_tracking_param.png)

[Läs mer om alternativ för URL-spårning](url-tracking.md)

1. Skicka leveransen till testmottagaren. [Läs om hur du skickar leveranser](configure-and-send.md)

## Steg 3: Verifiera spårningsfunktioner {#verify-tracking}

1. När du har fått e-postmeddelandet öppnar du det och klickar på länken för spegelsidan. [Lär dig mer om spegelsidor](mirror-page.md)
1. Klicka på olika länkar i e-postmeddelandet för att generera spårningsdata.
1. När du har omdirigerats korrekt till speglingssidan kan du komma åt mappen **[!UICONTROL Administration > Production > Technical workflows]**. [Läs mer om arbetsflöden](../config/workflows.md)
1. Öppna arbetsflödet **[!UICONTROL Tracking]**.
1. Starta arbetsflödet eller högerklicka på aktiviteten **[!UICONTROL Scheduler]** och välj **[!UICONTROL Execute pending task now]**.
1. Vänta i cirka 30 sekunder på att arbetsflödet bearbetar spårningsloggarna.
1. Välj fliken **[!UICONTROL Audit]** i arbetsflödet. Se till att minst en loggpost för spårning hittas. Klicka på **[!UICONTROL Refresh]** om du inte ser några nya loggar.

1. Verifiera spårningsloggar i leveransen:
   * Gå tillbaka till leveransen
   * Välj fliken **[!UICONTROL Tracking]**
   * Kontrollera att listan med spårningsloggar visas med URL:er som klickats och andra spårningshändelser

   ![](assets/s_ncs_user_delivery_tracking_tab.png)

## Steg 4: Kontrollera fliken för mottagarspårning {#check-recipient-tracking}

1. Gå till profilsidan för mottagaren som du använde för testet. [Läs om hur du visar profiler](../audiences/view-profiles.md)
   * Mottagarens profilsida finns som standard i mappen **[!UICONTROL Profiles and Targets > Recipients]**.

1. Klicka på fliken **[!UICONTROL Tracking]**.  [Läs mer om spårningsloggar](tracking-logs.md)

   ![](assets/s_ncs_user_select_tracking_tab_from_recipient.png)

1. Kontrollera att spårningsposter visas med:
   * Värdet **[!UICONTROL Mirror Page]** i kolumnen **[!UICONTROL Type]**
   * **[!UICONTROL Open]** värden i kolumnen **[!UICONTROL Type]** för e-post öppnas
   * **[!UICONTROL Email click]** värden i kolumnen **[!UICONTROL Type]** för länkklick

## Test av felsökningsspårning {#troubleshooting-tracking-test}

Om spårningsloggarna inte visas:

1. **Kontrollera leveransinställningarna**: Gå till leveransen och öppna dess **[!UICONTROL Properties]** för att kontrollera att både **[!UICONTROL Activate tracking]**- och **[!UICONTROL Opens tracking]**-alternativen är markerade. [Läs mer om alternativ för URL-spårning](url-tracking.md)

1. **Verifiera spårningsarbetsflödet**: Kontrollera att det tekniska arbetsflödet i **[!UICONTROL Tracking]** körs utan fel. [Läs mer om felsökning av arbetsflöden för spårning](tracking-logs.md#check-tracking-workflow)

1. **Kontrollera URL-format**: Verifiera att URL-adresserna är korrekt formaterade och omslutna av avgränsare. [Läs mer om hur du konfigurerar spårade länkar](tracked-links.md)

1. **Granska e-postklientens beteende**: Vissa e-postklienter kan blockera spårningspixlar eller ändra länkar. Testa med olika e-postklienter. [Lär dig mer om god leveranspraxis](../start/delivery-best-practices.md)

1. **Vänta på bearbetning**: Spårningsarbetsflödet körs timt som standard. Om du utlöser den manuellt bör du ge tillräckligt med tid för bearbetning innan du kontrollerar resultatet. [Läs mer om spårningsloggar](tracking-logs.md)

## Relaterade ämnen {#related-topics}

* [Lär dig konfigurera spårade länkar](tracked-links.md)
* [Lär dig hur du får åtkomst till spårningsloggar](tracking-logs.md)
* [Läs spårningsrapporter](../reporting/delivery-reports.md#tracking-indicators)

