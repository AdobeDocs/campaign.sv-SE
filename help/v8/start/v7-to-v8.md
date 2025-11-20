---
title: Övergång från Campaign Classic v7 till Campaign v8
description: Lär mer om skillnaderna mellan Campaign Classic v7 och Campaign v8.
feature: Overview
role: User
level: Beginner
exl-id: 00ba1c43-9558-4adb-83a1-6597c2bbca62
source-git-commit: 061197048885a30249bd18af7f8b24cb71def742
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 5%

---

# Övergång från [!DNL Campaign Classic] v7 till [!DNL Campaign] v8{#gs-matrix}

Som tidigare [!DNL Campaign Classic] v7-användare bör du inte förvänta dig några större störningar i det sätt som du vanligtvis interagerar med [!DNL Adobe Campaign]. De flesta ändringar i v8 är inte synliga, med undantag för små ändringar som uppstår i gränssnittet och konfigurationsstegen.

>[!AVAILABILITY]
>
>* För närvarande är Campaign v8 **endast** tillgängligt som hanterad Cloud Service och kan inte distribueras på en lokal eller hybridmiljö. [Läs mer](#cloud-services)
>
>* Automatisk migrering från en befintlig Campaign Classic v7-miljö är inte tillgänglig än.


## Hanterade molntjänster{#cloud-services}

Adobe Campaign v8 finns som **hanterad Cloud Service**.

Adobe Campaign Managed Cloud Services tillhandahåller en plattform för hanterade molntjänster för att utforma kundupplevelser över flera kanaler och erbjuder en miljö för visuell kampanjsamordning, interaktionshantering i realtid och kanalövergripande körning. Läs mer om Campaign Managed Cloud Services på [produktbeskrivningssidan](https://helpx.adobe.com/se/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Det nya erbjudandet kombinerar förstklassiga tjänster med proaktiv tillsyn och snabb varning, med fokus på tre områden:

* **Flexibilitet i molnet** - automatisering av Adobe, med optimerade, standardiserade molndistributioner för mer förutsägbara prestanda, större flexibilitet och förbättrad självbetjäning.
* **Tjänsteupplevelse** - proaktiv tillgänglighet, kapacitet, prestandaövervakning och åtgärder för att förhindra avbrott, åtgärda incidenter snabbare och granska tjänsten regelbundet för kontinuerlig förbättring.
* **Djupt kampanjkunnande** - service med hög affinitet från kundingenjörsteamen med experter för att tillgodose funktionalitets-, teknik- eller leveransbehov, minska distributionsriskerna och förbättra ändringshanteringen.

Som tidigare [!DNL Campaign Classic]-användare bör du tänka på att de flesta av funktionerna i [!DNL Campaign Classic] v7 är tillgängliga med [!DNL Campaign] v8, förutom en liten uppsättning, som listas i [det här avsnittet](#gs-removed).

>Den nya molnarkitekturen gör att Campaign kan effektivisera processer, minska kostnaderna, hantera risker och förbättra datasäkerheten. Din Campaign v8-miljö har ett dedikerat virtuellt privat moln (VPC) som är förkonfigurerat för dig.


## Hybridarkitektur {#hybrid-archi}

Campaign v8 är beroende av en **hybridarkitektur**. Om du går över från Campaign Classic v7 bör du tänka på att alla leveranser går via servern för mellanlagring.

Följden är att

* Intern routning är **inte möjlig** i Campaign v8 och det externa kontot har inaktiverats i enlighet därmed.
* Status för leveranserna uppdateras inte direkt - en teknisk process körs på Marketing-instansen som uppdaterar leveransstatus i tid.


Läs mer om hur du skickar transaktionsmeddelandekorrektur vid övergång från v7 på [den här sidan](../send/transactional-template.md#transition-from-v7).


## [!DNL Campaign] och [!DNL Snowflake] {#ac-gs-snowflake}

I sin [Enterprise (FFDA)-distribution](../architecture/enterprise-deployment.md) fungerar [!DNL Adobe Campaign] v8 med två databaser: en lokal [!DNL Campaign]-databas för användargränssnittet för meddelanden i realtid och enhetliga frågor och skrivningar via API:er samt en molndatabas [!DNL Snowflake] för kampanjkörning, gruppfrågor och arbetsflödeskörning.

Campaign v8 Enterprise innehåller konceptet **FDA (Full Federated Data Access)**: alla data finns nu på fjärrbasis i molndatabasen. Med den här nya arkitekturen förenklar driftsättningen av Campaign v8 Enterprise (FFDA) datahanteringen: inget index krävs för molndatabasen. Du behöver bara skapa tabellerna, kopiera data så kan du börja. Cloud-databastekniken kräver inget specifikt underhåll för att garantera prestandanivån.

Läs mer om arkitekturen [!DNL Campaign] v8 i [den här sidan](../architecture/architecture.md).


## Använd din Adobe ID för att ansluta till Campaign{#adobe-id}

Kampanjanvändare ansluter bara via sina Adobe ID. Samma Adobe ID används för att behålla alla Adobe-planer och -produkter som är kopplade till ett enda konto för alla Adobe Experience Cloud-lösningar.

Lär dig hur du ansluter till [!DNL Campaign] på [den här sidan](connect.md).

## Analysera data med kuber{#adobe-reporting}

Använd modulen Marketing Analytics för att analysera och mäta data, beräkna statistik, förenkla och optimera framtagning och beräkning av rapporter. Skapa dessutom rapporter och bygg upp målpopulationer: när de har identifierats lagras de i listor som kan användas i Adobe Campaign (målinriktning, segmentering osv.).

Med Adobe Campaign v8 är kubrapporterna optimerade och har bättre skalbarhet än Campaign Classic v7. I den specifika distributionsmodellen gäller inte tidigare begränsningar för kuber i Campaign v8. Läs mer om kuber i [det här avsnittet](../../v8/reporting/gs-cubes.md).

## Otillgängliga funktioner{#gs-unavailable-features}

Observera att vissa funktioner inte är tillgängliga i samband med en [Enterprise (FFDA)-distribution](../architecture/enterprise-deployment.md) av Campaign, till exempel:

* Hantera marknadsföringsresurser
* Kuponger
* Webbspårning
* Undersökningar

## Funktioner som inte stöds{#gs-removed}

Vissa tidigare Campaign Classic v7-funktioner stöds inte längre i Campaign v8, till exempel:

* Social marknadsföring med Facebook
* ACS Connector (Prime-erbjudande)
* Integrering med LDAP
* Logga in med användare/lösenord
* Hybrid/lokala distributionsmodeller


>[!NOTE]
>
>Vissa funktioner som inte är tillgängliga eller som inte stöds kan fortfarande visas i användargränssnittet.
