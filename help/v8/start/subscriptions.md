---
title: Hantera prenumerationer och avbeställningar i Campaign
description: Lär dig hur du hanterar prenumerationer och avslutar prenumerationer i Campaign v8.
feature: Subscriptions
role: User
level: Beginner
exl-id: d5933b12-8664-49b8-953c-ea98eb428cc2
source-git-commit: 08e04f3642320df94d719a415e878e3a26d2e00f
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 4%

---

# Hantera prenumerationer och avbeställningar {#optin-optout}

Använd Adobe Campaign för att skapa och övervaka informationstjänster som nyhetsbrev och för att hantera prenumerationer/avbeställningar av dessa tjänster. Flera tjänster kan definieras parallellt, till exempel: nyhetsbrev till specialister för vissa produktkategorier, teman eller områden på en webbplats, prenumerationer på olika typer av varningsmeddelanden och meddelanden i realtid.

Lär dig skapa en informationstjänst, skicka nyhetsbrev och hantera anmälan och avanmälan i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/subscriptions-and-referrals/managing-subscriptions.html?lang=sv-SE){target="_blank"}

Så här prenumererar du (anmäler dig) en profil för en tjänst:

* Lägg till tjänsten manuellt i mottagarprofilen: om du vill göra det klickar du på **[!UICONTROL Add]** på fliken **[!UICONTROL Subscriptions]** i profilen och väljer den aktuella informationstjänsten.

  ![](assets/subscribe-to-a-service.png)

  Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/profile-management/editing-a-profile.html?lang=sv-SE#deliveries-tab){target="_blank"}

* Prenumerera automatiskt på en uppsättning mottagare till tjänsten. Listan med mottagare kan komma från en filtreringsåtgärd, en grupp, en mapp, en import eller ett manuellt val. Om du vill prenumerera på dessa mottagare markerar du profilerna och högerklickar. Välj **[!UICONTROL Actions > Subscribe selection to a service...]**.

  ![](assets/subscribe-selection.png)

  Välj den berörda tjänsten och starta åtgärden.

  ![](assets/subscribe-confirm.png)

  Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/profile-management/editing-a-profile.html?lang=sv-SE#deliveries-tab){target="_blank"}


* Importera mottagare och prenumerera automatiskt på en informationstjänst. Det gör du genom att välja den berörda tjänsten i det sista steget i importguiden.

  Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/generic-imports-exports/executing-import-jobs.html?lang=sv-SE#step-5---additional-step-when-importing-recipients){target="_blank"}.

* Använd ett webbformulär så att mottagarna kan prenumerera på en tjänst.

  ![](assets/opt-in-webapp.png)

  Campaign innehåller ett standardwebbformulär som hanterar anmälan. Du kan anpassa den och mappa profildata.

  ![](assets/web-app.png)

  Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=sv-SE#create-a-subscription--form-with-double-opt-in){target="_blank"}.


* Skapa ett målarbetsflöde och använda en **[!UICONTROL Subscription service]**-aktivitet.

  ![](assets/wf-subscription.png)

  Läs mer på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/subscription-services.html?lang=sv-SE){target="_blank"}.

Så här avanmäler du en profil från en tjänst:

**Manuell avprenumeration**

* Personligt anpassad länk för att avbeställa prenumerationer eller webbformulär
* Manuell borttagning av en informationstjänst
* Manuell borttagning av mottagare från en viss prenumerationstjänst

**Automatisk avprenumeration**

* Ange en tidsgräns för informationstjänsten: mottagarna kommer att sluta prenumerera automatiskt när giltighetsperioden har gått ut. Den här perioden anges på fliken Redigera i tjänstens egenskaper. Den uttrycks i dagar.
* Ställ in ett avabonnemangsarbetsflöde för en population.

Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/subscriptions-and-referrals/managing-subscriptions.html?lang=sv-SE#unsubscribing-a-recipient-from-a-service){target="_blank"}.


>[!CAUTION]
>
>I en [Enterprise-distribution](../architecture/enterprise-deployment.md) (FFDA) är prenumerationer och avbeställningar **asynkrona** processer. Begäranden om anmälan och avanmälan behandlas varje timme. [Läs mer](../architecture/new-apis.md#sub-apis)

<!--
You can also enable your delivery recipients to forward messages to a friend. To do this, insert the relevant links into your delivery. You may then track this sharing process as well as the number of visits to the concerned pages. 

For more on this capability, refer to [Campaign Classic v7 documentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/subscriptions-and-referrals/viral-and-social-marketing.html?lang=sv-SE#viral-marketing--forward-to-a-friend){target="_blank"}
-->
