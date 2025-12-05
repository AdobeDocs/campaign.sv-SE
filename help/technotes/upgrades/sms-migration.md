---
title: Gå till den nya SMS-kopplingen v2
description: Lär dig hur du går över till den nya SMS-kopplingen v2
feature: Technote
role: Admin
exl-id: 61a5a3e8-59f8-47ea-afc9-66ec243b8265
source-git-commit: 30ab5a10f17baddfc455dc406a4f31f058ea05ba
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Gå till den nya SMS-kopplingen v2

Adobe Campaign v8 introducerar en ny **dedikerad SMS-processkontakt** (v2) som ger bättre prestanda och tillförlitlighet jämfört med den äldre MTA-baserade SMS-anslutningen.

## Varför ska jag byta till v2-kontakten?

I den dedikerade SMS-processen introduceras stöd för SMPP-sändningsläget, vilket minskar antalet anslutningar och förbättrar resurseffektiviteten, samtidigt som det fortfarande finns stöd för konfiguration av sändare/mottagare vid behov. Det ger betydligt större stabilitet, med snabbare återställning efter fel, beständiga anslutningar och utan beroende av lokala filer eller kommunikation mellan processer. Prestanda har också förbättrats med lägre latens, högre genomströmning och intelligent mikrobatchhantering för att balansera hastighet och tillförlitlighet. Dessutom förenklar isoleringen av SMS-processen felsökning och minimerar påverkan över flera kanaler. Dessa förbättringar gör den dedikerade kontakten till en mer robust och skalbar lösning för SMS-leverans.

## Konfiguration

Med Adobe Campaign Managed Cloud Services hanteras serverkonfigurationen och SMS-anslutningsmigrering av Adobe. Den här tekniska proceduren kräver direktåtkomst till serverkonfigurationsfilerna och databasåtgärder.

Om du behöver migrera till den nya SMS-kopplingen v2 kontaktar du Adobe eller Adobe kundtjänst. De schemalägger och utför de nödvändiga uppdateringarna för din instans.

Mer information om SMS-kanalen i Campaign v8 finns i [SMS-dokumentationen](../../v8/send/sms/sms.md).
