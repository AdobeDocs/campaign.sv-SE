---
title: Migrera Campaign-sändningsinfrastruktur till Amazon Web Services (AWS)
description: Migrera Campaign-sändningsinfrastruktur till Amazon Web Services (AWS)
hide: true
hidefromtoc: true
source-git-commit: 9401e3564b53b920dd6a640ca6d00531992a2f21
workflow-type: tm+mt
source-wordcount: '481'
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
* Campaign Standarder

## När kommer migreringen att ske?{#aws-timeline}

Migreringen av utvecklings- och mellanlagringsmiljöer kommer att äga rum i **Oktober 2023**.

Migreringen av produktionsmiljöer är schemalagd att börja i **Januari 2024**. Mer information ges när datumet närmar sig.

Som Campaign-kund får du ytterligare meddelanden när migreringsvågorna är schemalagda. Meddelanden skickas minst 7 dagar före migreringen för scenmiljöer och minst 30 dagar före migreringen för produktionsmiljöer.

## Vad ändras?{#impact}

Detta kommer att vara transparent för kunderna:

* Längden på varje migreringsvåg kan variera beroende på antalet påverkade Campaign-instanser. När en migreringsvåg är schemalagd kommer meddelandet att innehålla den förväntade längden.

* Kampanjinstanser kan inte skicka e-post under migreringsfönstret. Ingen annan Campaign-funktion påverkas.


## Vanliga frågor och svar {#aws-faq}

* **Varför är detta en obligatorisk uppgradering?**

  Adobe planerar att avveckla det gamla datacentret. Adobe Campaign-instanser som körs där måste överföras till det nya referensdatacentret, Amazon Web Services (AWS).

  Molnet för Adobe Managed Services ligger på Amazon Web Services (AWS), en modern, säker och optimerad miljö. [Läs mer om Amazon Web Services](https://aws.amazon.com/application-hosting/benefits/){target="_blank"}.

* **Vilka kunder är inriktade på migreringen?**

  Miljöerna migreras för alla Campaign v8-kunder och Campaign Classic v7-hybriden, värdservern och Campaign Managed Services. Campaign Standarden påverkas också.

* **Vilka är de förväntade driftsavbrotten?**

  Migreringen förväntas ta mellan 30 min och 60 min, men längden på varje migreringsvåg kan variera beroende på antalet påverkade Campaign-instanser. När en migreringsvåg är schemalagd kommer meddelandet att innehålla den förväntade längden.

* **Behöver kunden vidta några åtgärder för migreringen?**

  Inga åtgärder krävs eftersom migreringen automatiskt kommer att köras av Adobe.

* **Vilka valideringar behöver kunderna köra?**

  Det behövs ingen specifik testning för den här migreringen. Om något problem uppstår, kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support){target="_blank"}.


* **Kan jag begära en ändring av datum/tid för den schemalagda säkerhetsuppgraderingsplatsen?**

  Eftersom detta är en obligatorisk migrering kan vi inte hantera ändringar av det befintliga schemat.

För alla andra frågor kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support){target="_blank"}.
