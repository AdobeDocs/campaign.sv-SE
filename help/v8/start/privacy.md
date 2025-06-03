---
title: Hantera sekretessförfrågningar i Campaign
description: Lär dig hantera sekretessförfrågningar i Campaign
feature: Privacy
role: Admin
level: Beginner
exl-id: 0f81d318-dbfd-45c8-b391-b1d14d23e9c8
version: Campaign v8, Campaign Classic v7
source-git-commit: a2efad26232cd380eea850a589b22b23928253e8
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 33%

---

# Hantera sekretessförfrågningar i Campaign {#privacy}

Beroende på vilken typ av verksamhet ni bedriver och vilka jurisdiktioner ni bedriver under, kan det bero på att era uppgifter omfattas av lagenliga sekretessbestämmelser. Dessa bestämmelser ger ofta kunderna rätt att begära åtkomst till de uppgifter ni samlar in från dem och rätt att begära att lagrade uppgifter tas bort. Dessa kundförfrågningar om deras personuppgifter kallas i hela dokumentationen för&quot;sekretessförfrågningar&quot;.

Adobe erbjuder Data Controllers de verktyg de behöver för att skapa och bearbeta sekretessförfrågningar för data som lagras i Campaign. Det är emellertid ditt ansvar som personuppgiftsansvariga att verifiera identiteten på den registrerade som gör begäran och att bekräfta att de uppgifter som skickas tillbaka till den som gjorde begäran handlar om den registrerade. Läs mer om personuppgifter och de olika entiteter som hanterar data i [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html?lang=sv-SE#personal-data){target="_blank"}.


Om du vill hantera sekretessbegäran i Campaign måste du först [definiera ett namnområde](#namespaces). Du kan sedan skapa och hantera förfrågningar om sekretess. Använd integreringen **Adobe Privacy Service** för att utföra sekretessförfrågningar. Sekretessförfrågningar som skickas från Privacy Service till alla Adobe Experience Cloud-lösningar hanteras automatiskt av Campaign via ett dedikerat arbetsflöde. [Läs mer](#create-privacy-request)

Lär dig mer om **rätten till åtkomst** och **rättigheten att bli glömd** (borttagningsbegäran) i [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html?lang=sv-SE#right-access-forgotten){target="_blank"}.


>[!NOTE]
>
>Den här funktionen är tillgänglig från och med Campaign v8.3. Mer information om hur du kontrollerar versionen finns i [det här avsnittet](compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)

## Definiera ett namnutrymme {#namespaces}

Innan du skapar en sekretessförfrågan måste du **definiera namnutrymmet** för att kunna använda det. Namnutrymmet är nyckeln som används för att identifiera den registrerade i databasen.

>[!NOTE]
>
>Läs mer om identitetsnamnutrymmen i [Adobe Experience Platform-dokumentation](https://experienceleague.adobe.com/docs/experience-platform/identity/namespaces.html?lang=sv){target="_blank"}.

Adobe Campaign stöder för närvarande inte import av namnutrymmen från tjänsten Experience Platform Identity Namespace. När du har skapat ett namnutrymme i tjänsten Identity Namespace måste du därför skapa motsvarande namnutrymme manuellt i Adobe Campaign-gränssnittet. Följ stegen nedan för att göra detta.

<!--v7?
Three namespaces are available out-of-the-box: email, phone and mobile phone. If you need a different namespace (a recipient custom field, for example), you can create a new one from **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>For optimal performance, it is recommended to use out-of-the-box namespaces.
-->

1. Skapa ett namnområde i [tjänsten Identity Namespace](https://developer.adobe.com/experience-platform-apis/references/identity-service/#tag/Identity-Namespace){target="_blank"}.

1. När [visar en lista över de identitetsnamnutrymmen](https://developer.adobe.com/experience-platform-apis/references/identity-service/#operation/getIdNamespaces){target="_blank"} som är tillgängliga för din organisation, får du till exempel följande information om namnutrymmet:

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

1. I Adobe Campaign bläddrar du till **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]** och väljer **[!UICONTROL New]**.

   ![](assets/privacy-namespaces-new.png)

1. Ange en **[!UICONTROL Label]**.

1. Fyll i informationen om det nya namnutrymmet så att det matchar namnutrymmet som du skapade i tjänsten Identity Namespace:

   * **[!UICONTROL AEC Namespace ID]** måste matcha attributet &quot;id&quot;
   * **[!UICONTROL Internal name]** måste matcha attributet &quot;code&quot;
   * **[!UICONTROL Reconciliation key]** måste matcha attributet idType

   ![](assets/privacy-namespaces-details.png)

   Fältet **[!UICONTROL Reconciliation key]** används för att identifiera den registrerade i Adobe Campaign-databasen.

1. Välj en målmappning <!--(**[!UICONTROL Recipients]**, **[!UICONTROL Real time event]** or **[!UICONTROL Subscriptions]**)--> för att ange hur namnområdet ska förenas i Adobe Campaign.

   >[!NOTE]
   >
   >Om du behöver använda flera målmappningar skapar du ett namnutrymme per målmappning.

1. Spara ändringarna.

Du kan nu skapa förfrågningar om användarens information baserat på din nya namnrymd. Om du använder flera namnutrymmen skapar du en sekretessbegäran per namnutrymme för samma avstämningsvärde.

## Skapa en förfrågan om användarens information {#create-privacy-request}

Integreringen av **[!DNL Adobe Experience Platform Privacy Service]** gör att du kan automatisera dina sekretessförfrågningar i ett flerlösningssammanhang via ett enda JSON API-anrop. Adobe Campaign hanterar automatiskt förfrågningar som skickas från Privacy Service via ett dedikerat arbetsflöde.

Läs dokumentationen för [Experience Platform Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=sv){target="_blank"} om hur du skapar förfrågningar om användarens information via Privacy Core Service.

Varje **[!DNL Privacy Service]**-jobb delas upp i flera sekretessbegäranden i Adobe Campaign baserat på hur många namnutrymmen som används, en begäran som motsvarar ett namnutrymme.

Ett jobb kan även köras på flera instanser. Därför skapas flera filer för ett jobb. Om en förfrågan till exempel har två namnrymder och körs i tre instanser skickas totalt sex filer. En fil per namnrymd och instans.

Mönstret för ett filnamn är: `<InstanceName>-<NamespaceId>-<ReconciliationKey>.xml`

* **InstanceName**: namn på instansen i Campaign
* **NamespaceId**: identitetstjänstens namnrymd-ID för den namnrymd som används
* **Avstämningsnyckel**: krypterad avstämningsnyckel

>[!CAUTION]
>
>Om du vill skicka en begäran med den anpassade namnområdestypen använder du [JSON-metoden](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/user-guide.html?lang=sv#json){target="_blank"} och lägger till namespaceId i begäran, eller använder [API-anropet](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/privacy-jobs.html?lang=sv#access-delete){target="_blank"} för att göra begäran.
>
>Använd bara användargränssnittet [Sekretess](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/user-guide.html?lang=sv#request-builder){target="_blank"} för att skicka begäranden med standardnamnområdestypen.

### Tabeller som genomsökts vid bearbetning av begäranden {#list-of-tables}

När en förfrågan om radering eller åtkomst till användarens information utförs söker Adobe Campaign igenom alla den registrerades data baserat på **[!UICONTROL Reconciliation value]** i alla tabeller som har en länk till mottagartabellen (egen typ).

Listan med inbyggda tabeller som beaktas vid sekretessförfrågningar är:

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

Nedan finns olika statusar för sekretessförfrågningar i Adobe Campaign och hur du tolkar dem:

* **[!UICONTROL New]**/**[!UICONTROL Retry pending]**: arbetsflödet har inte bearbetat förfrågan ännu.
* **[!UICONTROL Processing]**/**[!UICONTROL Retry in progress]**: arbetsflödet bearbetar förfrågan.
* **[!UICONTROL Delete pending]**: arbetsflödet har identifierat alla mottagardata för borttagning.
* **[!UICONTROL Delete in progress]**: arbetsflödet bearbetar borttagningen.
* **[!UICONTROL Complete]**: behandlingen av förfrågan har slutförts utan fel.
* **[!UICONTROL Error]**: arbetsflödet har påträffat ett fel. Orsaken visas i listan över förfrågningar om användarens information i kolumnen **[!UICONTROL Request status]**. Till exempel innebär **[!UICONTROL Error data not found]** att inga mottagardata som matchar den registrerades **[!UICONTROL Reconciliation value]** har hittats i databasen.

**Relaterade ämnen i Campaign Classic v7-dokumentation:**

* [Integritet och medgivande](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html?lang=sv-SE){target="_blank"}

* [Komma igång med sekretesshantering](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html?lang=sv){target="_blank"}

* [Regler för sekretesshantering](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html?lang=sv-SE#privacy-management-regulations){target="_blank"} (GDPR, CCPA, PDPA och LGPD)

* [Avanmäl dig till försäljning av personuppgifter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-requests/privacy-requests-ccpa.html?lang=sv-SE){target="_blank"} (gäller endast CCPA)
