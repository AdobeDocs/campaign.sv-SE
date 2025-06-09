---
title: Kom igång med Campaign FFDA-distribution
description: Kom igång med Campaign FFDA-distribution
feature: Architecture, FFDA, Deployment
role: Admin, Developer
level: Beginner
exl-id: 0a6f6701-b137-4320-9732-31946509ee03
source-git-commit: 3235701e0939466d4275b1e9202f82694ccdb352
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 1%

---

# [!DNL Campaign] FFDA-distribution {#gs-ac-ffda}

Genom att utnyttja [[!DNL Snowflake]](https://www.snowflake.com/){target="_blank"}, en molndatabasteknik, förbättrar distributionen av Adobe Campaign Enterprise Full Federated Access (FFDA) dramatiskt dess skala och hastighet, med möjlighet att hantera ett större antal kundprofiler samt mycket högre leveransfrekvenser och transaktioner per timme.

## Fördelar {#ffda-benefits}

Campaign v8 Enterprise (FFDA) ger en heltäckande skala i alla steg av processen, från målinriktning till slutrapportering:

* Skala den datavolym du kan hantera (till 8 TB)
* Skala upp prestanda för frågor för segmentering och målinriktning men även för datainhämtning och urkunder
* Skala leveransberedningen (från timmar till minuter)

Detta är en grundläggande förändring i programvaruarkitekturen. Data är nu fjärrdata och Campaign federerar hela data, inklusive profiler. [!DNL Campaign] processer skalas nu från mål till mål till meddelandekörning: datainhämtning, segmentering, målinriktning, frågor, leveranser kommer nu att köras på några minuter. Den nya versionen löser hela skalförändringsproblemet samtidigt som den behåller samma nivå av flexibilitet och utbyggbarhet. Antalet profiler är nästan obegränsat och datalagringen kan utökas.

Molnlagring utförs i **[!DNL Snowflake]**: ett nytt inbyggt **externt konto** säkerställer anslutningen till molndatabasen. Den har konfigurerats av Adobe och får inte ändras. [Läs mer](../config/external-accounts.md)

Alla inbyggda scheman/tabeller som behöver flyttas eller replikeras i Cloud Database levereras med ett inbyggt schematillägg under namnområdet **xxl**. Dessa tillägg innehåller eventuella ändringar som krävs för att flytta inbyggda scheman från den lokala databasen [!DNL Campaign] till molndatabasen [!DNL Snowflake] och för att anpassa deras struktur efter detta: nytt UUID, uppdaterade länkar osv.

>[!CAUTION]
>
> Kunddata lagras inte i den lokala [!DNL Campaign]-databasen. Därför måste alla anpassade tabeller skapas i molndatabasen.
>

## Campaign Enterprise (FFDA)-arkitektur{#ffda-archi}

I en [Enterprise (FFDA)-distribution](../architecture/enterprise-deployment.md) fungerar [!DNL Adobe Campaign] v8 med två databaser: en lokal [!DNL Campaign]-databas för meddelanden i realtid i användargränssnittet och enhetliga frågor och skrivningar via API:er samt en Cloud [!DNL Snowflake]-databas för kampanjkörning, gruppfrågor och arbetsflödeskörning.

Campaign v8 Enterprise innehåller konceptet **FDA (Full Federated Data Access)**: alla data finns nu på fjärrbasis i molndatabasen.

Det finns specifika API:er för att hantera data mellan den lokala databasen och molndatabasen. Lär dig hur dessa nya API:er fungerar och hur du använder dem på [den här sidan](new-apis.md).

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/architecture.png)

* Modulerna för exekvering och studshantering är inaktiverade på instansen.
* Programmet är konfigurerat för att utföra meddelandekörning på en fjärrserver med &quot;mellanlagring&quot; som drivs med SOAP-anrop (via HTTP eller HTTPS).

Databasen [!DNL Snowflake] på marknadsföringssidan används för att:

* Lagra alla kunddata: profiler, anpassade data som transaktioner, produkter, platser osv.
* Lagra alla händelser- och beteendedata som genereras eller samlas in av Campaign, som leveransloggar, spårningsloggar, push-registreringar osv.
* Lagra alla dataaggregat för ovanstående.
* Lagra en kopia (h+1) av referenstabeller (som leveranser, uppräkningar, länder osv.) som används i arbetsflöden, kampanjer och rapporter.
* Kör alla batchprocesser och arbetsbelastningar


PostgreSQL-databasen på marknadsinstansen används för att:

* Kör vissa arbetsbelastningar, till exempel API:er med låg volym.
* Lagra alla kampanjdata, inklusive leverans- och kampanjinställningar, arbetsflödes- och tjänstdefinitioner.
* Lagra alla inbyggda referenstabeller (uppräkningar, länder osv.) som replikeras till [!DNL Snowflake].

  Du kan dock inte:
   * skapa anpassningar för kunddata, t.ex. inte skapa någon hushållstabell i PostgreSQL, utan endast i Snowflake
   * lagra leveransloggar, spårningsloggar osv. på FFDA:s målinriktningsdimension.
   * lagra stora datavolymer.


PostgreSQL-databasen i mellankällinstansen används för att:

* Kör batch- och realtidsleveranser.
* Skicka leverans- och spårningsloggar - observera att leverans- och spårningslogg-ID är UUID och inte 32-bitars ID.
* Samla in och lagra spårningsdata.


## Påverkan{#ffda-impacts}

### [!DNL Campaign] API-mellanlagringsmekanism{#staging-api}

I molndatabasen [!DNL Campaign] rekommenderas inte att enhetsanrop görs med avseende på prestanda (fördröjning och samtidighet). Om du inte skickar extremt låga volymer måste gruppåtgärder användas för att garantera optimala API-prestanda. För att förbättra prestandan omdirigeras API:er för inmatning till den lokala databasen. [Läs mer om mellanlagringsmekanismen för Campaign API](staging.md)

### Nya API:er{#new-apis}

Det finns nya API:er tillgängliga för att hantera datasynkronisering mellan den lokala databasen [!DNL Campaign] och molndatabasen. En ny mekanism har också införts för att hantera API-anrop på lokal databasnivå för att undvika fördröjning och öka den övergripande prestandan.

[Nya API:er finns på den här sidan](new-apis.md)


### Datareplikering{#data-replication}

Ett specifikt tekniskt arbetsflöde hanterar replikering av tabeller som måste finnas på båda sidor (Campaign-databasen och molndatabasen). Arbetsflödet aktiveras varje timme och är beroende av ett nytt inbyggt JavaScript-bibliotek.

>[!NOTE]
>
> Flera replikeringsprinciper har skapats, baserat på tabellens storlek (XS, XL osv.).
> > Vissa tabeller replikeras i realtid, andra replikeras per timme. Vissa tabeller kommer att innehålla stegvisa uppdateringar, andra kommer att genomgå en fullständig uppdatering.
>

[Läs mer om datareplikering](replication.md)

### ID-hantering{#id-mgt-ffda}

Kampanjv8-objekt använder nu ett **Universally Unique ID (UUID)** som tillåter ett obegränsat antal unika värden för att identifiera data.

Observera att detta ID är strängbaserat och inte sekventiellt. Primärnyckeln är inte ett numeriskt värde i Campaign v8, och du måste använda attributen **autouid** och **autopk** i dina scheman.

I Campaign Classic v7 och tidigare versioner hanteras uniciteten för en nyckel i ett schema (dvs. tabell) på databasmotornivå. Vanligtvis innehåller klassiska databasmotorer som PostgreSQL, Oracle eller SQL Server en inbyggd mekanism som förhindrar att duplicerade rader infogas baserat på en kolumn eller en uppsättning kolumner via primärnycklar och/eller unika index. Det finns inget duplicerat ID i dessa versioner när korrekt index och primärnycklar har angetts på databasnivå.

Adobe Campaign v8 levereras med Snowflake som kärndatabas. Eftersom Snowflake-databasens distribuerade arkitektur dramatiskt ökar antalet frågor, finns det inga sådana mekanismer för att hantera och sedan genomdriva enkelheten hos en nyckel i en tabell. I Adobe Campaign v8 förhindrar därför ingenting att duplicerade nycklar används i en tabell. Slutanvändare ansvarar nu för att säkerställa att nyckelord är konsekventa i Adobe Campaign-databasen. [Läs mer](keys.md)

### Tillgänglighet {#feature-availability}

Vissa funktioner är inte tillgängliga i samband med en Enterprise-distribution (FFDA) av Campaign, till exempel:

* Hantering av marknadsföringsresurser
* Kuponger
* Webbspårning
* Undersökningar


**Relaterade ämnen**

* [God praxis för datamodell](../dev/datamodel-best-practices.md)
