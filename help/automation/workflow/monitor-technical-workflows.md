---
product: campaign
title: Övervaka tekniska arbetsflöden
description: Övervaka tekniska arbetsflöden
feature: Workflows
role: Admin
version: Campaign v8, Campaign Classic v7
exl-id: 8524d916-8af7-4641-b047-9c348f1017fd
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 5%

---

# Övervaka tekniska arbetsflöden {#monitoring-technical-workflows}

Tekniska arbetsflöden måste övervakas, och åtgärder måste vidtas när de misslyckas.

## Instansövervakningsinstrumentpanel {#instance-monitoring-dashboard}

Instansövervakningens kontrollpanel kan nås via fliken **[!UICONTROL Monitoring]**.

![](assets/monitoring_technical_workflows1.png)

Under Systemindikatorer och grundfiler kontrollerar du att inga indikatorer är markerade i rött. Om så är fallet, och vissa av dem, bör du:

* Kontrollera att de nödvändiga processerna alltid körs,
* Kontrollera att ingen av processerna är för gammal,
* Kontrollera att loggfilerna för de olika processerna inte innehåller alarmerande och återkommande fel.

## Tekniska arbetsflöden {#technical-workflows}

Tekniska arbetsflöden är tillgängliga från **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

Beroende på det tekniska arbetsflödet följer du stegen nedan för att kontrollera att allt fungerar som det ska.

Mer information om vad varje tekniskt arbetsflöde ska göra finns i det här [avsnittet](technical-workflows.md).

För **[!UICONTROL Database Cleanup workflow ('cleanup')]**:

Kontrollera journalen för att verifiera att förfluten tid är relativt konstant över tid och inte stör andra arbetsflöden.

För **[!UICONTROL Tracking workflow ('tracking')]**:

Kontrollera att spårningsarbetsflödet körs som schemalagt (varje timme som standard) och att journalen inte visar återkommande fel. Mer information om detta hittar du i det här [avsnittet](delivery.md).

För **[!UICONTROL Deliverability update ('deliverabilityUpdate')]**:

1. Kontrollera att arbetsflödet för **[!UICONTROL Deliverability update]** körs och avslutas varje dag.
1. Kontrollera i journalen att reglerna uppdateras regelbundet.

För **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. Titta på alla arbetsflöden som finns i mappen **[!UICONTROL Campaign process]**. Se denna [sida](technical-workflows.md) för mer information om detta.
1. Kontrollera att arbetsflödena körs som schemalagda och att journalen inte visar återkommande fel.

## Arbetsflödesövervakning {#workflow-supervision}

Gruppen **[!UICONTROL Workflow supervisors]** ska innehålla operatorer som måste hållas informerade om fel och som kan vidta åtgärder i tid.

![](assets/monitoring_technical_workflows3.png)

En varning ska genereras och skickas till rätt grupp om ett problem uppstår.

Kontrollera att alla operatorer har en giltig e-postadress.

Alla arbetsflöden som ska köras för att plattformen ska fungera, t.ex. daglig dataimport, ska deklareras som &quot;Produktion&quot; (kryssruta) och visas i fet stil.

## Underhållslista för arbetsflöde {#workflow-maintenance-list}

Alla anpassade tekniska arbetsflöden bör dokumenteras i ett kalkylblad som innehåller:

* Arbetsflödets namn och plats.
* Syfte.
* Planering och beroenden.
* Ansvarig för övervakning.
* Instruktioner om vad som ska göras om fel uppstår.

![](assets/monitoring_technical_workflows4.png)

## Planering och automatisering av övervakning {#planning-and-automation-of-monitoring}

Övervakning av planeringsarbetsflöde förbättrar effektiviteten. Vissa uppgifter måste utföras dagligen medan andra uppgifter kan utföras varje vecka eller månad.

Genom att ställa in arbetsflöden i mappar som namnges av upprepningar och sorteras efter körningsschema blir övervakningen effektivare.

Automatisering av övervakning minskar de totala kostnaderna för resurser och ser till att aktiviteterna schemaläggs med rätt frekvens.

Du kan skapa ett övervakningsarbetsflöde för att skicka ett e-postmeddelande när vissa uppgifter misslyckas eller när en viktig tabell blir för stor.

Du kan skapa en vy så att alla arbetsflöden i ett funktionsområde eller hela systemet kan övervakas.

Du kan också använda Adobe Campaign-jobbet eller rapportfunktionen för att skapa dokumentation på begäran, som alltid är aktuell.
