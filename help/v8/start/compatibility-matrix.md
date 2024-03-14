---
title: Kompatibilitetsmatris för Campaign v8
description: Upptäck system och versioner som är kompatibla med Campaign v8
feature: Release Notes
role: Admin
level: Beginner
exl-id: 4be3a6dc-0c61-4534-b9dd-6c99c8a037a9
source-git-commit: a779f243b0ba13dc3fcb7839377ca8766e5f7841
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 16%

---

# Kompatibilitetsmatris för Campaign v8 {#compat-matrix}

Det här dokumentet innehåller en lista över alla system och komponenter som stöds för den senaste versionen av **Adobe Campaign v8** klientkonsol. Om inget annat anges stöds alla mindre releaser. Produkter och versioner som inte ingår i den här listan är inte kompatibla med Adobe Campaign.

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
>32-bitarsversionen av klientkonsolen har tagits bort sedan version 8.5. Från och med 8.6 är klientkonsolen endast tillgänglig med 64 bitar. Mer information om hur du uppgraderar systemet finns i [technote](../../technotes/upgrades/console.md).

### Webbläsare {#web-browsers}

* **Microsoft Edge**

* **Microsoft Edge WebView2**, senaste versionen. Hämta den från [Microsoft Developer Site](http://www.adobe.com/go/acc-ms-webview2-runtime-download){target="_blank"}.

## CRM-kopplingar {#CRMconnectors}

CRM (Customer Relationship Management)-system som är kompatibla med Adobe Campaign listas nedan. Läs mer om CRM-anslutningar [på den här sidan](../connect/crm.md).

* **Salesforce** API-version 49 för anslutning
* **Microsoft Dynamics** koppling, webb-API: Dynamics 365 lokalt och online

## Federerad dataåtkomst (FDA){#FederatedDataAccessFDA}

Externa databaser som är kompatibla med Adobe Campaign FDA-modulen (Federated Data Access) listas nedan. Läs mer om FDA [på den här sidan](../connect/fda.md).

* **[!DNL Amazon Redshift]**
* **[!DNL Azure Synapse]**, med start av Campaign v8.5
* **[!DNL Google Big Query]**
* **[!DNL Snowflake]**
* **[!DNL Vertica]**

## Mobil-SDK {#MobileSDK}

Skicka [push-meddelanden](../send/push.md) Med Campaign kan du använda Adobe Experience Platform Mobile SDK genom att konfigurera Adobe Campaign Classic-tillägget i användargränssnittet för datainsamling.

Kompatibla versioner för iOS och Android finns i [Adobe Developer-dokumentation](https://developer.adobe.com/client-sdks/home/){target="_blank"}.

## Webbgränssnitt {#web-ui}

Följande webbläsare är kompatibla med Campaign Web User Interface. Läs mer om Campaign Web UI [på den här sidan](campaign-ui.md#ac-web-ui).

* **Microsoft Edge**, **Google Chrome**, **Safari** (senaste versionerna)

## Webbåtkomst {#web-access}

Följande webbläsare är kompatibla med Campaign for Web Access. Läs mer om Campaign Web-åtkomst [på den här sidan](connect.md#web-access).

* **Microsoft Edge**, **Mozilla Firefox**, **Google Chrome**, **Safari** (senaste versionerna)

## Ytterligare resurser {#support}

* [Uppdateringar om kampanjreleaser](upgrades.md)
* [Kontrollera kampanjversionen](upgrades.md#version)
* [Installera Campaign-klientkonsolen](connect.md)
* [Versioner av Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=sv){target="_blank"}.

Om du vill få information om nya releaser för Experience Cloud kan du prenumerera på [Produktuppdatering Adobe Priority](https://www.adobe.com/se/subscription/priority-product-update.html){target="_blank"}.