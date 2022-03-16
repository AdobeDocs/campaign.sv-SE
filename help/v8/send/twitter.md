---
title: Posta meddelanden på Twitter med Adobe Campaign
description: Lär dig hur du använder Adobe Campaign Social Marketing Module för att publicera meddelanden på Twitter och samla in kontaktdata
role: Data Engineer
level: Beginner
hidefromtoc: true
hide: true
exl-id: 0783e289-ae8e-4bb7-80f1-f90937a528c1
source-git-commit: da6e585a789749ae0302f048940d104a36e2b477
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 1%

---


# Posta meddelanden på Twitter med Adobe Campaign {#post-tw-messages}

Adobe Campaign har en **Social marknadsföring** så att ni kan interagera med kunder och potentiella kunder via Twitter.

När integreringen är konfigurerad kan du:

* Skicka meddelanden på Twitter: Med Adobe Campaign kan du skicka meddelanden direkt till ditt twitter-konto. Du kan också skicka direktmeddelanden till alla dina följare.
* Samla in nya kontakter: Adobe Campaign kan automatiskt återställa profildata, vilket gör att ni kan genomföra riktade kampanjer och, när det är möjligt, implementera flerkanalsstrategier. Den här åtgärden kräver användarens samtycke.


Konfigurationssteg för att integrera ditt Twitter-konto med Adobe Campaign beskrivs i [den här sidan](../connect/ac-tw.md).

## Skapa och publicera ett Twitter-inlägg {#publish-on-tw}

Följ stegen nedan för att skicka ett meddelande till ditt Twitter-konto:

1. Skapa en Twitter-leverans

   Skapa en ny leverans baserad på **[!UICONTROL Tweet (twitter)]** leveransmall.

1. Välj huvudmålet

   Markera det eller de konton som du vill skicka tweets till.

   1. Klicka på länken **[!UICONTROL To]**.
   1. Klicka på knappen **[!UICONTROL Add]**.
   1. Välj **[!UICONTROL A Twitter account]**.
   1. I **[!UICONTROL Folder]** markerar du den tjänstmapp som innehåller Twitter-kontot. Välj sedan det Twitter-konto som du vill skicka tweeten till.

1. Välj korrekturmål

   The **[!UICONTROL Target of the proofs]** kan du definiera det Twitter-konto som ska användas för testleveranser före den slutliga leveransen.

   Enligt informationen i [konfigurationssteg](../connect/ac-tw.md#tw-test-account)måste du skapa ett privat Twitter-konto för att skicka korrektur.

   >[!NOTE]
   >
   >Om du använder samma Twitter-testkonto för alla leveranser kan du spara korrekturmålet i **[!UICONTROL Tweet]** leveransmall, via **[!UICONTROL Resources > Templates > Delivery templates]** nod. Korrekturmålet anges sedan som standard för varje ny leverans.

1. Definiera innehållet i ditt inlägg

   Ange innehållet i ditt inlägg i **[!UICONTROL Content]** -fliken.

   >[!CAUTION]
   >
   >När du publicerar på Twitter gäller begränsningarna:
   >
   >* Meddelandet får inte innehålla fler än 140 tecken.
   >* Formatet HTML stöds inte.


1. Förhandsgranska ditt inlägg

   Bläddra i **[!UICONTROL Preview]** för att kontrollera återgivningen av inlägget.

   1. Klicka på **[!UICONTROL Preview]** -fliken.
   1. Klicka på **[!UICONTROL Test personalization]** nedrullningsbar meny och välj **[!UICONTROL Service]**.
   1. I **[!UICONTROL Folder]** markerar du den tjänstmapp som innehåller ditt Twitter-konto.
   1. Välj det Twitter-konto som du vill testa förhandsgranskningen med.

1. Skicka ett bevis

   Innan du publicerar din tweet kontrollerar du att den är godkänd genom att skicka ett korrektur av din publikation: Du kan sedan få en exakt återgivning av publikationen på en privat testsida i Twitter.

   Mer information om hur du skapar ett privat Twitter-konto finns i [det här avsnittet](../connect/ac-tw.md#tw-test-account).

   ![](../assets/do-not-localize/book.png) [Lär dig viktiga steg för att validera en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html){target=&quot;_blank&quot;}

1. Lägg upp meddelandet

   1. När innehållet är godkänt klickar du på **[!UICONTROL Send]** -knappen.
   1. Välj **[!UICONTROL Deliver as soon as possible]** och klicka på **[!UICONTROL Analyze]** -knappen.
   1. Kontrollera resultatet när analysen är klar.
   1. Klicka **[!UICONTROL Confirm delivery]** och sedan klicka **[!UICONTROL Yes]**.


## Skicka direktmeddelanden till följare {#direct-tw-messages}

The **[!UICONTROL Synchronize Twitter accounts]** tekniska arbetsflöden återställer listan med Twitter följare så att du kan skicka direktmeddelanden till dem. [Läs mer](../connect/ac-tw.md#synchro-tw-accounts)

Följ stegen nedan för att skicka direktmeddelanden till dina följare:

1. Skapa en Twitter-leverans baserad på **[!UICONTROL Tweet (Direct Message)]** inbyggd leveransmall.

1. Välj huvudmålet

1. Välj **[!UICONTROL To]** länk och **[!UICONTROL Add]** -knappen.

1. Välj en typ av mål

   * Välj **[!UICONTROL Twitter subscribers]** för att skicka ett direktmeddelande till alla dina följare.

   * Välj **[!UICONTROL Filter conditions]** för att definiera en fråga och visa resultatet. Det här alternativet är detsamma som för e-postleveranser. Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/creating-queries/defining-filter-conditions.html){target=&quot;_blank&quot;}.

1. Från **[!UICONTROL Target of the proofs]** väljer du den följare som ska få korrekturet för ditt direktmeddelande.

   >[!NOTE]
   >
   >Om du vill skicka alla dina korrektur för direktmeddelanden till samma Twitter-följare kan du spara korrekturmålet i dialogrutan **[!UICONTROL Tweet (Direct Message)]** leveransmall, via **[!UICONTROL Resources > Templates > Delivery templates]** nod.

1. Ange innehållet i meddelandet i **[!UICONTROL Content]** -fliken.

   Anpassningsfält kan användas på samma sätt som för e-postleveranser, t.ex. för att lägga till följarens namn i meddelandets brödtext. Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/personalizing-deliveries/about-personalization.html){target=&quot;_blank&quot;}.

1. Förhandsgranska meddelandet

   Bläddra i **[!UICONTROL Preview]** för att kontrollera återgivningen av inlägget.

   1. Klicka på **[!UICONTROL Preview]** -fliken.
   1. Klicka på **[!UICONTROL Test personalization]** nedrullningsbar meny och välj **[!UICONTROL Service]**.
   1. I **[!UICONTROL Folder]** markerar du den tjänstmapp som innehåller ditt Twitter-konto.
   1. Välj det Twitter-konto som du vill testa förhandsgranskningen med.

1. Skicka ett bevis

   Innan du skickar meddelandet kontrollerar du att det är verifierat genom att skicka ett bevis till ett testkonto: kan du sedan få en exakt återgivning av meddelandet på ett privat Twitter-konto och kontrollera innehåll och personalisering.

   Mer information om hur du skapar ett privat Twitter-konto finns i [det här avsnittet](../connect/ac-tw.md#tw-test-account).

   ![](../assets/do-not-localize/book.png) [Lär dig viktiga steg för att validera en leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html){target=&quot;_blank&quot;}

1. Skicka direktmeddelandet

   1. När innehållet är godkänt klickar du på **[!UICONTROL Send]** -knappen.
   1. Välj **[!UICONTROL Deliver as soon as possible]** och klicka på **[!UICONTROL Analyze]** -knappen.
   1. Kontrollera resultatet när analysen är klar.
   1. Klicka **[!UICONTROL Confirm delivery]** och sedan klicka **[!UICONTROL Yes]**.

>[!CAUTION]
>
>Du kan inte skicka mer än 250 direktmeddelanden per dag. För att undvika att detta tröskelvärde överskrids kan du leverera i vågor. Mer information finns i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html?lang=en#sending-using-multiple-waves){target=&quot;_blank&quot;}.


## Åtkomstspårningsdata {#tw-tracking}

I den inbyggda **[!UICONTROL Tweet]** leveransmall, spårning är aktiverat som standard.

Spåra data kan visas i leveransrapporterna och i **[!UICONTROL Edit > Tracking]** fliken för leveransen och tjänsten.

Spårningskonfigurationen är densamma som för en e-postleverans. Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html){target=&quot;_blank&quot;}.

