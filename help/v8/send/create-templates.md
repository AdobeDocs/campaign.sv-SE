---
product: campaign
title: Arbeta med leveransmallar
description: Lär dig hur du skapar och använder leveransmallar i Campaign
feature: Email, Push, SMS, Direct Mail, Cross Channel Orchestration
role: User
level: Beginner
exl-id: 3a4de36e-ba24-49ec-8113-f32f12c8ecdd
source-git-commit: 34af97ae01f7dba418fd0a8c950fc549dfbbd98b
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 5%

---

# Arbeta med leveransmall{#work-with-delivery-template}

Använd leveransmallar för att standardisera det kreativa utseendet och känslan, så att ni kan genomföra och lansera kampanjer snabbare.

En mall kan innehålla:

* Typologier
* Avsändare och svarsadresser
* Grundläggande [personaliseringsblock](../send/personalization-blocks.md)
* Länkar till [spegelsidor](../send/mirror-page.md) och prenumerationslänkar
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

1. Välj leverans från leveranslistan som du kommer åt via **[!UICONTROL Campaign management]** nod i Campaign Explorer.

1. Högerklicka och välj **[!UICONTROL Actions > Save as template...]**.

   ![](assets/save-as-template.png)

1. Redigera leveransegenskaperna och välj den mapp där den nya mallen ska sparas (i **[!UICONTROL Folder]** fält) och den mapp där leveranser som skapats baserat på den här mallen måste skapas (i **[!UICONTROL Execution folder]** fält).

   ![](assets/template-select-folders.png)

### Skapa en ny mall {#create-a-new-template}

>[!NOTE]
>
>För att undvika konfigurationsfel rekommenderar Adobe att du [duplicera en inbyggd mall](#copy-an-existing-template) och anpassa egenskaperna i stället för att skapa en ny mall.

Så här konfigurerar du en leveransmall från grunden:

1. Bläddra till **Resurser** i Campaign Explorer och välj **Mallar** sedan **Leveransmallar**.
1. Klicka **Nytt** i verktygsfältet för att skapa en ny leveransmall.
1. Ange **Etikett** och **Internt namn** i mappen.
1. Spara mallen och öppna den igen.
1. Från **Egenskaper** anpassar inställningarna.
1. I **Allmänt** kan du bekräfta eller ändra de platser som du har valt på fliken **Körningsmapp**, **Mapp** och **Routning** nedrullningsbara menyer.
1. Slutför **E-postparametrar** -kategori med ditt e-postämne och din målgrupp.
1. Lägg till **HTML content** om du vill anpassa mallen kan du visa en [länk för spegelsida](../send/mirror-page.md) och en länk för att avsluta prenumerationen.
1. Välj **Förhandsgranska** -fliken. I **Testa personalisering** nedrullningsbar meny, välja **Mottagare** om du vill förhandsgranska mallen som den valda profilen.
1. Klicka **Spara**. Mallen kan nu användas i en leverans.


## Använd mallar{#use-a-delivery-template}

### Skapa en leverans från en mall{#create-a-delivery-from-a-template}

Om du vill skapa en leverans baserad på en befintlig mall väljer du mallen i listan med tillgängliga leveransmallar.

![](assets/select-the-new-template.png)

Om du inte ser mallen klickar du på **[!UICONTROL Select link]** till höger om fältet för att bläddra bland Campaign-mappar.

![](assets/browse-templates.png)

Välj önskad katalog i dialogrutan **[!UICONTROL Folder]** eller klicka på **[!UICONTROL Display sub-levels]** om du vill visa innehållet i katalogerna i underträden till den aktuella katalogen.

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

### Distribuera en ad hoc-leveransmall

I den här videon förklaras hur du distribuerar en mall för ad hoc-e-postleverans och den förklarar skillnaden mellan en e-postleverans och ett leveransarbetsflöde.

>[!VIDEO](https://video.tv.adobe.com/v/338965?quality=12)

Det finns ytterligare utbildningsvideor för Campaign [här](https://experienceleague.adobe.com/docs/campaign-learn/tutorials/getting-started/introduction-to-adobe-campaign.html){target="_blank"}.
