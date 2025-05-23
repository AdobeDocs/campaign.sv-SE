---
product: campaign
title: Mallar för marknadsföringskampanjer
description: Mallar för marknadsföringskampanjer
feature: Campaigns, Templates
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 1bd8d3e7-aaa9-4e00-96bb-0d30614ab380
source-git-commit: a5f7cf6e21b263f8a7fb4fa19a88bebb78390c3d
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Skapa och konfigurera kampanjmallar {#campaign-templates}

Alla marknadsföringskampanjer bygger på en mall som lagrar de viktigaste egenskaperna och funktionerna. Campaign innehåller en inbyggd mall för att skapa kampanjer. Den här mallen har alla funktioner aktiverade: Dokument, dirigeringsadresser, Godkännanden, Leveranskonturer osv.

Vilka funktioner som är tillgängliga beror på dina behörigheter, tillägg och konfigurationen för din Adobe Campaign-plattform.


>[!NOTE]
>
>Trädet visas när du klickar på ikonen **[!UICONTROL Explorer]** på startsidan.

En inbyggd mall tillhandahålls för att skapa en kampanj för vilken ingen specifik konfiguration har definierats. Du kan skapa och konfigurera kampanjmallar och sedan skapa kampanjer utifrån dessa mallar.

## Skapa en kampanjmall {#create-a-campaign-template}

Så här skapar du en kampanjmall:

1. Öppna Campaign **Explorer** och bläddra till **Resurser > Mallar > Campaign-mallar**.
1. Klicka på **Nytt** i verktygsfältet ovanför listan med mallar.

![](assets/campaign-template-node.png)

Du kan även **duplicera** den inbyggda mallen för att återanvända och anpassa konfigurationen. Om du vill göra det högerklickar du på mallen och väljer **Duplicera**.

1. Ange etiketten för den nya kampanjmallen.
1. Klicka på **Spara** och öppna mallen igen.
1. Definiera mallegenskaperna på fliken **Redigera**.
1. Välj länken **Avancerade kampanjparametrar..** om du vill lägga till ett arbetsflöde i kampanjmallen.

   ![](assets/campaign-template-parameters.png)

1. Ändra värdet **Mål och arbetsflöden** till **Ja** och bekräfta. Lär dig hur du lägger till funktioner i [det här avsnittet](#typology-of-enabled-modules).
1. Fliken **Mål och arbetsflöden** läggs till i mallen. Klicka på **Lägg till ett arbetsflöde..**, ange en **etikett** och klicka på **OK**.
1. Skapa arbetsflödet efter behov.

   ![](assets/campaign-template-create-wf.png)

1. Klicka på **Spara**. Mallen är nu klar att användas för att skapa en ny kampanj.

De olika flikarna och underflikarna i kampanjmallen ger dig åtkomst till inställningarna som beskrivs i [Allmän konfiguration](#general-configuration).

## Välj moduler {#select-modules}

Med länken **[!UICONTROL Advanced campaign parameters...]** kan du aktivera och inaktivera jobb för kampanjer som är baserade på den här mallen. Välj de funktioner som du vill aktivera i kampanjer som skapas baserat på den här mallen.

![](assets/campaign-template-select-modules.png)

Om ingen funktion väljs visas inte elementen som rör processen (menyer, ikoner, alternativ, flikar, underflikar osv.) i mallens gränssnitt eller i kampanjer som är baserade på den här mallen. Flikarna till vänster om kampanjinformationen och de tillgängliga flikarna sammanfaller med de funktioner som valts i mallen. Funktionen **Utgifter och mål** är till exempel inte aktiverad. Motsvarande **[!UICONTROL Budget]**-flik visas inte i kampanjer som baseras på den här mallen.

Dessutom läggs genvägar till konfigurationsfönstren till på kontrollpanelen för kampanjer. När en funktion är aktiverad får en direktlänk åtkomst till den från kontrollpanelen för kampanjer.

### Konfigurationsexempel

* Med följande inställningar:

  ![](assets/campaign-template-select-functionalities.png)

  Kampanjpanelen visar:

  ![](assets/campaign-template-dashboard-sample-1.png)

  Observera att fliken **[!UICONTROL Targeting and workflows]** saknas.

  Följande funktioner är tillgängliga:

  ![](assets/campaign-template-edit-sample-1.png)

  Observera att fliken **[!UICONTROL Budget]** saknas.

  De avancerade inställningarna för kampanjen återspeglar även den här konfigurationen.

  ![](assets/campaign-template-parameters-sample-1.png)

  Observera att fliken **[!UICONTROL Approvals]** inte är tillgänglig.

* Med den här konfigurationen:
  ![](assets/campaign-template-dashboard-sample-2.png)

  Kampanjpanelen visar:

  ![](assets/campaign-template-select-functionalities-2.png)

  Observera att fliken **[!UICONTROL Targeting and workflows]** är tillgänglig men att länken **Lägg till ett dokument** saknas.

  Följande funktioner är tillgängliga:

  ![](assets/campaign-template-edit-sample-2.png)

  Observera att fliken **[!UICONTROL Budget]** är tillgänglig.

  De avancerade inställningarna för kampanjen återspeglar även den här konfigurationen.

  ![](assets/campaign-template-parameters-sample-2.png)

  Observera att fliken **[!UICONTROL Approvals]** är tillgänglig men att flikarna **[!UICONTROL Control population]** och **[!UICONTROL Seed addresses]** inte är aktiverade.


## Modultyper {#typology-of-enabled-modules}

* **Kontrollgrupp**

  När den här modulen är markerad läggs en extra flik till i de avancerade inställningarna för mallen och kampanjerna som är baserade på den här mallen. Konfigurationen kan definieras via mallen eller individuellt för varje kampanj. Läs mer om kontrollgrupper i [det här avsnittet](marketing-campaign-deliveries.md#defining-a-control-group).

  ![](assets/template-activate-1.png)


* **Fröadresser**

  När den här modulen är markerad läggs en extra flik till i de avancerade inställningarna för mallen och kampanjerna som är baserade på den här mallen. Konfigurationen kan definieras via mallen eller individuellt för varje kampanj.

  ![](assets/template-activate-2.png)

* **Dokument**

  När den här modulen är markerad läggs en extra flik till på fliken **[!UICONTROL Edit]** i mallen och de kampanjer som är baserade på den här mallen. Bifogade dokument kan läggas till från mallen eller individuellt för varje kampanj. Läs mer om dokument i [det här avsnittet](marketing-campaign-deliveries.md#manage-associated-documents).

  ![](assets/template-activate-3.png)

* **Leveransbeskrivning**

  När den här modulen är markerad läggs en **[!UICONTROL Delivery outlines]**-underflik till på fliken **[!UICONTROL Documents]** för att definiera leveransdispositioner för kampanjen. Läs mer om leveransdispositioner i [det här avsnittet](marketing-campaign-assets.md#delivery-outlines).

  ![](assets/template-activate-4.png)

* **Målgruppsanpassning och arbetsflöden**

  När du väljer modulen **[!UICONTROL Targeting and workflows]** läggs en flik till så att du kan skapa ett eller flera arbetsflöden för kampanjer som är baserade på den här mallen. Arbetsflöden kan också konfigureras individuellt för varje kampanj baserat på den här mallen.Läs mer om kampanjarbetsflöden i [det här avsnittet](marketing-campaign-deliveries.md#build-the-main-target-in-a-workflow).

  ![](assets/template-activate-5.png)

  När den här modulen är aktiverad läggs en **[!UICONTROL Jobs]**-flik till i de avancerade inställningarna för kampanjen för att definiera processens körningssekvens.

* **Godkännanden**

  Om du aktiverar **[!UICONTROL Approvals]** kan du välja vilka processer som ska godkännas och vilka operatorer som ska ansvara för godkännandena. Läs mer om godkännanden i [det här avsnittet](marketing-campaign-approval.md#select-reviewers).

  ![](assets/template-activate-6.png)

  Du kan välja om du vill aktivera processgodkännande eller inte via fliken **[!UICONTROL Approvals]** i avsnittet med avancerade inställningar.

* **Utgifter och mål**

  När den här modulen har valts läggs en **[!UICONTROL Budget]**-flik till i informationen om mallen och kampanjer som är baserade på den här mallen, så att den associerade budgeten kan väljas.

  ![](assets/template-activate-7.png)


## Mallegenskaper {#template-properties}

![](assets/template-op-type.png)

När du skapar en kampanjmall måste du ange följande information:

* Ange mallens **etikett**: etiketten är obligatorisk och är standardetikett för alla kampanjer som baseras på den här mallen.
* Välj kampanjens **natur** i listrutan. De värden som är tillgängliga i den här listan är de som har sparats i uppräkningen **[!UICONTROL natureOp]**.

Lär dig hur du får åtkomst till och konfigurerar dina uppräkningar på [den här sidan](../../v8/config/ui-settings.md#enumerations).


* Välj typen **av kampanj**: unik, återkommande eller periodisk. Som standard används kampanjmallar för unika kampanjer. Återkommande och periodiska kampanjer beskrivs i [det här avsnittet](recurring-periodic-campaigns.md).
* Ange kampanjens varaktighet, dvs. antalet dagar som kampanjen ska äga rum. När du skapar en kampanj som baseras på den här mallen fylls start- och slutdatumet för kampanjen i automatiskt.

  Om kampanjen är återkommande måste du ange kampanjens start- och slutdatum direkt i mallen.

* Ange det **relaterade programmet** för mallen: kampanjer som är baserade på den här mallen är länkade till det valda programmet.

<!--
## Track campaign execution{#campaign-reverse-scheduling}

You can create a schedule for a campaign and track accomplishments, for instance to prepare an event schedule for a specific date. Campaign templates now let you calculate the start date of a task based on the end date of a campaign.


In the task configuration box, go to the **[!UICONTROL Implementation schedule]** area and check the **[!UICONTROL The start date is calculated based on the campaign end date]** box. (Here, "start date" is the task start date). Go to the **[!UICONTROL Start]** field and enter an interval: the task will start this long before the campaign end date. If you enter a period which is longer than the campaign is set to last, the task will begin before the campaign.

![](assets/mrm_task_in_template_start_date.png)

When you create a campaign using this template, the task start date will be calculated automatically. However, you can always change it later.-->
