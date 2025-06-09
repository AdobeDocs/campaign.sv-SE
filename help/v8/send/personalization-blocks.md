---
title: Använd personaliseringsblock
description: Lär dig använda inbyggda personaliseringsblock i ditt meddelandeinnehåll
feature: Personalization
role: User
level: Beginner
exl-id: 214ad693-d456-47ec-a9c8-199ba23c3d9c
source-git-commit: c248dd899ea704e43873652545c6b945c2915b57
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Använd personaliseringsblock{#personalization-blocks}

Personaliseringsblock är dynamiskt innehåll som innehåller en specifik återgivning som du kan infoga i dina leveranser. Du kan till exempel lägga till en logotyp, ett gratulationsmeddelande eller en länk till en spegelsida.

Bläddra till noden **[!UICONTROL Resources > Campaign Management > Personalization blocks]** i Utforskaren för att få åtkomst till anpassade innehållsblock. Inbyggda personaliseringsblock visas i [det här avsnittet](#ootb-personalization-blocks).

Ni kan också definiera nya block för att optimera er leveranspersonalisering. [Läs mer](#create-custom-personalization-blocks).

## Infoga personaliseringsblock {#insert-personalization-blocks}

Följ stegen nedan om du vill infoga ett personaliseringsblock i ett meddelande:

1. Klicka på ikonen för anpassning i innehållsredigeraren i leveransguiden och välj menyn **[!UICONTROL Include]**.
1. Välj ett anpassningsblock i listan eller klicka på menyn **[!UICONTROL Other...]** för att få tillgång till den fullständiga listan.

   ![](assets/perso-content-block.png)

1. Personaliseringsblocket infogas sedan som ett skript. Den anpassas automatiskt till mottagarprofilen när personalisering genereras.
1. Bläddra till fliken **[!UICONTROL Preview]** och välj en mottagare för att visa innehållet i det här blocket för en viss mottagare.

Du kan inkludera källkoden för ett personaliseringsblock i leveransinnehållet. Om du vill göra det väljer du **[!UICONTROL Include the HTML source code of the block]** när du markerar den.

## Inbyggda personaliseringsblock {#ootb-personalization-blocks}

Inbyggda personaliseringsblock är:

* **[!UICONTROL Enabled by Adobe Campaign]**: infogar logotypen&quot;Enabled by Adobe Campaign&quot;.
* **[!UICONTROL Formatting function for proper nouns]**: genererar JavaScript-funktionen **[!UICONTROL toSmartCase]** som ändrar den första bokstaven i varje ord till versaler.
* **[!UICONTROL Greetings]**: infogar hälsningar med mottagarens fullständiga namn följt av ett komma. Exempel:&quot;Hello John Doe,&quot;.
* **[!UICONTROL Insert logo]**: infogar en logotyp som är definierad i instansinställningarna.
* **[!UICONTROL Link to mirror page]**: infogar en länk till [spegelsidan](mirror-page.md). Standardformatet är:&quot;Om du inte kan visa det här meddelandet korrekt klickar du här&quot;.
* **[!UICONTROL Mirror page URL]**: infogar spegelsidans URL, vilket gör att leveransdesigners kan kontrollera länken.
* **[!UICONTROL Offer acceptance URL in unitary mode]**: infogar en URL som gör att ett erbjudande kan anges till **[!UICONTROL Accepted]**. (Det här blocket är tillgängligt om interaktionsmodulen är aktiverad)
* **[!UICONTROL Registration confirmation]**: infogar en länk som bekräftar prenumerationen.
* **[!UICONTROL Registration link]**: infogar en prenumerationslänk. Den här länken definieras i instansinställningarna. Standardinnehållet är:&quot;Klicka här om du vill registrera dig.&quot;
* **[!UICONTROL Registration link (with referrer)]**: infogar en prenumerationslänk som gör det möjligt att identifiera besökaren och leveransen. Den här länken definieras i instansinställningarna.
* **[!UICONTROL Registration page URL]**: infogar en prenumerations-URL
* **[!UICONTROL Style of content emails]** och **[!UICONTROL Notification style]**: generera kod som formaterar ett e-postmeddelande med fördefinierade HTML-format.
* **[!UICONTROL Unsubscription link]**: infogar en länk som gör det möjligt att avbryta prenumerationen på alla leveranser (blockeringslista). Standardinnehållet är:&quot;Du får det här meddelandet eftersom du har varit i kontakt med ***ditt organisationsnamn*** eller ett dotterbolag. Klicka här om du inte längre vill få meddelanden från ***din organisation***.&quot;

## Skapa anpassade personaliseringsblock {#create-custom-personalization-blocks}

Du kan definiera nya personliga innehållsblock som ska infogas från personaliseringsikonen.

Följ stegen nedan för att skapa ett personaliseringsblock:

1. Bläddra till mappen **[!UICONTROL Resources > Campaign Management > Personalization blocks]** i Campaign Explorer.
1. Klicka på **[!UICONTROL New]** ovanför listan med inbyggda block.

   ![](assets/perso-new-block.png)

1. Fyll i inställningarna för anpassningsblocket:

   ![](assets/perso-custom-block.png)

   * Ange blockets etikett. Den här etiketten visas i fönstret för infogning av anpassningsfält.
   * Välj innehållstypen **Leverans**.
   * Aktivera alternativet **[!UICONTROL Visible in the customization menus]** för att göra det här blocket tillgängligt från ikonen för infogning av anpassningsfält.
   * Om det behövs kan du aktivera alternativet **[!UICONTROL The content of the personalization block depends upon the format]** för att definiera två olika block för HTML- och textmeddelanden.
   * Ange innehållet (i HTML, text, JavaScript osv.) i personaliseringsblocket och klicka på **[!UICONTROL Save]**.

När du har sparat det nya personaliseringsblocket är det tillgängligt i leveransredigeraren.

## Självstudievideo {#personalization-blocks-video}

Lär dig hur du skapar dynamiska innehållsblock och hur du använder dem för att anpassa innehållet i din e-postleverans i följande video.

>[!VIDEO](https://video.tv.adobe.com/v/3449010?quality=12&captions=swe)
