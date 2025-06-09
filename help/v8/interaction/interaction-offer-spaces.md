---
title: Kampanjinteraktion - erbjudandemellanslag
description: Lär dig hur du skapar erbjudandemellanslag
feature: Interaction, Offers
role: User, Admin
level: Beginner
exl-id: c116d86a-d3e2-47e3-a641-e2d7c8cc575c
source-git-commit: 061197048885a30249bd18af7f8b24cb71def742
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 1%

---

# Skapa erbjudandeplatser{#creating-offer-spaces}

Innehållet i erbjudandekatalogen är konfigurerat i erbjudandemellanslag. Som standard kan innehållet innehålla följande fält: **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** och **[!UICONTROL Text content]**. Fältsekvensen är konfigurerad i erbjudandeutrymmet.

Som **teknisk administratör** kan du skapa erbjudanden i designmiljön. Du måste ha tillgång till undermappen för erbjudandeutrymmet. När erbjudandet har skapats dupliceras dessa erbjudanden automatiskt till Live-miljön när erbjudandet godkänns.

HTML-återgivningen skapas via en återgivningsfunktion. Sekvensen för fälten som definieras i återgivningsfunktionen måste vara identisk med sekvensen som konfigurerats i innehållet.

![](assets/offer_space_create_009.png)

Följ stegen nedan för att skapa ett nytt erbjudandeutrymme:

1. Klicka på **[!UICONTROL New]** i listan med erbjudanden.

   ![](assets/offer_space_create_001.png)

1. Markera den kanal som du vill använda och ändra etiketten för erbjudandeutrymmet.

   ![](assets/offer_space_create_002.png)

1. Markera alternativet **[!UICONTROL Enable unitary mode]**

1. Gå till fönstret **[!UICONTROL Content field]** och klicka på **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. Gå till noden **[!UICONTROL Content]** och markera fälten i följande ordning: **[!UICONTROL Title]**, sedan **[!UICONTROL Image URL]**, sedan **[!UICONTROL HTML content]** och sedan **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. Markera alternativet **[!UICONTROL Required]** för att göra varje fält obligatoriskt.

   >[!NOTE]
   >
   >Det här alternativet används vid förhandsgranskningen och gör att erbjudandemellanslag blir ogiltiga vid publicering om ett av de obligatoriska fälten saknas i erbjudandet. Om ett erbjudande redan finns på en plats i ett erbjudande beaktas dock inte dessa kriterier.

   ![](assets/offer_space_create_005.png)

1. Klicka på **[!UICONTROL Edit functions]** för att skapa en återgivningsfunktion.

   Dessa funktioner används för att generera offertrepresentationer på ett visst erbjudandeutrymme. Det finns flera möjliga format: HTML eller text.

   **Obs!** - XML-formatet är begränsat till inkommande interaktioner som inte är tillgängliga i den här versionen av produkten. [Läs mer](../start/v7-to-v8.md#gs-unavailable-features)

   ![](assets/offer_space_create_006.png)_

1. Gå till fliken **[!UICONTROL HTML rendering]** och välj **[!UICONTROL Overload the HTML rendering function]**.
1. Infoga återgivningsfunktionen.

   ![](assets/offer_space_create_007.png)

## Erbjud förslagsstatus {#offer-proposition-statuses}

Status för erbjudandeförslag varierar beroende på interaktionen med målpopulationen. Campaign Interaction Module innehåller en uppsättning värden som kan tillämpas på erbjudandet under hela dess livscykel. Du måste konfigurera plattformen så att statusen ändras när erbjudandeförslaget skapas och godkänns.

>[!NOTE]
>
>Statusuppdateringen är en **asynkron** process. Den utförs av spårningsarbetsflödet som aktiveras varje timme.

### Statuslista för erbjudande {#status-list}

Erbjudandestatus är:

* **[!UICONTROL Accepted]**
* **[!UICONTROL Scheduled]**
* **[!UICONTROL Generated]**
* **[!UICONTROL Interested]**
* **[!UICONTROL Presented]**
* **[!UICONTROL Rejected]**

Dessa värden används inte som standard, utan måste konfigureras.

>[!NOTE]
>
>Status för ett erbjudande ändras automatiskt till Presenterat om erbjudandet är kopplat till en leverans med statusen Skickat.

### Erbjudandestatus när erbjudandet skapas {#configuring-the-status-when-the-proposition-is-created}

När ett erbjudandeförslag är **skapat** uppdateras dess status.

I miljön **[!UICONTROL Design]** konfigurerar du statusen som ska gälla när ett förslag skapas, beroende på vilken information du vill visa i erbjudanderapporten.

Gör så här:

1. Gå till fliken **[!UICONTROL Storage]** för önskat utrymme.
1. Välj den status som ska användas för förslaget när det skapas.

   ![](assets/offer_update_status_001.png)

### Erbjudandestatus när erbjudandet godkänns {#configuring-the-status-when-the-proposition-is-accepted}

När ett offertförslag har **accepterats** kan du använda ett av de värden som anges som standard för att konfigurera förslagets nya status. Uppdateringen tillämpas när en mottagare klickar på en länk i erbjudandet.

Gör så här:

1. Gå till fliken **[!UICONTROL Storage]** för önskat utrymme.
1. Välj den status som du vill tillämpa på förslaget när det godkänns.

   ![](assets/offer_update_status_002.png)


**Inkommande interaktion**

På fliken **[!UICONTROL Storage]** kan du bara definiera status för **föreslagen** och **accepterad** erbjudandeförslag. För inkommande interaktion ska status för erbjudandeförslag anges direkt i URL:en för anrop av erbjudandemotorn, i stället för via gränssnittet. På så sätt kan du ange vilken status som ska gälla i andra fall, t.ex. om ett erbjudande avvisas.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

Det erbjudande (identifierare **40004**) som matchar erbjudandet om **hemförsäkring** som visas på webbplatsen **Neobank** innehåller följande URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

Så snart en besökare klickar på erbjudandet, och därmed URL:en, tillämpas statusen **[!UICONTROL Accepted]** (värdet **3**) på erbjudandet och besökaren omdirigeras till en ny sida på webbplatsen **Neobank** för att teckna försäkringsavtalet.

>[!NOTE]
>
>Om du vill ange en annan status på URL:en (till exempel om ett erbjudande avvisas) använder du värdet som motsvarar önskad status. Exempel: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; och så vidare.
>
>Statuser och deras värden kan hämtas i databasschemat **[!UICONTROL Offer propositions (nms)]**. Mer information finns på [den här sidan](../dev/create-schema.md).

**Utgående interaktion**

Du kan automatiskt tillämpa statusen **[!UICONTROL Interested]** på ett erbjudande när leveransen innehåller en länk. Lägg bara till värdet **_urlType=&quot;11&quot;** till länken:

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## Förhandsgranska per utrymme {#offer-preview-per-space}

På fliken **[!UICONTROL Preview]** kan du visa de erbjudanden som mottagaren är berättigad till via en vald metod. I exemplet nedan är mottagaren berättigad till tre offertförslag via post.

![](assets/offer_space_overview_002.png)

Om en mottagare inte är berättigad till något erbjudande visas detta i förhandsgranskningen.

![](assets/offer_space_overview_001.png)


Förhandsvisningen kan ignorera kontexter när de är begränsade till ett mellanslag. Detta är fallet när interaktionsschemat har utökats för att lägga till fält som refereras i ett utrymme med en inkommande kanal.

Mer information finns i det här exemplet i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/managing-offers/advanced-parameters/extension-example.html?lang=sv-SE){target="_blank"}.