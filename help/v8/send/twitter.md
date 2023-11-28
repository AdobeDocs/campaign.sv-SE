---
title: Posta meddelanden på X (Twitter) med Adobe Campaign
description: Lär dig hur du använder Adobe Campaign Social Marketing Module för att skicka meddelanden på X (tidigare Twitter) och skicka direktmeddelanden till dina följare
role: User
level: Beginner, Intermediate
exl-id: 0783e289-ae8e-4bb7-80f1-f90937a528c1
source-git-commit: f463c5747b844544ba561a63e4cb0359c0c258c8
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 1%

---


# Posta meddelanden på X (Twitter) med Adobe Campaign {#post-tw-messages}

Adobe Campaign har en **Social marknadsföring** så att ni kan interagera med kunder och prospects via X (tidigare Twitter).

När integreringen är konfigurerad kan du:

* Skicka direktmeddelanden till dina följare
* Lägg upp på ditt X-konto
* Samla in nya kontakter genom att återställa profildata, vilket gör att ni kan genomföra riktade kampanjer och, när det är möjligt, implementera flerkanalsstrategier. Den här åtgärden kräver användarens samtycke.


Konfigurationssteg för att integrera ditt X-konto med Adobe Campaign beskrivs i [den här sidan](../connect/ac-tw.md).

## Skapa och publicera ett X-inlägg {#publish-on-tw}

Följ stegen nedan för att publicera ett meddelande på ditt X-konto:

1. Skapa en X-leverans

   Skapa en ny leverans baserad på **[!UICONTROL Tweet (twitter)]** leveransmall.

   ![](assets/tw-new-delivery.png)

1. Välj huvudmålet

   Markera det eller de konton som du vill skicka inlägg till.

   ![](assets/tw-define-target.png)

   1. Klicka på länken **[!UICONTROL To]**.
   1. Klicka på knappen **[!UICONTROL Add]**.
   1. Välj **[!UICONTROL A Twitter account]**.
   1. I **[!UICONTROL Folder]** markerar du den tjänstmapp som innehåller X-kontot. Välj sedan det X-konto som du vill skicka tweeten till.

1. Välj korrekturmål

   The **[!UICONTROL Target of the proofs]** På -fliken kan du definiera X-kontot som ska användas för testleveranser före den slutliga leveransen.

   Enligt informationen i [konfigurationssteg](../connect/ac-tw.md#tw-test-account)måste du skapa ett X-konto för privat test som är dedikerat för att skicka korrektur.

   >[!NOTE]
   >
   >Om du använder samma X-testkonto för alla leveranser kan du spara korrekturmålet i **[!UICONTROL Tweet]** leveransmall, via **[!UICONTROL Resources > Templates > Delivery templates]** nod. Korrekturmålet anges sedan som standard för varje ny leverans.

1. Definiera innehållet i ditt inlägg

   Ange innehållet i ditt inlägg i **[!UICONTROL Content]** -fliken.

   ![](assets/tw-delivery-content.png)

   >[!CAUTION]
   >
   >Vid bokföring på X gäller begränsningarna:
   >
   >* Meddelandet får inte innehålla fler än 140 tecken.
   >* Formatet HTML stöds inte.
   >

1. Förhandsgranska ditt inlägg

   Sök i **[!UICONTROL Preview]** för att kontrollera återgivningen av inlägget.

   ![](assets/tw-delivery-preview.png)

   1. Klicka på **[!UICONTROL Preview]** -fliken.
   1. Klicka på **[!UICONTROL Test personalization]** nedrullningsbar meny och välj **[!UICONTROL Service]**.
   1. I **[!UICONTROL Folder]** markerar du den tjänstmapp som innehåller ditt X-konto.

1. Skicka en korrektur

   Innan du publicerar din tweet måste du verifiera den genom att skicka ett korrektur av publikationen: du kan sedan få en exakt återgivning av publikationen på en privat X-testsida.

1. Lägg upp meddelandet

   1. När innehållet är godkänt klickar du på **[!UICONTROL Send]** -knappen.
   1. Välj **[!UICONTROL Deliver as soon as possible]** och klicka på **[!UICONTROL Analyze]** -knappen.
   1. Kontrollera resultatet när analysen är klar.
   1. Klicka **[!UICONTROL Confirm delivery]** och sedan klicka **[!UICONTROL Yes]**.

## Skicka direktmeddelanden till följare {#direct-tw-messages}

The **[!UICONTROL Synchronize Twitter accounts]** tekniskt arbetsflöde återställer listan med X-följare så att du kan skicka direktmeddelanden till dem. [Läs mer](../connect/ac-tw.md#synchro-tw-accounts)

Följ stegen nedan för att skicka direktmeddelanden till dina följare:

1. Skapa en X-leverans baserad på **[!UICONTROL Tweet (Direct Message)]** inbyggd leveransmall.

1. Välj huvudmålet

   ![](assets/tw-dm-define-target.png)

   1. Välj **[!UICONTROL To]** -länken och **[!UICONTROL Add]** -knappen.

   1. Välj en typ av målinriktning

      * Välj **[!UICONTROL Twitter subscribers]** för att skicka ett direktmeddelande till alla dina följare.

      * Välj **[!UICONTROL Filter conditions]** för att definiera en fråga och visa resultatet. Lär dig hur du skapar ett filter i [det här avsnittet](../audiences/create-filters.md#advanced-filters).

1. Välj korrekturmålet på menyn **[!UICONTROL Target of the proofs]** flik: det här kontot kommer att få ett bevis på ditt direktmeddelande.

   Enligt informationen i [konfigurationssteg](../connect/ac-tw.md#tw-test-account)måste du skapa ett X-konto för privat test som är dedikerat för att skicka korrektur.


   >[!NOTE]
   >
   >Om du vill skicka alla korrektur för direktmeddelanden till samma X-konto kan du spara korrekturmålet i **[!UICONTROL Tweet (Direct Message)]** leveransmall, via **[!UICONTROL Resources > Templates > Delivery templates]** nod.

1. Ange innehållet i meddelandet i **[!UICONTROL Content]** -fliken.

   ![](assets/tw-dm-content.png)

   Anpassningsfält kan användas på samma sätt som för e-postleveranser, t.ex. för att lägga till följarens namn i meddelandets brödtext. Läs mer i [det här avsnittet](../send/personalize.md).

1. Förhandsgranska meddelandet

   Sök i **[!UICONTROL Preview]** för att kontrollera återgivningen av inlägget.

   ![](assets/tw-dm-preview.png)

   1. Klicka på **[!UICONTROL Preview]** -fliken.
   1. Klicka på **[!UICONTROL Test personalization]** nedrullningsbar meny och välj **[!UICONTROL Visitor Subscription]**.
   1. Välj ett X-konto som du vill testa förhandsvisningen med.

1. Skicka en korrektur

   Innan du skickar meddelandet måste du verifiera det av [skicka ett bevis till ett testkonto](../send/preview-and-proof.md): du kan sedan få en exakt återgivning av meddelandet på ett privat X-konto och kontrollera innehåll och personalisering.

1. Skicka direktmeddelandet

   1. När innehållet är godkänt klickar du på **[!UICONTROL Send]** -knappen.
   1. Välj **[!UICONTROL Deliver as soon as possible]** och klicka på **[!UICONTROL Analyze]** -knappen.
   1. Kontrollera resultatet när analysen är klar.
   1. Klicka **[!UICONTROL Confirm delivery]** och sedan klicka **[!UICONTROL Yes]**.

>[!CAUTION]
>
>Du kan inte skicka mer än 250 direktmeddelanden per dag. För att undvika att detta tröskelvärde överskrids kan du leverera i vågor. Mer information finns i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves){target="_blank"}.


## Åtkomstspårningsdata {#tw-tracking}

I den inbyggda **[!UICONTROL Tweet]** leveransmall, spårning är aktiverat som standard.

Spåra data kan visas i leveransrapporterna och i **[!UICONTROL Edit > Tracking]** fliken för leveransen och tjänsten.

Spårningskonfigurationen är densamma som för en e-postleverans. Läs mer i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html){target="_blank"}.

