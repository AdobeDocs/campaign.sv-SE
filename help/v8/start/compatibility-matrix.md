---
title: Kompatibilitetsmatris för Campaign v8
description: Upptäck system och versioner som är kompatibla med Campaign v8
feature: Overview
role: Admin
level: Beginner, Intermediate, Experienced
exl-id: 4be3a6dc-0c61-4534-b9dd-6c99c8a037a9,870a336f-94ac-4171-891b-67614feef6ef,bebdd930-c7f6-4629-a489-3c704b33f058,d493e613-eb61-43b1-9c6d-1bd881af0734
source-git-commit: dcb12339d891c61f308cf7b7e518784f3ba1ff31
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 31%

---

# Kompatibilitetsmatris för Campaign v8

Det här dokumentet listar alla system och komponenter som stöds för den senaste builden av **Adobe Campaign v8**. Om inget annat anges stöds alla mindre versioner. Produkter och versioner som inte ingår i den här listan är inte kompatibla med Adobe Campaign.

Eftersom vissa versioner av dessa system och verktyg från tredje part når slutet av livscykeln, kommer Adobe Campaign inte längre att vara kompatibelt med dessa versioner och kommer att tas bort från den här kompatibilitetsmatrisen. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

>[!NOTE]
>
>Adobe Campaign Server och Client Console måste finnas i samma version. [Lär dig hur du kontrollerar din version](#version).

## Klientkonsol{#ClientConsoleoperatingsystems}

Följande operativsystem och webbläsare krävs för att använda klientkonsolen i Campaign. [Läs mer](connect.md).

>[!NOTE]
>
>Observera att 32-bitarsversionen av klientkonsolen kommer att bli inaktuell i version 8.5. Från och med 8.6 är klientkonsolen endast tillgänglig i 64 bitar. Mer information om hur du uppgraderar ditt operativsystem finns i [technote](https://experienceleague.corp.adobe.com/docs/campaign/technotes-ac/tn-new/console.html).

### Operativsystem{#op-systems}

* **Microsoft Windows Server** 2019, 2016, 2012
* **Microsoft Windows** 11, 10, 8

### Webbläsare{#web-browsers}

* **Microsoft Edge**

* **Microsoft Edge WebView2**, senaste versionen. Hämta den från [Microsoft Developer Site](http://www.adobe.com/go/acc-ms-webview2-runtime-download){target="_blank"}.

## CRM-kopplingar{#CRMconnectors}

CRM (Customer Relationship Management)-system som är kompatibla med Adobe Campaign listas nedan. [Läs mer](../connect/crm.md).

* **Salesforce** API för anslutning version 49
* **Microsoft Dynamics** koppling, webb-API: Dynamics 365 lokalt och online

## Federerad dataåtkomst (FDA){#FederatedDataAccessFDA}

Externa databaser som är kompatibla med Adobe Campaign FDA-modulen (Federated Data Access) listas nedan. [Läs mer](../connect/fda.md).

* **Amazon Redshift**
* **[!DNL Google Big Query]**
* **[!DNL Snowflake]**
* **[!DNL Vertica]**

## Mobil-SDK{#MobileSDK}

Skicka [push-meddelanden](../send/push.md) Med Campaign kan du använda Adobe Experience Platform Mobile SDK genom att konfigurera Adobe Campaign Classic-tillägget i användargränssnittet för datainsamling.


## Webbåtkomst{#web-access}

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
