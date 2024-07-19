---
product: campaign
title: Arbeta med leveransmallar
description: Lär dig skapa och använda leveransmallar i Campaign
feature: Email, Push, SMS, Direct Mail, Cross Channel Orchestration
role: User
level: Beginner
exl-id: 3a4de36e-ba24-49ec-8113-f32f12c8ecdd
source-git-commit: 34af97ae01f7dba418fd0a8c950fc549dfbbd98b
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 4%

---

# Arbeta med leveransmall{#work-with-delivery-template}

Använd leveransmallar för att standardisera det kreativa utseendet och känslan, så att ni kan genomföra och lansera kampanjer snabbare.

En mall kan innehålla:

* Typologier
* Avsändare och svarsadresser
* Grundläggande [anpassningsblock](../send/personalization-blocks.md)
* Länkar till [spegelsidor](../send/mirror-page.md) och länkar för att avbryta prenumeration
* Innehåll, företagslogotyp eller signatur
* Andra leveransegenskaper, som resursgiltighet, återförsöksparametrar eller karantäninställningar.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#delivery-template-video)


## Skapa en mall{#create-a-delivery-template}

Om du vill skapa en leveransmall kan du duplicera en inbyggd mall, konvertera en befintlig leverans till en mall eller skapa en leveransmall från början.

### Duplicera en befintlig mall{#copy-an-existing-template}

Campaign innehåller en uppsättning inbyggda mallar för varje kanal: e-post, push, SMS, direktreklam med mera.

Det enklaste sättet att skapa en leveransmall är att duplicera och anpassa en inbyggd mall.

Så här duplicerar du en leveransmall:

1. Bläddra till **[!UICONTROL Resources > Templates > Delivery templates]** i Adobe Campaign Explorer.
1. Välj en inbyggd leveransmall. Inbyggda mallar är fogade i listan.
1. Högerklicka och välj **[!UICONTROL Duplicate]**.

   ![](assets/duplicate-built-in-template.png)

1. Definiera mallinställningarna och spara den nya mallen.

   ![](assets/delivery-template-new.png)

Mallen läggs till i listan med leveransmallar. Du kan nu välja den när du skapar en ny leverans.

![](assets/select-the-new-template.png)

### Konvertera en befintlig leverans till en mall {#convert-an-existing-delivery}

En leverans kan konverteras till en mall för nya upprepade leveransåtgärder.

Så här konverterar du en leverans till en mall:

1. Välj leveransen från leveranslistan, tillgänglig via noden **[!UICONTROL Campaign management]** i Campaign Explorer.

1. Högerklicka och välj **[!UICONTROL Actions > Save as template...]**.

   ![](assets/save-as-template.png)

1. Redigera leveransegenskaperna och välj den mapp där den nya mallen måste sparas (i fältet **[!UICONTROL Folder]**) och den mapp där leveranser som skapats baserat på den här mallen måste skapas (i fältet **[!UICONTROL Execution folder]**).

   ![](assets/template-select-folders.png)

### Skapa en ny mall {#create-a-new-template}

>[!NOTE]
>
>För att undvika konfigurationsfel rekommenderar Adobe att du [duplicerar en inbyggd mall](#copy-an-existing-template) och anpassar dess egenskaper i stället för att skapa en ny mall.

Så här konfigurerar du en leveransmall från grunden:

1. Bläddra till mappen **Resources** i Campaign Explorer och välj **Mallar** och sedan **Leveransmallar**.
1. Klicka på **Nytt** i verktygsfältet för att skapa en ny leveransmall.
1. Ange mappens **etikett** och **interna namn**.
1. Spara mallen och öppna den igen.
1. Anpassa inställningarna från knappen **Egenskaper** .
1. På fliken **Allmänt** bekräftar du eller ändrar de platser som har valts i listrutorna **Körningsmapp**, **Mapp** och **Routning**.
1. Fyll i kategorin **E-postparametrar** med ditt e-postämne och målpopulationen.
1. Lägg till ditt **HTML-innehåll** om du vill anpassa mallen kan du visa en [länk för spegelsida](../send/mirror-page.md) och en länk för att avbryta prenumerationen.
1. Välj fliken **Förhandsgranska**. I listrutan **Testa anpassning** väljer du **Mottagare** om du vill förhandsgranska mallen som den valda profilen.
1. Klicka på **Spara**. Mallen kan nu användas i en leverans.


## Använd mallar{#use-a-delivery-template}

### Skapa en leverans från en mall{#create-a-delivery-from-a-template}

Om du vill skapa en leverans baserad på en befintlig mall väljer du mallen i listan med tillgängliga leveransmallar.

![](assets/select-the-new-template.png)

Om du inte kan se din mall klickar du på mappen **[!UICONTROL Select link]** till höger om fältet för att bläddra bland Campaign-mappar.

![](assets/browse-templates.png)

Välj önskad katalog i fältet **[!UICONTROL Folder]** eller klicka på ikonen **[!UICONTROL Display sub-levels]** för att visa innehållet i katalogerna i underträden till den aktuella katalogen.

Välj den leveransmall som ska användas och klicka på **[!UICONTROL Ok]**.

### Kör en mall {#execute-a-template}

Du kan starta körningen av en mall direkt från malllistan utan att först skapa en leverans.

Om du vill göra det väljer du den mall som ska köras och högerklickar. Välj **[!UICONTROL Actions>Execute the delivery template...]**.

Du kan också använda **[!UICONTROL File>Actions>Execute the delivery template...]**.

![](assets/execute-delivery-template.png)

Ange leveransparametrarna och klicka på **[!UICONTROL Send]**.

Den här åtgärden genererar en leverans i den mapp som är associerad med mallen. Namnet på den här leveransen är namnet på leveransmallen som den skapades från.


## Självstudievideor {#delivery-template-video}

### Konfigurera en leveransmall

I följande video visas hur du konfigurerar en mall för en ad hoc-leverans.

>[!VIDEO](https://video.tv.adobe.com/v/342082?quality=12)

### Så här ställer du in egenskaper för leveransmallar

I följande video visas hur du ställer in leveransmallsegenskaperna och förklarar varje egenskap i detalj.

>[!VIDEO](https://video.tv.adobe.com/v/338969?quality=12)

### Så här distribuerar du en ad hoc-leveransmall

I den här videon förklaras hur du distribuerar en mall för ad hoc-e-postleverans och den förklarar skillnaden mellan en e-postleverans och ett leveransarbetsflöde.

>[!VIDEO](https://video.tv.adobe.com/v/338965?quality=12)

Det finns ytterligare utbildningsvideor för Campaign [här](https://experienceleague.adobe.com/docs/campaign-learn/tutorials/getting-started/introduction-to-adobe-campaign.html){target="_blank"}.
