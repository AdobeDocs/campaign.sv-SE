---
solution: Campaign v8
product: Adobe Campaign
title: Hantera prenumerationer och avbeställningar i Campaign
description: Lär dig hur du hanterar prenumerationer och avbeställningar i Campaign v8
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: ab7e458db5ad5696d144c17f6e89e4437a476d11
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Hantera prenumerationer och avbeställningar{#optin-optout}

Använd Adobe Campaign för att skapa och övervaka informationstjänster som nyhetsbrev och för att hantera prenumerationer/avbeställningar av dessa tjänster. Flera tjänster kan definieras parallellt, till exempel: särskilda nyhetsbrev för vissa produktkategorier, teman eller områden på en webbplats, prenumerationer på olika typer av varningsmeddelanden och meddelanden i realtid. Se Hantera prenumerationer.

[!DNL :arrow_upper_right:] Lär dig hur du skapar en informationstjänst, skickar nyhetsbrev och hanterar anmälan och avanmälan i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/subscriptions-and-referrals/managing-subscriptions.html)

Så här prenumererar du (anmäler dig) en profil för en tjänst:

* Lägg till tjänsten manuellt i mottagarprofilen: Om du vill göra det går du till fliken **[!UICONTROL Subscriptions]** i profilen och klickar på **[!UICONTROL Add]** och väljer den aktuella informationstjänsten.

   [!DNL :arrow_upper_right:] Läs mer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/profile-management/editing-a-profile.html?lang=en#deliveries-tab)

* Prenumerera automatiskt på en uppsättning mottagare till tjänsten. Listan med mottagare kan komma från en filtreringsåtgärd, en grupp, en mapp, en import eller ett manuellt val. Om du vill prenumerera på dessa mottagare markerar du profilerna och högerklickar. Välj **[!UICONTROL Actions > Subscribe selection to a service...]**, markera den aktuella tjänsten och starta åtgärden.

   [!DNL :arrow_upper_right:] Läs mer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/profile-management/editing-a-profile.html?lang=en#deliveries-tab)


* Importera mottagare och prenumerera automatiskt på en informationstjänst. Det gör du genom att välja den berörda tjänsten i det sista steget i importguiden.

   [!DNL :arrow_upper_right:] Läs mer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/generic-imports-exports/executing-import-jobs.html?lang=en#step-5---additional-step-when-importing-recipients)

* Använd ett webbformulär så att mottagarna kan prenumerera på en tjänst.

   [!DNL :arrow_upper_right:] Läs mer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=en#create-a-subscription--form-with-double-opt-in)


* Skapa ett målarbetsflöde och använda en **[!UICONTROL Subscription service]**-aktivitet.

   [!DNL :arrow_upper_right:] Läs mer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/subscription-services.html?lang=en#example--subscribe-a-list-of-recipients-to-a-newsletter)


Så här avanmäler du en profil från en tjänst:

**Manuell avprenumeration**

* Personligt anpassad länk för att avbeställa prenumerationer eller webbformulär
* Manuell borttagning av en informationstjänst
* Manuell borttagning av mottagare från en viss prenumerationstjänst

**Automatisk avprenumeration**

* Ange en tidsgräns för informationstjänsten: när giltighetsperioden har löpt ut kommer mottagarna att avbeställa prenumerationen automatiskt. Den här perioden anges på fliken Redigera i tjänstens egenskaper. Den uttrycks i dagar.
* Ställ in ett avabonnemangsarbetsflöde för en population

[!DNL :arrow_upper_right:] Läs mer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/subscriptions-and-referrals/managing-subscriptions.html?lang=en#unsubscribing-a-recipient-from-a-service)


>[!CAUTION]
>
>Prenumerationer och avbeställningar är **asynkrona** processer. Begäranden om anmälan och avanmälan behandlas varje timme. [Läs mer](../dev/new-apis.md#sub-apis)

Du kan också göra det möjligt för leveransmottagarna att vidarebefordra meddelanden till en vän. Om du vill göra det infogar du länkarna i leveransen. Du kan sedan följa upp denna delningsprocess samt antalet besök på de berörda sidorna.

[!DNL :arrow_upper_right:] Mer information om den här funktionen finns i dokumentationen [ för ](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/subscriptions-and-referrals/viral-and-social-marketing.html?lang=en#viral-marketing--forward-to-a-friend)Campaign Classic v7.