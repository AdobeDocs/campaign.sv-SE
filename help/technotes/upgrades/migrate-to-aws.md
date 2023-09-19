---
title: Migrera Campaign-sändningsinfrastruktur till Amazon Web Services (AWS)
description: Migrera Campaign-sändningsinfrastruktur till Amazon Web Services (AWS)
hide: true
hidefromtoc: true
source-git-commit: 557d61e0e015fa955b70858d614e476febd467cb
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 2%

---


# Kampanj för att skicka infrastrukturmigrering till Amazon Web Services (AWS) {#migrate-infra-to-aws}

## Vad har ändrats?{#aws-changes}

Som en del av vårt pågående arbete med att tillhandahålla e-postleveranstjänster av högsta kvalitet har e-postinfrastrukturen för Campaign flyttats från datacentraler på Adobe till Amazon Web Services (AWS).

Detta kommer att säkerställa hög tillgänglighet, optimal genomströmning och möjlighet att skala efter kundernas behov.

## Påverkas du?{#aws-impact}

Ändringen påverkar:

* Campaign Classic v7 som värd och hybridkunder
* Kunder med Managed Services Campaign
* Alla kunder med Campaign v8

## När kommer migreringen att ske?{#aws-timeline}

Migreringen av utvecklings- och mellanlagringsmiljöer kommer att äga rum i **Oktober 2023**.

Migreringen av produktionsmiljöer är schemalagd att börja i **Januari 2024**. Mer information ges när datumet närmar sig.

Som Campaign-kund får du ytterligare meddelanden när migreringsvågorna är schemalagda. Meddelanden skickas minst 7 dagar före migreringen för scenmiljöer och minst 30 dagar före migreringen för produktionsmiljöer.

## Vad ändras?{#impact}

Detta kommer att vara transparent för kunderna:

* Migreringen förväntas ta mellan 30 min och 60 min

* Kampanjinstanser kan inte skicka e-post under migreringsfönstret. Ingen annan Campaign-funktion påverkas.


## Vanliga frågor och svar {#aws-faq}

* **Varför är detta en obligatorisk uppgradering?**

  Den nya Campaign-sändningsinfrastrukturen som tillhandahålls av Adobe Web Services (AWS) ger bättre kvalitet och tillförlitlighet för våra kunder. Den erbjuder också en stark och modern infrastruktur för att säkerställa bättre tillgänglighet och optimalt dataflöde.

* **Vilka kunder är inriktade på migreringen?**

  Miljöerna migreras för alla Campaign v8-kunder och Campaign Classic v7-hybriden, värdservern och Campaign Managed Services.

* **Vilka är de förväntade driftsavbrotten?**

  Förväntat driftstopp är mellan 30 och 60 minuter.

* **Behöver kunden vidta några åtgärder för migreringen?**

  Inga åtgärder krävs eftersom migreringen kommer att köras automatiskt av Adobe.

* **Vilka valideringar behöver kunderna köra?**

  Ingen specifik testning krävs för denna säkerhetsuppgradering. Om något problem uppstår, kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **Kan jag begära en ändring av datum/tid för den schemalagda säkerhetsuppgraderingsplatsen?**

  Eftersom detta är en obligatorisk migrering rekommenderar vi dig att anpassa dig till det befintliga schemat.


För alla andra frågor kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support).
