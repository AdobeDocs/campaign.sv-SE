---
solution: Campaign v8
product: Adobe Campaign
title: Arbeta med Campaign och Adobe Analytics
description: Lär dig hur du arbetar med Campaign och Adobe Analytics
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: d1d57aa8-b811-470f-a8a6-18da3a700f1a
source-git-commit: 4ae0c968bd68d76d7ceffb91023d5426d6a810ea
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 2%

---

# Arbeta med Campaign och Adobe Analytics


## Adobe Analytics Connector

Ni kan konfigurera Adobe Analytics Connectors för att integrera Campaign och Analytics.

Med Adobe Analytics Connector kan Adobe Campaign och Adobe Analytics interagera via **Web Analytics-anslutningarna**. Den här integreringen delar data från Analytics till Campaign som segment relaterade till användarbeteende efter ett e-postmeddelande. Omvänt skickas indikatorer och attribut för e-postkampanjer som levereras av Adobe Campaign till Adobe Analytics - Datakoppling.

Med Adobe Analytics Connector kan Adobe Campaign mäta internetpublik (Web Analytics). Tack vare dessa integreringar kan Adobe Campaign återställa data om besökares beteende för en eller flera webbplatser efter en marknadsföringskampanj och (efter analys) köra återmarknadsföringskampanjer i syfte att konvertera dem till köpare. Omvänt gör webbanalysverktygen att Adobe Campaign kan vidarebefordra indikatorer och kampanjattribut till sina plattformar.

Åtgärdsfälten för varje verktyg är följande:

* **Adobe Analytics**

   * markerar de e-postkampanjer som lanserats med Adobe Campaign
   * sparar mottagarnas beteende, på den webbplats som de bläddrade efter att ha klickat på kampanjmeddelandet, i form av segment. Segmenten är relaterade till övergivna produkter (visade men inte tillagda i kundvagnen eller köpta), inköp eller övergivna varukorgar.

* **Adobe Campaign**

   * skickar indikatorerna och kampanjattributen till kopplingen, som i sin tur vidarebefordrar dem till webbanalysverktyget
   * återställer och analyserar segment
   * utlöser en återmarknadsföringskampanj

Läs mer om Adobe Campaign och Adobe Analytics på [den här sidan](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/connectors/adobe-analytics-data-connector.html)

[!DNL :speech_balloon:]  Som användare av hanterade Cloud Services  [kontaktar du ](../start/campaign-faq.md#support) Adobe för att integrera Adobe Analytics Data Connector med Campaign.


## Utlösare i Experience Cloud

Du kan använda Experience Cloud Triggers för att koppla data mellan Adobe Campaign och Adobe Analytics med hjälp av pipeline. Pipelinen hämtar användarens åtgärder eller utlösare från din webbplats. En kundvagnsöverläggning är ett exempel på utlösare. Utlösare bearbetas i Adobe Campaign för att skicka e-post i nära realtid.

Läs mer om utlösare för Adobe Campaign och Experience Cloud på [den här sidan](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/experience-triggers/about-triggers.html?lang=en).

[!DNL :speech_balloon:]  Som användare av hanterade Cloud Services  [kontaktar du ](../start/campaign-faq.md#support) Adobe implementera utlösare för Experience Cloud med Campaign.
