---
title: Nyheter i Campaign v8
description: Upptäck nyckelfunktionerna i Campaign v8
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 7771a02c-ebd4-48b6-b25e-6b6e420ad493
source-git-commit: d2f4e54b0c37cc019061dd3a7b7048cd80876ac0
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 6%

---

# Nyheter i Adobe Campaign v8? {#ac-gs-what-is-new}

Adobe Campaign v8 har avsevärda förbättringar vad gäller infrastruktur, säkerhet, leveransbarhet och övervakning. Genom att utnyttja [[!DNL Snowflake]](https://www.snowflake.com/), som är en teknik för molndatabaser, förbättrar Adobe Campaign dramatiskt sin skala och hastighet, med möjlighet att hantera ett större antal kundprofiler samt mycket högre leveransfrekvenser och transaktioner per timme.

## Viktiga möjligheter{#key-capabilities}

Viktiga funktioner:

* **Hastighet och skala**. Adobe Campaign v8 utnyttjar Cloud Database Manager, vilket leder till frågor som går upp till 200 gånger snabbare, skalning av flera petabyte, ökat antal meddelanden per timme, med upp till 20 MB/timme eller 1 MB/timme för transaktionsmeddelanden, och hanterar upp till 200 miljoner aktiva profiler med potential att nå 1B.

* **Anslutningar till Adobe Experience Platform**. Adobe Campaign v8 har stöd för dataanslutningar med Adobe Experience Platform/RT-CDP, enhetlig kundprofil och inbyggd integrering med Journey Orchestration. Dessa investeringar kommer att optimera Adobe Campaign kundupplevelse och frigöra nya användningsfall som möjligheten att lägga till individuella kundresor i realtid till kampanjer.

* **Hanterade Cloud Services**. Adobe Campaign v8 är en av de bästa hanterade Cloud Servicens som ger proaktiv tillsyn, snabb varning och servicestyrning. Marknadsförarens värde är en mer flexibel och skalbar kanalövergripande kampanjhantering.

>[!CAUTION]
>
>För tillfället är Campaign v8 **endast** finns som hanterad Cloud Service och kan inte distribueras på plats eller i hybridmiljöer.
>
>Migrering från en befintlig Campaign Classic v7-miljö är inte tillgänglig än.
>
>Om du är osäker på din distributionsmodell eller har frågor kontaktar du ditt kontoteam.

![](assets/home-page.png)

## Skala{#scale}

Campaign v8 ger en heltäckande skala i alla steg av processen, från målinriktning till slutrapportering:

* Skala den datavolym du kan hantera (till 8 TB)
* Skala upp prestanda för frågor för segmentering och målinriktning men även för datainhämtning och urkunder
* Skala leveransberedningen (från timmar till minuter)

## Självbetjäningsadministratörsgränssnitt{#self-service-admin}

Som produktadministratör kan du hantera inställningar och spåra användningen av var och en av era Campaign v8-instanser med **Kontrollpanelen för kampanj**.

Via ett intuitivt användargränssnitt kan administratörer övervaka användningen av nyckelresurser, utföra avancerade uppgifter som IP-adresser som tillåter listning, SFTP-lagringsövervakning, nyckelhantering med mera. Det här självbetjäningsgränssnittet ger dig större flexibilitet och hjälper dig att:

* Gör ändringar av inställningarna själv utan att kontakta Adobe Support
* Konfigurera inställningar baserat på olika affärsbehov vid olika tidpunkter
* kontrollera åtkomstinställningarna efter behov för att förbättra säkerheten

![](assets/subdomain1.png)

![](../assets/do-not-localize/glass.png) [Läs mer om Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html){target=&quot;_blank&quot;}



## Förenkling och prestandaökning{#simplification-and-perf-increase}

Campaign v8 innehåller konceptet **Fullständig federerad dataåtkomst** (FFDA): alla data är nu fjärranslutna till molndatabasen.

Med den här nya arkitekturen förenklar Campaign v8 datahanteringen: inget index krävs för molndatabasen. Du behöver bara skapa tabellerna, kopiera data så kan du börja.

[!DNL Snowflake] är Campaign Cloud-databasen, vilket ger er snabbhet och uthållighet: ingen överbelastning av systemaktivitetens toppar.

Cloud-databastekniken kräver inget specifikt underhåll för att garantera prestandanivån.

## Integrerat ekosystem

Ni kan integrera Campaign med en uppsättning kraftfulla Adobe-lösningar, som: Adobe Analytics, Adobe Journey Orchestration, Real-Time CDP med flera.

Ni kan också konfigurera prediktiv optimering av sändningstiden och prediktiv poängsättning med Journey AI samt öka antalet öppna samtal, antalet klick och intäkterna.

![](../assets/do-not-localize/glass.png) [Läs mer om Campaign-integreringar](../connect/integration.md)

