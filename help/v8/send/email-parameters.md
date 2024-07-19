---
title: E-postparametrar i Adobe Campaign
description: Läs mer om alternativ och inställningar som är specifika för e-postleverans i Adobe Campaign.
feature: Email
role: User
level: Beginner
exl-id: ad75f01e-2c6c-4607-b15a-8870d399002a
source-git-commit: 87c971ac6cf4abb6b04d52ce60ac2036055e1e02
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 7%

---

# E-postparametrar {#email-parameters}

I det här avsnittet visas de alternativ och parametrar som är tillgängliga från leveransegenskaperna som är specifika för e-postleverans.

## Använd e-postkopia {#email-bcc}

Du kan konfigurera Adobe Campaign att behålla en kopia av e-postmeddelanden som skickas från din plattform. Det här alternativet beskrivs på [den här sidan](email-bcc.md).

## Välj meddelandeformat {#selecting-message-formats}

Du kan ändra formatet för skickade e-postmeddelanden. Om du vill göra det redigerar du leveransegenskaperna och klickar på fliken **[!UICONTROL Delivery]**.

![](assets/email-message-format.png)

Välj formatet för e-postmeddelandet i fönstrets nedre del:

* **[!UICONTROL Use recipient preferences]** (standardläge)

  Meddelandeformatet definieras enligt data som lagras i mottagarprofilen och lagras som standard i fältet **[!UICONTROL email format]** (@emailFormat). Om en mottagare vill ta emot meddelanden i ett visst format är detta det format som skickas. Om fältet inte är ifyllt skickas ett multipart-alternativt meddelande (se nedan).

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

På fliken **[!UICONTROL SMTP]** i leveransparametrarna kan du ange en specifik kodning i avsnittet **[!UICONTROL Character encoding]**.

Standardkodningen är UTF-8. Om vissa av mottagarnas e-postleverantörer inte har stöd för UTF-8-standardkodning kanske du vill ställa in en specifik kodning så att specialtecknen visas korrekt för mottagarna av e-postmeddelanden.

Du vill till exempel skicka ett e-postmeddelande som innehåller japanska tecken. Om du vill vara säker på att alla tecken visas korrekt för mottagarna i Japan kan du använda en kodning som stöder de japanska tecknen i stället för standard UTF-8.

Det gör du genom att välja alternativet **[!UICONTROL Force the encoding used for messages]** i avsnittet **[!UICONTROL Character encoding]** och välja en kodning i listrutan som visas.

![](assets/email-smtp-encoding.png)

## Hantera studsmeddelanden {#managing-bounce-emails}

På fliken **[!UICONTROL SMTP]** i leveransegenskaperna kan du även konfigurera hanteringen av studsmeddelanden.

* **[!UICONTROL Errors-to-address]**: Som standard tas studsade e-postmeddelanden emot i standardfelrutan för plattformen, men du kan definiera en specifik feladress för en leverans.

* **[!UICONTROL Bounce address]**: Du kan också definiera en annan adress dit obearbetade studsade e-postmeddelanden vidarebefordras. Med den här adressen kan du undersöka orsaken till att studsa när e-postmeddelanden inte automatiskt kunde kvalificeras av programmet.

Vart och ett av dessa fält kan anpassas med den dedikerade ikonen. Läs mer om anpassningsfält i [det här avsnittet](personalization-fields.md).

![](assets/email-smtp-bounce.png)

Mer information om hantering av studsade e-postmeddelanden finns i [det här avsnittet](delivery-failures.md#bounce-mail-management).

## Lägg till SMTP-rubriker {#adding-smtp-headers}

Det går att lägga till SMTP-huvuden i leveranserna. Det gör du genom att använda relevant avsnitt på fliken **[!UICONTROL SMTP]** i leveransen.

Skriptet som anges i det här fönstret måste referera till en rubrik per rad i följande format: **name:value**.

Värden kodas automatiskt om det behövs.

>[!IMPORTANT]
>
>Att lägga till ett skript för att infoga ytterligare SMTP-rubriker är reserverat för avancerade användare.
>
>Syntaxen för det här skriptet måste uppfylla kraven för den här innehållstypen: Inget oanvänt utrymme, ingen tom rad, o.s.v.

![](assets/email-smtp-headers.png)


## Generera spegelsida {#generating-mirror-page}

Spegelsidan är en HTML-sida som är tillgänglig online via en webbläsare. Innehållet är identiskt med e-postmeddelandet. Det kan vara användbart om dina mottagare får problem med återgivningen eller om det uppstår problem med brutna bilder när de försöker visa e-postmeddelandet i sin inkorg.

Lär dig hur du infogar en länk till spegelsidan i [det här avsnittet](mirror-page.md)
