---
title: Kompatibilitetsmatris för Campaign v8
description: Lär dig system och versioner som är kompatibla med Campaign v8
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 4be3a6dc-0c61-4534-b9dd-6c99c8a037a9,870a336f-94ac-4171-891b-67614feef6ef,bebdd930-c7f6-4629-a489-3c704b33f058,d493e613-eb61-43b1-9c6d-1bd881af0734
source-git-commit: f89bc8baeb4b934bdde6b6fd33ee494195ab61b3
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 32%

---

# Kompatibilitetsmatris för Campaign v8

Det här dokumentet listar alla system och komponenter som stöds för den senaste builden av **Adobe Campaign v8**. Om inget annat anges stöds alla mindre versioner. Produkter och versioner som inte ingår i den här listan är inte kompatibla med Adobe Campaign.

Eftersom vissa versioner av dessa system och verktyg från tredje part når slutet av livscykeln, kommer Adobe Campaign inte längre att vara kompatibelt med dessa versioner och kommer att tas bort från den här kompatibilitetsmatrisen. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

>[!NOTE]
>
>Adobe Campaign Server och Client Console måste finnas i samma version. [Lär dig hur du kontrollerar din version](#version).

## Klientkonsol{#ClientConsoleoperatingsystems}

Följande operativsystem och webbläsare krävs för att använda klientkonsolen i Campaign. [Läs mer](connect.md).

### Operativsystem

* **Microsoft Windows Server** 2019, 2016, 2012
* **Microsoft Windows** 11 (med början Campaign v8.3), 10, 8,

>[!NOTE]
>
>Microsoft Windows 10 rekommenderas för japanska förekomster.

### Webbläsare

**Microsoft Internet Explorer** 11

## CRM-kopplingar{#CRMconnectors}

CRM (Customer Relationship Management)-system som är kompatibla med Adobe Campaign listas nedan. [Läs mer](../connect/crm.md).

* **Salesforce** API för anslutning version 49
* **Microsoft Dynamics** koppling, webb-API: Dynamics 365 On-Local and Online

## Federerad dataåtkomst (FDA){#FederatedDataAccessFDA}

Externa databaser som är kompatibla med Adobe Campaign FDA-modulen (Federated Data Access) listas nedan. [Läs mer](../connect/fda.md).

* **Amazon Redshift**
* **[!DNL Google Big Query]**
* **[!DNL Snowflake]**
* **[!DNL Vertica]**

## Mobilt SDK{#MobileSDK}

Du kan använda Campaign för att skicka [push-meddelanden](../send/push.md) i de operativsystem som anges nedan med tillhörande mobil-SDK.

* **Android** 12 (med början Campaign v8.3), 9.0, 8.x, 7.x, med Campaign Android SDK build 1.1.1.
* **Apple iOS** 9 - 15 med Campaign iOS SDK build 1.0.26, kompatibelt med 32- och 64-bitarsversioner. iOS 15 stöds från och med Campaign v8.

## Webbåtkomst

Följande webbläsare är kompatibla med Campaign för [Web Access](connect.md#web-access).

* **Microsoft Edge**, **Mozilla Firefox**, **Google Chrome**, **Safari** (senaste versionerna)

## Så här kontrollerar du Campaign-versionen och bygget{#version}

Öppna **Hjälp > Om...** -menyn för att kontrollera versionen.

![](assets/ac-version.png)

Du kommer åt följande information:

* The **version** numret på klientkonsolen och programservern. I exemplet ovan är versionen 8.1.5 för både klientkonsolen och programservern.
* SHA-talet mellan parenteser.
* Länk till Adobe kundtjänst.
* Länkar till Adobe sekretesspolicy, användarvillkor och cookies-policy.
