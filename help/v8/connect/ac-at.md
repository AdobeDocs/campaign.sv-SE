---
title: Arbeta med Campaign och Adobe Target
description: Lär dig hur du arbetar med Campaign och Adobe Target
feature: Overview
role: Data Engineer
level: Beginner
source-git-commit: 391eac2f5e4d4c8c5d4dadd3394798361640e1d8
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 1%

---

# Arbeta med Campaign och Adobe Target

Anslut Campaign och Target för att inkludera ett erbjudande från Adobe Target i en e-postleverans från Adobe Campaign.

Den här integreringen hjälper dig att implementera användningsexempel enligt följande: När en mottagare öppnar ett e-postmeddelande som skickas via Adobe Campaign kan du med ett anrop till Adobe Target visa en dynamisk version av innehållet. Den här dynamiska versionen beräknas utifrån de regler som anges i förväg när e-postmeddelandet skapas.

>[!NOTE]
>Integreringen stöder bara statiska bilder. De andra typerna av innehåll kan inte personaliseras.

? Som användare av hanterade Cloud Services ska du [kontakta Adobe](../start/campaign-faq.md#support) för att implementera utlösare för Experience Cloud med Campaign.

Adobe Target kan använda följande datatyper:

* Data från Adobe Campaign-databasen
* Segment som är länkade till besökar-ID i Adobe Target, endast om de data som används inte omfattas av juridiska begränsningar
* Adobe Target data: användaragent, IP-adress, geolokaliseringsdata

## Infoga ett dynamiskt innehåll

I exemplet nedan får du lära dig att integrera **ett dynamiskt erbjudande** från Adobe Target i ett Adobe Campaign-e-postmeddelande.

Vi vill skapa ett meddelande med en bild som ändras dynamiskt beroende på mottagarens land. Data skickas med varje mbox-begäran och beror på besökarens IP-adress.

I det här e-postmeddelandet vill vi att en av bilderna ska variera dynamiskt enligt följande användarupplevelser:

* E-postmeddelandet öppnas i Frankrike.
* E-postmeddelandet öppnas i USA.
* Om inget av dessa villkor gäller visas en standardbild.

![](assets/target_4.png)

Följande steg måste utföras i Adobe Campaign och Adobe Target:

1. [Infoga det dynamiska erbjudandet i ett e-postmeddelande](#inserting-dynamic-offer)
1. [Skapa omdirigeringserbjudanden](#create-redirect-offers)
1. [Skapa målgrupper](#audiences-target)
1. [Skapa en upplevelseinriktad aktivitet](#creating-targeting-activity)
1. [Förhandsgranska och skicka meddelandet](#preview-send-email)

### Infoga det dynamiska erbjudandet i ett e-postmeddelande {#inserting-dynamic-offer}

Ange mål och innehåll för e-postmeddelandet i Adobe Campaign. Du kan infoga en dynamisk bild från Adobe Target.

Det gör du genom att ange standardbildens URL-adress, platsnamn och de fält som du vill överföra till Adobe Target.

I Adobe Campaign finns det två sätt att infoga en dynamisk bild från Target i ett e-postmeddelande:

* Om du använder redigeraren för digitalt innehåll väljer du en befintlig bild och väljer **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** i verktygsfältet.

   ![](assets/target_5.png)

* Om du använder standardredigeraren placerar du markören där du vill infoga bilden och väljer **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** i listrutan för anpassning.

   ![](assets/target_12.png)

Du kan sedan definiera bildparametrarna:

* URL:en för **[!UICONTROL Default image]** är den bild som visas när inget av villkoren är uppfyllt. Du kan också välja en bild från ditt resursbibliotek.
* **[!UICONTROL Target location]** är namnet på platsen för ditt dynamiska erbjudande. Du måste välja den här platsen i din Adobe Target-aktivitet.
* Med **[!UICONTROL Landing Page]** kan du dirigera om standardbilden till en standardstartsida. Den här URL:en används bara när standardbilden visas i det slutliga e-postmeddelandet. Det är valfritt.
* **[!UICONTROL Additional decision parameters]** definierar mappningen mellan fälten som definieras i Adobe Target-segmenten och Adobe Campaign-fälten. De Adobe Campaign-fält som används måste ha angetts i rutan. I vårt exempel har vi lagt till fältet Land.

Om du använder Enterprise-behörigheter i inställningarna för Adobe Target lägger du till motsvarande egenskap i det här fältet. Läs mer om behörigheter för målföretag i [den här sidan](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html?lang=en#administer).

![](assets/target_13.png)

### Skapa omdirigeringserbjudanden {#create-redirect-offers}

I Adobe Target kan du skapa olika versioner av ditt erbjudande. Beroende på användarupplevelsen kan ett omdirigeringserbjudande skapas och du kan ange vilken bild som ska visas.

I vårt fall behöver vi två omdirigeringserbjudanden, det tredje (standarderbjudandet) ska definieras i Adobe Campaign.

1. Om du vill skapa ett nytt omdirigeringserbjudande i Target Standard går du till fliken **[!UICONTROL Content]** och klickar på **[!UICONTROL Code offers]**.

1. Klicka **[!UICONTROL Create]** och sen **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Ange ett namn för erbjudandet och URL:en för bilden.

   ![](assets/target_6.png)

1. Följ samma procedur för det återstående omdirigeringserbjudandet. Se denna [sida](https://experienceleague.adobe.com/docs/target/using/experiences/offers/offer-redirect.html?lang=en#experiences) för mer information om detta.

### Skapa målgrupper {#audiences-target}

I Adobe Target måste ni skapa de två målgrupper som de personer som besöker ert erbjudande kategoriseras efter det innehåll som ska levereras. För varje målgrupp lägger du till en regel som definierar vilka som ska kunna se erbjudandet.

1. Om du vill skapa en ny målgrupp i Target går du till fliken **[!UICONTROL Audiences]** och klickar på **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. Ge era målgrupper ett namn.

   ![](assets/audiences_2.png)

1. Klicka på **[!UICONTROL Add a rule]** och välj en kategori. Regeln använder särskilda kriterier för att rikta in sig på besökarna. Du kan förfina reglerna genom att lägga till villkor eller genom att skapa nya regler i andra kategorier.

1. Följ samma procedur för de återstående målgrupperna.

### Skapa en upplevelseinriktad aktivitet {#creating-targeting-activity}

I Adobe Target måste vi skapa en Experience Targeting-aktivitet, definiera olika upplevelser och koppla dem till motsvarande erbjudanden.

Först måste ni definiera målgruppen:

1. Om du vill skapa en Experience Targeting-aktivitet går du till fliken **[!UICONTROL Activities]** och klickar på **[!UICONTROL Create Activity]** och sedan på **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. Välj **[!UICONTROL Form]** som **[!UICONTROL Experience Composer]**.

1. Välj en målgrupp genom att klicka på knappen **[!UICONTROL Change audience]**.

   ![](assets/target_10_2.png)

1. Välj målgruppen som skapades i föregående steg.

   ![](assets/target_10_3.png)

1. Skapa en ny upplevelse genom att klicka på **[!UICONTROL Add Experience Targeting]**.

Lägg sedan till innehåll för varje målgrupp:

1. Välj det platsnamn du valde när du infogade det dynamiska erbjudandet i Adobe Campaign.

   ![](assets/target_15.png)

1. Klicka på listruteknappen och välj **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Välj det omdirigeringserbjudande som du tidigare har skapat.

   ![](assets/target_content_2.png)

1. Följ samma steg för den andra upplevelsen.

Fönstret **[!UICONTROL Target]** sammanfattar din aktivitet. Om det behövs kan ni lägga till andra upplevelser.

![](assets/target_experience.png)

I fönstret **[!UICONTROL Goal & Settings]** kan du anpassa din aktivitet genom att ange en prioritet, ett mål eller en varaktighet.

I **[!UICONTROL Reporting Settings]**-avsnittet kan du välja en åtgärd och redigera parametrarna som avgör när målet uppnås.

![](assets/target_experience_2.png)

## Förhandsgranska och skicka meddelandet {#preview-send-email}

I Adobe Campaign kan du nu förhandsgranska ditt e-postmeddelande och testa återgivningen i olika mottagare.

Du kommer att märka att bilden ändras beroende på de olika upplevelser som skapas.

Du kan nu skicka ditt e-postmeddelande med ett dynamiskt erbjudande från Target.

![](assets/target_20.png)
