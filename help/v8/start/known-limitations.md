---
product: Adobe Campaign
title: Kända begränsningar för Campaign v8
description: Kända begränsningar
feature: Översikt
role: Data Engineer
level: Beginner
hidefromtoc: true
source-git-commit: 5363950db5092bc7e0a72a0823db1132a17dda33
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 1%

---

# Kända begränsningar

Kända begränsningar identifierar funktioner, arkitektur eller processer som inte stöds i den här versionen av produkten, eller som inte fungerar som de ska. Granska dessa begränsningar noggrant.

För Adobe Campaign v8 gäller följande begränsningar:

* Adobe Campaign v8 är inte tillgängligt för anläggningsdistributioner/hybriddistributioner - endast släppt som en Adobe-hanterad Cloud Service.
* Befintliga kunder kan inte migrera från en befintlig Adobe Campaign-miljö till Adobe Campaign v8
* Ingen dubbelriktad datareplikering: replikering sker endast från den lokala Campaign-databasen till molndatabasen
* Funktioner som anges [i det här avsnittet](capability-matrix.md#gs-unavailable-features) är inte tillgängliga i den aktuella versionen av Campaign v8
* Vissa funktioner som inte är tillgängliga eller har tagits bort visas fortfarande i användargränssnittet
* Prenumerations- (opt-in) och avanmälnings- (opt-out) och mobilregistrering är asynkrona processer. Begäranden behandlas varje timme i ett specifikt tekniskt arbetsflöde. [Läs mer](../config/replication.md#tech-wf)
* ID-hantering - dubbletter - för att bekräfta +-information
* RAD - för att bekräfta + detaljer
* Latens - för att bekräfta +-information
