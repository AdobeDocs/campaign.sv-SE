---
title: Kom igång med Campaign FDA-distribution
description: Kom igång med Campaign FDA-distribution
feature: Architecture, Federated Data Access, Deployment
role: Admin, Developer
level: Beginner
exl-id: b3df0336-f40e-4ac1-b6a4-068b8827dca2
source-git-commit: 561e4b6d2c99e98e068132c80c2bebb756b60a44
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# [!DNL Campaign] FDA-distribution{#gs-fda}

I sin Campaign FDA-distribution (standard) kan [!DNL Adobe Campaign] v8 anslutas till [!DNL Snowflake] för att komma åt data via funktionen [Federated Data Access](../connect/fda.md): du kan sedan komma åt och bearbeta externa data och information som lagras i din [!DNL Snowflake]-databas utan att ändra strukturen för Adobe Campaign-data.

>[!NOTE]
>
>I den här distributionsmodellen är den sekundära databasen [!DNL Snowflake] endast tillgänglig på begäran. Kontakta din Adobe Transition Manager om du vill uppdatera din distribution med [!DNL Snowflake].
>

## Fördelar{#fda-benefits}

Den här distributionsmodellen har följande fördelar:

* **Lagring och prestanda**
Du kan flytta dina historiska data till [!DNL Snowflake] och sedan minska beroendet av Adobe Campaign ID:n. Denna arkitektur minskar också ditt beroende av PostgreSQL-lagring och prestandagränser. Eftersom mindre data lagras i Campaign-databasen blir prestandan bättre och underhållsuppgifterna utförs snabbare.

* **Datamodelltillägg och datahantering**
Du kan skapa tabeller i [!DNL Snowflake] och länka dem till Adobe Campaign, t.ex. för att använda arkiverade data under kvarhållningsperioder eller köra segmenteringsprocesser med enastående prestanda.

  Med den här arkitekturen kan du även använda arbetsflödesfunktioner för datahantering i [!DNL Snowflake]. Endast aggregat och tillfälliga register flyttas till Campaign för personalisering och leverans.


## Arkitektur{#fda-archi}

Med den här distributionsmodellen kan Adobe Campaign-användare utöka sina data till [!DNL Snowflake] och utnyttja fördelarna med en enda integrerad dataplattform för kraftfull datainsikter om marknadsföringskampanjer i realtid. Det ger användarna möjlighet att utnyttja data till fullo genom att erbjuda en enda, enhetlig och lättanvänd plattform för dataanalys. Molndataplattformen kräver ingen hantering eftersom den oändligt kan skalas för att stödja alla marknadsföringsdata från Adobe Campaign.

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/fda-architecture.png)

PostgreSQL är den primära databasen och Snowflake kan användas som den sekundära databasen. Du kan utöka din datamodell och lagra dina data på Snowflake. Därefter kan ni köra ETL, segmentering och rapporter på en stor datauppsättning med enastående prestanda.
