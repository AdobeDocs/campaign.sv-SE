---
product: campaign
title: Schemaläggare
description: Läs mer om arbetsflödesaktiviteten i schemaläggaren
feature: Workflows
role: User
exl-id: ed70d2d3-251e-4ee8-84d4-73ad03e8dd35
source-git-commit: ba8cf031db178f6575104858340e16d4e7bd6a31
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 8%

---

# Schemaläggare {#scheduler}



**Schemaläggaren** är en beständig aktivitet som aktiverar övergången vid de tidpunkter som anges i schemat.

**[!UICONTROL Scheduler]**-aktiviteten bör betraktas som en planerad start.  Reglerna för aktivitetspositionering i diagrammet är desamma som för **[!UICONTROL Start]**-aktiviteten.  Den här aktiviteten får inte ha en inkommande övergång.

## Bästa praxis {#best-practices}

**Starta om arbetsflödet efter ändring av tidsplanering** - När du ändrar den schemalagda tiden för aktiviteten **[!UICONTROL Scheduler]** är det viktigt att starta om arbetsflödet. Detta garanterar att arbetsflödet körs vid de uppdaterade tidpunkterna. Utan att starta om fortsätter arbetsflödet att köras enligt det gamla schemat.

**Begränsa schemaläggarfrekvens** - Undvik schemaläggning av arbetsflöden så att de körs oftare än var femtonde minut. Om du kör dem oftare kan systemprestanda försämras och databasbelastningen ökar.

**Använd en schemaläggare per gren** - Varje gren i ditt arbetsflöde ska bara ha en **[!UICONTROL Scheduler]**-aktivitet. Mer information om de effektivaste strategierna för att använda aktiviteter i arbetsflöden finns på [sidan ](workflow-best-practices.md#using-activities) Arbetsflöden för bästa praxis.

**Förhindra samtidig körning av arbetsflöden** - Om ett arbetsflöde aktiveras av en schemaläggare bör du tänka på att flera instanser av arbetsflödet kan köras samtidigt. Om en schemaläggare till exempel utlöser arbetsflödet varje timme, men arbetsflödeskörningen tar mer än en timme, kan det resultera i överlappande körningar. Undvik detta genom att konfigurera kontroller för att förhindra flera samtidiga körningar. [Lär dig hur du förhindrar samtidig körning av flera arbetsflöden](monitor-workflow-execution.md#preventing-simultaneous-multiple-executions).

**Konto för fördröjda övergångar** - Övergångar som utlöses av schemaläggaren kan fördröjas om arbetsflödet kör långvariga aktiviteter (som importer) eller om wfserver-modulen har stoppats tillfälligt. Begränsa aktiveringstiderna för schemaläggaren för att se till att aktiviteterna körs inom ett angivet tidsfönster.

## Konfigurera aktiviteten Schemaläggaren {#configuring-scheduler-activity}

Schemaläggaren definierar aktiveringsschemat för övergången. Om du vill konfigurera det dubbelklickar du på det grafiska objektet och sedan på **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

Med en guide kan du definiera aktivitetens frekvens och giltighetsperiod. Konfigurationsstegen är följande:

1. Välj aktiveringsfrekvens och klicka på **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Ge aktiveringstid och dagar. Parametrarna för det här steget beror på den frekvens som valdes i föregående steg. Om du väljer att starta aktiviteten flera gånger om dagen blir konfigurationsalternativen följande:

   ![](assets/s_user_segmentation_scheduler3.png)

1. Definiera tidsplanens giltighetsperiod eller ange hur många gånger den ska köras.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Kontrollera konfigurationen och klicka på **[!UICONTROL Finish]** för att spara.

   ![](assets/s_user_segmentation_scheduler5.png)
