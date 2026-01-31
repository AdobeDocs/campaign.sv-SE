---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: 6693bb8a62c0d126b871dc24a75b76de71b86f8d
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 14%

---

# Senaste releaser {#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i Campaign v8 (konsol) **de senaste versionerna**. Läs mer om Campaign-versioner, -versioner och -uppgraderingar på [den här sidan](upgrades.md). Andra versioner listas i avsnittet Tidigare versioner i den här dokumentationen.

## Version 8.9.1 {#release-8-9-1}

_27 januari 2026_

>[!CAUTION]
>
> Uppgradering av klientkonsolen är obligatorisk. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../start/connect.md#upgrade-ac-console).

### Nya funktioner {#new-8-9-1}

Den **nya SMS-sändningsanslutningen** är nu tillgänglig för alla kunder (GA). Mer information finns i [detaljerad dokumentation](../send/sms/sms.md).

Den här versionen innehåller en uppsättning funktioner som är tillgängliga med användargränssnittet för Campaign-webben:

* [Funktioner för flerspråkig leverans (GA)](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/multilingual.html?lang=sv-SE){target="_blank"}
* [Profilberikning i transaktionsmeddelanden (GA)](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/transactional-messages/profile-enrichment.html?lang=sv-SE){target="_blank"}
* [Adobe Experience Manager live- och språkversioner](https://experienceleague.adobe.com/docs/campaign-web/v8/integrations/aem-multilingual.html?lang=sv-SE){target="_blank"}
* [Innehållsexperiment - A/B-testning](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/email/ab-testing.html?lang=sv-SE)
* [Kontinuerlig leveransaktivitet](https://experienceleague.adobe.com/docs/campaign-web/v8/wf/design-workflows/continuous-delivery.html?lang=sv-SE)
* [Hantering av kampanjgodkännande](https://experienceleague.adobe.com/docs/campaign-web/v8/campaigns/campaign-approvals.html?lang=sv-SE)

Se versionsinformationen för Campaign Web UI [&#128279;](https://experienceleague.adobe.com/docs/campaign-web/v8/release-notes/release-notes.html?lang=sv-SE){target="_blank"}

### Säkerhetsförbättringar {#security-8-9-1}

* Snowflake externa konton har nu stöd för OAuth2-autentisering, vilket ger moderna och säkra autentiseringsmetoder för federerade dataåtkomstanslutningar. (NEO-87013)
* Ett problem med filåtkomst i arbetsflödet har åtgärdats genom att åtgärderna begränsas till auktoriserade kataloger, vilket förhindrar obehörig åtkomst och eventuell fjärrexekvering av kod. (NEO-88460)
* FTP URL-tillåtslista kontroller har lagts till i arbetsflödet för JavaScript-kodaktiviteter, vilket begränsar utgående FTP-anslutningar till endast auktoriserade adresser. (NEO-89083)

### Andra ändringar {#changes-8-9-1}

* Förbättrad hantering av behållarminne genom automatisk arbetsflödesbegränsning under höga minnesförhållanden, med smarta funktioner för omstart av arbetsflödet och minnesskydd för icke-kritiska processer. (NEO-89041)
* Stöd för asymmetrisk kryptering och dekrypteringsfunktioner i Campaign-arbetsflöden har lagts till. (NEO-80257)
* Förbättrade replikeringsagentprestanda och minnesflexibilitet för stora dataöverföringar i FFDA-distributioner. (NEO-88430)


### Korrigeringar {#fixes-8-9-1}

* Ett problem har korrigerats där dynamiska rapporter visade felaktiga antal vid gruppering efter vissa kolumner. (NEO-86898)
* Löste diskrepanser mellan dynamiska rapporter och faktiska kampanjdata. (NEO-88068)
* Åtgärdade sammanfogningsproblem med PostgreSQL &quot;char&quot;-fälttyper som orsakade oväntade resultat i frågor. (NEO-87769)
* Ett problem har korrigerats där JavaScript logInfo-kommando inte kunde hantera vissa parametrar korrekt. (NEO-88263)
* Löste problem med låsning av synkronisering vid händelsebearbetning i realtid i Message Center. (NEO-88330)
* Ett problem har korrigerats där HTML-innehåll formaterades om automatiskt i Visual Editor, vilket ledde till layoutändringar. (NEO-88409)
* Ett problem har korrigerats där dedupliceringsaktiviteten inte fungerade korrekt med temporära scheman. (NEO-88577)
* Ett problem som förhindrade att dirigerade adresser genereras när korrektur skickas har åtgärdats. (NEO-88720)
* Förbättrade PostSQL-frågeprestanda genom att optimera hantering av partitionskolumner. (NEO-88771)
* Ett problem har korrigerats där filöverföringsaktiviteter inte hanterar radfortsättningstecken korrekt. (NEO-88812)
* Förbättrad PostSQL-frågeoptimering för bättre prestanda i stora datamängder. (NEO-88885)
* Korrigerade ett fel om nekad behörighet som förhindrade att hybridkampanjer öppnades. (NEO-88955)
* Utökat stöd för streckkodsfunktioner som hanterar längre textsträngar. (NEO-88958)
* Ett fel i kampanjloggar som inträffade när korrektur med återkommande leveranser användes har korrigerats. (NEO-88976)
* Korrigerade ett problem som påverkade e-postsändningsåtgärder i vissa scenarier. (NEO-89019)
* Ett problem där arbetsflödets startläge oväntat ändrades från Omedelbart till Normal har åtgärdats. (NEO-89025)
* Korrigerade fel som uppstod när aktiviteten Uppdatera data kördes under specifika förhållanden. (NEO-89031)
* Ett problem där aktiviteten Uppdatera data förlorade anpassade schemadata har korrigerats. (NEO-89056)
* Ett valideringsfel som uppstod under leveransförberedelsen har korrigerats. (NEO-89063)
* Löste ogiltig SQL-generering när frågor innehöll filter för 1-1-länkrelationer. (NEO-89065)
* Ett problem har korrigerats där aktiviteten Inkrementell fråga inte uppfyllde den konfigurerade storleksgränsen. (NEO-89066)
* Förbättrade arbetsflödesprestanda i FFDA-distributioner för storskaliga åtgärder. (NEO-89098)
* Förbättrad minneshantering och stabilitet för arbetsflödesprocesser. (NEO-89105)
* Aktiverade strikt kolumnvalidering för webbformulär för att förhindra inkonsekvenser i data. (NEO-89111)
* Löste problem med synkronisering av meddelandecenter som orsakade bearbetningsförseningar. (NEO-89138)
* Korrigerade fel i arbetsflödet Uppdatera för slutbarhet som förhindrade att programmet kördes korrekt. (NEO-89160)
* Fel som uppstod när JavaScript-kodaktiviteter kördes i arbetsflöden har korrigerats. (NEO-89169)
* Tog bort hårdkodade Snowflake-lagerställekonfigurationer för att tillåta lämpliga externa kontoinställningar. (NEO-89201)
* Korrigerade 403 Otillåtna fel som uppstod under filöverföringsåtgärder i arbetsflödet. (NEO-89226)
* Optimerade långsamma frågor i mottagartabellen i FFDA-distributioner. (NEO-89268)
* Ett problem har korrigerats där inkrementella frågeaktiviteter ignorerade konfigurerade scheman. (NEO-89317)
* Åtgärdade åtkomstfel när kampanjer öppnades i hybridmiljöer. (NEO-89320)
