---
product: Adobe Campaign
title: Nyheter i Campaign v8
description: Läs mer om de viktigaste funktionerna
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 7771a02c-ebd4-48b6-b25e-6b6e420ad493
source-git-commit: 36e29801bcc95565c32e51742a23d4d74d4e3049
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Nyheter i Adobe Campaign v8? {#ac-gs-what-is-new}

Adobe Campaign v8 har avsevärda förbättringar vad gäller infrastruktur, säkerhet, leveransbarhet och övervakning. Genom att utnyttja [[!DNL Snowflake]](https://www.snowflake.com/), en molndatabasteknik, förbättrar Adobe Campaign dramatiskt sin skala och hastighet, med möjlighet att hantera ett större antal kundprofiler samt mycket högre leveransfrekvenser och transaktioner per timme.

Viktiga funktioner:

* **Snabbhet och skala**. Adobe Campaign v8 utnyttjar Cloud Database Manager, vilket leder till frågor som går upp till 200 gånger snabbare, skalning av flera petabyte, ökat antal meddelanden per timme, med upp till 20 MB/timme eller 1 MB/timme för transaktionsmeddelanden, och hanterar upp till 200 miljoner aktiva profiler med potential att nå 1B.

* **Anslutningar till Adobe Experience Platform**. Adobe Campaign v8 har stöd för dataanslutningar med Adobe Experience Platform/RT-CDP, enhetlig kundprofil och inbyggd integrering med Journey Orchestration. Dessa investeringar kommer att optimera Adobe Campaign kundupplevelse och frigöra nya användningsfall som möjligheten att lägga till individuella kundresor i realtid till kampanjer.

* **Hanterade Cloud Services**. Adobe Campaign v8 är en av de bästa hanterade Cloud Servicens som ger proaktiv tillsyn, snabb varning och servicestyrning. Marknadsförarens värde är en mer flexibel och skalbar kanalövergripande kampanjhantering.

>[!CAUTION]
>
>För närvarande är Campaign v8 **endast** tillgängligt som hanterad Cloud Service och kan inte distribueras på en lokal eller hybridmiljö.
>
>Migrering från en befintlig Campaign Classic v7-miljö är inte tillgänglig än.
>
>Om du är osäker på din distributionsmodell eller har frågor kontaktar du ditt kontoteam.


## Skala

Campaign v8 ger en heltäckande skala i alla steg av processen, från målinriktning till slutrapportering:

* Skala den datavolym du kan hantera (till 8 TB)
* Skala upp prestanda för frågor för segmentering och målinriktning men även för datainhämtning och urkunder
* Skala leveransberedningen (från timmar till minuter)

## Förenkling och prestandaökning

Campaign v8 innehåller konceptet **Fullständig federerad dataåtkomst** (FFDA): alla data är nu fjärranslutna till molndatabasen.

Med den här nya arkitekturen förenklar Campaign v8 datahanteringen: inget index krävs för molndatabasen. Du behöver bara skapa tabellerna, kopiera data så kan du börja.

[!DNL Snowflake] är Campaign Cloud-databasen, vilket ger er snabbhet och uthållighet: ingen överbelastning av systemaktivitetens toppar.

Cloud-databastekniken kräver inget specifikt underhåll för att garantera prestandanivån.

## Integrerat ekosystem

Ni kan integrera Campaign med en uppsättning kraftfulla Adobe-lösningar, som: Adobe Analytics, Adobe Journey Orchestration, CDP i realtid med mera.

Ni kan också konfigurera prediktiv optimering av sändningstiden och prediktiv poängsättning med Journey AI samt öka antalet öppna samtal, antalet klick och intäkterna.

[!DNL :bulb:] [Läs mer om Campaign-integreringar](../connect/integration.md)

