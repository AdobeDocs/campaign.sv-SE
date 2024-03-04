---
product: campaign
title: Technote - Adobe Campaign systemuppgraderingar
description: Adobe Campaign systemuppgradering
hide: true
hidefromtoc: true
source-git-commit: c362e6ff932f5017530434c4b458070ec1a97abc
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 9%

---

# Adobe Campaign 2023 miljöuppgraderingar {#ac-system-upgrade}

Kampanjinfrastrukturen bygger på tredjepartssystem som regelbundet måste uppdateras med de senaste versionerna och korrigeringarna. Dessa uppdateringar är obligatoriska för att säkerställa kontinuitet i tjänsten och säkra kampanjmiljöer från säkerhetsrisker. Dessutom krävs en Campaign-uppgradering för att säkerställa kompatibilitet med systemändringar från tredje part.

Som en **Kund för hanterade Cloud Service** får du information från Adobe om dessa uppgraderingar när de behövs. Miljöerna måste uppgraderas i enlighet med rekommendationerna för att säkerställa regelefterlevnad.

Av säkerhetsskäl måste Adobe [installera den senaste Campaign-versionen](#ac-upgrade)och sedan uppgradera [operativsystem](#os-upgrade) och/eller [RDBMS (Relation Database Management System)](#pg-upgrade).

>[!NOTE]
>
>Om du har frågor om de här ändringarna kan du kontakta [Adobes kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Uppgradering av kampanjbygge {#ac-upgrade}

**Påverkas du?**

Om du påverkas av [uppgradering av operativsystem](#os-upgrade) och/eller [databassystemuppgradering](#pg-upgrade) som beskrivs nedan måste Adobe uppgradera era Campaign-miljöer till [den senaste 8.4.3-versionen](../../v8/start/release-notes.md)som är kompatibelt med dessa system.

**Hur uppdaterar jag?**

Som kund med hanterade Cloud Service kommer Adobe att kontakta dig och uppgradera din Campaign-version.

## Uppgradering av operativsystem {#os-upgrade}

**Påverkas du?**

Om ni kör Campaign på ett Debian-operativsystem och vill dra nytta av de senaste säkerhetsuppdateringarna för Debian, måste Adobe flytta Campaign-infrastrukturen till **Debian 11**. Observera att säkerhetssupport för Debian 9 kommer att vara tillgänglig till 30 juni 2023.

**Hur uppdaterar jag?**

Som kund hos Managed Cloud Services kommer Adobe att kontakta dig och uppgradera din miljö.

## Uppgradering av databassystem {#pg-upgrade}

**Påverkas du?**

Om ditt databassystem för Campaign är PostgreSQL och du vill kunna dra nytta av de senaste PostgreSQL-innovationerna och säkerhetsuppdateringarna måste Adobe uppgradera till **PostgreSQL 14**. Observera att PostgreSQL 11 når slutet av livscykeln den 9 november 2023.

**Hur uppdaterar jag?**

Som kund med hanterade Cloud Service kommer Adobe att kontakta dig och uppgradera ditt databassystem från PostgreSQL 11 till PostgreSQL 14.
