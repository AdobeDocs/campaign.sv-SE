---
title: Skicka e-post med Adobe Campaign
description: Kom igång med e-post i Campaign
feature: Email
role: Data Engineer
level: Beginner
exl-id: 97dcd0e0-db5b-45a4-96af-817e49f6cb64
source-git-commit: 0a55d947a7646aab64ab2f9d0d09a6f930db576e
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# Designa och skicka e-post

Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen.

![](../assets/do-not-localize/book.png) Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/about-email-channel.html){target=&quot;_blank&quot;}

## Skapa din första e-postleverans

Skapa personaliserade och sammanhangsberoende e-postmeddelanden som överensstämmer med resten av kundupplevelsen.

![](assets/new-email-content.png)


I följande exempel får du lära dig hur du utformar en e-postleverans i Adobe Campaign som innehåller personaliserade data, länkar till en extern URL och en länk till spegelsidan.

1. **Skapa leveransen**

   Bläddra till **Kampanjer** flik, klicka **Leveranser** och klicka på **Skapa** ovanför listan över befintliga leveranser.

   ![](assets/delivery_step_1.png)

1. **Välj mallen**

   Välj en leveransmall och ge sedan leveransen ett namn. Det här namnet visas endast för användare av Adobe Campaign-konsolen och inte för dina mottagare, men den här rubriken visas i din lista över leveranser. Klicka på **[!UICONTROL Continue]**.

   ![](assets/dce_delivery_model.png)

1. **Importera innehåll**

   Klicka på **Källa** för att klistra in HTML-innehåll.

   ![](assets/paste-content.png)


1. **Anpassa meddelandet**


   * Lägg till förnamn och efternamn för mottagarna

      Om du vill infoga för- och efternamnen på målprofilerna i innehållet i meddelandet placerar du markören där du vill infoga dem och klickar på den sista ikonen i verktygsfältet. Klicka sedan på **[!UICONTROL Include]** och markera **[!UICONTROL Greetings]**.

      ![](assets/include-greetings.png)

      Bläddra till fliken Förhandsgranska om du vill kontrollera personaliseringen genom att välja en mottagare.

      ![](assets/perso-check.png)

   * Infoga en spårad länk

      Om du vill dirigera leveransmottagare till en extern adress via en bild eller text markerar du den och klickar på knappen **[!UICONTROL Add a link]** i verktygsfältet.

      Ange länkens URL i dialogrutan **URL** fält med följande format **https://www.myURL.com**, och bekräfta sedan.

      ![](assets/add-a-link.png)

   * Lägga till en spegelsida

      Om du vill att mottagarna ska kunna se ditt leveransinnehåll i en webbläsare lägger du till en länk på meddelandets spegelsida.

      Placera markören där du vill infoga länken, klicka på den sista ikonen i verktygsfältet och klicka sedan på **[!UICONTROL Include]** och markera **[!UICONTROL link to mirror page]**.
   När innehållet är klart klickar du på **Spara**: den visas nu i din lista över leveranser i **[!UICONTROL Campaigns > Deliveries]** -fliken. Din första e-postleverans är klar. Nu måste ni definiera målgruppen, validera leveransen och skicka den.


Lär dig hur du importerar ett e-postinnehåll i det här [användningsfall](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/load-delivery-content.html).

Läs mer i dessa avsnitt av **Campaign Classic v7-dokumentation**:

* Designa ett e-postmeddelande i Campaign
   ![](../assets/do-not-localize/book.png) [Lär dig hur du utformar ett e-postmeddelande](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/defining-the-email-content.html){target=&quot;_blank&quot;}
* Skapa och använda en e-postmall
   ![](../assets/do-not-localize/book.png) [Läs mer om e-postmallar](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-delivery-templates/about-templates.html){target=&quot;_blank&quot;}
* Välj publik för ditt e-postmeddelande
   ![](../assets/do-not-localize/book.png) [Lär dig definiera målpopulationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-defining-the-target-population.html){target=&quot;_blank&quot;}
* Validera en leverans och skicka korrektur
   ![](../assets/do-not-localize/book.png) [Lär dig viktiga steg för att validera en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html){target=&quot;_blank&quot;}
* Lägg till [dirigeringsadresser](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-seed-addresses/about-seed-addresses.html){target=&quot;_blank&quot;}

## Testa och validera dina e-postmeddelanden

Campaign erbjuder flera sätt att testa och validera dina e-postmeddelanden innan de skickas till era målgrupper.

![](../assets/do-not-localize/book.png) [Tillämpa bästa praxis som anges i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/check-before-sending.html){target=&quot;_blank&quot;}

Du kan:

* Kontrollera leveransanalysloggar
* Skicka korrektur
* Lägg till dirigerade adresser
* Använd kontrollgrupper
* Kontrollera e-poståtergivning

![](../assets/do-not-localize/book.png) [Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html){target=&quot;_blank&quot;}
