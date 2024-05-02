---
product: campaign
title: Granskningskedja
description: Lär dig övervaka instansen med granskningsspår för Campaign
feature: Audit Trail, Monitoring, Workflows
source-git-commit: bb74393f0b24fa5b9781eee15c4527daba527192
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---

# Granskningskedja{#audit-trail}

The **[!UICONTROL Audit trail]** i Adobe Campaign finns detaljinformation om alla ändringar som gjorts på viktiga enheter i instansen, vanligtvis sådana som avsevärt påverkar en mjuk funktion i instansen. Den fungerar som en realtidslogg och innehåller en detaljerad lista över åtgärder och händelser allt eftersom de inträffar.

>[!NOTE]
>
>Adobe Campaign granskar inte ändringar som gjorts i användarrättigheter, mallar, personalisering eller kampanjer.\
>Granskningsspårning kan bara hanteras av administratörer för instansen.

+++ Läs mer om tillgängliga enheter för granskningsspår

* **Schema - granskningsspår**: låter dig utforska de ändringar du gjort i dina scheman samt identifiera vem som gjort ändringarna och när de gjordes.

  Mer information om scheman finns i [page](../dev/schemas.md).

* **Granskningsspår för arbetsflöde** spårar alla åtgärder som rör dina arbetsflöden, inklusive:

   * Starta
   * Pausa
   * Stoppa
   * Starta om
   * Rensning som motsvarar åtgärden Rensa historik
   * Simulera vilket motsvarar åtgärden Starta i simuleringsläge
   * Aktivering som är lika med åtgärden Kör väntande uppgifter nu
   * Ovillkorligt stopp

  Mer information om arbetsflöden finns i [page](../../automation/workflow/about-workflows.md).

  Mer information om hur du övervakar arbetsflöden finns i [dedikerad sektion](../../automation/workflow/monitor-workflow-execution.md).

* **Alternativ granskningsspår** gör att du kan kontrollera aktiviteter och de senaste ändringarna som du har gjort.

  Mer information om alternativen finns i [page](https://experienceleague.adobe.com/en/docs/campaign-classic/using/installing-campaign-classic/appendices/configuring-campaign-options).

* **Granskningsspår för leverans** gör att du kan kontrollera aktiviteter och senaste ändringar som gjorts i leveranserna.

  Mer information om leveranser finns i [page](../start/create-message.md).

* **Externt konto** gör det möjligt att kontrollera ändringar som gjorts i externa konton, som används av tekniska processer som tekniska arbetsflöden eller kampanjarbetsflöden.

  Mer information om externt konto finns i [page](../config/external-accounts.md).

* **Leveransmappning** Med kan du övervaka aktiviteter och nyligen gjorda ändringar i leveransmappningar.

  Mer information om leveransmappning finns i [page](../audiences/target-mappings.md).

* **Webbprogram** Med kan du kontrollera ändringar som gjorts i webbformulär i Campaign V8 som används för att skapa sidor med indata- och urvalsfält, och som kan innehålla data från databasen.

  Mer information om webbprogram finns i [page](../dev/webapps.md).

* **Erbjudande** gör att du kan kontrollera aktiviteter och senaste ändringar som gjorts i dina erbjudanden.

  Mer information finns i [page](../interaction/interaction.md).

* **Operator** gör att du kan övervaka aktiviteter och nyligen gjorda ändringar av dina operatorer.

  Mer information om operatorer finns i [page](../interaction/interaction-operators.md).

+++

## Åtkomst till granskningsspår {#accessing-audit-trail}

Så här kommer du åt instansens **[!UICONTROL Audit trail]**:

1. Öppna **[!UICONTROL Explorer]** -menyn för instansen.

1. Under **[!UICONTROL Administration]** meny, välja **[!UICONTROL Audit]** sedan **[!UICONTROL Audit Trail]**.

   ![](assets/audit-trail-1.png)

1. The **[!UICONTROL Audit trail]** öppnas med listan över dina enheter. Adobe Campaign granskar åtgärderna för att skapa, redigera och ta bort för olika enheter.

   Välj en av enheterna om du vill veta mer om de senaste ändringarna.

1. The **[!UICONTROL Audit entity]** I fönstret finns mer detaljerad information om den valda enheten, till exempel:

   * **[!UICONTROL Type]**: Arbetsflöde, alternativ, leveranser eller scheman.
   * **[!UICONTROL Entity]**: Internt namn på dina aktiviteter.
   * **[!UICONTROL Modified by]**: Användarnamn för den sista personen som senast ändrade den här entiteten.
   * **[!UICONTROL Action]**: Senaste åtgärden som utfördes på den här entiteten, antingen Skapad, Ändrad eller Borttagen.
   * **[!UICONTROL Modification date]**: Datum för den senaste åtgärden som utfördes på den här entiteten.

   ![](assets/audit-trail-2.png)

>[!NOTE]
>
>Som standard är kvarhållningsperioden 180 dagar för **[!UICONTROL Audit logs]**. Det här värdet kan ändras i distributionsguiden.

## Aktivera/inaktivera granskningsspår {#enable-disable-audit-trail}

Granskningsspårning kan enkelt aktiveras eller inaktiveras för en viss aktivitet om du t.ex. vill spara utrymme i databasen.

För att göra detta:

1. Öppna **[!UICONTROL Explorer]** -menyn för instansen.

1. Under **[!UICONTROL Administration]** meny, välja **[!UICONTROL Platform]** sedan **[!UICONTROL Options]**.

1. Välj något av följande alternativ beroende på vilken enhet du vill aktivera/inaktivera:

   * För arbetsflöde: **[!UICONTROL XtkAudit_Workflows]**
   * För scheman: **[!UICONTROL XtkAudit_DataSchema]**
   * För alternativ: **[!UICONTROL XtkAudit_Option]**
   * För leveranser: **[!UICONTROL XtkAudit_Delivery]**
   * För externt konto: **[!UICONTROL XtkAudit_ExtAccount]**
   * För leveransmappning: **[!UICONTROL XtkAudit_DeliveryMapping]**
   * För webbprogram: **[!UICONTROL XtkAudit_WebApp]**
   * Erbjudande: **[!UICONTROL XtkAudit_Offer]**
   * För operator: **[!UICONTROL XtkAudit_Operator]**
   * För varje enhet: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit-trail-3.png)

1. Ändra **[!UICONTROL Value]** till 1 om du vill aktivera enheten eller till 0 om du vill inaktivera den.

   ![](assets/audit-trail-4.png)

1. Klicka på **[!UICONTROL Save]**.
