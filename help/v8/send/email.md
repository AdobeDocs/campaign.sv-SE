---
product: Adobe Campaign
title: Skicka e-post med Adobe Campaign
description: Kom igång med e-post i Campaign
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: d1e96b1311d9de24ceb918230186cd3cad609ab2
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 1%

---

# Designa och skicka e-post

Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen.

[!DNL :arrow_upper_right:] Läs mer i dokumentationen [ till ](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/about-email-channel.html)Campaign Classic v7.

## Skapa din första e-postleverans

Skapa personaliserade och sammanhangsberoende e-postmeddelanden som överensstämmer med resten av kundupplevelsen.

![](assets/new-email-content.png)

[!DNL :arrow_upper_right:] [Lär dig hur du skapar e-postleveranser i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/editing-html-content/use-case--creating-an-email-delivery.html)


I följande exempel får du lära dig hur du utformar en e-postleverans i Adobe Campaign som innehåller personaliserade data, länkar till en extern URL, en länk till spegelsidan och en länk till ett webbformulär.

1. Skapa leveransen

   Om du vill skapa en ny leverans går du till fliken **Kampanjer**, klickar på **Leveranser** och klickar på knappen **Skapa** ovanför listan över befintliga leveranser.

   ![](assets/delivery_step_1.png)

1. Välj mallen

   Välj en leveransmall och ge sedan leveransen ett namn. Det här namnet visas endast för användare av Adobe Campaign-konsolen och inte för dina mottagare, men den här rubriken visas i din lista över leveranser. Klicka på **[!UICONTROL Continue]**.

   ![](assets/dce_delivery_model.png)

1. Importera innehåll

   Klicka på fliken **Källa** för att klistra in HTML-innehållet.

   ![](assets/paste-content.png)


1. Anpassa meddelandet


   * Visa de första och andra namnen på mottagarna

      Om du vill infoga mottagarnas för- och efternamn i ett textfält i leveransen klickar du på det valda textfältet och placerar sedan markören där du vill att de ska visas. Klicka på den första ikonen i popup-verktygsfältet och klicka sedan på **[!UICONTROL Personalization block]**. Välj **[!UICONTROL Greetings]** och klicka sedan på **[!UICONTROL OK]**.

   * Infoga en länk i en bild

      Om du vill dirigera mottagare till en extern adress via en bild, klickar du på den relevanta bilden för att visa popup-verktygsfältet, placerar markören på den första ikonen och klickar sedan på **[!UICONTROL Link to an external URL]**.

      Ange länkens URL i fältet **URL** med följande format **https://www.myURL.com** och bekräfta sedan.

      Länken kan ändras när som helst med hjälp av avsnittet till höger om fönstret.

   * Infoga en länk i text

      Om du vill integrera en extern länk i texten i leveransen markerar du en del text eller ett textblock och klickar sedan på den första ikonen i popup-verktygsfältet. Klicka på **[!UICONTROL Link to an external URL]** och ange länkadressen i fältet **[!UICONTROL URL]**.

      Länken kan ändras när som helst med hjälp av avsnittet till höger om fönstret.

   * Lägga till en spegelsida

      Om du vill att mottagarna ska kunna se leveransinnehållet i en webbläsare kan du integrera en länk till en spegelsida i leveransen.

      Klicka i det textfält där du vill se länken publicerad. Klicka på den första ikonen i popup-verktygsfältet, välj **[!UICONTROL Personalization block]** och **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Bekräfta genom att klicka på **[!UICONTROL Save]**.

   * Integrera en länk till ett webbprogram

      Med Digital Content Editor kan du integrera länkar till webbprogram från Adobe Campaign-konsolen, till exempel en landningssida eller en formulärsida. Mer information finns i [Länka till ett webbprogram](../../web/using/editing-content.md#link-to-a-web-application).

      Markera ett textfält för länken till ett webbprogram och klicka sedan på den första ikonen. Välj **[!UICONTROL Link to a Web application]** och välj sedan önskat program genom att klicka på ikonen i slutet av fältet **Webbprogram**.

1. Skicka meddelanden

   När innehållet är integrerat sparar du leveransen genom att klicka på **Spara**. Den visas nu i din lista över leveranser på fliken **[!UICONTROL Campaigns > Deliveries]**.


## Skapa innehåll och välj målgrupp

Ni kan skapa direkt i Campaign eller importera er målgrupp samt ert e-postinnehåll. Använd länkarna nedan för att lära dig mer om:

* Designa ett e-postmeddelande i Campaign
   [!DNL :arrow_upper_right:] [Lär dig hur du utformar ett e-postmeddelande](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/defining-the-email-content.html)
* Importera ett e-postinnehåll
   [!DNL :arrow_upper_right:] [Användningsfall: Skapa ett arbetsflöde för att läsa in ett leveransinnehåll](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/loading-delivery-content.html)
* Skapa och använda en e-postmall
   [!DNL :arrow_upper_right:] [Läs mer om e-postmallar](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-delivery-templates/about-templates.html)
* Välj publik för ditt e-postmeddelande
   [!DNL :arrow_upper_right:] [Lär dig definiera målpopulationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-defining-the-target-population.html)
* Validera en leverans och skicka korrektur
   [!DNL :arrow_upper_right:] [Lär dig viktiga steg för att validera en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html)
* Lägg till [dirigerade adresser](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-seed-addresses/about-seed-addresses.html)

## Testa och validera dina e-postmeddelanden

Campaign erbjuder flera sätt att testa och validera dina e-postmeddelanden innan de skickas till era målgrupper.

[!DNL :arrow_upper_right:] [Tillämpa bästa praxis som anges i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/check-before-sending.html)

Du kan:

* Kontrollera leveransanalysloggar
* Skicka korrektur
* Lägg till dirigerade adresser
* Använda kontrollgrupper
* Kontrollera e-poståtergivning

[!DNL :arrow_upper_right:] [Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html)

## Övervaka dina e-postmeddelanden

När du har skickat den kontrollerar du leveransstatus på kontrollpanelen och får åtkomst till leveransloggar och rapporter som bekräftar att meddelanden har skickats korrekt.

[!DNL :arrow_upper_right:] [Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/track-and-monitor.html)

