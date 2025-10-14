---
product: campaign
title: SpamAssassin
description: Lär dig hur du konfigurerar identifiering av skräppost med SpamAssets
feature: Email, Deliverability
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: 96f1518f252be7ffa27ba8157b8a090bf4d4510d
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# SpamAssassin{#spamassassin}

Adobe Campaign kan konfigureras för att fungera med [SpamAssets](https://spamassassin.apache.org){target="_blank"}, en tredjepartstjänst som används för skräppostfiltrering. På så sätt kan du poängsätta e-postmeddelanden för att avgöra om ett meddelande löper risk att betraktas som skräppost av de antispam-verktyg som används vid mottagande.

SpamAssassin utnyttjar en mängd olika tekniker för skräppostavkänning, bland annat:

* DNS-baserad och otydlig kontrollsummebaserad skräppostavkänning
* Bayesisk filtrering
* Externa program
* Blockeringslista
* Online-databaser

>[!NOTE]
>
>SpamAssassin måste installeras och konfigureras på Adobe Campaign programserver. Kontakta Adobe om du vill ha mer information.
>
>Reglerna som styr om ett element är spam eller inte hanteras via SpamAssets och kan redigeras av en administratör med behörighet.

## Använd SpamAssassin i Campaign {#using-spamassassin}

När du har skapat din e-postleverans och definierat innehållet följer du stegen nedan för att utvärdera riskerna.

Mer information om hur du skapar och utformar en leverans finns på [sidan](defining-the-email-content.md).


1. Gå till fliken **[!UICONTROL Preview]**.
1. Välj en mottagare om du vill förhandsgranska leveransen.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Om du inte väljer någon mottagare kan skräppostkontrollen inte utföras.

1. Ett varningsmeddelande ger resultatet av testet. Om en hög risknivå upptäcks visas följande varningsmeddelande:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Klicka på länken **[!UICONTROL More...]** bredvid varningen.
1. Klicka på fliken **[!UICONTROL Anti-spam checking]**.  
1. Gå till avsnittet **[!UICONTROL Points / Rule / Description]** om du vill visa orsaken till den här risken.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Varje gång du klickar på **[!UICONTROL Anti-spam checking]** anropas SpamAssassin-tjänsten och meddelandet analyseras igen för att identifiera skräppostskydd. Kontrollera att du har ändrat innehållet innan du kör skräppostanalysen igen.
