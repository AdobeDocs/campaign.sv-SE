---
title: Skicka e-post med Adobe Campaign
description: Kom igång med e-post i Adobe Campaign. Skicka personanpassade e-postmeddelanden till en målgrupp.
feature: Email
role: User
level: Beginner
exl-id: 97dcd0e0-db5b-45a4-96af-817e49f6cb64
source-git-commit: 1baeb8827a0eab4f9487bb5e5afe4d779e00efe4
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 5%

---

# Designa och skicka e-post

Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen. [Läs mer](../send/send.md).

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

      Läs mer om personaliseringsalternativ i [det här avsnittet](personalize.md).

   * Infoga en spårad länk

      Om du vill dirigera leveransmottagare till en extern adress via en bild eller text markerar du den och klickar på knappen **[!UICONTROL Add a link]** i verktygsfältet.

      Ange länkens URL i dialogrutan **URL** fält med följande format **https://www.myURL.com**, och bekräfta sedan.

      ![](assets/add-a-link.png)

   * Lägga till en spegelsida

      Lägg till en länk till [spegelsida](../send/mirror-page.md) av ditt meddelande.

      Placera markören där du vill infoga länken, klicka på den sista ikonen i verktygsfältet och klicka sedan på **[!UICONTROL Include]** och markera **[!UICONTROL link to mirror page]**.
   När innehållet är klart klickar du på **Spara**: den visas nu i din lista över leveranser i **[!UICONTROL Campaigns > Deliveries]** -fliken. Din första e-postleverans är klar. Nu måste ni definiera målgruppen, validera leveransen och skicka den.


Lär dig hur du importerar ett e-postinnehåll i det här [användningsfall](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/load-delivery-content.html).

Läs mer i följande avsnitt:

* [Designa ett e-postmeddelande i Campaign](../send/email.md)
* [Skapa och använda en e-postmall](../send/create-templates.md)
* [Välj publik för ditt e-postmeddelande](../audiences/gs-audiences.md)
* [Validera en leverans och skicka korrektur](../send/preview-and-proof.md)

## Testa och validera dina e-postmeddelanden

Campaign erbjuder flera sätt att testa och validera dina e-postmeddelanden innan de skickas till era målgrupper. Lär dig hur du förhandsgranskar och testar e-postinnehåll i [den här sidan](../send/preview-and-proof.md).

Du kan:

* Kontrollera leveransanalysloggar
* Skicka korrektur
* Lägg till dirigerade adresser

[Läs mer](../send/delivery-analysis.md)
