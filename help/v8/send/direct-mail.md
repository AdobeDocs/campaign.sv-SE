---
title: Skicka direktreklam med Adobe Campaign
description: Kom igång med direktreklam i Campaign
feature: Direct Mail
role: User
level: Beginner
version: Campaign v8, Campaign Classic v7
exl-id: ff2be012-72f3-428d-a973-196fea7ec4ab
source-git-commit: 110a2cac920ca3087f6fcb3cab8474729f6075be
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 4%

---

# Skapa direktutskicksleveranser

Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen. Du kan sedan dela den här filen med leverantören som levererar meddelanden till målpopulationerna.

Steg för att generera filen är:

1. [Skapa leveransen](#creating-a-direct-mail-delivery)
1. [Definiera målgruppen](#defining-the-direct-mail-audience)
1. [Definiera filens innehåll](#defining-the-direct-mail-content)
1. [Validera leveransen](#validating)
1. [Påbörja leveransen](#start-delivery)

## Skapa leveransen{#creating-a-direct-mail-delivery}

Skapa en direktutskick baserat på mallen. Du kan duplicera och konfigurera den inbyggda mallen **[!UICONTROL Deliver by direct mail (paper)]**.

Så här skapar du en ny direktutskick:

>[!NOTE]
>
>Globala koncept för leveransskapande presenteras i [det här avsnittet](../start/create-message.md).

1. Skapa en ny leverans, till exempel från kontrollpanelen Leverans.
1. Välj leveransmallen **Leverera via direktreklam (papper)**.

   ![](assets/direct_mail.png)

1. Identifiera leveransen med en etikett, kod och beskrivning. Mer information om detta finns i [det här avsnittet](../start/create-message.md#create-the-delivery).
1. Klicka på **Fortsätt** för att bekräfta den här informationen och visa meddelandekonfigurationsfönstret.

## Definiera målgruppen{#defining-the-direct-mail-audience}

Mottagarprofilerna måste innehålla minst namn och postadresser.

Postadresser är beräkningsfält. En adress kan som standard innehålla upp till sex rader: den första innehåller förnamnet och efternamnet, de följande raderna innehåller postadressen (väg osv.) och den sista raden innehåller postnumret och ort eller stad. Definitionen av standardfältet för beräknad postadress kan granskas i nms:recipient-schemat.

En adress anses vara fullständig om fälten för namn, postnummer och ort inte är tomma. Mottagare med ofullständiga adresser utesluts från direktutskick.

Läs mer i [det här avsnittet](../start/create-message.md#target-population).

## Definiera filens innehåll{#defining-the-direct-mail-content}

Använd extraheringsguiden för att definiera informationen (kolumnerna) som ska exporteras till utdatafilen.

Namnet på filen som innehåller extraherade data definieras i fältet **[!UICONTROL File]**. Med knappen till höger om fältet kan du använda anpassningsfält för att skapa filnamnet.

Som standard skapas extraheringsfilen och lagras på servern. Du kan spara den på datorn. Kontrollera **[!UICONTROL Download the generated file after the analysis of the delivery]** om du vill göra det. I det här fallet måste du ange åtkomstsökvägen till den lokala lagringskatalogen samt filnamnet.

![](assets/s_ncs_user_mail_delivery_local_file.png)

För direktutskick definieras innehållet i extraheringen i länken **[!UICONTROL Edit the extraction file format...]**.

![](assets/s_ncs_user_mail_delivery_format_link.png)

Med den här länken kan du komma åt extraheringsassistenten och definiera den information (kolumner) som ska exporteras till utdatafilen.

![](assets/s_ncs_user_mail_delivery_format_wz.png)

Du kan infoga en anpassad URL i extraheringsfilen. Mer information finns i Adobe Campaign Classic [dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/publishing-a-web-form.html?lang=sv-SE){target="_blank"}.

>[!NOTE]
>
>Den här assistenten innehåller de steg i exportassistenten som beskrivs i Adobe Campaign Classic [dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/generic-imports-exports/executing-export-jobs.html?lang=sv-SE){target="_blank"}.

## Validera leveransen{#validating}

Kontrollera resultatet av analysen och innehållet i utdatafilen.

Extraheringsfilen skapas i samband med en marknadsföringskampanj på extraheringsdatumet. Du kan visa innehållet i den extraherade filen, godkänna den eller ändra formatet och starta extraheringen igen om det behövs. När filen har godkänts kan du skicka e-postmeddelandet till routern. Läs mer på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html?lang=sv-SE){target="_blank"}.

Globala koncept vid validering av en leverans visas i [det här avsnittet](../start/create-message.md#validate-the-delivery).

Utdatafilen för en direktpostleverans genereras under leveransanalysen. Filens innehåll beror på de markerade utdatakolumnerna (se den här [avsnittsfilen](#defining-the-direct-mail-content)).

>[!NOTE]
>
>Analysfasen beskrivs i det här [avsnittet](delivery-analysis.md).

Under analysfasen genereras filen, men informationen om mottagarna (dvs. leveransloggar) uppdateras inte. Du kan därför avbryta det här jobbet utan att köra några risker.

Kontrollera resultatet av analysen och innehållet i utdatafilen innan du klickar på **[!UICONTROL Confirm delivery]**. Med ett bekräftelsemeddelande kan du starta leveransen.

Skicka-bekräftelsen startar dataextraheringen i den angivna filen.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Du kan sedan stänga assistenten och titta på leveransloggarna via fliken **[!UICONTROL Delivery]** som du kommer åt via leveransinformationen.

Du kan konfigurera hämtningsläget för leveransloggar på fliken **[!UICONTROL Analysis]** i leveransegenskaperna.

Det finns två lägen:

* **[!UICONTROL Messages are considered sent after validation]** (standardläge): i det här funktionsläget uppdateras alla utsändningsloggar när operatorn bekräftar sändningen (deras status går från Väntande leverans till Skickat) och leveransen ställs automatiskt in på **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : I det här läget kan du uppdatera utsändningsloggarna via en extern fil som skickas av tjänsteleverantören. I det här fallet måste ett arbetsflöde för att bearbeta informationen användas för att uppdatera sändningsstatusen.

  >[!NOTE]
  >
  >I det här fallet måste leveransens status också ändras till **[!UICONTROL Finished]** av användaren så snart som utsändningsloggarna uppdateras.

## Påbörja leveransen{#start-delivery}

När du har validerat extraheringsfilen klickar du på **Bekräfta leverans** så att du kan starta leveransen.

Bekräftelsen startar dataextraheringen i den angivna filen.

När alla godkännanden har beviljats inom ramen för en marknadsföringskampanj skapas extraheringsfilerna via ett särskilt arbetsflöde som, i en standardkonfiguration, startar automatiskt när en direktleverans väntar på extrahering. Läs mer i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html?lang=sv-SE){target="_blank"}.
