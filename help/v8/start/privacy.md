---
title: Hantera sekretessförfrågningar i Campaign
description: Lär dig hantera sekretessförfrågningar i Campaign
feature: Privacy
role: Admin
level: Beginner
exl-id: 0f81d318-dbfd-45c8-b391-b1d14d23e9c8
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 36%

---

# Hantera sekretessförfrågningar i Campaign {#privacy}

Beroende på vilken typ av verksamhet ni bedriver och vilka jurisdiktioner ni bedriver under, kan det bero på att era uppgifter omfattas av lagenliga sekretessbestämmelser. Dessa bestämmelser ger ofta kunderna rätt att begära åtkomst till de uppgifter ni samlar in från dem och rätt att begära att lagrade uppgifter tas bort. Dessa kundförfrågningar om deras personuppgifter kallas i hela dokumentationen för&quot;sekretessförfrågningar&quot;.

Adobe erbjuder datakontrollanter de verktyg som behövs för att skapa och bearbeta sekretessförfrågningar för data som lagras i Campaign. Det är emellertid ditt ansvar som personuppgiftsansvariga att verifiera identiteten på den registrerade som gör begäran och att bekräfta att de uppgifter som skickas tillbaka till den som gjorde begäran handlar om den registrerade. Läs mer om personuppgifter och olika enheter som hanterar data i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html#personal-data){target="_blank"}.


Om du vill hantera sekretessbegäran i Campaign måste du först [definiera ett namnutrymme](#namespaces). Du kan sedan skapa och hantera förfrågningar om sekretess. Om du vill utföra sekretessförfrågningar använder du **Adobe Privacy Service** integrering. Sekretessförfrågningar som skickas från Privacy Servicen till alla Adobe Experience Cloud-lösningar hanteras automatiskt av Campaign via ett dedikerat arbetsflöde. [Läs mer](#create-privacy-request)

Läs mer om **Rätt till åtkomst** och **Rätt att glömma** (ta bort begäran) i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html#right-access-forgotten){target="_blank"}.

<!--
>[!NOTE]
>
>This capability is available starting Campaign v8.3. To check your version, refer to [this section](compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)-->

## Definiera ett namnutrymme {#namespaces}

Innan du skapar en sekretessförfrågan måste du **definiera namnutrymmet** att använda. Namnutrymmet är nyckeln som används för att identifiera den registrerade i databasen.

>[!NOTE]
>
>Läs mer om identitetsnamnutrymmen i [Adobe Experience Platform-dokumentation](https://experienceleague.adobe.com/docs/experience-platform/identity/namespaces.html?lang=sv){target="_blank"}.

För närvarande stöder inte Adobe Campaign import av namnutrymmen från Experience Platform Identity Namespace. När du har skapat ett namnutrymme i tjänsten Identity Namespace måste du därför skapa motsvarande namnutrymme manuellt i Adobe Campaign-gränssnittet. Följ stegen nedan för att göra detta.

<!--v7?
Three namespaces are available out-of-the-box: email, phone and mobile phone. If you need a different namespace (a recipient custom field, for example), you can create a new one from **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>For optimal performance, it is recommended to use out-of-the-box namespaces.
-->

1. Skapa ett namnutrymme på [Identitetsnamnområdestjänst](https://developer.adobe.com/experience-platform-apis/references/identity-service/#tag/Identity-Namespace){target="_blank"}.

1. När [lista identitetsnamnutrymmen](https://developer.adobe.com/experience-platform-apis/references/identity-service/#operation/getIdNamespaces){target="_blank"} som är tillgängliga för din organisation, får du följande information om namnutrymmet, till exempel:

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

   * den **[!UICONTROL AEC Namespace ID]** måste matcha attributet &quot;id&quot;
   * den **[!UICONTROL Internal name]** måste matcha attributet &quot;code&quot;
   * den **[!UICONTROL Reconciliation key]** måste matcha attributet &quot;idType&quot;

   ![](assets/privacy-namespaces-details.png)

   The **[!UICONTROL Reconciliation key]** ska användas för att identifiera den registrerade i Adobe Campaign-databasen.

1. Välj en målmappning <!--(**[!UICONTROL Recipients]**, **[!UICONTROL Real time event]** or **[!UICONTROL Subscriptions]**)--> för att ange hur namnutrymmet ska förenas i Adobe Campaign.

   >[!NOTE]
   >
   >Om du behöver använda flera målmappningar skapar du ett namnutrymme per målmappning.

1. Spara ändringarna.

Du kan nu skapa förfrågningar om användarens information baserat på din nya namnrymd. Om du använder flera namnutrymmen skapar du en sekretessbegäran per namnutrymme för samma avstämningsvärde.

## Skapa en förfrågan om användarens information {#create-privacy-request}

The **[!DNL Adobe Experience Platform Privacy Service]** integreringen gör att ni kan automatisera era sekretessförfrågningar i ett flerlösningssammanhang genom ett enda JSON API-anrop. Adobe Campaign hanterar automatiskt begäranden som skickas från Privacy Servicen via ett dedikerat arbetsflöde.

Se [Experience Platform Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=sv){target="_blank"} dokumentation som visar hur man skapar sekretessförfrågningar från Privacy Core-tjänsten.

Varje **[!DNL Privacy Service]**  jobbet delas upp i flera sekretessbegäranden i Adobe Campaign baserat på hur många namnutrymmen som används, en begäran som motsvarar ett namnutrymme.

Ett jobb kan även köras på flera instanser. Därför skapas flera filer för ett jobb. Om en förfrågan till exempel har två namnrymder och körs i tre instanser skickas totalt sex filer. En fil per namnrymd och instans.

Mönstret för ett filnamn är: `<InstanceName>-<NamespaceId>-<ReconciliationKey>.xml`

* **InstanceName**: namn på instansen i Campaign
* **NamespaceId**: identitetstjänstens namnrymd-ID för den namnrymd som används
* **Avstämningsnyckel**: krypterad avstämningsnyckel

>[!CAUTION]
>
>Om du vill skicka en begäran med den anpassade namnrymdstypen utnyttjar du [JSON-metoden](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/user-guide.html?lang=sv#json){target="_blank"} and add the namespaceId to the request, or use the [API call](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/privacy-jobs.html?lang=sv#access-delete){target="_blank"} för att skicka den.
>
>Använd bara [Användargränssnittet för sekretess](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/user-guide.html?lang=sv#request-builder){target="_blank"} om du vill skicka begäranden med standardnamnrymdstypen.

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

* [Sekretess och samtycke](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html){target="_blank"}

* [Komma igång med Integritetshantering](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html?lang=sv){target="_blank"}

* [Bestämmelser om sekretesshantering](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-management.html#privacy-management-regulations){target="_blank"} (GDPR, CCPA, PDPA och LGPD)

* [Avanmäl dig till försäljning av personuppgifter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-requests/privacy-requests-ccpa.html){target="_blank"} (specifikt för CCPA)
