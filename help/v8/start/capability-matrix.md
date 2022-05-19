---
title: Campaign Classic v7 - Funktionsmatris för kampanj v8
description: Förstå skillnaderna mellan Campaign Classic v7 och Campaign v8
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 00ba1c43-9558-4adb-83a1-6597c2bbca62
source-git-commit: 6de5c93453ffa7761cf185dcbb9f1210abd26a0c
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 4%

---

# [!DNL Campaign Classic] v7 - [!DNL Campaign] v8-funktioner{#gs-matrix}

Som tidigare [!DNL Campaign Classic] v7-användare, du bör inte förvänta dig några större störningar i ditt sätt att interagera med [!DNL Adobe Campaign]. De flesta ändringar i v8 är inte synliga, med undantag för små ändringar som uppstår i gränssnittet och konfigurationsstegen.

Adobe Campaign v8 finns som **Hanterad Cloud Service**. Det nya erbjudandet kombinerar förstklassiga tjänster med proaktiv tillsyn och snabb varning, med fokus på tre områden:

* **Flexibilitet i molnet** - automatisering av Adobe, med optimerade, standardiserade molndriftsättningar för mer förutsägbara prestanda, större flexibilitet och förbättrad självbetjäning.
* **Tjänsteupplevelse** — proaktiv tillgänglighet, kapacitet, prestandaövervakning och åtgärder för att förhindra avbrott, åtgärda incidenter snabbare och regelbundet granska tjänsten för kontinuerlig förbättring.
* **Djupgående kampanjexpertis** — service med hög affinitet från expertgrupper för kundkonstruktion för att tillgodose behov av funktionalitet, teknik eller leveransförmåga, minska driftsättningsriskerna och förbättra ändringshanteringen.

Som tidigare [!DNL Campaign Classic] användare, observera att de flesta av [!DNL Campaign Classic] v7-funktioner är tillgängliga med [!DNL Campaign] v8, förutom en liten uppsättning, som listas i [det här avsnittet](#gs-removed). Andra kommer i framtida versioner. [Läs mer i det här avsnittet](#gs-unavailable-features)

>[!NOTE]
>
> Campaign v8 bygger på en hybridarkitektur. Om du går över från Campaign Classic v7 bör du tänka på att alla leveranser går via servern för mellanlagring. [Läs mer](../architecture/architecture.md)
>
> Följaktligen är intern routning **inte möjligt** i Campaign v8 och det externa kontot har inaktiverats i enlighet med detta.


## [!DNL Campaign] och [!DNL Snowflake] {#ac-gs-snowflake}

Campaign v8 fungerar med [!DNL Snowflake]. Det finns två distributionsmodeller.

![](../assets/do-not-localize/glass.png) Läs mer om [!DNL Campaign] v8-arkitektur i [den här sidan](../architecture/architecture.md).


## Använd din Adobe ID för att ansluta till Campaign{#adobe-id}

Kampanjanvändare ansluter via sina Adobe ID. Samma Adobe ID används för att behålla alla dina Adobe-planer och produkter som är kopplade till ett enda konto för alla Adobe Experience Cloud-lösningar.

![](../assets/do-not-localize/glass.png) Lär dig hur du ansluter till [!DNL Campaign] in [den här sidan](connect.md).

## Analysera data med kuber{#adobe-reporting}

Använd modulen Marketing Analytics för att analysera och mäta data, beräkna statistik, förenkla och optimera framtagning och beräkning av rapporter. Skapa dessutom rapporter och bygg målpopulationer: när de har identifierats lagras de i listor som kan användas i Adobe Campaign (målinriktning, segmentering osv.).

Adobe Campaign kubrapporter är optimerade och har bättre skalbarhet än Campaign Classic v7. Tidigare begränsningar för kuber gäller inte i Campaign v8.

## Ändra datakälla {#change-data-source}

Campaign v8 erbjuder en ytterligare arbetsflödesaktivitet för målinriktning: **[!UICONTROL Change data source]**.

The **[!UICONTROL Change data source]** kan du ändra datakällan för ett arbetsflöde **[!UICONTROL Working table]** för att hantera data över olika datakällor, som FDA, FFDA och lokala databaser.

![](../assets/do-not-localize/glass.png) Läs mer på **[!UICONTROL Change data source]** aktivitet i [den här sidan](../config/workflows.md#change-data-source-activity).

## Otillgängliga funktioner{#gs-unavailable-features}

Observera att vissa funktioner inte är tillgängliga i den här versionen av Campaign, till exempel:

* Hantera marknadsföringsresurser
* Distribuerad marknadsföring
* Responshanteraren
* Hybrid/lokala distributionsmodeller

>[!CAUTION]
>
>* För tillfället är Campaign v8 **endast** finns som hanterad Cloud Service och kan inte distribueras på plats eller i hybridmiljöer.
>
>* Migrering från en befintlig Campaign Classic v7-miljö är inte tillgänglig än.
>
>* Om du är osäker på din distributionsmodell eller har frågor kontaktar du din kontoansvarige på Adobe.


## Funktioner som inte stöds{#gs-removed}

För att passa den nya arkitekturen och distributionsmodellen i Campaign v8 stöds inte längre vissa tidigare Campaign Classic v7-funktioner i Campaign v8, som:

* Kuponger
* Webbspårning
* Undersökningar
* Social marknadsföring med Facebook
* ACS Connector (Prime offer)
* Integrering med LDAP
* Logga in med användare/lösenord

>[!NOTE]
>
>Vissa funktioner som inte är tillgängliga eller som inte stöds kan fortfarande visas i användargränssnittet.
