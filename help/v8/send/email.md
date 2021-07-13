---
product: Adobe Campaign
title: Skicka e-post med Adobe Campaign
description: Kom igång med e-post i Campaign
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: c61d8aa8e0a68ccc81a6141782f860daf061bc61
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 2%

---

# Designa och skicka e-post

Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen.

↗️ Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/about-email-channel.html).

## Skapa din första e-postleverans

Skapa personaliserade och sammanhangsberoende e-postmeddelanden som överensstämmer med resten av kundupplevelsen.

![](assets/new-email-content.png)


I följande exempel får du lära dig hur du utformar en e-postleverans i Adobe Campaign som innehåller personaliserade data, länkar till en extern URL och en länk till spegelsidan.

1. **Skapa leveransen**

   Om du vill skapa en ny leverans går du till fliken **Kampanjer**, klickar på **Leveranser** och klickar på knappen **Skapa** ovanför listan över befintliga leveranser.

   ![](assets/delivery_step_1.png)

1. **Välj mallen**

   Välj en leveransmall och ge sedan leveransen ett namn. Det här namnet visas endast för användare av Adobe Campaign-konsolen och inte för dina mottagare, men den här rubriken visas i din lista över leveranser. Klicka på **[!UICONTROL Continue]**.

   ![](assets/dce_delivery_model.png)

1. **Importera innehåll**

   Klicka på fliken **Källa** för att klistra in HTML-innehållet.

   ![](assets/paste-content.png)


1. **Anpassa meddelandet**


   * Lägg till förnamn och efternamn för mottagarna

      Om du vill infoga för- och efternamnen på målprofilerna i innehållet i meddelandet placerar du markören där du vill infoga dem och klickar på den sista ikonen i verktygsfältet, klickar sedan på **[!UICONTROL Include]** och väljer **[!UICONTROL Greetings]**.

      ![](assets/include-greetings.png)

      Bläddra till fliken Förhandsgranska om du vill kontrollera personaliseringen genom att välja en mottagare.

      ![](assets/perso-check.png)

   * Infoga en spårad länk

      Om du vill dirigera mottagare till en extern adress via en bild eller text markerar du den och klickar på ikonen **[!UICONTROL Add a link]** i verktygsfältet.

      Ange länkens URL i fältet **URL** med följande format **https://www.myURL.com** och bekräfta sedan.

      ![](assets/add-a-link.png)

   * Lägga till en spegelsida

      Om du vill att mottagarna ska kunna se ditt leveransinnehåll i en webbläsare lägger du till en länk på meddelandets spegelsida.

      Placera markören där du vill infoga länken och klicka på den sista ikonen i verktygsfältet, klicka sedan på **[!UICONTROL Include]** och välj **[!UICONTROL link to mirror page]**.
   När innehållet är klart klickar du på **Spara**: den kommer nu att visas i din lista över leveranser på fliken **[!UICONTROL Campaigns > Deliveries]**. Din första e-postleverans är klar. Nu måste ni definiera målgruppen, validera leveransen och skicka den.


Läs mer i följande avsnitt av dokumentationen för Campaign Classic v7:

* Designa ett e-postmeddelande i Campaign
↗️ [Lär dig hur du utformar ett e-postmeddelande](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/defining-the-email-content.html)
* Importera ett e-postinnehåll
↗️ [Användningsfall: Skapa ett arbetsflöde för att läsa in ett leveransinnehåll](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/deliveries/loading-delivery-content.html)
* Skapa och använda en e-postmall
↗️ [Läs mer om e-postmallar](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-delivery-templates/about-templates.html)
* Välj publik för ditt e-postmeddelande
↗️ [Lär dig definiera målpopulationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-defining-the-target-population.html)
* Validera en leverans och skicka korrektur
↗️ [Lär dig viktiga steg för att validera en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html)
* Lägg till [dirigerade adresser](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-seed-addresses/about-seed-addresses.html)

## Testa och validera dina e-postmeddelanden

Campaign erbjuder flera sätt att testa och validera dina e-postmeddelanden innan de skickas till era målgrupper.

↗️ [Använd de bästa metoderna som anges i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/check-before-sending.html)

Du kan:

* Kontrollera leveransanalysloggar
* Skicka korrektur
* Lägg till dirigerade adresser
* Använd kontrollgrupper
* Kontrollera e-poståtergivning

↗️ [Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html)

## Övervaka dina e-postmeddelanden

När du har skickat den kontrollerar du leveransstatus på kontrollpanelen och öppnar leveransloggar och rapporter för att bekräfta att meddelandena har skickats korrekt.

↗️ [Läs mer i dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/track-and-monitor.html)

