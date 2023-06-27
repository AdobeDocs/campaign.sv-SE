---
title: Skicka push-meddelanden med Adobe Campaign
description: Kom igång med push-meddelanden i Campaign
feature: Push
role: Data Engineer
level: Beginner
exl-id: f04c6e0c-f2b9-496a-9697-04ef4c3411ee
source-git-commit: d941d9a364ffb2df77ba6726e655ca2916448f89
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 3%

---

# Skapa och skicka push-meddelanden{#push-notifications-create}

Med mobilappsleveranser kan du skicka meddelanden till iOS- och Android-enheter.

Innan du börjar skicka push-meddelanden med Adobe Campaign måste du se till att det finns konfigurationer och integreringar på mobilappen och för taggar i Adobe Experience Platform. [Läs mer om push-konfiguration.](push-settings.md)

## Skapa ditt första push-meddelande{#push-create}

I det här avsnittet beskrivs de element som är specifika för leveransen av iOS- och Android-meddelanden.

>[!CAUTION]
>
>När det gäller [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), mobilregistrering är nu **asynkron**. [Läs mer](../architecture/staging.md)

Bläddra till **[!UICONTROL Campaigns]** flik, klicka **[!UICONTROL Deliveries]** och klicka på **[!UICONTROL Create]** ovanför listan över befintliga leveranser.

![](assets/delivery_step_1.png)

>[!BEGINTABS]

>[!TAB iOS]

Så här skickar du meddelanden till iOS-enheter:

1. Välj **[!UICONTROL Deliver on iOS]** leveransmall.

   ![](assets/push_ios_1.png)

1. Om du vill definiera målet för meddelandet klickar du på knappen **[!UICONTROL To]** klicka på **[!UICONTROL Add]**.

   ![](assets/push_ios_2.png)

1. Välj **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, väljer den tjänst som är relevant för ditt mobilprogram och väljer sedan iOS-versionen av programmet.

   ![](assets/push_ios_3.png)

1. Välj **[!UICONTROL Notification type]** mellan **[!UICONTROL General notification (Alert, Sound, Badge)]** eller **[!UICONTROL Silent notification]**.

   ![](assets/push_ios_4.png)

   >[!NOTE]
   >
   >The **Tyst push** I läget kan ett tyst meddelande skickas till ett mobilprogram. Användaren har inte informerats om meddelandets ankomst. Den överförs direkt till programmet.

1. I **[!UICONTROL Title]** anger du etiketten för den titel som du vill ska visas i listan med meddelanden som är tillgängliga från meddelandecentret.

   I det här fältet kan du definiera värdet för **title** -parametern för iOS-meddelandenyttolasten.

1. Du kan lägga till en **[!UICONTROL Subtitle]**, värdet för **underrubrik** -parametern för iOS-meddelandenyttolasten.

1. Ange innehållet i meddelandet i **[!UICONTROL Message content]** i guiden.

1. Från **[!UICONTROL Sound and Badge]** kan du redigera följande alternativ:

   * **[!UICONTROL Clean Badge]**: aktivera det här alternativet för att uppdatera badge-värdet.

   * **[!UICONTROL Value]**: Ange ett tal som ska användas för att visa antalet nya olästa uppgifter direkt på programikonen.

   * **[!UICONTROL Critical alert mode]**: aktivera det här alternativet för att lägga till ljud i meddelandet även om användarens telefon är inställd på fokusläge eller om iPhone är avstängt.

   * **[!UICONTROL Name]**: Välj det ljud som ska spelas upp av mobilterminalen när meddelandet tas emot.

   * **[!UICONTROL Volume]**: ljudvolymen från 0 till 100.

     >[!NOTE]
     > 
     >Ljud måste inkluderas i programmet och definieras när tjänsten skapas.
     >

   ![](assets/push_ios_5.png)

1. Från **[!UICONTROL Application variables]** -fliken, **[!UICONTROL Application variables]** läggs till automatiskt. De gör att du kan definiera meddelandebeteende, till exempel kan du konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. Från **[!UICONTROL Advanced]** kan du redigera följande allmänna alternativ:

   * **[!UICONTROL Mutable content]**: aktivera det här alternativet om du vill tillåta att mobilprogrammet hämtar medieinnehåll.

   * **[!UICONTROL Thread-id]**: identifierare som används för att gruppera relaterade meddelanden tillsammans.

   * **[!UICONTROL Category]**: namnet på ditt kategori-ID som kommer att visa åtgärdsknappar. Dessa meddelanden ger användaren ett snabbare sätt att utföra olika åtgärder som svar på ett meddelande utan att öppna eller navigera i programmet.

   ![](assets/push_ios_6.png)

1. För tidskänsliga meddelanden kan du ange följande alternativ:

   * **[!UICONTROL Target content ID]**: Identifierare som används för att ange vilket programfönster som ska flyttas fram när meddelandet öppnas.

   * **[!UICONTROL Launch image]**: namnet på startbildfilen som ska visas. Om användaren väljer att starta programmet visas den valda bilden i stället för programmets startskärm.

   * **[!UICONTROL Interruption level]**:

      * **[!UICONTROL Active]**: Som standard visas meddelandet omedelbart, skärmen visas och ett ljud kan spelas upp. Meddelanden går inte igenom fokusläget.

      * **[!UICONTROL Passive]**: Systemet lägger till meddelandet i meddelandelistan utan att skärmen eller ljudet ljussätts upp. Meddelanden går inte igenom fokusläget.

      * **[!UICONTROL Time sensitive]** Systemet visar meddelandet omedelbart, lyser upp skärmen, kan spela upp ett ljud och gå igenom fokus-lägen. Den här nivån kräver inget särskilt tillstånd från Apple.

      * **[!UICONTROL Critical]** Systemet visar meddelandet omedelbart, lyser upp skärmen och kringgår avstängningsväxeln eller fokusläget. Observera att den här nivån kräver ett särskilt tillstånd från Apple.

   * **[!UICONTROL Relevance score]**: Ange ett relevansvärde mellan 0 och 100. Systemet använder detta för att sortera meddelandena i meddelandesammanfattningen.

   ![](assets/push_ios_7.png)

1. När meddelandet har konfigurerats klickar du på **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/push-ios-preview.png)


>[!TAB Android]

Så här skickar du meddelanden på Android-enheter:

1. Välj **[!UICONTROL Deliver on Android (android)]** leveransmall.

   ![](assets/push-template-android.png)

1. Om du vill definiera målet för meddelandet klickar du på knappen **[!UICONTROL To]** klicka på **[!UICONTROL Add]**.

   ![](assets/push-android-select-target.png)

1. Välj **[!UICONTROL Subscribers of an Android mobile application]** väljer du den tjänst som är relevant för ditt mobilprogram (i det här fallet Neotrips) och väljer sedan Android-versionen av programmet.

   ![](assets/push-android-subscribers.png)

1. Ange sedan innehållet för meddelandet.

   ![](assets/push-android-content.png)

1. Klicka på **[!UICONTROL Insert emoticon]** om du vill infoga uttryckssymboler i ditt push-meddelande.

1. I **[!UICONTROL Application variables]** anger du värdet för varje variabel. Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. När meddelandet har konfigurerats klickar du på **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   <!--![](assets/push-android-preview.png)-->

>[!ENDTABS]

## Testa, skicka och övervaka dina push-meddelanden

Använd samma process som för andra leveranser när du vill skicka ett korrektur och den slutliga leveransen.

Lär dig hur du validerar en leverans i [den här sidan](preview-and-proof.md).

Lär dig hur du bekräftar och skickar leveransen i [den här sidan](send.md)

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Läs mer om orsaker till leveransfel vid push-meddelanden i [den här sidan](delivery-failures.md#push-error-types).

