---
title: Kända begränsningar för Campaign v8
description: Kända begränsningar
feature: Overview
role: Data Engineer
level: Beginner
hidefromtoc: true
exl-id: 50c254ba-cc33-49b2-b7d5-12aa69883c07
source-git-commit: e41816003958c3373e92d5ea82240fd7ceda5857
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 1%

---

# Kända begränsningar

Kända begränsningar identifierar funktioner, arkitektur eller processer som inte stöds i den här versionen av produkten, eller som inte fungerar som de ska. Granska dessa begränsningar noggrant.

För Adobe Campaign v8 gäller följande begränsningar:

* Adobe Campaign v8 är inte tillgängligt för anläggningsdistributioner/hybriddistributioner - endast släppt som en Adobe-hanterad Cloud Service.
* Befintliga kunder kan inte migrera från en befintlig Adobe Campaign-miljö till Adobe Campaign v8
* Ingen dubbelriktad datareplikering: replikering sker endast från den lokala Campaign-databasen till molndatabasen
* Angivna funktioner [i det här avsnittet](capability-matrix.md#gs-unavailable-features) är inte tillgängliga i den aktuella versionen av Campaign v8
* Vissa funktioner som inte är tillgängliga eller har tagits bort visas fortfarande i användargränssnittet
* Prenumerations- (opt-in) och avanmälnings- (opt-out) och mobilregistrering är asynkrona processer. Begäranden behandlas varje timme i ett specifikt tekniskt arbetsflöde. [Läs mer](../config/replication.md#tech-wf)
* Dubbletter måste hanteras manuellt av slutanvändarna. [Läs mer](../dev/keys.md)
* Adobe Campaign v8 stöder inte utökad genomströmning i API och webbprogram. Om det finns särskilda behov kan du kontakta Adobe för att få hjälp.
* Adobe Campaign Campaign-optimeringsmodulen tar inte hänsyn till schemalagda leveranser i regler för trycktypologi. Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html?lang=en#setting-the-period).