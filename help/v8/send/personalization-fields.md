---
title: Lägg till anpassningsfält
description: Lär dig hur du infogar personaliseringsdata i ditt meddelandeinnehåll
feature: Personalization
role: User
level: Beginner
exl-id: 14a741dd-794e-4760-bfa3-bafbe993a3f7
source-git-commit: c248dd899ea704e43873652545c6b945c2915b57
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Lägg till anpassningsfält{#personalization-fields}

Använd personaliseringsfält för att leverera personaliserat innehåll individuellt, baserat på de regler ni anger för varje mottagare.

Ett anpassningsfält är en enskild datafältreferens som används vid anpassning av en leverans för en viss mottagare. Det faktiska datavärdet infogas under leveransanalysfasen.

![meddelandepersonaliseringsexempel](assets/perso-name-sample.png)

## Syntax

En personaliseringstagg använder alltid följande syntax: `<%=table.field%>`.

Om du till exempel vill infoga namnet på mottagaren, som lagras i mottagartabellen, använder anpassningsfältet syntaxen `<%= recipient.lastName %>`.

>[!CAUTION]
>
>Innehållet i anpassningsfält får inte vara längre än 1 024 tecken.

## Infoga ett anpassningsfält {#insert-a-personalization-field}

Om du vill infoga anpassningsfält klickar du på den nedrullningsbara ikonen som är tillgänglig från ett sidhuvud-, ämne- eller meddelandefält.

![infoga ett anpassningsfält](assets/perso-field-insert.png)

Anpassningsfälten infogas och kan tolkas av Adobe Campaign: under meddelandeförberedelsen ersätts fälten med deras värde för en viss mottagare.

![anpassningsfält i ett e-postmeddelande](assets/perso-fields-in-msg.png)

Ersättningen kan sedan testas på fliken **[!UICONTROL Preview]**.

<!--Learn more about message preview in [this page]().-->

## Användningsfall: personalisera e-postämne {#personalization-fields-uc}

Läs om hur du anpassar ett e-postämne och en brödtext med mottagardata i exemplet nedan:

1. Skapa en ny leverans eller öppna en befintlig e-postleverans.
1. Bläddra till länken **[!UICONTROL Subject]** om du vill redigera meddelandets ämne.
1. Ange **specialerbjudande för** och använd knappen i verktygsfältet för att infoga ett anpassningsfält. Välj **[!UICONTROL Recipients>Title]**.
1. Upprepa åtgärden för att infoga namnet på mottagaren. Infoga mellanslag mellan alla anpassningsfält.
1. Klicka på **[!UICONTROL OK]** för att validera.
1. Infoga personaliseringen i meddelandetexten. Det gör du genom att klicka i meddelandeinnehållet och klicka på fältinfogningsknappen.
1. Välj **[!UICONTROL Recipient>Other...]**.
1. Markera fältet med den information som ska visas och klicka på **[!UICONTROL OK]**.
1. Klicka på fliken **[!UICONTROL Preview]** för att visa personaliseringsresultatet. Du måste välja en mottagare för att kunna visa mottagarens meddelande.



## Självstudievideo {#personalization-field-video}

Lär dig hur du lägger till ett anpassningsfält på ämnesraden och innehållet i en e-postleverans i följande video.

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)
