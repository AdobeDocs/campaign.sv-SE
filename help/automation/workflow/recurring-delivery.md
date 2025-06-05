---
product: campaign
title: Återkommande leverans
description: Läs mer om arbetsflödesaktiviteten Återkommande leverans
feature: Workflows
role: User, Data Engineer
version: Campaign v8, Campaign Classic v7
exl-id: 27308b0d-cbfc-4bc6-9061-d771ceac95fd
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 13%

---

# Återkommande leverans{#recurring-delivery}



Med en **[!UICONTROL Recurring delivery]**-aktivitet kan du konfigurera en leveransmallförekomst som är specifik för en kampanj.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#recurring-delivery-video)

Den här aktiviteten är bara tillgänglig från fliken **[!UICONTROL Targeting and workflows]** som finns i en kampanj.

Så här gör du:

1. Välj den leveransmall som aktiviteten ska baseras på.

   ![](assets/recurring_delivery_001.png)

1. Konfigurera leveransmallen.

Konfigurationsprocessen för den här aktiviteten liknar den för att skapa en leveransmall utifrån tillgängliga alternativ.

Ett exempel på den här aktiviteten som används finns i [avsnittet](send-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Så här ställer du in återkommande leverans

En **återkommande leverans** skapar en ny leveransinstans varje gång den körs. Om arbetsflödet till exempel är schemalagt att köras en gång i veckan resulterar det i 52 leveranser efter ett år. Det innebär också att de breda loggarna och spårningsloggarna separeras av varje leveransinstans.

![Återkommande leverans](assets/delivery_recurring.jpg)

Om du vill stoppa en återkommande leverans från att köras bör du helt avbryta kampanjen eller stoppa arbetsflödet som körs. Om du stoppar leveransen från kontrollpanelen för Campaign stoppas endast leveransförekomsten: nästa instans av den återkommande leveransen kommer att fortsätta skapas vid varje arbetsflödeskörning.

>[!NOTE]
>
>Det går inte att skicka ett bevis från en aktivitet av typen **[!UICONTROL Recurring delivery]**.
> 
>Om du vill skapa en leverans direkt via ett kampanjarbetsflöde använder du de kanalspecifika aktiviteter som är förkonfigurerade (t.ex. **[!UICONTROL Email delivery]**).

## Självstudievideo (#reciing-delivery-video)

I den här videon förklaras hur du konfigurerar en återkommande leverans och en schemaläggningsaktivitet.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Ytterligare utbildningsvideor för Campaign är tillgängliga [här](https://experienceleague.adobe.com/docs/campaign-learn/tutorials/getting-started/introduction-to-adobe-campaign.html){target="_blank"}.
