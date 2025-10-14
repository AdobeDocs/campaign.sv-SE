---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: d31368428fc7d5b982bb5fc67d0369bb17ea0b2c
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 8%

---

# Senaste releaser {#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i Campaign v8 (konsol) **de senaste versionerna**. Läs mer om Campaign-versioner, -versioner och -uppgraderingar på [den här sidan](upgrades.md). Andra versioner listas i avsnittet Tidigare versioner i den här dokumentationen.

## Version 8.8.2 {#release-8-8-2}

_9 okt 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA).

### Nya funktioner {#features-8-8-2}

Den **nya SMS-sändningskonnektorn** är nu tillgänglig för [Campaign FFDA-distributioner](../architecture/enterprise-deployment.md). Mer information finns i [detaljerad dokumentation](../send/sms/sms.md).

Den här versionen innehåller även en uppsättning funktioner som är tillgängliga med användargränssnittet för Campaign-webben:

* [Profilberikning i transaktionsmeddelanden](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/transactional-messages/profile-enrichment.html){target="_blank"}
* [Flerspråkiga funktioner för transaktionsmeddelanden, push-meddelanden och SMS](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/multilingual.html){target="_blank"}

Se versionsinformationen för Campaign Web UI [](https://experienceleague.adobe.com/docs/campaign-web/v8/release-notes/release-notes.html){target="_blank"}

### Korrigeringar {#fixes-8-8-2}

<!--
* Fixed an issue which prevented dynamic reporting from being available for transactional messages.
-->
* Korrigerade ett problem som kunde leda till att arbetsflödet för databasrensning misslyckades. (NEO-87949)
* Korrigerade ett fel i distribuerad marknadsföring där spårningsdata inte registrerades för samverkanskampanjleveranser. (NEO-86836)
<!--
* Issue SMS2.0 with FFDA Continuous Deliveries (NEO-88785)
-->
* Ett problem som kunde förhindra personalisering i fragment från att fungera korrekt har korrigerats. (NEO-88161)
* Ett problem har korrigerats efter migrering till den nya ODBC-kopplingen för Redshift, vilket kan leda till att den delade arbetsflödesaktiviteten misslyckas med SQL-fel. (NEO-87466)
* Korrigerade ett problem som kunde orsaka felaktiga undantagsfel i arbetsflöden. (NEO-89207)
* Korrigerade ett problem som kunde orsaka felaktiga klickindikeringar för push-meddelanden. (NEO-89503)
* Ett problem där SMS-leveransloggar inte uppdaterades korrekt har korrigerats, vilket förhindrar korrekt statusrapportering i Adobe Campaign. (NEO-88479)
* Ett problem har korrigerats där franska citattecken felaktigt konverterades till engelska citattecken i leveransinnehåll. (NEO-89631)
* Korrigerade ett problem där Real-Time Server returnerade en felaktig svarskod för ogiltiga IMS-tokens i stället. (NEO-87428)
* Ett problem har korrigerats där leveransstatistik för e-post och SMS inte räknades om fullständigt, vilket gav felaktiga resultatindikatorer. (NEO-88106)
* Ett problem med den nya SMS-sändningsanslutaren där leveransloggar felaktigt tilldelade leveransstatus för en liten delmängd av meddelanden har åtgärdats. (NEO-89581)
* Korrigerade ett problem med den nya SMS-sändningskonnektorn där leveransvärdena inte uppdaterades korrekt på både marknadsförings- och mellanservrar. (NEO-89850)
* Korrigerade ett synkroniseringsproblem mellan Real-Time- och Marketing-instanserna som orsakade saknade spårningsloggar och felaktig rapportering. (NEO-90247)
* Ett problem med arbetsflödesberikning som kan orsaka fel när fält markeras över två på varandra följande 1-N-länkar i anpassade scheman har åtgärdats. (NEO-87682)

