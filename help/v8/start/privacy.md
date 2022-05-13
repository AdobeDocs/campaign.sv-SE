---
title: Hantera sekretessförfrågningar i Campaign
description: Lär dig hur du hanterar sekretessförfrågningar i Campaign
feature: Audiences
role: Data Engineer
level: Beginner
source-git-commit: 9457652f62810eb401c4010acd9b5da42d88d796
workflow-type: tm+mt
source-wordcount: '1050'
ht-degree: 47%

---

# Hantera sekretessförfrågningar i Campaign {#privacy}

<!--Adobe Campaign is a powerful tool for collecting and processing large volume of data, including personal information and sensitive data. It is therefore essential that you receive and monitor consent from your recipients.-->

>[!NOTE]
>
>Den här funktionen är tillgänglig från och med Campaign v8.3. Om du vill kontrollera din version kan du läsa [det här avsnittet](compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)

För att underlätta beredskapen gällande din integritet kan du hantera förfrågningar om åtkomst och borttagning med Adobe Campaign.

![](../assets/do-not-localize/speech.png) Läs mer om **Rätt till åtkomst** och **Rätt att glömma** (ta bort begäran) i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html#right-access-forgotten){target=&quot;_blank&quot;}.

För att kunna utföra dessa förfrågningar måste du använda integreringen **Privacy Core Service**. Förfrågningar om användarens information som skickas från Privacy Core Service till alla lösningar i Experience Cloud hanteras automatiskt av Campaign via ett dedikerat arbetsflöde. [Läs mer](#create-privacy-request)

Adobe erbjuder datakontrollanter de verktyg som behövs för att skapa och bearbeta sekretessförfrågningar för data som lagras i Campaign. Det är emellertid ditt ansvar som personuppgiftsansvariga att verifiera identiteten på den registrerade som gör begäran och att bekräfta att de uppgifter som skickas tillbaka till den som gjorde begäran avser den registrerade. Läs mer om personuppgifter och olika enheter som hanterar data i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html#personal-data){target=&quot;_blank&quot;}.

## Definiera ett namnutrymme {#namespaces}

Innan du skapar en sekretessförfrågan måste du **definiera namnutrymmet** kommer du att använda. Namnrymden är nyckeln som används för att identifiera den registrerade i databasen i Adobe Campaign.

>[!NOTE]
>
>Mer information om namnutrymmen för identiteter finns i [Experience Platform dokumentation](https://experienceleague.adobe.com/docs/experience-platform/identity/namespaces.html){target=&quot;_blank&quot;}.

För närvarande stöder inte Adobe Campaign import av namnutrymmen från Experience Platform Identity Namespace. När du har skapat ett namnutrymme i tjänsten Identity Namespace måste du därför skapa motsvarande namnutrymme manuellt i Adobe Campaign-gränssnittet. Följ stegen nedan för att göra detta.

<!--v7?
Three namespaces are available out-of-the-box: email, phone and mobile phone. If you need a different namespace (a recipient custom field, for example), you can create a new one from **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>For optimal performance, it is recommended to use out-of-the-box namespaces.
-->

1. Skapa ett namnutrymme på [Identitetsnamnområdestjänst](https://developer.adobe.com/experience-platform-apis/references/identity-service/#tag/Identity-Namespace){target=&quot;_blank&quot;}.

1. När [lista identitetsnamnutrymmen](https://developer.adobe.com/experience-platform-apis/references/identity-service/#operation/getIdNamespaces){target=&quot;_blank&quot;} som är tillgänglig för din organisation får du exempelvis följande information om namnutrymmet:

   ```
   {
           "updateTime": 1632903236731,
           "code": "lumanamespace",
           "status": "ACTIVE",
           "description": "new namespace for Luma privacy requests",
           "id": 10998717,
           "createTime": 1632903236731,
           "idType": "Email",
           "namespaceType": "Custom",
           "name": "Luma Namespace",
           "custom": true
   }
   ```

1. I Adobe Campaign går du till **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]** och markera **[!UICONTROL New]**.

   ![](assets/privacy-namespaces-new.png)

1. Ange en **[!UICONTROL Label]**.

1. Fyll i informationen om det nya namnutrymmet så att det matchar namnutrymmet som du skapade i tjänsten Identity Namespace:

   * den **[!UICONTROL AEC Namespace ID]** måste matcha attributet &quot;id&quot;;
   * den **[!UICONTROL Internal name]** måste matcha&quot;code&quot;-attributet,
   * den **[!UICONTROL Reconciliation key]** måste matcha attributet &quot;idType&quot;.

   ![](assets/privacy-namespaces-details.png)

   The **[!UICONTROL Reconciliation key]** ska användas för att identifiera den registrerade i Adobe Campaign-databasen.

1. Välj en målmappning <!--(**[!UICONTROL Recipients]**, **[!UICONTROL Real time event]** or **[!UICONTROL Subscriptions]**)--> för att ange hur namnutrymmet ska förenas i Adobe Campaign.

   >[!NOTE]
   >
   >    Om du vill använda flera målmappningar måste du skapa ett namnutrymme per målmappning.

1. Spara ändringarna.

Du kan nu skapa förfrågningar om användarens information baserat på din nya namnrymd. Om du använder flera namnutrymmen skapar du en sekretessbegäran per namnutrymme för samma avstämningsvärde.

## Skapa en förfrågan om användarens information {#create-privacy-request}

The **Integritet - grundtjänst** integreringen gör att ni kan automatisera era sekretessförfrågningar i ett flerlösningssammanhang genom ett enda JSON API-anrop. Adobe Campaign hanterar automatiskt förfrågningar som skickas från Privacy Core Service via ett dedikerat arbetsflöde.

>[!CAUTION]
>
>För att sekretessbegäranden ska kunna behandlas måste du på din Adobe Campaign-instans skapa ett namnutrymme som matchar det namnutrymme som du skapade i Experience Platform Identity Namespace-tjänsten.

Se [Experience Platform Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=sv){target=&quot;_blank&quot;}-dokumentation som lär dig hur du skapar sekretessförfrågningar från Privacy Core-tjänsten.

Varje sekretessjobb delas upp i flera sekretessförfrågningar i Adobe Campaign baserat på hur många namnutrymmen som används, en begäran som motsvarar ett namnutrymme.

Ett jobb kan även köras på flera instanser. Därför skapas flera filer för ett jobb. Om en förfrågan till exempel har två namnrymder och körs i tre instanser skickas totalt sex filer. En fil per namnrymd och instans.

Mönstret för ett filnamn är: `<InstanceName>-<NamespaceId>-<ReconciliationKey>.xml`

* **InstanceName**: namn på instansen i Campaign
* **NamespaceId**: identitetstjänstens namnrymd-ID för den namnrymd som används
* **Avstämningsnyckel**: krypterad avstämningsnyckel

>[!CAUTION]
>
>För att skicka en begäran med den anpassade namnrymdstypen använder du [JSON-metoden](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/user-guide.html?lang=sv#json) {target=&quot;_blank&quot;} och lägger till ID:et för namnrymden i begäran. Du kan också använda [API-anropet](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/privacy-jobs.html?lang=sv#access-delete){target=&quot;_blank&quot;} för att skicka begäran.
>
>Använd bara [Användargränssnittet för sekretess](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/user-guide.html?lang=sv#request-builder){target=&quot;_blank&quot;} om du vill skicka begäranden med standardnamnrymdstypen.

### Tabeller som genomsökts vid bearbetning av begäranden {#list-of-tables}

När en förfrågan om radering eller åtkomst till användarens information utförs söker Adobe Campaign igenom alla den registrerades data baserat på **[!UICONTROL Reconciliation value]** i alla tabeller som har en länk till mottagartabellen (egen typ).

Här följer en lista över färdiga tabeller som tas i beaktande när förfrågningar om användarens information utförs:

* Mottagare (recipient)
* Logg över mottagarleverans (broadLogRcp)
* Logg över mottagarspårning (trackingLogRcp)
* Arkiverad logg över händelseleverans (broadLogEventHistory)
* Innehåll i mottagarlista (rcpGrpRel)
* Erbjudandeförslag för besökare (propositionVisitor)
* Besökare (visitor)
* Prenumerationshistorik (subHisto)
* Prenumerationer (subscription)
* Erbjudandeförslag för mottagare (propositionRcp)

Om du har skapat anpassade tabeller som har en länk till mottagartabellen (egen typ) beaktas även de. Om du till exempel har en transaktionstabell länkad till mottagartabellen och en transaktionsinformationstabell länkad till transaktionstabellen beaktas båda.
<!--
>[!CAUTION]
>
>If you perform Privacy batch requests using profile deletion workflows, please take into consideration the following remarks:
>* Profile deletion via workflows do not process children tables.
>* You need to handle the deletion for all the children tables.
>* Adobe recommends that you create an ETL workflow that add the lines to delete in the Privacy Access table and let the **[!UICONTROL Delete privacy requests data]** workflow perform the deletion. We suggest to limit to 200 profiles per day to delete for performance reasons.-->

### Status gällande förfrågningar om användarens information {#privacy-request-statuses}

Här är de olika statusvärdena för sekretessförfrågningar i Adobe Campaign:

* **[!UICONTROL New]**/**[!UICONTROL Retry pending]**: arbetsflödet har inte bearbetat förfrågan ännu.
* **[!UICONTROL Processing]**/**[!UICONTROL Retry in progress]**: arbetsflödet bearbetar förfrågan.
* **[!UICONTROL Delete pending]**: arbetsflödet har identifierat alla mottagardata för borttagning.
* **[!UICONTROL Delete in progress]**: arbetsflödet bearbetar borttagningen.
* **[!UICONTROL Complete]**: behandlingen av förfrågan har slutförts utan fel.
* **[!UICONTROL Error]**: arbetsflödet har påträffat ett fel. Orsaken visas i listan över förfrågningar om användarens information i kolumnen **[!UICONTROL Request status]**. Till exempel innebär **[!UICONTROL Error data not found]** att inga mottagardata som matchar den registrerades **[!UICONTROL Reconciliation value]** har hittats i databasen.

**Relaterade ämnen** Campaign Classic v7-dokumentation:

* [Sekretess och samtycke](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html){target=&quot;_blank&quot;}

* [Komma igång med Integritetshantering](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html){target=&quot;_blank&quot;}

* [Bestämmelser om sekretesshantering](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html#privacy-management-regulations){target=&quot;_blank&quot;} (GDPR, CCPA, PDPA och LGPD)

* [Avanmäl dig till försäljning av personuppgifter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-requests/privacy-requests-ccpa.html){target=&quot;_blank&quot;} (specifikt för CCPA)