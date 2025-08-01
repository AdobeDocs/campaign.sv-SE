---
title: SMS i en infrastruktur med flera leverantörer
description: Lär dig hur du konfigurerar en SMS-leverans i en infrastruktur med flera leverantörer
feature: SMS
role: User
level: Beginner, Intermediate
exl-id: b5eb9eaa-0ca8-478c-9ed5-e5006e9b5609
source-git-commit: ea51863bdbc22489af35b2b3c81259b327380be4
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# SMS i en infrastruktur med flera leverantörer {#sms-mid}

>[!AVAILABILITY]
>
>Den här funktionen är tillgänglig för alla Campaign FDA-miljöer. Det är **inte** tillgängligt för Campaign FFDA-distributioner. Denna dokumentation gäller Adobe Campaign v8.7.2 och senare. Om du vill växla från den gamla till den nya SMS-anslutningen läser du i den här [technote](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/sms-migration){target="_blank"}
>
>Om du har äldre versioner kan du läsa [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/sv/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up/sms-set-up){target="_blank"}.

För att skicka SMS-leveranser med en infrastruktur för medelhög källkod krävs:

1. En SMS-operator på Mid-servern. [Lär dig skapa här](#sms-operator-mid)
1. Ett externt SMS-konto på marknadsföringsservern som kommer att använda den tidigare skapade operatorn. [Lär dig skapa här](#sms-external-account)
1. Ett externt SMPP-konto på MID-servern som anger leveransläget för kanal och mellanleverantörer. [Lär dig skapa här](#smpp-external-account-mid)
1. En leveransmall som refererar till det externa kontot för att effektivisera sändningsprocessen. [Lär dig skapa här](#sms-delivery-template)

## Skapa SMS-operatorn på Mid-servern {#sms-operator-mid}

Först måste du skapa en SMS-operator på mellanservern som ska användas av det externa SMS-kontot på marknadsföringsservern.

Följ stegen nedan för att skapa en SMS-operator:

1. I **[!UICONTROL Administration]** > **[!UICONTROL Access management]** > **[!UICONTROL Operators]** klickar du på **[!UICONTROL New]** och fyller i formuläret i det nya fönstret som öppnas.

   * **[!UICONTROL Name (login)]** och **[!UICONTROL Label]** är obligatoriska.
   * Lösenord är inte obligatoriskt men rekommenderas av säkerhetsskäl.

   Observera att namnet (inloggningen) ska användas senare för att namnge ditt SMPP-externa konto på Mid-servern.

   ![](assets/smsoperator_mid.png){zoomable="yes"}

1. Klicka på knappen **[!UICONTROL Groups and named rights]** i delen **[!UICONTROL Add]**.
I det nya fönstret som öppnas väljer du **[!UICONTROL Named rights]** i listan **[!UICONTROL Folder]** och väljer **[!UICONTROL ADMINISTRATION]** i den högra listan.

1. Klicka på knappen **[!UICONTROL Ok]**.

   ![](assets/smsoperator_rights.png){zoomable="yes"}

1. Klicka på knappen **[!UICONTROL Save]** för att slutföra skapandet av SMS-operatorn.

   ![](assets/smsoperator_save.png){zoomable="yes"}

Nu kan du se det i operatorlistan.

![](assets/smsoperator_list.png){zoomable="yes"}

## Skapa ett externt SMS-konto på marknadsföringsservern {#sms-external-account}

I en medelhög infrastruktur måste du skapa ett externt SMS-konto på marknadsföringsservern enligt nedan

>[!IMPORTANT]
>
>Om du använder samma konto och lösenord för flera externa SMS-konton kan det leda till konflikter och överlappning mellan kontona. Läs mer på [SMS-felsökningssidan](smpp-connection.md#sms-troubleshooting).

1. Klicka på ikonen **[!UICONTROL Administration]** i **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** > **[!UICONTROL New]**

   ![](assets/sms_extaccount.png){zoomable="yes"}

1. Konfigurera **[!UICONTROL Label]** och **[!UICONTROL Internal name]** för ditt externa konto. Definiera kontotypen som **[!UICONTROL Routing]**, markera kryssrutan **[!UICONTROL Enabled]**, välj **[!UICONTROL Mobile (SMS)]** för kanalen och **[!UICONTROL Mid-sourcing]** som leveransläge.

   ![](assets/mid_smsextaccount.png){zoomable="yes"}

1. På fliken **[!UICONTROL Mid-sourcing]** fyller du i formuläret med URL:en för mellankällservern och SMS-operatorn som tidigare skapats på mittservern.

   Bekräfta anslutningen genom att klicka på knappen **[!UICONTROL Test the connection]**.

   ![](assets/midtab_smsextaccount.png){zoomable="yes"}

1. Klicka på **[!UICONTROL Save]**.

## Skapa ett externt SMPP-konto på Mid-servern {#smpp-external-account-mid}

>[!IMPORTANT]
>
>Om du använder samma konto och lösenord för flera externa SMS-konton kan det leda till konflikter och överlappning mellan kontona. Se sidan [SMS-felsökning](smpp-connection.md#sms-troubleshooting).

Målet är nu att skapa ett externt SMPP-konto på Mid-servern.

Gör så här:

1. Klicka på ikonen **[!UICONTROL Administration]** i **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** > **[!UICONTROL New]** på mittservern

1. Konfigurera **[!UICONTROL Label]** och **[!UICONTROL Internal name]** för ditt externa konto.

   >[!WARNING]
   >
   >När du tilldelar ett internt namn måste du följa den angivna namnkonventionen: `SMS Operator Name_Internal Name of the Marketing SMS external account`.
   >

   Definiera kontotypen som **[!UICONTROL Routing]**, markera kryssrutan **[!UICONTROL Enabled]**, välj **[!UICONTROL Mobile (SMS)]** för kanalen och **[!UICONTROL Bulk delivery]** som leveransläge.
   ![](assets/mid_extaccount.png){zoomable="yes"}

1. På fliken **[!UICONTROL Mobile]** håller du **[!UICONTROL Extended generic SMPP]** i listrutan **[!UICONTROL Connector]**.

   Rutan **[!UICONTROL Send messages through a dedicated process]** är markerad som standard.

   ![](assets/sms_extaccount_connector.png){zoomable="yes"}

   Om du vill upprätta anslutningen måste du fylla i flikarna i det här formuläret. Mer information finns i [läs mer om det externa SMPP-kontot](smpp-external-account.md#smpp-connection-settings).

## Konfigurera leveransmallen {#sms-delivery-template}

Skapa en SMS-leveransmall där alla inställningar refereras för att underlätta skapandet av din SMS-leverans.

Högerklicka på den befintliga mallen för mobil leverans i **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** på marknadsföringsservern och välj **[!UICONTROL Duplicate]**.

![](assets/sms_template_duplicate.png){zoomable="yes"}

Ändra **[!UICONTROL Label]** och **[!UICONTROL Internal name]** för mallen så att den lätt känns igen och klicka på knappen **[!UICONTROL Properties]**.

![](assets/sms_template_name.png){zoomable="yes"}

På fliken **[!UICONTROL General]** i **[!UICONTROL Routing]** väljer du ett externt SMPP-konto.

![](assets/mid_template.png){zoomable="yes"}

På fliken **[!UICONTROL SMS]** kan du lägga till valfria parametrar i mallen.

![](assets/sms_template_properties.png){zoomable="yes"}

[Läs mer om konfigurationen för SMS-fliken](sms-delivery-settings.md).
