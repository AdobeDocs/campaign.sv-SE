---
product: campaign
title: AND-join
description: AND-join
feature: Workflows
role: User
version: Campaign v8, Campaign Classic v7
exl-id: c70a106d-3518-4eac-9944-6f7c93d85bac
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 5%

---

# AND-join{#and-join}



En join utlöser sin utgående övergång endast när alla inkommande övergångar är aktiverade, dvs. när alla tidigare aktiviteter är slutförda. På så sätt kan du se till att vissa aktiviteter har slutförts innan du fortsätter att köra arbetsflödet.

Du kan till exempel använda en AND-join-aktivitet när du skapar innehåll och skickar automatisering för att se till att en leverans bara startas när målfrågor och innehållsuppdateringar är klara. Ett ärende för dedikerad användning finns i

![](assets/and-join-usage.png)

>[!NOTE]
>
>Observera att inkommande övergångar som har konfigurerats med olika målinriktningsdimensioner inte kan kombineras med en **[!UICONTROL AND-join]**-aktivitet.

Den utgående skickade populationen av aktiviteten bestäms genom att en huvuduppsättning väljs bland de inkommande övergångarna i aktiviteten.

Den utgående övergången kan bara innehålla en av de ingående övergångspopulationerna. Om aktiviteten inte är konfigurerad kommer den utgående övergången att slumpmässigt välja en av de inkommande populationerna.

>[!CAUTION]
>
>När det gäller aktiviteter av typen **AND-join** sammanfogas händelsvariablerna, men om samma variabel har definierats två gånger uppstår en konflikt och värdet är obestämt. Mer information om detta finns i [det här avsnittet](javascript-scripts-and-templates.md#event-variables).
