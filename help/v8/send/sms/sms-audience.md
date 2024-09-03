---
title: SMS väljer målgrupp
description: Lär dig hur du konfigurerar målgruppen för en SMS-leverans
feature: SMS
role: User
level: Beginner, Intermediate
source-git-commit: 24a6d56a79995cd0113d8438d1bd3314a3872e35
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Välj mottagare för SMS-leveransen {#sms-audience}

[Läs mer om målgruppen här](../../audiences/gs-audiences.md) innan du väljer målgrupp.

I de flesta fall hämtas huvudmålet för en leverans från Adobe Campaign-databasen (standardläge). Publiken kan dock också lagras i en extern fil. [Läs mer i det här avsnittet](#external-audience).

## Målgrupp i Adobe Campaign

Följ stegen nedan för att välja målgrupp:

1. Klicka på länken **[!UICONTROL To]** i leveransredigeraren. Ett **[!UICONTROL Select target]**-fönster öppnas

1. Eftersom målgruppen lagras i Adobe Campaign-databasen väljer du alternativet **[!UICONTROL Defined in the database]** på fliken **[!UICONTROL Main target]**.

   ![](assets/audience_to.png){zoomable="yes"}

1. Välj **[!UICONTROL Target mapping]** i listrutan. Adobe Campaign standardmålmappning är Mottagare, baserat på schemat **[!UICONTROL nms:recipient]**.

   Andra målmappningar är tillgängliga, och vissa kan vara relaterade till din specifika konfiguration. Mer information om målmappningar finns i [Arbeta med målmappningar](../../audiences/target-mappings.md).

1. Klicka på knappen **[!UICONTROL Add]** för att definiera begränsningsfilter.

   Du kan sedan välja vilken typ av filtrering du vill använda:

   ![](assets/audience_filters.png){zoomable="yes"}

   Om du vill använda en måltyp markerar du den och klickar på knappen **[!UICONTROL Next]**.

   Här är de måltyper som erbjuds som standard:

   * **[!UICONTROL Filtering conditions]**: låter dig definiera en fråga och visa resultatet.
   * **[!UICONTROL A list of recipients]**: låter dig välja en lista som du har förberett och som innehåller din målgrupp
   * **[!UICONTROL A recipient]**: gör att du kan välja en mottagare direkt i tabellen.
   * **[!UICONTROL Recipients included in a folder]**: du kan välja en mapp i utforskarens navigeringsträd
   * **[!UICONTROL Recipients of a delivery]**: du kan välja målgrupp för en tidigare leverans
   * **[!UICONTROL Recipients of deliveries belonging to a folder]**: gör att du kan välja målgrupp för alla leveranser i en viss mapp
   * **[!UICONTROL Subscribers of an information service]**: Med det här alternativet kan du välja ett nyhetsbrev som mottagarna måste prenumerera på för att få det mål som den leverans som skapas har.
   * **[!UICONTROL User filters]**: gör att du kan använda de fördefinierade filtren.

   Med alternativet **[!UICONTROL Exclude recipients from this segment]** kan du rikta in dig på mottagare som inte uppfyller de definierade målvillkoren. Om du vill använda det här alternativet markerar du lämplig ruta och tillämpar sedan målinriktning, enligt definitionen ovan, för att utesluta de resulterande profilerna.

1. Ange målgruppens namn i etikettfältet och klicka på knappen **[!UICONTROL Finish]** för att validera målgruppen.

   ![](assets/audience_finish.png){zoomable="yes"}

   Du kan lägga till målpopulationen så många som du behöver genom att klicka igen på knappen **[!UICONTROL Add]**. Du kan även ta bort vissa av dem genom att klicka på krysset efter etiketten.

## Målgrupp i en extern fil {#external-audience}

Du kan använda Adobe Campaign för att skicka en leverans till en publik som inte finns i databasen, utan i en extern fil.

Så här gör du:

1. Klicka på länken **[!UICONTROL To]** i leveransredigeraren. Ett **[!UICONTROL Select target]**-fönster öppnas

1. Välj alternativet **[!UICONTROL Defined in an external file]**.

   ![](assets/audience_externalfile.png){zoomable="yes"}

1. Som standard importeras mottagarna i databasen. Du måste välja **[!UICONTROL Target mapping]** i så fall. Mer information om målmappningar finns i [Arbeta med målmappningar](../../audiences/target-mappings.md).

   Annars kan du också välja **[!UICONTROL Do not import the recipients into the database]**.

1. När du importerar filen klickar du på länken **[!UICONTROL File format definition…]** för att markera och konfigurera den externa filen.

1. Klicka på knappen **[!UICONTROL Finish]** för att validera din målgrupp.
