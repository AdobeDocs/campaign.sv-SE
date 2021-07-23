---
product: Adobe Campaign
title: Campaign Classic v7 - Funktionsmatris för kampanj v8
description: Förstå skillnaderna mellan Campaign Classic v7 och Campaign v8
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 00ba1c43-9558-4adb-83a1-6597c2bbca62,7105477f-d29e-4af8-8789-82b4459761b0
source-git-commit: bfd2df90e5e6bee89bdfc7c5da82c755ac5726df
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 4%

---

# [!DNL Campaign Classic] Funktioner för v7- [!DNL Campaign] v8{#gs-matrix}

Som befintlig [!DNL Campaign Classic] v7-användare bör du inte förvänta dig några större avbrott i det sätt som du vanligtvis interagerar med [!DNL Adobe Campaign]. De flesta ändringar i v8 är inte synliga, med undantag för små ändringar som uppstår i gränssnittet och konfigurationsstegen.

Viktiga ändringar:

* Skapa segment upp till 200 gånger snabbare
* Snabbare leverans
* Realtidsrapportering med kuber

Som [!DNL Campaign Classic]-användare bör du tänka på att de flesta [!DNL Campaign Classic] v7-funktionerna är tillgängliga med [!DNL Campaign] v8, förutom en liten uppsättning av dem, som listas i [det här avsnittet](#gs-removed). Andra kommer i framtida versioner. [Läs mer i det här avsnittet](#gs-unavailable-features)

? Läs mer om v8-arkitekturen i [den här sidan](../dev/architecture.md).[!DNL Campaign]

## Produktkonfigurationsändringar

### [!DNL Campaign] och  [!DNL Snowflake] {#ac-gs-snowflake}

[!DNL Adobe Campaign] v8 fungerar med två databaser: en lokal databas för användargränssnittet för meddelanden i realtid och enhetliga frågor och skrivningar via API:er samt en molndatabas för kampanjkörning, gruppfrågor och arbetsflödeskörning.

Detta är en grundläggande förändring i programvaruarkitekturen. Data är nu fjärrdata och Campaign federerar hela data, inklusive profiler. [!DNL Campaign] -processer kan nu skalas från början till slut, från målinriktning till meddelandekörning: datainmatning, segmentering, målgruppsanpassning, frågor och leveranser kommer nu att köras på några minuter. Den nya versionen löser hela skalförändringsproblemet samtidigt som den behåller samma nivå av flexibilitet och utbyggbarhet. Antalet profiler är nästan obegränsat och datalagringen kan utökas.

Molnlagring utförs i **[!DNL Snowflake]**: ett nytt inbyggt **externt konto** säkerställer anslutningen till molndatabasen. Den är konfigurerad av Adobe och får inte ändras. [Läs mer](../config/external-accounts.md)

Alla inbyggda scheman/tabeller som behöver flyttas eller replikeras i molndatabasen har ett inbyggt schematillägg under namnområdet **xxl**. Dessa tillägg innehåller eventuella ändringar som krävs för att flytta inbyggda scheman från den lokala [!DNL Campaign]-databasen till molndatabasen [!DNL Snowflake] och för att anpassa strukturen därefter: nytt UUID, uppdaterade länkar osv.

>[!CAUTION]
>
> Kunddata lagras inte i den lokala [!DNL Campaign]-databasen. Därför måste alla anpassade tabeller skapas i molndatabasen.


Det finns specifika API:er för att hantera data mellan den lokala databasen och molndatabasen. Lär dig hur dessa nya API:er fungerar och hur du använder dem i [den här sidan](../dev/new-apis.md).

### Datareplikering

Ett specifikt tekniskt arbetsflöde hanterar replikering av tabeller som måste finnas på båda sidor (Campaign-databasen och molndatabasen). Det här arbetsflödet aktiveras varje timme och är beroende av ett nytt inbyggt JavaScript-bibliotek.

>[!NOTE]
>
> Flera replikeringsprinciper har skapats, baserat på tabellens storlek (XS, XL osv.).
> Vissa tabeller replikeras i realtid, andra replikeras per timme. Vissa tabeller kommer att innehålla stegvisa uppdateringar, andra kommer att genomgå en fullständig uppdatering.


[Läs mer om datareplikering](../config/replication.md)

### ID-hantering

Kampanjv8-objekt använder nu ett **UID (Universally Unique ID)**, som tillåter ett obegränsat antal unika värden för att identifiera data.

Observera att detta ID är strängbaserat och inte sekventiellt. Primärnyckeln är inte ett numeriskt värde i Campaign v8, och du måste använda attributen **autouid** och **autopk** i dina scheman.

I Campaign Classic v7 och tidigare versioner hanteras uniciteten för en nyckel i ett schema (dvs. tabell) på databasmotornivå. Vanligtvis innehåller klassiska databasmotorer som PostgreSQL, Oracle eller SQL Server en inbyggd mekanism som förhindrar att duplicerade rader infogas baserat på en kolumn eller en uppsättning kolumner via primärnycklar och/eller unika index. Det finns inget duplicerat ID i dessa versioner när korrekt index och primärnycklar har angetts på databasnivå.

Adobe kampanj v8 levereras med Snowflake som kärndatabas. Eftersom sökningen dramatiskt ökar antalet frågor, har den distribuerade arkitekturen i Snowflake-databasen inte sådana mekanismer för att hantera och sedan genomdriva enkelheten hos en nyckel i en tabell. I Adobe Campaign v8 förhindrar därför ingenting att duplicerade nycklar används i en tabell. Slutanvändare ansvarar nu för att säkerställa att nyckelord är konsekventa i Adobe Campaign-databasen. [Läs mer](../dev/keys.md)

### Förenklat underhåll

Kampanjanvändare behöver inte vara databasexperter: det inte längre finns något behov av komplexa databasunderhållsåtgärder eller komplex tabellindexering.

## Anslutning till kampanj

Kampanjanvändare ansluter via sina Adobe ID. Samma Adobe ID används för att behålla alla planer och produkter för Adobe som är kopplade till ett enda konto.

? Lär dig hur du ansluter till [!DNL Campaign] på [den här sidan](connect.md).

## Rapportering

Observera att Adobe Campaign rapporter är optimerade och har bättre skalbarhet än Campaign Classic v7. Befintliga begränsningar för kuber gäller inte.

## Arbetsflöde {#workflow}

Campaign v8 erbjuder en ytterligare arbetsflödesaktivitet för målinriktning: **[!UICONTROL Change data source]**.

Med aktiviteten **[!UICONTROL Change data source]** kan du ändra datakällan för ett arbetsflöde **[!UICONTROL Working table]** för att hantera data över olika datakällor som FDA, FFDA och den lokala databasen.

? Läs mer om aktiviteten **[!UICONTROL Change data source]** i [den här sidan](../config/workflows.md#change-data-source-activity).

## Otillgängliga funktioner{#gs-unavailable-features}

Observera att vissa funktioner inte är tillgängliga i den första versionen, som:

* Hantera marknadsföringsresurser
* Distribuerad marknadsföring
* Inkommande erbjudandehantering (interaktionsmodul)
* Kampanjoptimering
* Responshanteraren
* Hybrid/lokala distributionsmodeller
* LINE-meddelanden
* Kontrollpanelen i Campaign

>[!CAUTION]
>
>För närvarande är Campaign v8 **endast** tillgängligt som hanterad Cloud Service och kan inte distribueras på en lokal eller hybridmiljö.
>
>Migrering från en befintlig Campaign Classic v7-miljö är inte tillgänglig än.
>
>Om du är osäker på din distributionsmodell eller har frågor kontaktar du ditt kontoteam.

## Borttagna funktioner{#gs-removed}

För att den nya arkitekturen och distributionsmodellen i Campaign v8 ska överensstämma med Campaign v8 är vissa tidigare Campaign Classic v7-funktioner inte längre tillgängliga i Campaign v8.

* Kuponger
* Webbspårning
* Undersökningar
* Social marknadsföring
* ACS Connector (Prime offer)
* Integrering med LDAP
* Logga in med användare/lösenord
