---
product: campaign
title: Leverans
description: Läs mer om arbetsflödesaktiviteten av typen Delivery
feature: Workflows, Channels Activity
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 58574983-86c7-46f5-b41b-bae90171048d
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# Leverans{#delivery}

Med en aktivitet av typen **Leverans** kan du skapa en leveransåtgärd. Den kan skapas med indataelement.

Om du vill konfigurera den redigerar du aktiviteten och anger leveransalternativen.

![](assets/edit_diffusion.png)

1. **Leverans**

   Du kan:

   * Agera på leveransen som anges i den inkommande övergången. Om du vill göra det väljer du det första alternativet i avsnittet **[!UICONTROL Delivery]** i fönstret.

     Det här alternativet kan användas när en tidigare arbetsflödesaktivitet redan har skapats eller specificerat leveransen. Detta kan ha gjorts, som i exemplet nedan, av en aktivitet av samma typ som har genererat en utgående övergång.

     I följande exempel skapas leveransen för första gången. Populationen och innehållet definieras senare. Därefter anges informationen för dessa tre element på nytt i en ny leveransaktivitet med hjälp av övergången för inkommande trafik så att den kan skickas.

     ![](assets/specified_transition_option_exemple.png)

   * Välj den aktuella leveransen direkt. Det gör du genom att välja alternativet **[!UICONTROL Explicit]** och välja leveransen i listrutan i fältet **[!UICONTROL Delivery]**.

     I listan visas oavslutade leveranser i mappen **Leveranser** som standard. Klicka på ikonen **[!UICONTROL Select link]** om du vill komma åt andra kampanjer.

     ![](assets/diffusion_edit_1.png)

     Välj kampanjen i listrutan för fältet **[!UICONTROL Folder]** eller klicka på **[!UICONTROL Display sub-levels]** om du vill visa alla leveranser som finns i undermapparna:

     ![](assets/diffusion_edit_2.png)

     När du har valt leveransåtgärden kan du visa innehållet genom att klicka på ikonen **[!UICONTROL Edit link]**.

   * Skapa ett skript för att beräkna leveransen. Om du vill göra det väljer du alternativet **[!UICONTROL Computed by a script]** och anger skriptet. Du kan öppna ett inmatningsfönster genom att klicka på alternativet **[!UICONTROL Edit...]**. I följande exempel återskapas leveransens identifierare:

     ![](assets/diffusion_edit_3.png)

   * Skapa en ny leverans. Om du vill göra det väljer du alternativet **[!UICONTROL New, created from a template]** och väljer den leveransmall som leveransen ska baseras på.

     ![](assets/diffusion_edit_4.png)

     Klicka på ikonen **[!UICONTROL Select link]** för att bläddra bland mapparna och klicka på ikonen **[!UICONTROL Edit link]** om du vill visa innehållet i den valda mallen.

1. **Mottagare**

   Mottagarna kan anges av de inkommande händelserna, till exempel efter en filimport, eller anges i leveransåtgärden. De kan också lagras i en eller flera filer.

   ![](assets/diffusion_edit_5.png)

1. **Innehåll**

   Innehållet i meddelandet kan definieras i leverans- eller inkommande-händelsen.

   ![](assets/diffusion_edit_6.png)

1. **Åtgärd som ska köras**

   Du kan skapa leveransen, förbereda den, starta den, beräkna målet eller skicka ett korrektur.

   ![](assets/diffusion_edit_7.png)

   Välj vilken typ av åtgärd som ska utföras:

   * **[!UICONTROL Save]**: Med det här alternativet kan du skapa leveransen och spara den. Den kommer inte att analysera eller leverera den.
   * **[!UICONTROL Estimate the target]**: Med det här alternativet kan du beräkna leveransmålet för att bedöma dess potential (första analysfasen). Den här åtgärden motsvarar att välja alternativet **[!UICONTROL Estimate the population to be targeted]** och klicka på **[!UICONTROL Analyze]** när du skickar en leverans till huvudmålet via **Leverans**.
   * **[!UICONTROL Prepare]**: Med det här alternativet kan du köra hela analysprocessen (målberäkning och förberedelse av innehåll). Leveransen har inte skickats. Den här åtgärden motsvarar att välja alternativet **[!UICONTROL Deliver as soon as possible]** och klicka på **[!UICONTROL Analyze]** när du skickar en leverans till huvudmålet med **Leverans**.
   * **[!UICONTROL Send a proof]**: Med det här alternativet kan du skicka ett leveransbevis. Den här åtgärden motsvarar att klicka på knappen **[!UICONTROL Send a proof]** i verktygsfältet för en leverans med **Leverans**
   * **[!UICONTROL Prepare and start]**: Det här alternativet startar den fullständiga analysprocessen (målberäkning och förberedelse av innehåll) och skickar leveransen. Den här åtgärden motsvarar att klicka på **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]** och **[!UICONTROL Confirm delivery]** när du skickar en leverans till huvudmålet med **Leverans**.

   Med aktiviteten **[!UICONTROL Act on a delivery]** som används ytterligare i arbetsflödet kan du starta alla återstående steg som krävs för att starta leveransen (målberäkning, förberedelse av innehåll, leverans). Mer information finns i [Leveranskontroll](delivery-control.md).

   Följande alternativ är också tillgängliga:

   * **[!UICONTROL Generate an outbound transition]**

     Skapar en utgående övergång som ska aktiveras i slutet av körningen. Du kan välja om du vill hämta målet för den utgående leveransen eller inte.

   * **[!UICONTROL Do not recover target]**

     Återställer inte målet för åtgärden för utgående leverans.

   * **[!UICONTROL Processing errors]**

     Se [Leveranskontroll](delivery-control.md).

   På fliken **Skript** kan du ändra leveransparametrarna.

   ![](assets/edit_diffusion_fil_script.png)

## Exempel: leveransarbetsflöde {#example--delivery-workflow}

Skapa ett nytt arbetsflöde och lägg till aktiviteter enligt bilden nedan:

![](assets/new-workflow-5.png)

Öppna aktiviteten **Leverans** och definiera egenskaperna enligt följande:

* Välj **[!UICONTROL New, created from a template]** i avsnittet **[!UICONTROL Delivery]** och välj en leveransmall.
* Välj **[!UICONTROL Specified in the delivery]** i avsnittet **[!UICONTROL Recipients]**.
* Behåll alternativet **[!UICONTROL Prepare]** i avsnittet **[!UICONTROL Action to execute]**.

![](assets/new-workflow-param-delivery.png)

Klicka på **[!UICONTROL OK]** för att stänga egenskapsfönstret. Du har just konfigurerat en aktivitet som består av att skapa och förbereda en ny leverans baserat på en leveransmall vars mål ska anges i den.

Öppna aktiviteten **Approval** och definiera egenskaperna enligt följande:

1. I fältet **[!UICONTROL Assignment type]** väljer du en grupp som du är registrerad i. Om du är ansluten med administratörskontot väljer du gruppen Administration.
1. Ange sedan en titel och infoga följande text i meddelandetexten:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Detta är ett meddelande som innehåller ett uttryck skrivet i JavaScript: **[!UICONTROL vars.recCount]** representerar antalet mottagare som är mål för leveransen av föregående aktivitet. Mer information om JavaScript-uttryck finns i [JavaScript-skript och -mallar](javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   Godkännandeaktiviteten anges i [Godkännande](approval.md).

## Indataparametrar {#input-parameters}

Leverans-ID, om alternativet **[!UICONTROL Specified in the transition]** har valts i avsnittet **[!UICONTROL Delivery]**.

* deliveryId
* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

>[!NOTE]
>
>Den här parametern visas bara om alternativet **[!UICONTROL Specified by inbound event(s)]** har valts i avsnittet **[!UICONTROL Recipients]**.

* filnamn

  Fullständigt namn på filen som genereras om alternativet **[!UICONTROL File(s) specified by inbound event(s)]** väljs i avsnittet **[!UICONTROL Recipients]**.

* contentId

  Innehållsidentifierare om alternativet **[!UICONTROL Specified by inbound events]** har valts i avsnittet **[!UICONTROL Content]**.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som är resultatet av leveransen. **[!UICONTROL tableName]** är namnet på den tabell som memorerar målets identifierare, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Övergången som är associerad med komplementet har samma parametrar.

>[!NOTE]
>
>Det finns inga utdataparametrar när alternativet **[!UICONTROL Do not recover target]** väljs.
