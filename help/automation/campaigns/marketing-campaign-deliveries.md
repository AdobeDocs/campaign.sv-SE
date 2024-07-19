---
product: campaign
title: Leveranser av marknadsföringskampanjer
description: Läs mer om kampanjleveranser
feature: Campaigns, Resource Management, Cross Channel Orchestration
role: User
exl-id: 1d9638cb-0fc9-4d04-a9c5-bcab8f4ebe95
source-git-commit: c3f4ad0b56dd45d19eebaa4d2f06551c8fecac1d
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 1%

---

# Leveranser av marknadsföringskampanjer {#marketing-campaign-deliveries}

Samordna era flerkanalsleveranser i era kampanjer: effektivisera kommunikationen med Adobe Campaign via personaliserade e-postmeddelanden, SMS, push-meddelanden och meddelanden i appen. Du kan använda multimedia som videor, känslolägesikoner eller GIF och integrera dem direkt.

Leveranser kan skapas via kampanjkontrollpanelen, ett kampanjarbetsflöde eller direkt via leveransöversikten. När leveranser skapas från en kampanj länkas de till den här kampanjen och konsolideras på kampanjnivå.

## Skapa leveranser {#create-deliveries}

Det finns två sätt att lägga till leveranser till era marknadsföringskampanjer:

* Från länken **[!UICONTROL Add a delivery]** i kampanjinstrumentpanelen.

![](assets/campaign_op_add_delivery.png)

När leveransen har sparats läggs den till på kampanjkontrollpanelen.

* Från ett kampanjarbetsflöde på fliken **[!UICONTROL Targeting and workflows]** genom att lägga till leveransen.

  ![](assets/campaign-wf-delivery.png)

  När arbetsflödet har startats läggs leveransen till på kontrollpanelen för kampanjer.

Lär dig hur du konfigurerar och kör leveransgodkännandeflödet [på den här sidan](marketing-campaign-approval.md).

## Starta en leverans {#start-a-delivery}

En leverans kan skickas när alla godkännanden har beviljats. Körningsprocessen beror på kanalen.

* Information om leveranser via e-post eller mobilkanal finns i [det här avsnittet](#start-an-online-delivery)

* För direktreklam, se [det här avsnittet](#start-an-offline-delivery)

### Påbörja e-post- eller mobilleverans {#start-an-online-delivery}

När alla godkännandebegäranden har beviljats ändras leveransstatusen till **[!UICONTROL Pending confirmation]** och kan startas. Granskare som kan starta leveransen får ett meddelande om att en leverans är klar att startas.

![](assets/confirm-delivery.png)

Informationen visas också på kampanjkontrollpanelen. Med länken **[!UICONTROL Confirm delivery]** kan du påbörja leveransen.

![](assets/confirm-delivery-from-dashboard.png)

Bekräftelsen av leveransen är begränsad till administratörer och till den operatör eller grupp av operatorer som uttryckligen anges i leverans- eller kampanjegenskaperna. Om ingen operator är utformad kan administratörer och kampanjägaren godkänna.

![](assets/select-delivery-reviewers.png)

Du kan även tillåta kampanjägaren att bekräfta sändningen, även om specifika granskare har definierats i leverans- eller kampanjegenskaperna. Om du vill göra det som administratör skapar du alternativet **NmsCampaign_Activate_OwnerConfirmation** och anger det som **1**. Alternativen hanteras från mappen **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** i Campaign Explorer.


### Starta direktleverans av e-post {#start-an-offline-delivery}

När alla godkännanden har beviljats ändras leveransstatusen till **[!UICONTROL Pending extraction]**. Extraheringsfilerna skapas med ett dedikerat [tekniskt arbetsflöde](../workflow/technical-workflows.md) som i en standardkonfiguration startar automatiskt när en direktmeddelandeleverans väntar på extrahering. När en process pågår visas den på kontrollpanelen och kan redigeras via länken.

När extraheringsarbetsflödet har körts måste extraheringsfilen godkännas (förutsatt att godkännande av extraheringsfilen har valts i leveransinställningarna). [Läs mer](marketing-campaign-approval.md#approving-an-extraction-file).

Följ stegen nedan för att validera innehåll och skicka filen till leverantören:

1. När extraheringsfilen har godkänts kan du generera ett korrektur av routerns e-postmeddelande. Det här e-postmeddelandet är konstruerat baserat på en leveransmall. Det måste godkännas.

   Det här steget är bara tillgängligt om alternativet **[!UICONTROL Enable the sending and validation of proofs (Direct mail)]** aktiverades på fliken **[!UICONTROL Approvals]** för de avancerade kampanjparametrarna.

   ![](assets/enable-proof-validation.png)

1. Klicka på knappen **[!UICONTROL Send a proof]** för att skapa korrektur.

   Korrekturmålet måste definieras i förväg.

   Du kan skapa så många korrektur som behövs. Dessa nås via länken **[!UICONTROL Direct mail...]** i leveransinformationen.

1. Leveransstatusen ändras till **[!UICONTROL To submit]**. Klicka på knappen **[!UICONTROL Submit proofs]** för att starta godkännandeprocessen.

1. Leveransstatusen ändras till **[!UICONTROL Proof to validate]** och med en knapp kan du acceptera eller avvisa godkännande.

   Du kan antingen godkänna eller avvisa det här godkännandet eller återgå till extraheringssteget.

1. När korrekturet är godkänt skickas extraheringsfilen till routern och leveransen är klar.

### Budget- och kostnadsberäkning {#compute-costs-and-stocks}

Filextraheringen startar två processer: budgetberäkning och lagerberäkning. Budgetposterna uppdateras.

* På fliken **[!UICONTROL Budget]** kan du hantera budgeten för kampanjen. Summan av kostnadsposterna visas i fältet **[!UICONTROL Calculated cost]** på kampanjens huvudflik och det program som den tillhör. Beloppen återspeglas också i kampanjbudgeten.

  ![](assets/campaign-budget-tab.png)

  Den verkliga kostnaden kommer till slut att beräknas utifrån information som tillhandahålls av routern. Endast meddelanden som skickas faktureras.

* Stock definieras i noden **[!UICONTROL Administration > Campaign management > Stocks]** i trädet.

  ![](assets/campaign-stocks.png)

  Kostnadsstrukturer i noden **[!UICONTROL Administration > Campaign management > Service providers]**.

  ![](assets/campaign-service-providers.png)

  Lagerrader visas i lagersektionen. Om du vill definiera det ursprungliga lagret öppnar du en aktielinje. Lagret minskas varje gång en leverans sker. Du kan definiera en varningsnivå och meddelanden.


  >[!NOTE]
  >
  >Läs mer om budgeten [i det här avsnittet](providers-stocks-and-budgets.md).
