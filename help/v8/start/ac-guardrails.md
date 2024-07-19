---
title: Skyddsutkast för Campaign v8
description: Skyddsutkast för Campaign v8
feature: Configuration
role: User
level: Beginner
exl-id: 50c254ba-cc33-49b2-b7d5-12aa69883c07
source-git-commit: f577ee6d303bab9bb07350b60cf0fa6fc9d3a163
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 2%

---

# Produktskyddsräcken{#guardrails}

Tillstånd, produktbegränsningar och prestandaskydd visas på [Adobe Campaign Managed Cloud Services produktbeskrivningssida](https://helpx.adobe.com/se/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Nedan finns ytterligare skyddsutkast och begränsningar när du använder [!DNL Adobe Campaign].

Garantier och begränsningar identifierar funktioner, arkitektur eller processer som inte stöds i den här versionen av produkten, eller som inte fungerar som de ska. Granska dessa begränsningar noggrant.

* Adobe Campaign v8 är inte tillgängligt för anläggningsdistributioner/hybriddistributioner - endast som en Adobe-hanterad Cloud Service
* Ingen automatisk migrering till Adobe Campaign v8 är tillgänglig för befintliga kunder
* Ingen dubbelriktad datareplikering tillhandahålls i samband med en [Enterprise-distribution (FFDA)](../architecture/enterprise-deployment.md): replikering sker endast från den lokala Campaign-databasen till molndatabasen
* Funktioner som anges [ i det här avsnittet](v7-to-v8.md#gs-unavailable-features) är inte tillgängliga i den aktuella Campaign v8-versionen
* Vissa funktioner som inte är tillgängliga eller har tagits bort visas fortfarande i användargränssnittet
* I samband med en [Enterprise-distribution](../architecture/enterprise-deployment.md) (FFDA) är funktionerna för prenumeration (opt-in) och avanmälan (opt-out) samt Mobile-registrering asynkrona processer. Begäranden behandlas varje timme i ett specifikt tekniskt arbetsflöde. [Läs mer](../architecture/replication.md#tech-wf)
* I kontexten för en [Enterprise (FFDA)-distribution](../architecture/enterprise-deployment.md) måste dubbletter hanteras manuellt av slutanvändare. [Läs mer](../architecture/keys.md)
* Adobe Campaign v8 stöder inte utökad genomströmning i API och webbprogram - om det finns särskilda behov kan du kontakta Adobe för att få hjälp
* I samband med en [Enterprise-distribution](../architecture/enterprise-deployment.md) (FFDA) tar Adobe Campaign Campaign Optimization-modulen inte hänsyn till schemalagda leveranser i regler för trycktypologi. Läs mer på [den här sidan](../../automation/campaign-opt/pressure-rules.md)