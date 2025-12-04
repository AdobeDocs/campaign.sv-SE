---
title: Konfigurera spårade länkar
description: Lär dig konfigurera spårade länkar i leveranser
feature: Monitoring
role: User, Developer
level: Beginner
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: 5b23be4cb8f0896d2482e525e416713b1a6c4514
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 6%

---

# Konfigurera spårade länkar {#how-to-configure-tracked-links}

För varje leverans kan du spåra mottagningen av meddelanden och aktiveringen av länkarna som har infogats i meddelandets innehåll. På så sätt kan du spåra mottagarnas beteende beroende på de leveransåtgärder de har fått som mål.

>[!NOTE]
>
>Länkarna i e-postinnehåll som innehåller personalisering måste spåras med specifik syntax. Läs mer om hur du lägger till länkar i e-postmeddelanden som kan personaliseras och som stöder spårning i [det här avsnittet](personalized-links.md).

Spårning av meddelanden är aktiverat som standard. Följ stegen nedan för att anpassa hur URL-adresser spåras:

1. Välj alternativet **[!UICONTROL Display URLs]** i den nedre delen av leveransassistenten, under meddelandeinnehållet.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   När du väljer en URL i listan med spårade URL:er markeras den i leveransinnehållet, med undantag för länken på speglingssidan och den länk för att avbryta prenumerationen som anges som standard.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. För varje URL för meddelandet väljer du om spårning ska aktiveras eller inte.

   >[!IMPORTANT]
   >
   >När länkens URL används som etikett bör du inaktivera spårning för att undvika risken för avvisning på grund av nätfiske.
   >
   >Om till exempel www.adobe.com URL infogas i meddelandet och spårning aktiveras på det, ändras innehållet i hypertextlänken till https://nlt.adobe.net/r/?id=xxxxxx. Det innebär att det kan anses vara bedrägligt av mottagare som skickar meddelanden.

1. Ändra spårningsetiketten om det behövs, dubbelklicka på etiketten och ange en ny.

   >[!NOTE]
   >
   >Etiketterna för de spårade URL-adresserna och etiketterna kan ändras för att förenkla läsningen av information vid spårning av leveranser. Två URL-adresser eller två etiketter med samma namn läggs ihop när antalet klickningar beräknas.

1. Om det behövs kan du ändra spårningsläget och välja ett nytt läge i kolumnen **[!UICONTROL Tracking]** som matchar mållänken, vilket visas nedan:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   För varje enskild URL kan du ange spårningsläget till något av följande värden:

   * **[!UICONTROL Enabled]**: aktiverar spårning på den här URL:en.
   * **[!UICONTROL Not tracked]**: inaktiverar spårning på den här URL:en.
   * **[!UICONTROL Always enabled]**: aktiverar alltid spårning av den här URL:en. Den här informationen sparas så att spårningen aktiveras nästa gång URL:en visas igen i ett framtida meddelandeinnehåll.
   * **[!UICONTROL Never tracked]**: aktiverar aldrig spårning av den här URL:en. Den här informationen sparas så att spårningen inaktiveras nästa gång URL:en visas igen i ett framtida meddelande.
   * **[!UICONTROL Opt-out]**: betraktar den här URL:en som en avanmälnings- eller avanmälnings-URL.
   * **[!UICONTROL Mirror page]**: anser att den här URL:en är en URL för en spegelsida.

1. Du kan dessutom välja en kategori för varje spårad URL i den nedrullningsbara listan i kolumnen **[!UICONTROL Category]**. Dessa kategorier kan visas i rapporter, till exempel i rapporten **[!UICONTROL URLs and click streams]** (se [det här avsnittet](../reporting/delivery-reports.md#urls-and-click-streams)). Kategorierna definieras i en specifik uppräkning: **[!UICONTROL urlCategory]**. Läs mer om hur du arbetar med uppräkningar i [det här avsnittet](../config/enumerations.md).

## Bästa tillvägagångssätt för URL-avgränsare {#url-delimiters}

Vi rekommenderar att du omsluter URL:er i avgränsare på fliken **[!UICONTROL Text content]** innan du använder spårningsformeln. De URL-avgränsare som du anger på den här fliken används av Adobe Campaign för att identifiera URL:er i teckensträngar. Du kan använda dessa par med avgränsare:

* Parenteser ( )
* Hakparenteser [ ]
* Klammerparenteser {}

I det här exemplet följs URL:en https://www.adobe.com av ett semikolon. Semikolon kan tolkas av mottagarens e-postklienter som en del av URL:en. Därför kan länken brytas. För att undvika det här problemet kan du omge URL-adressen i avgränsare på något av följande sätt:

* (https://www.adobe.com);
* [https://www.adobe.com];
* {https://www.adobe.com};
