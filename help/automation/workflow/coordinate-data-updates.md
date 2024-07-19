---
product: campaign
title: Koordinera datauppdateringar
description: Koordinera datauppdateringar
feature: Workflows, Data Management
role: User
exl-id: 9faf7ee7-07c1-415b-b234-a945994792c7
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# Koordinera datauppdateringar{#coordinating-data-updates}



I det här användningsexemplet beskrivs hur du skapar ett arbetsflöde som gör att du kan hantera samtidiga uppdateringar när du använder flera körningar av ett arbetsflöde.

Syftet är att kontrollera att uppdateringsprocessen har avslutats innan en annan uppdateringsåtgärd körs. För att göra detta skapar vi en instansvariabel och låter arbetsflödet testa om instansen körs för att bestämma om körningen av arbetsflödet ska fortsätta eller inte och utföra uppdateringen.

![](assets/uc_dataupdate_wkf.png)

Det här arbetsflödet består av:

* en **schemaläggaraktivitet** som kör arbetsflödet med en viss frekvens.
* en **Test**-aktivitet som kontrollerar om arbetsflödet redan körs.
* **Fråga** och **Uppdatera data** om arbetsflödet inte redan körs, följt av en **End**-aktivitet som initierar om arbetsflödesinstansvariabeln till false.
* En **End**-aktivitet om arbetsflödet redan körs.

Följ stegen nedan för att skapa arbetsflödet:

1. Lägg till en **schemaläggaraktivitet** och konfigurera sedan dess frekvens efter dina behov.
1. Lägg till en **Test**-aktivitet för att kontrollera om arbetsflödet redan körs och konfigurera den enligt nedan.

   >[!NOTE]
   >
   >&quot;isRunning&quot; är instansvariabelnamnet som vi har valt för det här exemplet. Det här är inte en inbyggd variabel.

   ![](assets/uc_dataupdate_test.png)

1. Lägg till en **End**-aktivitet i **No**-gaffeln. På så sätt kommer inget att köras om arbetsflödet redan körs.
1. Lägg till önskade aktiviteter i **Ja**-gaffeln. I det här fallet **Aktiviteter för** och **Uppdatera data**.
1. Öppna den första aktiviteten och lägg sedan till kommandot **instance.vars.isRunning = true** på fliken **[!UICONTROL Advanced]**. På så sätt ställs instansvariabeln in som running.

   ![](assets/uc_dataupdate_query.png)

1. Lägg till en **End**-aktivitet i slutet av **[!UICONTROL Yes]**-gaffeln och lägg sedan till kommandot **instance.vars.isRunning = false** på fliken **[!UICONTROL Advanced]**.

   På så sätt kommer ingen åtgärd att utföras så länge arbetsflödet körs.

   ![](assets/uc_dataupdate_end.png)

**Relaterade ämnen:**

* [Förhindra samtidiga körningar](monitor-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Uppdatera dataaktivitet](update-data.md)
