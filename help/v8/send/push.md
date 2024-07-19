---
title: Skicka push-meddelanden med Adobe Campaign
description: Kom igång med push-meddelanden i Campaign
feature: Push
role: User
level: Beginner
exl-id: f04c6e0c-f2b9-496a-9697-04ef4c3411ee
source-git-commit: 48aba38f3dc8bb322e6d0b38c1b743e980671cd7
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 4%

---

# Skapa och skicka push-meddelanden{#push-notifications-create}

Med mobilappsleveranser kan du skicka meddelanden till iOS- och Android-enheter.

Innan du börjar skicka push-meddelanden med Adobe Campaign måste du se till att det finns konfigurationer och integreringar på mobilappen och för taggar i Adobe Experience Platform. [Läs mer om push-konfiguration.](push-settings.md).

>[!CAUTION]
>
>Viktiga ändringar av tjänsten Android Firebase Cloud Messaging (FCM) släpps under 2024, vilket kan påverka implementeringen av Adobe Campaign. Konfigurationen för prenumerationstjänster för push-meddelanden för Android kan behöva uppdateras för att den här ändringen ska fungera. Du kan redan kontrollera och vidta åtgärder. [Läs mer](../../technotes/upgrades/push-technote.md).


## Skapa ditt första push-meddelande {#push-create}

I det här avsnittet beskrivs de element som är specifika för leveransen av iOS- och Android-meddelanden.

>[!IMPORTANT]
>
>I samband med en [Enterprise (FFDA)-distribution](../architecture/enterprise-deployment.md) är mobilregistreringen nu **asynkron**. [Läs mer](../architecture/staging.md)


Om du vill skapa en ny leverans går du till fliken **[!UICONTROL Campaigns]**, klickar på **[!UICONTROL Deliveries]** och klickar på knappen **[!UICONTROL Create]** ovanför listan med befintliga leveranser.

![](assets/delivery_step_1.png)


Som standard har Adobe Campaign två leveransmallar: en för iOS och en för Android. Du kan duplicera dem för att definiera egna inställningar. Stegen för att konfigurera en push-leverans baserat på dessa mallar beskrivs nedan.

>[!BEGINTABS]

>[!TAB iOS]

Så här skickar du meddelanden till iOS-enheter:

1. Välj leveransmallen **[!UICONTROL Deliver on iOS]**.

   ![](assets/push_ios_1.png)

1. Om du vill definiera målet för meddelandet klickar du på länken **[!UICONTROL To]** och sedan på **[!UICONTROL Add]**.

   ![](assets/push_ios_2.png)

1. Välj **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, välj den tjänst som är relevant för ditt mobilprogram och välj sedan iOS-versionen av programmet.

   ![](assets/push_ios_3.png)

1. Välj **[!UICONTROL Notification type]** mellan **[!UICONTROL General notification (Alert, Sound, Badge)]** eller **[!UICONTROL Silent notification]**.

   ![](assets/push_ios_4.png)

   >[!NOTE]
   >
   >I läget **Tyst överföring** kan ett tyst meddelande skickas till ett mobilprogram. Användaren har inte informerats om meddelandets ankomst. Den överförs direkt till programmet.

1. I fältet **[!UICONTROL Title]** anger du etiketten för titeln som du vill ska visas i listan med meddelanden som är tillgängliga från meddelandecentret.

   I det här fältet kan du definiera värdet för parametern **title** i iOS-meddelandenyttolasten.

1. Du kan lägga till **[!UICONTROL Subtitle]**, värdet för parametern **subtitle** i iOS-meddelandenyttolasten.

1. Ange innehållet i meddelandet i avsnittet **[!UICONTROL Message content]** i guiden.

1. På fliken **[!UICONTROL Sound and Badge]** kan du redigera följande alternativ:

   * **[!UICONTROL Clean Badge]**: aktivera de här alternativen för att uppdatera badge-värdet.

   * **[!UICONTROL Value]**: ange ett tal som ska användas för att visa antalet nya olästa uppgifter direkt på programikonen.

   * **[!UICONTROL Critical alert mode]**: aktivera det här alternativet om du vill lägga till ljud i meddelandet även om användarens telefon är inställd på fokusläge eller om iPhone är avstängt.

   * **[!UICONTROL Name]**: välj ljudet som ska spelas upp av mobilterminalen när meddelandet tas emot.

   * **[!UICONTROL Volume]**: ljudvolym från 0 till 100.

     >[!NOTE]
     > 
     >Ljud måste inkluderas i programmet och definieras när tjänsten skapas.
     >

   ![](assets/push_ios_5.png)

1. **[!UICONTROL Application variables]** läggs automatiskt till på fliken **[!UICONTROL Application variables]**. De gör att du kan definiera meddelandebeteende, till exempel kan du konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. På fliken **[!UICONTROL Advanced]** kan du redigera följande allmänna alternativ:

   * **[!UICONTROL Mutable content]**: aktivera det här alternativet om du vill tillåta mobilprogrammet att hämta medieinnehåll.

   * **[!UICONTROL Thread-id]**: Identifierare som används för att gruppera relaterade meddelanden tillsammans.

   * **[!UICONTROL Category]**: namnet på ditt kategori-ID som kommer att visa åtgärdsknappar. Dessa meddelanden ger användaren ett snabbare sätt att utföra olika åtgärder som svar på ett meddelande utan att öppna eller navigera i programmet.

   ![](assets/push_ios_6.png)

1. För tidskänsliga meddelanden kan du ange följande alternativ:

   * **[!UICONTROL Target content ID]**: Identifierare som används för att ange vilket programfönster som ska flyttas fram när meddelandet öppnas.

   * **[!UICONTROL Launch image]**: namnet på startbildfilen som ska visas. Om användaren väljer att starta programmet visas den valda bilden i stället för programmets startskärm.

   * **[!UICONTROL Interruption level]**:

      * **[!UICONTROL Active]**: Som standard visas meddelandet omedelbart, skärmen visas och ett ljud kan spelas upp. Meddelanden går inte igenom fokusläget.

      * **[!UICONTROL Passive]**: Systemet lägger till meddelandet i meddelandelistan utan att skärmen eller ett ljud spelas upp. Meddelanden går inte igenom fokusläget.

      * **[!UICONTROL Time sensitive]** Systemet presenterar meddelandet omedelbart, lyser upp skärmen, kan spela upp ett ljud och gå igenom fokus-lägen. Den här nivån kräver inget särskilt tillstånd från Apple.

      * **[!UICONTROL Critical]** Systemet visar meddelandet omedelbart, lyser upp skärmen och kringgår avstängningsväxeln eller fokusläget. Observera att den här nivån kräver ett särskilt tillstånd från Apple.

   * **[!UICONTROL Relevance score]**: Ange ett relevansvärde mellan 0 och 100. Systemet använder detta för att sortera meddelandena i meddelandesammanfattningen.

   ![](assets/push_ios_7.png)

1. När meddelandet har konfigurerats klickar du på fliken **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/push-ios-preview.png)


>[!TAB Android]

Så här skickar du meddelanden till Android-enheter:

1. Välj leveransmallen **[!UICONTROL Deliver on Android (android)]**.

   ![](assets/push-template-android.png)

   >[!NOTE]
   > 
   >Med de senaste FCM API:erna (HTTP v1) måste du uppdatera dina **leveransmallar** för Android push-meddelanden för att öka antalet batchmeddelanden. Det gör du genom att bläddra till egenskaperna för din Android-leveransmall och ange [Antal meddelandebatchar](../../v8/send/configure-and-send.md#delivery-batch-quantity) till **256** på fliken **Leverans**. Använd ändringen på alla leveransmallar som används för dina Android-leveranser och på alla befintliga Android-leveranser.


1. Om du vill definiera målet för meddelandet klickar du på länken **[!UICONTROL To]** och sedan på **[!UICONTROL Add]**.

   ![](assets/push-android-select-target.png)

1. Välj **[!UICONTROL Subscribers of an Android mobile application]**, välj den tjänst som är relevant för ditt mobilprogram (Neotrips, i det här fallet) och välj sedan Android-versionen av programmet.

   ![](assets/push-android-subscribers.png)

1. Ange sedan innehållet för meddelandet.

   ![](assets/push-android-content.png)

1. Klicka på ikonen **[!UICONTROL Insert emoticon]** om du vill infoga uttryckssymboler i push-meddelandet.

1. Ange värdet för varje variabel i fältet **[!UICONTROL Application variables]**. Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

1. När meddelandet har konfigurerats klickar du på fliken **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   <!--![](assets/push-android-preview.png)-->

>[!ENDTABS]


## Testa, skicka och övervaka dina push-meddelanden {#push-test}

Använd samma process som för andra leveranser när du vill skicka ett korrektur och den slutliga leveransen.

Lär dig hur du validerar en leverans på [den här sidan](preview-and-proof.md).

Lär dig hur du bekräftar och skickar leveransen på [den här sidan](send.md)

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Läs mer om orsaker till leveransfel i push-meddelanden på [den här sidan](delivery-failures.md#push-error-types).

