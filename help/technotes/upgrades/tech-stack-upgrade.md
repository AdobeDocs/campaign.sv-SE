---
product: campaign
title: Technote - Adobe Campaign systemuppgraderingar
description: Adobe Campaign systemuppgradering
hide: true
hidefromtoc: true
exl-id: cc64cce1-2473-4136-aadc-8b13e89ef7f9
source-git-commit: 0f5efba364ef924447324bdd806e15e6db8d799d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 9%

---

# Adobe Campaign 2023 miljöuppgraderingar {#ac-system-upgrade}

Kampanjinfrastrukturen bygger på tredjepartssystem som regelbundet måste uppdateras med de senaste versionerna och korrigeringarna. Dessa uppdateringar är obligatoriska för att säkerställa kontinuitet i tjänsten och säkra kampanjmiljöer från säkerhetsrisker. Dessutom krävs en Campaign-uppgradering för att säkerställa kompatibilitet med systemändringar från tredje part.

Som **kund hos hanterade Cloud Service** informerar Adobe dig om dessa uppgraderingar när de behövs. Miljöerna måste uppgraderas i enlighet med rekommendationerna för att säkerställa regelefterlevnad.

Av säkerhetsskäl måste Adobe [installera den senaste Campaign-versionen](#ac-upgrade) och sedan uppgradera ditt [operativsystem](#os-upgrade) och/eller ditt [Relation Database Management System (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Om du har frågor om de här ändringarna kan du kontakta [Adobes kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Uppgradering av kampanjbygge {#ac-upgrade}

**Påverkas du?**

Om du påverkas av [operativsystemsuppgraderingen](#os-upgrade) och/eller [databassystemsuppgraderingen](#pg-upgrade) som anges nedan måste Adobe uppgradera dina Campaign-miljöer till [den senaste 8.4.3-versionen](../../v8/start/release-notes.md), som är kompatibel med dessa system.

**Hur uppdaterar jag?**

Som kund med hanterade Cloud Service kommer Adobe att kontakta dig och uppgradera din Campaign-version.

## Uppgradering av operativsystem {#os-upgrade}

**Påverkas du?**

Om du kör Campaign på ett Debian-operativsystem måste Adobe flytta din Campaign-infrastruktur till **Debian 11** för att få tillgång till de senaste Debian-säkerhetsuppdateringarna. Observera att säkerhetssupport för Debian 9 kommer att vara tillgänglig till 30 juni 2023.

**Hur uppdaterar jag?**

Som kund hos Managed Cloud Services kommer Adobe att kontakta dig och uppgradera din miljö.

## Uppgradering av databassystem {#pg-upgrade}

**Påverkas du?**

Om ditt databassystem för Campaign är PostgreSQL, och du vill använda de senaste PostgreSQL-innovationerna och säkerhetsuppdateringarna, måste Adobe uppgradera till **PostgreSQL 14**. Observera att PostgreSQL 11 når slutet av livscykeln den 9 november 2023.

**Hur uppdaterar jag?**

Som kund med hanterade Cloud Service kommer Adobe att kontakta dig och uppgradera ditt databassystem från PostgreSQL 11 till PostgreSQL 14.
