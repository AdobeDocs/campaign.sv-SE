---
title: Skicka e-post med Adobe Campaign
description: Kom igång med e-post i Adobe Campaign. Skicka personanpassade e-postmeddelanden till en målgrupp.
feature: Email
role: User
level: Beginner
version: Campaign v8, Campaign Classic v7
exl-id: 97dcd0e0-db5b-45a4-96af-817e49f6cb64
source-git-commit: 96f1518f252be7ffa27ba8157b8a090bf4d4510d
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 6%

---

# Designa och skicka e-post

Med Adobe Campaign kan du skapa e-postleveranser för att skicka personaliserade e-postmeddelanden till målgruppen. [Läs mer](../send/send.md)

>[!NOTE]
>
>Bläddra till [webbanvändargränssnittet](../start/campaign-ui.md#campaign-web-user-interface-ac-web-ui) om du vill skapa engagerande och individuellt anpassade e-postmeddelanden. Adobe Campaign har e-postprogrammet Designer, ett intuitivt dra och släpp-gränssnitt som gör att du kan utforma och förfina allt innehåll för alla e-postmeddelanden.


Lär dig hur du skapar och konfigurerar en leverans på [den här sidan](../start/create-message.md).

## Skapa en e-postleverans

Skapa personaliserade och sammanhangsberoende e-postmeddelanden som överensstämmer med resten av kundupplevelsen.

![](assets/new-email-content.png)


I följande exempel får du lära dig hur du utformar en e-postleverans i Adobe Campaign som innehåller personaliserade data, länkar till en extern URL och en länk till spegelsidan.

1. **Skapa leveransen**

   Om du vill skapa en ny leverans går du till fliken **Kampanjer**, klickar på **Leveranser** och klickar på knappen **Skapa** ovanför listan över befintliga leveranser.

   ![](assets/delivery_step_1.png)

1. **Välj mallen**

   Välj en leveransmall och ge sedan leveransen ett namn. Det här namnet visas endast för användare av Adobe Campaign-konsolen och inte för dina mottagare, men den här rubriken visas i din lista över leveranser. Klicka på **[!UICONTROL Continue]**.

   ![](assets/dce_delivery_model.png)

1. **Importera ditt innehåll**

   Klicka på fliken **Source** för att klistra in ditt HTML-innehåll.

   ![](assets/paste-content.png)

   >[!NOTE]
   >
   >För att undvika prestandaproblem får bilderna i e-postmeddelanden inte överstiga 100 kB.

1. **Anpassa meddelandet**

   * Lägg till förnamn och efternamn för mottagarna

     Om du vill infoga för- och efternamnen på målprofilerna i innehållet i meddelandet placerar du markören där du vill infoga dem och klickar på den sista ikonen i verktygsfältet, klickar på **[!UICONTROL Include]** och väljer **[!UICONTROL Greetings]**.

     ![](assets/include-greetings.png)

     Bläddra till fliken Förhandsgranska för att kontrollera personaliseringen genom att välja en mottagare.

     ![](assets/perso-check.png)

     Läs mer om personaliseringsalternativ i [det här avsnittet](personalize.md).

   * Infoga en spårad länk

     Om du vill dirigera leveransmottagare till en extern adress via en bild eller text markerar du den och klickar på ikonen **[!UICONTROL Add a link]** i verktygsfältet.

     Ange URL-adressen för länken i fältet **URL** med följande format: **https://www.myURL.com** och bekräfta sedan.

     ![](assets/add-a-link.png)

   * Lägga till en spegelsida

     Om du vill att mottagarna ska kunna visa ditt leveransinnehåll i en webbläsare lägger du till en länk på meddelandets [spegelsida](mirror-page.md).

     Placera markören där du vill infoga länken, klicka på den sista ikonen i verktygsfältet, klicka på **[!UICONTROL Include]** och välj **[!UICONTROL link to mirror page]**.

     Läs mer om hur du hanterar spegelsidan i [det här avsnittet](mirror-page.md#link-to-mirror-page).

1. Du kan definiera ytterligare parametrar för e-postmeddelandet, till exempel skicka en kopia av meddelandena till en BBC-adress, ändra meddelandeformatet, ange en viss kodning osv. Läs mer i [det här avsnittet](email-parameters.md).

1. När innehållet är klart klickar du på **Spara**: det visas nu i listan över leveranser på fliken **[!UICONTROL Campaigns > Deliveries]** .

Din första e-postleverans är klar. Nu måste ni definiera målgruppen, validera leveransen och skicka den.

Lär dig hur du skapar ett arbetsflöde för att importera ett e-postinnehåll i det här [användningsfallet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/load-delivery-content.html){target="_blank"}.

>[!MORELIKETHIS]
>
>* [Skapa en leverans](../start/create-message.md)
>* [Skapa och använda en e-postmall](create-templates.md)
>* [Välj publik för ditt e-postmeddelande](../audiences/gs-audiences.md)
>* [Validera en leverans och skicka korrektur](preview-and-proof.md)
>* [Konfigurera och skicka leveransen](configure-and-send.md)
>* [God praxis för leverans](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html){target="_blank"}

## Testa och validera dina e-postmeddelanden

Campaign erbjuder flera sätt att testa och validera dina e-postmeddelanden innan de skickas till era målgrupper. Lär dig hur du förhandsgranskar och testar ditt e-postinnehåll i [det här avsnittet](../send/preview-and-proof.md).

Du kan:

* [Skicka korrektur](preview-and-proof.md)
* [Lägg till dirigerade adresser](../audiences/test-profiles.md)
* [Kontrollera leveransanalysloggar](delivery-analysis.md)

