---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-versionen
feature: Release Notes
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: f25b0a0fea5f32dd509d8b78e6f6a010d9598a9f
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 12%

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
* [Innehållsexperiment - A/B-testning](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/email/ab-testing.html?lang=sv-SE){target="_blank"}
* [Kontinuerlig leveransaktivitet](https://experienceleague.adobe.com/docs/campaign-web/v8/wf/design-workflows/continuous-delivery.html?lang=sv-SE){target="_blank"}
* [Hantering av kampanjgodkännande](https://experienceleague.adobe.com/docs/campaign-web/v8/campaigns/campaign-approvals.html?lang=sv-SE){target="_blank"}

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

* Ett problem har korrigerats där databasstrukturen inte kunde uppdateras efter sysFilter-ändringar. (NEO-93306)
* Korrigerade ett problem där dynamiska rapportdata saknades efter migreringen. (NEO-92962)
* Ett problem har korrigerats där leveransstatusen inte uppdaterades korrekt. (NEO-92908)
* Korrigerade ett problem relaterat till begränsningen Databriker för FDA-användning av katalog. (NEO-92900)
* Ett problem som kan orsaka layoutfel i HTML i Outlook på skrivbordet har korrigerats. (NEO-92611)
* Ett dataintegritetsproblem har korrigerats där primära nycklar för leverans duplicerades på mittinstansen efter en uppgradering. (NEO-92424)
* Ett problem där länkar inte kunde inaktiveras i dialogrutan Spåra och bilder i en leverans har korrigerats. (NEO-92381)
* Ett problem har korrigerats där funktionen nms.subscribtion.RecipientSubscribe() inte fungerade för massprenumeration. (NEO-92308)
* Korrigerade ett problem där leveransfel uppstod på grund av saknade leveransdelar efter en uppgradering. (NEO-92278)
* Ett problem i spårningsarbetsflödet där dubblettstatusfel och SQL-syntaxfel förhindrade att spårningsindikatorer uppdaterades har åtgärdats. (NEO-92239)
* Ett problem har korrigerats där uppräkningsfältetiketter saknades eller visades felaktigt i listor som skapades via arbetsflödet när dbEnum-fält användes. (NEO-91158)
* Ett problem har korrigerats där dialogrutan för publicering/avpublicering inte stängdes och låstes. (NEO-91038)
* Korrigerade ett problem som uppstod för mottagare med statusen &quot;som tagits med i beräkningen av tjänsteleverantören&quot;. (NEO-90927)
* Ett problem har korrigerats där (un)prenumerationens ursprung saknades för avanmälningslänkar. (NEO-90714)
* Ett problem har korrigerats där leveransförberedelsen för att lägga till kuponger misslyckades. (NEO-90547)
* Ett problem har korrigerats där antalet ignorerade infogningar inte återspeglades korrekt på fliken Granskning. (NEO-90318)
* Korrigerade ett säkerhetsproblem som kunde orsaka denial of service-fel i programmet. (NEO-89984)
* Korrigerade ett problem där den hämtade PDF-versionen av Hotclick-rapporten bröts. (NEO-89954)
* Löste ett SSL-fel som inträffade efter en uppgradering, vilket orsakade ett oväntat EOF-fel vid läsning. (NEO-89108)
* Korrigerade ett problem där data inte kunde läsas i ett dataschema efter en uppgradering. (NEO-88663)
* Ett fel som uppstod när ett teckenfält i PostgreSQL 15 skulle sammanfogas har åtgärdats. (NEO-88028)
* Ett problem har korrigerats där leveransmallvariablerna ändrades när mallen sparades eller duplicerades. (NEO-87845)
* Ett problem har korrigerats där webbgränssnittet kraschade när ett nytt databiblioteksschema skapades. (NEO-87816)
* Korrigerade ett problem där komplementuppsättningar i aktiviteten Deduplicering fanns med. (NEO-87711)
* Korrigerade en begäran om installationspaket utan X11-beroende. (NEO-87471)
* Ett problem där segmentkoder inte kunde användas i dynamiska rapporter har korrigerats. (NEO-87276)
* Ett problem där arbetsflöden fastnade i aktiviteten Uppdatera data har korrigerats. (NEO-87252)
* Ett problem där BigQuery använde en felaktig tidszon har korrigerats. (NEO-86622)
* Korrigerade ett JavaScript-fel som uppstod när skriptet mcSynch_mcExec1/jsReplicateUrl utvärderades. (NEO-86553)
* Korrigerade ett problem där dubbletthändelser påträffades i tabellen eventHistory på grund av en felaktig identifierarberäkningsmetod. (NEO-86544)
* Ett problem har korrigerats där fliken Avancerat inte visades för iOS Push vid kopiering. (NEO-86231)
* Ett problem har korrigerats där arbetsflödet för replikerade referenstabeller misslyckades med att replikera nms:delivery-schemat. (NEO-85884)
* Ett problem har korrigerats där null-domänfel som motsvarar MXIP-adresser påträffades i felloggarna när leveranser skickades. (NEO-85238)
* Ett problem har korrigerats där mallar för teknisk leverans inte uppdaterades efter ändringar av alternativen. (NEO-84149)
* Korrigerade ett fel i det färdiga arbetsflödet för fakturering. (NEO-83624)
* Korrigerade ett problem med undantag av dubbletter som bara baseras på primärnyckeln för målposter. (NEO-82910)
* Korrigerade avvikelser i webbgränssnittsrapporter för Campaign där spårningsstatistik visade olika värden jämfört med konsolen. (NEO-82339)
* Ett problem har korrigerats där det senaste ändringsdatumet ändrades även om posten inte skulle uppdateras i aktiviteten Uppdatera data. (NEO-82002)
* Ett problem har korrigerats där tillägg av nya attribut i en lista gjorde att arbetsflöden inte kunde läsa listan. (NEO-80258)
* Ett problem har korrigerats där spårningsindikatorn visade felaktiga värden för distinkta öppningar. (NEO-79466)