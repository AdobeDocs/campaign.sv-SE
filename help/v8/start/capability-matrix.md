---
solution: Campaign v8
product: Adobe Campaign
title: Campaign Classic v7 - Funktionsmatris för kampanj v8
description: Förstå skillnaderna mellan Campaign Classic v7 och Campaign v8
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 00ba1c43-9558-4adb-83a1-6597c2bbca62,7105477f-d29e-4af8-8789-82b4459761b0
source-git-commit: 93004d69f33fce39f8f2abb18eec2562177a7adf
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 2%

---

# [!DNL Campaign Classic] Funktioner för v7- [!DNL Campaign] v8{#gs-matrix}

Som befintlig [!DNL Campaign Classic] v7-användare bör du inte förvänta dig några större avbrott i det sätt som du vanligtvis interagerar med [!DNL Adobe Campaign]. De flesta ändringar i v8 är inte synliga, med undantag för små ändringar som uppstår i gränssnittet och konfigurationsstegen.

Viktiga ändringar:

* Skapa segment upp till 200 gånger snabbare
* Snabbare leverans
* Realtidsrapportering med kuber

Som [!DNL Campaign Classic]-användare bör du tänka på att de flesta [!DNL Campaign Classic] v7-funktionerna är tillgängliga med [!DNL Campaign] v8, förutom en liten uppsättning av dem, som listas i [det här avsnittet](#gs-removed). Andra kommer i framtida versioner. [Läs mer i det här avsnittet](#gs-unavailable-features)

[!DNL :bulb:] Läs mer om  [!DNL Campaign] v8-arkitekturen på  [den här sidan](../dev/architecture.md).

## Produktkonfigurationsändringar

### [!DNL Campaign] och  [!DNL Snowflake] {#ac-gs-snowflake}

[!DNL Adobe Campaign] v8 fungerar med två databaser: en lokal databas för användargränssnittet för meddelanden i realtid och enhetliga frågor och skrivningar via API:er samt en molndatabas för kampanjkörning, gruppfrågor och arbetsflödeskörning.

Detta är en grundläggande förändring i programvaruarkitekturen. Data är nu fjärrdata och Campaign federerar hela data, inklusive profiler. [!DNL Campaign] -processer kan nu skalas från början till slut, från målinriktning till meddelandekörning: datainmatning, segmentering, målgruppsanpassning, frågor och leveranser kommer nu att köras på några minuter. Den nya versionen löser hela skalförändringsproblemet samtidigt som den behåller samma nivå av flexibilitet och utbyggbarhet. Antalet profiler är nästan obegränsat och datalagringen kan utökas.

Molnlagring utförs i **[!DNL Snowflake]**: ett nytt inbyggt **externt konto** säkerställer anslutningen till molndatabasen. Den är konfigurerad av Adobe och får inte ändras. [Läs mer](../config/external-accounts.md).

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

Kampanjv8-objekt använder nu ett **UID (Universally Unique ID)**, som tillåter ett obegränsat antal unika värden för att identifiera data

Observera att detta ID är strängbaserat och inte sekventiellt.

### Förenklat underhåll

Kampanjanvändare behöver inte vara databasexperter: det inte längre finns något behov av komplexa databasunderhållsåtgärder eller komplex tabellindexering.

## Otillgängliga funktioner{#gs-unavailable-features}

Observera att vissa funktioner inte är tillgängliga i den första versionen, som:

* Hantering av marknadsföringsresurser
* Distribuerad marknadsföring
* Inkommande erbjudandehantering (interaktionsmodul)
* Kampanjoptimering
* Responshanteraren
* Hybrid/lokala distributionsmodeller

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

