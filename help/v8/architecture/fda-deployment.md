---
title: Kom igång med Campaign FDA-Snowflake-distribution
description: Kom igång med Campaign FDA-Snowflake-distribution
feature: Architecture, Federated Data Access, Deployment
role: Admin, Developer, User
level: Beginner
exl-id: b3df0336-f40e-4ac1-b6a4-068b8827dca2
source-git-commit: 1a0b473b005449be7c846225e75a227f6d877c88
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# [!DNL Campaign] FDA [!DNL Snowflake] distribution{#gs-fda-snowflake}

I en [!DNL Snowflake] FDA-distribution (standard), [!DNL Adobe Campaign] v8 är ansluten till [!DNL Snowflake] få tillgång till data via [Åtkomst till federerade data](../connect/fda.md) funktion: du kan komma åt och bearbeta externa data och information som lagras i [!DNL Snowflake] utan att ändra strukturen på Adobe Campaign-data.

## Fördelar{#fda-benefits}

Den här distributionsmodellen har följande fördelar:

* **Lagring och prestanda**
Du kan flytta dina historiska data till [!DNL Snowflake] och sedan minska beroendet av Adobe Campaign ID:n. Denna arkitektur minskar också ditt beroende av PostgreSQL-lagring och prestandagränser. Eftersom mindre data lagras i Campaign-databasen blir prestandan bättre och underhållsuppgifterna utförs snabbare.

* **Datamodelltillägg och datahantering**
Du kan skapa tabeller i [!DNL Snowflake] och länka dem till Adobe Campaign, t.ex. för att använda arkiverade data under kvarhållningsperioder, eller för segmenteringsprocesser med enastående prestanda.

  Med den här arkitekturen kan du även använda arbetsflödesfunktioner för datahantering i [!DNL Snowflake]. Endast aggregat och tillfälliga register flyttas till Campaign för personalisering och leverans.


## Arkitektur{#fda-archi}

Med den här distributionsmodellen kan Adobe Campaign-användare utöka sina data till [!DNL Snowflake] och utnyttja fördelarna med en enda integrerad dataplattform för att få kraftfulla insikter om marknadsföringskampanjer i realtid. Det ger användarna möjlighet att utnyttja data till fullo genom att erbjuda en enda, enhetlig och lättanvänd plattform för dataanalys. Molndataplattformen kräver ingen hantering eftersom den oändligt kan skalas för att stödja alla marknadsföringsdata från Adobe Campaign.

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/fda-architecture.png)

PostgreSQL är den primära databasen och Snowflake är den sekundära databasen. Du kan utöka datamodellen och lagra data på Snowflake. Därefter kan ni köra ETL, segmentering och rapporter på en stor datauppsättning med enastående prestanda.
