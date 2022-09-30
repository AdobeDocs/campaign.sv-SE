---
title: Arbeta med Campaign och Adobe Experience Platform
description: Lär dig hur du arbetar med Campaign och Adobe Experience Platform
feature: Platform Integration
role: Data Engineer
level: Beginner
source-git-commit: 2ce1ef1e935080a66452c31442f745891b9ab9b3
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Arbeta med Campaign och Adobe Experience Platform

Adobe Campaign Managed Cloud Service-målet och källanslutningarna möjliggör smidig integrering mellan Adobe Campaign och Adobe Experience Platform:

* Använd **Adobe Campaign-anslutning för hanterade molnkällor** för att skicka Experience Platform segment till Adobe Campaign för aktivering,

   ![](assets/aep-destination.png)

* Använd **Adobe Campaign hanterade molnmålsanslutning** för att skicka leverans- och spårningsloggar till Adobe Experience Platform.

   ![](assets/aep-logs.png)

Så här konfigurerar du integreringen i Adobe Experience Platform:

1. Konfigurera en ny Adobe Campaign Managed Cloud Services-målanslutning för att aktivera ett segment/en målgrupp och skicka data till Adobe Campaign.

   Ange information om Campaign-instansen som ska användas, markera segment som ska aktiveras för målet och konfigurera sedan de attribut som du vill exportera till Campaign.

   [Lär dig hur du skapar en Adobe Campaign Managed Cloud Services-målanslutning](https://www.adobe.com/go/destinations-adobe-campaign-managed-cloud-services-en)

1. Konfigurera en ny källanslutning till Adobe Campaign Managed Cloud Services för att importera Campaign-händelser till Adobe Experience Platform.

   Ange information om Campaign-instansen och det schema som ska användas, välj en datauppsättning där data ska hämtas och konfigurera sedan fälten som ska hämtas.

   [Lär dig hur du skapar en källanslutning till Adobe Campaign Managed Cloud Services](https://www.adobe.com/go/sources-campaign-ui-en)
