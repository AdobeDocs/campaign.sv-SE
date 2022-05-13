---
title: Kom igång med Campaign FFDA-distribution
description: Kom igång med Campaign FFDA-distribution
feature: Overview
role: Data Engineer
level: Beginner
source-git-commit: 13d19f0052880c0b0930e96441163f26038c071a
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 1%

---

# [!DNL Campaign] FFDA-distribution{#gs-ac-ffda}

Genom att utnyttja [[!DNL Snowflake]](https://www.snowflake.com/), en molndatabasteknik, Adobe Campaign Enterprise Full Federated Access (FFDA) som dramatiskt förbättrar skalan och hastigheten, med möjlighet att hantera ett större antal kundprofiler samt mycket högre leveransfrekvenser och transaktioner per timme.

## Fördelar {#ffda-benefits}

Campaign v8 Enterprise (FFDA) ger en heltäckande skala i alla steg av processen, från målinriktning till slutrapportering:

* Skala den datavolym du kan hantera (till 8 TB)
* Skala upp prestanda för frågor för segmentering och målinriktning men även för datainhämtning och urkunder
* Skala leveransberedningen (från timmar till minuter)

Detta är en grundläggande förändring i programvaruarkitekturen. Data är nu fjärrdata och Campaign federerar hela data, inklusive profiler. [!DNL Campaign] -processer kan nu skalas från början till slut, från målinriktning till meddelandekörning: datainmatning, segmentering, målgruppsanpassning, frågor och leveranser kommer nu att köras på några minuter. Den nya versionen löser hela skalförändringsproblemet samtidigt som den behåller samma nivå av flexibilitet och utbyggbarhet. Antalet profiler är nästan obegränsat och datalagringen kan utökas.

Molnlagring utförs i **[!DNL Snowflake]**: en ny inbyggd **externt konto** säkerställer anslutningen till molndatabasen. Den är konfigurerad av Adobe och får inte ändras. [Läs mer](../config/external-accounts.md)

Alla inbyggda scheman/tabeller som behöver flyttas eller replikeras i Cloud Database levereras med ett inbyggt schematillägg under **xxl** namnutrymme. Dessa tillägg innehåller alla ändringar som krävs för att flytta inbyggda scheman från [!DNL Campaign] lokal databas till [!DNL Snowflake] Cloud-databas och anpassa deras struktur efter detta: nytt UUID, uppdaterade länkar osv.

>[!CAUTION]
>
> Kunddata lagras inte lokalt [!DNL Campaign] databas. Därför måste alla anpassade tabeller skapas i molndatabasen.

## Campaign Enterprise (FFDA)-arkitektur{#ffda-archi}

I en [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), [!DNL Adobe Campaign] v8 fungerar med två databaser: en lokal [!DNL Campaign] databas för användargränssnittet för meddelanden i realtid och enhetliga frågor samt skriva via API:er och ett molnbaserat [!DNL Snowflake] databas för kampanjkörning, batchfrågor och arbetsflödeskörning.

Campaign v8 Enterprise innehåller konceptet **Fullständig federerad dataåtkomst** (FFDA): alla data är nu fjärranslutna till molndatabasen.

Det finns specifika API:er för att hantera data mellan den lokala databasen och molndatabasen. Lär dig hur dessa nya API:er fungerar och hur du använder dem i [den här sidan](new-apis.md).

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/architecture.png)

* Modulerna för exekvering och studshantering är inaktiverade på instansen.
* Programmet är konfigurerat att utföra meddelandekörning på en fjärrserver med &quot;mellanlagring&quot; som drivs med SOAP-anrop (via HTTP eller HTTPS).

The [!DNL Snowflake] databasen på marknadsföringssidan används för att

* Lagra alla kunddata: profiler, anpassade data som transaktioner, produkter, platser osv.
* Lagra alla händelser- och beteendedata som genereras eller samlas in av Campaign, som leveransloggar, spårningsloggar, push-registreringar osv.
* Lagra alla dataaggregat för ovanstående.
* Lagra en kopia (h+1) av referenstabeller (som leveranser, uppräkningar, länder osv.) som används i arbetsflöden, kampanjer och rapporter.
* Kör alla batchprocesser och arbetsbelastningar


PostgreSQL-databasen på marknadsinstansen används för att:

* Kör vissa arbetsbelastningar, till exempel API:er med låg volym.
* Lagra alla kampanjdata, inklusive leverans- och kampanjinställningar, arbetsflöden och tjänstdefinitioner.
* Lagra alla inbyggda referenstabeller (uppräkningar, länder osv.) som replikeras till [!DNL Snowflake].

   Du kan dock inte:
   * skapa anpassningar för kunddata, t.ex. inte skapa någon hushållstabell i PostgreSQL, utan bara i Snowflake
   * lagra leveransloggar, spårningsloggar osv. på FFDA:s målinriktning.
   * lagra stora datavolymer.


PostgreSQL-databasen i mellankällinstansen används för att:

* Kör batch- och realtidsleveranser.
* Skicka leverans- och spårningsloggar - observera att leverans- och spårningslogg-ID är UUID och inte 32-bitars ID.
* Samla in och lagra spårningsdata.


## Påverkan{#ffda-impacts}

### [!DNL Campaign] API-mellanlagringsmekanism{#staging-api}

Med [!DNL Campaign] Molndatabas rekommenderas inte snabba enhetsanrop på grund av prestanda (fördröjning och samtidighet). Gruppåtgärd är alltid att föredra. För att garantera optimala prestanda för API:er fortsätter Campaign att hantera API-anrop på lokal databasnivå.

![](../assets/do-not-localize/glass.png) [API-mellanlagringsmekanismen beskrivs på den här sidan](staging.md)

### Nya API:er{#new-apis}

Det finns nya API:er för att hantera datasynkronisering mellan [!DNL Campaign] lokal databas och molndatabas. En ny mekanism har också introducerats för att hantera API-anrop på lokal databasnivå för att undvika fördröjning och öka den övergripande prestandan.

![](../assets/do-not-localize/glass.png) [Nya API:er finns på den här sidan](new-apis.md)


### Datareplikering{#data-replication}

Ett specifikt tekniskt arbetsflöde hanterar replikering av tabeller som måste finnas på båda sidor (Campaign-databasen och molndatabasen). Det här arbetsflödet aktiveras varje timme och är beroende av ett nytt inbyggt JavaScript-bibliotek.

>[!NOTE]
>
> Flera replikeringsprinciper har skapats, baserat på tabellens storlek (XS, XL osv.).
> Vissa tabeller replikeras i realtid, andra replikeras per timme. Vissa tabeller kommer att innehålla stegvisa uppdateringar, andra kommer att genomgå en fullständig uppdatering.

[Läs mer om datareplikering](replication.md)

### ID-hantering{#id-mgt-ffda}

Kampanjv8-objekt använder nu en **Universally Unique ID (UUID)**, vilket möjliggör ett obegränsat antal unika värden för att identifiera data.

Observera att detta ID är strängbaserat och inte sekventiellt. Primärnyckeln är inte ett numeriskt värde i Campaign v8, och du måste använda **autouuid** och **autopk** attribut i dina scheman.

I Campaign Classic v7 och tidigare versioner hanteras uniciteten för en nyckel i ett schema (dvs. tabell) på databasmotornivå. Vanligtvis innehåller klassiska databasmotorer som PostgreSQL, Oracle eller SQL Server en inbyggd mekanism som förhindrar att duplicerade rader infogas baserat på en kolumn eller en uppsättning kolumner via primärnycklar och/eller unika index. Det finns inget duplicerat ID i dessa versioner när korrekt index och primärnycklar har angetts på databasnivå.

Adobe Campaign v8 levereras med Snowflake som kärndatabas. Eftersom sökningen dramatiskt ökar antalet frågor, har den distribuerade arkitekturen i Snowflake-databasen inte sådana mekanismer för att hantera och sedan genomdriva enkelheten hos en nyckel i en tabell. I Adobe Campaign v8 förhindrar därför ingenting att duplicerade nycklar används i en tabell. Slutanvändare ansvarar nu för att säkerställa att nyckelord är konsekventa i Adobe Campaign-databasen. [Läs mer](keys.md)

**Relaterade ämnen**

* [God praxis för datamodell](../dev/datamodel-best-practices.md)
