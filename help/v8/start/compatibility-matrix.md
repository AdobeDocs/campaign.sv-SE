---
title: Kompatibilitetsmatris för Campaign v8
description: Upptäck system och versioner som är kompatibla med Campaign v8
feature: Release Notes
role: Admin
level: Beginner
exl-id: 4be3a6dc-0c61-4534-b9dd-6c99c8a037a9
source-git-commit: 329130d716054e5054fc0a5989a77d950c546ec0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 19%

---

# Kompatibilitetsmatris för Campaign v8 {#compat-matrix}

I det här dokumentet visas alla system och komponenter som stöds för den senaste versionen av **Adobe Campaign v8** klientkonsolen. Om inget annat anges stöds alla mindre releaser. Produkter och versioner som inte ingår i den här listan är inte kompatibla med Adobe Campaign.

Eftersom vissa versioner av dessa system och verktyg från tredje part når slutet av livscykeln, kommer Adobe Campaign inte längre att vara kompatibelt med dessa versioner och kommer att tas bort från den här kompatibilitetsmatrisen. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

>[!NOTE]
>
>Adobe Campaign server och Campaign-klientkonsolen måste vara i samma version. [Lär dig kontrollera din version](upgrades.md#version).

## Klientkonsol {#ClientConsoleoperatingsystems}

Följande operativsystem och webbläsare krävs för att använda Campaign-klientkonsolen. [Läs mer](connect.md).

### Operativsystem {#op-systems}

* **Microsoft Windows Server** 2019, 2016
* **Microsoft Windows** 11, 10

>[!NOTE]
>32-bitarsversionen av klientkonsolen har tagits bort sedan version 8.5. Från och med 8.6 är klientkonsolen endast tillgänglig med 64 bitar. Mer information om hur du uppgraderar systemet finns i denna [technote](../../technotes/upgrades/console.md).

### Webbläsare {#web-browsers}

* **Microsoft Edge**

* **Microsoft Edge WebView2**, senaste versionen. Hämta den från [Microsoft Developer site](http://www.adobe.com/go/acc-ms-webview2-runtime-download){target="_blank"}.

## CRM-kopplingar {#CRMconnectors}

CRM (Customer Relationship Management)-system som är kompatibla med Adobe Campaign listas nedan. Läs mer om CRM-anslutningar [på den här sidan](../connect/crm.md).

* **Salesforce** API-version 49 för anslutning
* **Microsoft Dynamics**-anslutning, webb-API: Dynamics 365 lokalt och online

## Federerad dataåtkomst (FDA){#FederatedDataAccessFDA}

Externa databaser som är kompatibla med Adobe Campaign FDA-modulen (Federated Data Access) listas nedan. Läs mer om FDA [på den här sidan](../connect/fda.md).

* **[!DNL Amazon Redshift]** ODBC-anslutning, startar Campaign v8.6.4 / v8.7.1
* **[!DNL Amazon Redshift]** äldre koppling
* **[!DNL Azure Synapse]**, startar Campaign v8.5
* **[!DNL Databricks]**, starta Campaign v8.6.4 / v8.7
* **[!DNL Google Big Query]**
* **[!DNL Snowflake]**
* **[!DNL Vertica]**
* **[!DNL Fabrics]**


>[!AVAILABILITY]
>Med [tillägget Förbättrat skydd](../config/enhanced-security.md#secure-vpn-tunneling) får du dessutom tillgång till dina lokala databaser via den säkra VPN-justeringen. [Läs mer](../config/enhanced-security.md#vpn-callouts)

## Mobil-SDK {#MobileSDK}

Om du vill skicka [push-meddelanden](../send/push.md) med Campaign använder du Adobe Experience Platform Mobile SDK genom att konfigurera Adobe Campaign Classic-tillägget i användargränssnittet för datainsamling.

Kompatibla versioner för iOS och Android finns i [Adobe Developer-dokumentationen](https://developer.adobe.com/client-sdks/home/){target="_blank"}.

## Webbgränssnitt {#web-ui}

Följande webbläsare är kompatibla med Campaign Web User Interface. Läs mer om Campaign Web UI [på den här sidan](campaign-ui.md#ac-web-ui).

* **Microsoft Edge**, **Google Chrome**, **Safari** (senaste versionerna)

## Webbåtkomst {#web-access}

Följande webbläsare är kompatibla med Campaign for Web Access. Läs mer om Campaign-webbåtkomsten [på den här sidan](connect.md#web-access).

* **Microsoft Edge**, **Mozilla Firefox**, **Google Chrome**, **Safari** (senaste versionerna)

## Ytterligare resurser {#support}

* [Uppdateringar om kampanjreleaser](upgrades.md)
* [Kontrollera kampanjversionen](upgrades.md#version)
* [Installera Campaign-klientkonsolen](connect.md)
* [Versioner av Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=sv){target="_blank"}

Prenumerera på [Adobes prioriterade produktuppdatering](https://www.adobe.com/se/subscription/priority-product-update.html){target="_blank"} för att få information om nya versioner av lösningen Experience Cloud.