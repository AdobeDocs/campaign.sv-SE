---
product: campaign
title: Schemaläggare
description: Läs mer om arbetsflödesaktiviteten i schemaläggaren
feature: Workflows
role: User
exl-id: ed70d2d3-251e-4ee8-84d4-73ad03e8dd35
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---

# Schemaläggare {#scheduler}



The **Schemaläggare** är en beständig uppgift som aktiverar övergången vid de tidpunkter som anges i schemat.

**[!UICONTROL Scheduler]**-aktiviteten bör betraktas som en planerad start.  Reglerna för aktivitetspositionering i diagrammet är desamma som för **[!UICONTROL Start]**-aktiviteten.  Den här aktiviteten får inte ha en inkommande övergång.

## Bästa praxis {#best-practices}

* Schemalägg inte ett arbetsflöde så att det körs mer än var 15:e minut eftersom det kan påverka den totala systemprestandan negativt och skapa block i databasen.

* Använd aldrig mer än en **[!UICONTROL Scheduler]** aktivitet per gren i ett arbetsflöde. Se [Använda aktiviteter](workflow-best-practices.md#using-activities).

* Användning av en schemaläggaraktivitet kan leda till att ett arbetsflöde körs flera gånger samtidigt. Du kan till exempel ha en schemaläggare som utlöser arbetsflödeskörningen varje timme, men ibland tar körningen av hela arbetsflödet mer än en timme.

  Du kanske vill hoppa över körningen om arbetsflödet redan körs. Mer information om hur du förhindrar samtidig körning av ett arbetsflöde finns i [den här sidan](monitor-workflow-execution.md#preventing-simultaneous-multiple-executions).

* Observera att övergången kan aktiveras flera timmar senare om arbetsflödet utförde en långvarig uppgift, till exempel en import, eller om wfserver-modulen stoppades en tid. I det här fallet kan det vara nödvändigt att begränsa körningen av den uppgift som har aktiverats av schemaläggaren till ett visst tidsintervall.

## Konfigurera aktiviteten Schemaläggaren {#configuring-scheduler-activity}

Schemaläggaren definierar aktiveringsschemat för övergången. Konfigurera den genom att dubbelklicka på det grafiska objektet och sedan klicka på **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

Med en guide kan du definiera aktivitetens frekvens och giltighetsperiod. Konfigurationsstegen är följande:

1. Välj aktiveringsfrekvens och klicka på **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Ge aktiveringstid och dagar. Parametrarna för det här steget beror på den frekvens som valdes i föregående steg. Om du väljer att starta aktiviteten flera gånger om dagen blir konfigurationsalternativen följande:

   ![](assets/s_user_segmentation_scheduler3.png)

1. Definiera tidsplanens giltighetsperiod eller ange hur många gånger den ska köras.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Kontrollera konfigurationen och klicka på **[!UICONTROL Finish]** att spara.

   ![](assets/s_user_segmentation_scheduler5.png)
