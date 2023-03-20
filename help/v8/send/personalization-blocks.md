---
title: Använd personaliseringsblock
description: Lär dig hur du använder inbyggda personaliseringsblock i ditt meddelandeinnehåll
feature: Personalization
role: User
level: Beginner
source-git-commit: badcbb83c4bd0cf509c156557f5ea6f7cf7ae771
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---


# Använd personaliseringsblock{#personalization-blocks}

Personaliseringsblock är dynamiskt innehåll som innehåller en specifik återgivning som du kan infoga i dina leveranser. Du kan till exempel lägga till en logotyp, ett gratulationsmeddelande eller en länk till en spegelsida.

Om du vill komma åt anpassade innehållsblock går du till **[!UICONTROL Resources > Campaign Management > Personalization blocks]** Utforskarens nod. Inbyggda personaliseringsblock listas i [det här avsnittet](#ootb-personalization-blocks).

Ni kan också definiera nya block för att optimera er leveranspersonalisering. [Läs mer](#create-custom-personalization-blocks).

## Infoga personaliseringsblock {#insert-personalization-blocks}

Följ stegen nedan om du vill infoga ett anpassningsblock i ett meddelande:

1. Klicka på personaliseringsikonen i innehållsredigeraren i leveransguiden och välj **[!UICONTROL Include]** -menyn.
1. Välj ett anpassningsblock i listan eller klicka på **[!UICONTROL Other...]** -menyn för att komma åt den fullständiga listan.

   ![](assets/perso-content-block.png)

1. Personaliseringsblocket infogas sedan som ett skript. Den anpassas automatiskt till mottagarprofilen när personalisering genereras.
1. Bläddra till **[!UICONTROL Preview]** och välj en mottagare för att visa innehållet i det här blocket för en viss mottagare.

Du kan inkludera källkoden för ett personaliseringsblock i leveransinnehållet. Välj **[!UICONTROL Include the HTML source code of the block]** när du markerar den.

## Inbyggda personaliseringsblock {#ootb-personalization-blocks}

Inbyggda personaliseringsblock är:

* **[!UICONTROL Enabled by Adobe Campaign]**: infogar logotypen&quot;Enabled by Adobe Campaign&quot;.
* **[!UICONTROL Formatting function for proper nouns]**: genererar **[!UICONTROL toSmartCase]** Javascript-funktionen, som ändrar den första bokstaven i varje ord till versaler.
* **[!UICONTROL Greetings]**: infogar hälsningar med mottagarens fullständiga namn följt av ett kommatecken. Exempel: &quot;Hej John Doe.&quot;
* **[!UICONTROL Insert logo]**: infogar en logotyp som är definierad i instansinställningarna.
* **[!UICONTROL Link to mirror page]**: infogar en länk till [spegelsida](mirror-page.md). Standardformatet är: &quot;Om du inte kan visa det här meddelandet korrekt klickar du här&quot;.
* **[!UICONTROL Mirror page URL]**: infogar spegelsidans URL, vilket gör att leveransdesigners kan kontrollera länken.
* **[!UICONTROL Offer acceptance URL in unitary mode]**: infogar en URL som gör att ett erbjudande kan anges till **[!UICONTROL Accepted]**. (Det här blocket är tillgängligt om interaktionsmodulen är aktiverad)
* **[!UICONTROL Registration confirmation]**: infogar en länk som bekräftar prenumerationen.
* **[!UICONTROL Registration link]**: infogar en prenumerationslänk. Den här länken definieras i instansinställningarna. Standardinnehållet är: &quot;Registrera dig genom att klicka här.&quot;
* **[!UICONTROL Registration link (with referrer)]**: infogar en prenumerationslänk som gör det möjligt att identifiera besökaren och leveransen. Den här länken definieras i instansinställningarna.
* **[!UICONTROL Registration page URL]**: infogar en prenumerations-URL
* **[!UICONTROL Style of content emails]** och **[!UICONTROL Notification style]**: generera kod som formaterar ett e-postmeddelande med fördefinierade HTML-format.
* **[!UICONTROL Unsubscription link]**: infogar en länk som gör det möjligt att avbryta prenumerationen på alla leveranser (blockeringslista). Standardinnehållet är: &quot;Du får det här meddelandet eftersom du har haft kontakt med ***ditt organisationsnamn*** eller ett närstående bolag. Ta inte längre emot meddelanden från ***ditt organisationsnamn*** klicka här.&quot;

## Skapa anpassade personaliseringsblock {#create-custom-personalization-blocks}

Du kan definiera nya personliga innehållsblock som ska infogas från personaliseringsikonen.

Följ stegen nedan för att skapa ett personaliseringsblock:

1. Bläddra till **[!UICONTROL Resources > Campaign Management > Personalization blocks]** mapp för Campaign Explorer.
1. Ovanför listan med inbyggda block klickar du på **[!UICONTROL New]**.

   ![](assets/perso-new-block.png)

1. Fyll i inställningarna för anpassningsblocket:

   ![](assets/perso-custom-block.png)

   * Ange blockets etikett. Den här etiketten visas i insättningsfönstret för anpassningsfältet.
   * Välj en **Leverans** innehållstyp.
   * Aktivera **[!UICONTROL Visible in the customization menus]** om du vill göra det här blocket tillgängligt från ikonen för infogning av anpassningsfält.
   * Aktivera **[!UICONTROL The content of the personalization block depends upon the format]** om du vill definiera två olika block för e-post med HTML och text.
   * Ange innehåll (i HTML, text, JavaScript osv.) i personaliseringsblocket och klicka **[!UICONTROL Save]**.

När du har sparat det nya personaliseringsblocket är det tillgängligt i leveransredigeraren.

## Videokurs {#personalization-blocks-video}

Lär dig hur du skapar dynamiska innehållsblock och hur du använder dem för att anpassa innehållet i din e-postleverans i följande video.

>[!VIDEO](https://video.tv.adobe.com/v/342088?quality=12)


