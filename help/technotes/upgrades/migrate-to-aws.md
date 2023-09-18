---
title: Migrera Campaign-sändningsinfrastruktur till Amazon Web Services (AWS)
description: Migrera Campaign-sändningsinfrastruktur till Amazon Web Services (AWS)
hide: true
hidefromtoc: true
source-git-commit: 53080e3641e0070b0b6e47d1ec8b55b4c7aa2b1a
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 5%

---


# Kampanj för att skicka infrastrukturmigrering till Amazon Web Services (AWS) {#migrate-infra-to-aws}

## Vad har ändrats?{#aws-changes}

Som en del av vårt pågående arbete med att tillhandahålla e-postleveranstjänster av högsta kvalitet har e-postinfrastrukturen för Campaign flyttats från datacentraler på Adobe till Amazon Web Services (AWS).

Detta kommer att säkerställa hög tillgänglighet, optimal genomströmning och möjlighet att skala efter kundernas behov.

## Påverkas du?{#aws-impact}

Som v8-kund, eller en v7-kund, hybrid- eller Managed Services Campaign-kund påverkas ni.

## När kommer migreringen att ske?{#aws-timeline}

Migreringen av utvecklings- och mellanlagringsmiljöer kommer att äga rum i **Oktober 2023**.

Migreringen av produktionsmiljöer är schemalagd att börja i **Januari 2024**. Mer information ges när datumet närmar sig.

Som Campaign-kund får du ytterligare meddelanden när migreringsvågorna är schemalagda. Meddelanden skickas minst sju dagar före migreringen.

## Vad ändras?{#impact}

Detta kommer att vara transparent för kunderna:

* Sändande IP-adresser och versionen för Campaign-bygget förblir desamma som de var före flytten.

* Under migreringsfönstret kan Campaign-instanser inte skicka e-post. Ingen annan Campaign-funktion påverkas.

* Alla e-postmeddelanden som köats för leverans innan underhållsfönstret måste skickas igen.

>[!NOTE]
>
>Om du har frågor om migreringen kan du kontakta din Adobe-representant eller kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>


