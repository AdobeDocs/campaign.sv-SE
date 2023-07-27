---
title: Skyddsutkast för Campaign v8
description: Skyddsutkast för Campaign v8
feature: Overview
role: User
level: Beginner, Intermediate, Experienced
exl-id: 50c254ba-cc33-49b2-b7d5-12aa69883c07
source-git-commit: 754a575b4359633f2bba5c51598725ca577b28d5
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# Produktskyddsräcken{#guardrails}

Tillstånd, produktbegränsningar och prestandaskydd finns i [Adobe Campaign Managed Cloud Services produktbeskrivningssida](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Nedan finns ytterligare skyddsutkast och begränsningar när du använder [!DNL Adobe Campaign].

Garantier och begränsningar identifierar funktioner, arkitektur eller processer som inte stöds i den här versionen av produkten, eller som inte fungerar som de ska. Granska dessa begränsningar noggrant.

* Adobe Campaign v8 är inte tillgängligt för anläggningsdistributioner/hybriddistributioner - endast som en Adobe-hanterad Cloud Service
* Ingen automatisk migrering till Adobe Campaign v8 är tillgänglig för befintliga kunder
* När det gäller en [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), ingen dubbelriktad datareplikering tillhandahålls: replikering sker endast från den lokala Campaign-databasen till molndatabasen
* Angivna funktioner [i det här avsnittet](v7-to-v8.md#gs-unavailable-features) är inte tillgängliga i den aktuella versionen av Campaign v8
* Vissa funktioner som inte är tillgängliga eller har tagits bort visas fortfarande i användargränssnittet
* När det gäller en [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), prenumerationer (deltagande) och avanmälan (avanmälan) och mobilregistrering är asynkrona processer. Begäranden behandlas varje timme i ett specifikt tekniskt arbetsflöde. [Läs mer](../architecture/replication.md#tech-wf)
* När det gäller en [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md)måste dubbletter hanteras manuellt av slutanvändarna. [Läs mer](../architecture/keys.md)
* Adobe Campaign v8 stöder inte utökad genomströmning i API och webbprogram - om det finns särskilda behov kan du kontakta Adobe för att få hjälp
* När det gäller en [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md)Adobe Campaign Campaign Optimization Module tar inte hänsyn till schemalagda leveranser i regler för trycktypologi. Läs mer i [den här sidan](../../automation/campaign-opt/pressure-rules.md)