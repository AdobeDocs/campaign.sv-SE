---
title: Övergång från Campaign Classic v7 till Campaign v8
description: Lär dig om skillnaderna mellan Campaign Classic v7 och Campaign v8.
feature: Overview
role: Admin, Developer, User
level: Beginner, Intermediate, Experienced
exl-id: 00ba1c43-9558-4adb-83a1-6597c2bbca62
source-git-commit: 2d0c82df052c9b8c9f264c2ad15ac6050025f770
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 5%

---

# Övergång från [!DNL Campaign Classic] v7 till [!DNL Campaign] v8{#gs-matrix}

Som tidigare [!DNL Campaign Classic] v7-användare, du bör inte förvänta dig några större störningar i ditt sätt att interagera med [!DNL Adobe Campaign]. De flesta ändringar i v8 är inte synliga, med undantag för små ändringar som uppstår i gränssnittet och konfigurationsstegen.

>[!AVAILABILITY]
>
>* För tillfället är Campaign v8 **endast** finns som hanterad Cloud Service och kan inte distribueras på plats eller i hybridmiljöer. [Läs mer](#cloud-services)
>
>* Automatisk migrering från en befintlig Campaign Classic v7-miljö är inte tillgänglig än.


## Hanterade Cloud Services{#cloud-services}

Adobe Campaign v8 finns som **Hanterad Cloud Service**.

Adobe Campaign Managed Cloud Services har en plattform för hanterade Cloud Services för att utforma kundupplevelser i flera kanaler och erbjuder en miljö för visuell kampanjsamordning, interaktionshantering i realtid och kanalövergripande körning. Läs mer om Campaign Managed-Cloud Services i [produktbeskrivningssida](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Det nya erbjudandet kombinerar förstklassiga tjänster med proaktiv tillsyn och snabb varning, med fokus på tre områden:

* **Flexibilitet i molnet** - automatisering av Adobe, med optimerade, standardiserade molndriftsättningar för mer förutsägbara prestanda, större flexibilitet och förbättrad självbetjäning.
* **Tjänsteupplevelse** — proaktiv tillgänglighet, kapacitet, prestandaövervakning och åtgärder för att förhindra avbrott, åtgärda incidenter snabbare och regelbundet granska tjänsten för kontinuerlig förbättring.
* **Djupgående kampanjexpertis** — service med hög affinitet från expertgrupper för kundkonstruktion för att tillgodose behov av funktionalitet, teknik eller leveransförmåga, minska driftsättningsriskerna och förbättra ändringshanteringen.

Som tidigare [!DNL Campaign Classic] användare, observera att de flesta av [!DNL Campaign Classic] v7-funktioner är tillgängliga med [!DNL Campaign] v8, förutom en liten uppsättning, som listas i [det här avsnittet](#gs-removed).

Campaign v8 bygger på en **hybridarkitektur**. Om du går över från Campaign Classic v7 bör du tänka på att alla leveranser går via servern för mellanlagring. Följaktligen är intern routning **inte möjligt** i Campaign v8 och det externa kontot har inaktiverats i enlighet med detta. [Läs mer](../architecture/architecture.md).

>[!NOTE]
>
>Den nya molnarkitekturen gör att Campaign kan effektivisera processer, minska kostnaderna, hantera risker och förbättra datasäkerheten. Din Campaign v8-miljö har ett dedikerat VPC (Virtual Private Cloud) som är förkonfigurerat för dig.

## [!DNL Campaign] och [!DNL Snowflake] {#ac-gs-snowflake}

Campaign v8 fungerar med [!DNL Snowflake].

I [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), [!DNL Adobe Campaign] v8 fungerar med två databaser: en lokal [!DNL Campaign] databas för användargränssnittet för meddelanden i realtid och enhetliga frågor samt skriva via API:er och ett molnbaserat [!DNL Snowflake] databas för kampanjkörning, batchfrågor och arbetsflödeskörning.

Campaign v8 Enterprise innehåller konceptet **Fullständig federerad dataåtkomst** (FFDA): alla data är nu fjärranslutna till molndatabasen. Med den här nya arkitekturen förenklar driftsättningen av Campaign v8 Enterprise (FFDA) datahanteringen: inget index krävs för molndatabasen. Du behöver bara skapa tabellerna, kopiera data så kan du börja. Cloud-databastekniken kräver inget specifikt underhåll för att garantera prestandanivån.

![](../assets/do-not-localize/glass.png) Läs mer om [!DNL Campaign] v8-arkitektur i [den här sidan](../architecture/architecture.md).


## Använd din Adobe ID för att ansluta till Campaign{#adobe-id}

Kampanjanvändare ansluter bara via sina Adobe ID. Samma Adobe ID används för att behålla alla dina Adobe-planer och produkter som är kopplade till ett enda konto för alla Adobe Experience Cloud-lösningar.

![](../assets/do-not-localize/glass.png) Lär dig hur du ansluter till [!DNL Campaign] in [den här sidan](connect.md).

## Analysera data med kuber{#adobe-reporting}

Använd modulen Marketing Analytics för att analysera och mäta data, beräkna statistik, förenkla och optimera framtagning och beräkning av rapporter. Skapa dessutom rapporter och bygg upp målpopulationer: när de har identifierats lagras de i listor som kan användas i Adobe Campaign (målinriktning, segmentering osv.).

Med Adobe Campaign v8 är kubrapporterna optimerade och ger bättre skalbarhet än Campaign Classic v7. I den specifika distributionsmodellen gäller inte tidigare begränsningar för kuber i Campaign v8. Läs mer om kuber i [det här avsnittet](../../v8/reporting/gs-cubes.md).

## Otillgängliga funktioner{#gs-unavailable-features}

Observera att vissa funktioner inte är tillgängliga i samband med en [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md) för Campaign, till exempel:

* Hantera marknadsföringsresurser
* Kuponger
* Webbspårning
* Undersökningar

## Funktioner som inte stöds{#gs-removed}

Vissa historiska Campaign Classic v7-funktioner stöds inte längre i Campaign v8, till exempel:

* Social marknadsföring med Facebook
* ACS Connector (Prime offer)
* Integrering med LDAP
* Logga in med användare/lösenord
* Hybrid/lokala distributionsmodeller


>[!NOTE]
>
>Vissa funktioner som inte är tillgängliga eller som inte stöds kan fortfarande visas i användargränssnittet.
