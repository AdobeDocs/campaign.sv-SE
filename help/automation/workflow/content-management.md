---
product: campaign
title: Innehållshantering
description: Innehållshantering
feature: Workflows, Data Management
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 9b225f78-1959-4e4f-aa4e-ff8a63051154
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 2%

---

# Innehållshantering{#content-management}

Med en **innehållshantering** -aktivitet kan du skapa och ändra ett innehåll och generera filer baserat på det här innehållet. Innehållet kan sedan levereras via en &#39;Delivery&#39;-aktivitet.

>[!CAUTION]
>
>Innehållshantering är en valfri Adobe Campaign-modul. Kontrollera licensavtalet.

>[!NOTE]
>
>Med Adobe Campaign webbanvändargränssnitt kan du använda innehållsfragment för ditt innehåll. Marknadsförare kan skapa flera anpassade innehållsblock i förväg tack vare återanvändbara komponenter som kan refereras i ett eller flera meddelanden, vilket gör att ni snabbt kan sammanställa meddelandeinnehållet i en förbättrad designprocess. Mer information om innehållsfragment finns i [Adobe Campaign Web UI-dokumentationen.](https://experienceleague.adobe.com/sv/docs/campaign-web/v8/content/manage-reusable-content/fragments/fragments){target=_blank}

Aktivitetens egenskaper är uppdelade i tre steg:

* **Innehållsmarkering**: Innehållet kan ha skapats tidigare eller kan skapas via aktiviteten.
* **Innehållsuppdatering**: aktiviteten kan ändra innehållets ämne eller importera allt XML-innehåll.
* **Åtgärd**: det resulterande innehållet kan sparas eller genereras.

  ![](assets/content_mgmt_edit.png)

1. **Innehåll**

   * **[!UICONTROL Specified in the transition]**

     Med det här alternativet kan du använda innehållet som anges i övergången, d.v.s. händelsen som aktiverar innehållshantering måste innehålla en **[!UICONTROL contentId]**-variabel. Den här variabeln kan ha angetts av en tidigare innehållshantering eller av ett skript.

   * **[!UICONTROL Explicit]**

     Med det här alternativet kan du välja innehåll som redan har skapats via fältet **[!UICONTROL Content]**. Det här fältet visas bara när alternativet **[!UICONTROL Explicit]** har valts.

     ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

     Innehållsidentifieraren beräknas av ett skript. I fältet **[!UICONTROL Script]** kan du definiera en JavaScript-mall som utvärderar innehållets identifierare (primärnyckel). Det här fältet visas bara när alternativet **[!UICONTROL Calculated by a script]** har valts.

     ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

     Skapar ett nytt innehåll från en publiceringsmall. Det nya innehållet sparas i filen som anges i fältet **[!UICONTROL String]**. Fältet **[!UICONTROL Template]** anger den publiceringsmall som ska användas för att skapa innehållet.

     ![](assets/content_mgmt_new.png)

1. **Uppdatera innehåll**

   * **[!UICONTROL Subject]**

     I det här fältet kan du ändra innehållets ämne.

   * **[!UICONTROL Access to data from an XML feed]**

     Med det här alternativet kan du skapa innehåll från ett XML-dokument som hämtats via en XSL-formatmall. När det här alternativet är markerat anger fältet **[!UICONTROL URL]** URL:en för hämtning av XML-innehåll. Med **[!UICONTROL XSL stylesheet]** kan du ange vilken formatmall som ska användas för att omforma det hämtade XML-dokumentet. Den här egenskapen är valfri.

     ![](assets/content_mgmt_xmlcontent.png)

1. **Åtgärd som ska köras**

   * **[!UICONTROL Save]**

     Med det här alternativet sparas det skapade eller ändrade innehållet.

     Den utgående övergången aktiveras bara en gång, med innehållet sparat i variabeln **[!UICONTROL contentId]** som en parameter.

   * **[!UICONTROL Generate]**

     Det här alternativet sparar innehållet och genererar sedan utdatafilerna för varje omformningsmall med en publikation av typen File.

     ![](assets/content_mgmt_generate.png)

     Den utgående övergången aktiveras för varje fil som skapas med identifieraren för innehållet som sparas i variabeln **[!UICONTROL contentId]** som dess parameter och filnamnet i variabeln **[!UICONTROL filename]**.

## Indataparametrar {#input-parameters}

* contentId

Identifierare för innehållet som ska användas om alternativet **[!UICONTROL Specified in the transition]** är aktiverat.

## Utdataparametrar {#output-parameters}

* contentId

  Innehållsidentifierare.

* filnamn

  Det genererade filens fullständiga namn om den valda åtgärden är **[!UICONTROL Generate]**.
