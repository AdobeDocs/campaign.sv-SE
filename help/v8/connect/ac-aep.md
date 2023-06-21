---
title: Arbeta med Campaign och Adobe Experience Platform
description: Lär dig hur du arbetar med Campaign och Adobe Experience Platform
feature: Platform Integration
role: Data Engineer
level: Beginner
exl-id: 21cf5611-ccaa-4e83-8891-a1a2353515aa
source-git-commit: f8c4e05ba2fc97d981fb31f9b11c5de1dcc1ff6e
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Arbeta med Campaign och Adobe Experience Platform

Adobe Campaign Managed Cloud Service Destination och Source-anslutningarna möjliggör smidig integrering mellan Adobe Campaign och Adobe Experience Platform.

* Använda en Adobe Campaign Managed Cloud Services **Målanslutning** för att skicka Experience Platform segment till Adobe Campaign för aktivering:

  Konfigurera en ny Adobe Campaign Managed Cloud Services **Målanslutning** för att aktivera ett segment/en målgrupp och skicka data till Adobe Campaign. Ange information om Campaign-instansen som ska användas, markera segment som ska aktiveras för målet och konfigurera sedan de attribut som du vill exportera till Campaign. [Lär dig hur du skapar en Adobe Campaign Managed Cloud Services-målanslutning](https://www.adobe.com/go/destinations-adobe-campaign-managed-cloud-services-en)

  ![](assets/aep-destination.png){width="800" align="center"}

* Använda en Adobe Campaign Managed Cloud Services **Källanslutning** för att skicka leverans- och spårningsloggar till Adobe Experience Platform:

  Konfigurera en ny Adobe Campaign Managed Cloud Services **Källanslutning** att importera Campaign-event till Adobe Experience Platform. Ange information om Campaign-instansen och det schema som ska användas, välj en datauppsättning där data ska hämtas och konfigurera sedan fälten som ska hämtas. [Lär dig hur du skapar en källanslutning till Adobe Campaign Managed Cloud Services](https://www.adobe.com/go/sources-campaign-ui-en)

  ![](assets/aep-logs.png){width="800" align="center"}
