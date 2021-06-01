---
product: Adobe Campaign
title: Kompatibilitetsmatris för Campaign v8
description: Lär dig system och versioner som är kompatibla med Campaign v8
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 4be3a6dc-0c61-4534-b9dd-6c99c8a037a9,870a336f-94ac-4171-891b-67614feef6ef,bebdd930-c7f6-4629-a489-3c704b33f058,d493e613-eb61-43b1-9c6d-1bd881af0734
source-git-commit: 5363950db5092bc7e0a72a0823db1132a17dda33
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 30%

---

# Kompatibilitetsmatris för Campaign v8

I det här dokumentet visas alla system och komponenter som stöds för den senaste versionen av **Adobe Campaign v8**. Produkter och versioner som inte ingår i den här listan är inte kompatibla med Adobe Campaign.

>[!CAUTION]
>
>* Om inget annat anges stöds alla mindre versioner.
>* Eftersom vissa versioner av dessa system och verktyg från tredje part når slutet av livscykeln, kommer Adobe Campaign inte längre att vara kompatibelt med dessa versioner och kommer att tas bort från den här kompatibilitetsmatrisen. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.


## Kompatibla system

### Client Console{#ClientConsoleoperatingsystems}

:varning: Följande operativsystem och webbläsare krävs för att använda Campaign Client Console.

**Operativsystem**

* **Microsoft Windows Server**  2016, 2012
* **Microsoft Windows** 8, 10 (rekommenderas för japanska förekomster)

**Webbläsare**

**Microsoft Internet Explorer** 11

### CRM-kopplingar{#CRMconnectors}

* **** Salesforceconnector API version 49
* **Microsoft** DynamicConnector, webb-API: Dynamics 365 On-Local and Online

### Federerad dataåtkomst (FDA){#FederatedDataAccessFDA}

* **Amazon Redshift**
* **[!DNL Snowflake]**

### Mobilt SDK{#MobileSDK}

* **Android** 7.x, 8.x, 9.0 med mobil SDK build 1.0.27.
* **Apple iOS** 9 - 14 med mobil SDK build 1.0.26, kompatibelt med 32- och 64-bitarsversioner.

### Webbläsare som stöds {#Browsers}

Följande webbläsare är kompatibla med Campaign for Web Access.

* **Microsoft Edge**,  **Mozilla Firefox**,  **Google Chrome**,  **Safari**  (senaste versionerna)

* **Internet Explorer** 11

## Så här kontrollerar du Campaign-versionen

Använd menyn **Hjälp > Om...** för att kontrollera versionen.

![](assets/ac-version.png)

Du kommer åt följande information:

* **version**-numret för klientkonsolen och programservern. I exemplet ovan är versionen 8.1.5 för både klientkonsolen och programservern.
* SHA-talet mellan parenteser.
* Länk till Adobe kundtjänst.
* Länkar till Adobe sekretesspolicy, användarvillkor och cookies-policy.
