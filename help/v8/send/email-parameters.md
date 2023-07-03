---
title: E-postparametrar i Adobe Campaign
description: Läs mer om alternativ och inställningar som är specifika för e-postleverans i Adobe Campaign.
feature: Email
role: User
level: Beginner, Intermediate, Experienced
source-git-commit: 44f30f753e3ed75b7e56caf7bd8cdfa7cbee5c35
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 8%

---

# E-postparametrar {#email-parameters}

I det här avsnittet visas de alternativ och parametrar som är tillgängliga från leveransegenskaperna som är specifika för e-postleverans.

## Använd e-postkopia {#email-bcc}

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
>**[!UICONTROL Email BCC]** är inte aktiverat som standard. Du måste aktivera det manuellt i mallen för e-postleverans eller leverans.

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

* BCC för e-post <!--with Enhanced MTA--> skickar till e-postadressen till BCC innan den skickas till mottagarna, vilket kan leda till att BCC-meddelanden skickas trots att de ursprungliga leveranserna kan ha studsat. Mer information om studsar finns i [Förstå leveransfel](delivery-failures.md).

* Om e-postmeddelanden som skickas till BCC-adressen öppnas och klickas igenom, kommer detta att beaktas i **[!UICONTROL Total opens]** och **[!UICONTROL Clicks]** från sändningsanalysen, vilket kan orsaka några felberäkningar.

<!--Only successfully sent emails are taken in account, bounces are not.-->

## Välj meddelandeformat {#selecting-message-formats}

Du kan ändra formatet för skickade e-postmeddelanden. Det gör du genom att redigera leveransegenskaperna och klicka på **[!UICONTROL Delivery]** -fliken.

![](assets/email-message-format.png)

Välj formatet för e-postmeddelandet i fönstrets nedre del:

* **[!UICONTROL Use recipient preferences]** (standardläge)

  Meddelandeformatet definieras enligt de data som lagras i mottagarprofilen och lagras som standard i **[!UICONTROL email format]** fält (@emailFormat). Om en mottagare vill ta emot meddelanden i ett visst format är detta det format som skickas. Om fältet inte är ifyllt skickas ett multipart-alternativt meddelande (se nedan).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

  Meddelandet innehåller båda formaten: text och HTML. Formatet som visas vid mottagning beror på konfigurationen av mottagarens e-postprogramvara (multipart-option).

  >[!IMPORTANT]
  >
  >Det här alternativet inkluderar båda versionerna av dokumentet. Det minskar därför leveransflödet eftersom meddelandestorleken är större.

* **[!UICONTROL Send all messages in text format]**

  Meddelandet skickas i textformat. Formatet HTML skickas inte, utan används endast för spegelsidan när mottagaren klickar på meddelandet.

<!--
>[!NOTE]
>
>For more on defining the email content, see [this section]().-->

## Ange teckenkodning {#character-encoding}

I **[!UICONTROL SMTP]** -fliken för leveransparametrarna, **[!UICONTROL Character encoding]** kan du ange en viss kodning.

Standardkodningen är UTF-8. Om vissa av mottagarnas e-postleverantörer inte har stöd för UTF-8-standardkodning kanske du vill ställa in en specifik kodning så att specialtecknen visas korrekt för mottagarna av e-postmeddelanden.

Du vill till exempel skicka ett e-postmeddelande som innehåller japanska tecken. Om du vill vara säker på att alla tecken visas korrekt för mottagarna i Japan kan du använda en kodning som stöder de japanska tecknen i stället för standard UTF-8.

Om du vill göra det väljer du **[!UICONTROL Force the encoding used for messages]** i **[!UICONTROL Character encoding]** och välj en kodning i listrutan som visas.

![](assets/email-smtp-encoding.png)

## Hantera studsmeddelanden {#managing-bounce-emails}

The **[!UICONTROL SMTP]** -fliken i leveransegenskaperna kan du även konfigurera hanteringen av studsmeddelanden.

* **[!UICONTROL Errors-to-address]**: Som standard tas studsade e-postmeddelanden emot i standardfelrutan för plattformen, men du kan definiera en specifik feladress för en leverans.

* **[!UICONTROL Bounce address]**: Du kan också definiera en annan adress dit obearbetade studsade e-postmeddelanden vidarebefordras. Med den här adressen kan du undersöka orsaken till att studsa när e-postmeddelanden inte automatiskt kunde kvalificeras av programmet.

Vart och ett av dessa fält kan anpassas med den dedikerade ikonen. Läs mer om personaliseringsfält i [det här avsnittet](personalization-fields.md).

![](assets/email-smtp-bounce.png)

Mer information om hantering av studsade e-postmeddelanden finns i [det här avsnittet](delivery-failures.md#bounce-mail-management).

## Lägg till SMTP-rubriker {#adding-smtp-headers}

Det går att lägga till SMTP-huvuden i leveranserna. Använd relevanta avsnitt i **[!UICONTROL SMTP]** -fliken i leveransen.

Skriptet som anges i det här fönstret måste referera till en rubrik per rad i följande formulär: **name:value**.

Värden kodas automatiskt om det behövs.

>[!IMPORTANT]
>
>Tillägg av ett skript för att infoga ytterligare SMTP-rubriker är reserverat för avancerade användare.
>
>Syntaxen för det här skriptet måste uppfylla kraven för den här innehållstypen: Inget oanvänt utrymme, ingen tom rad, o.s.v.

![](assets/email-smtp-headers.png)

<!--
## Generate mirror page {#generating-mirror-page}

The mirror page is an HTML page accessible online via a web browser. Its content is identical to the email. It can be useful if your recipients are experiencing rendering issues or broken images when trying to view your email in their inbox.

Learn how to insert a link to the mirror page in [this section](mirror-page.md).-->