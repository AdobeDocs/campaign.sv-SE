---
title: SMS-kopplingar
description: Läs om SMS-anslutningar i Adobe Campaign
feature: SMS
role: User, Admin
level: Intermediate
source-git-commit: e349e9f236c3eeb28ffe96bcc5ec72ab64c4c127
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---

# Om SMS-anslutningstyper {#sms-connectors}

Adobe Campaign har stöd för två SMS-anslutningar som används för att skicka SMS-meddelanden till dina kunder:

* **Äldre SMS-koppling**: Första versionen av kopplingen som används i Campaign v7 och tidigare versioner av Campaign v8. [Läs mer](#legacy-sms-connector)
* **SMS-kontakt v2**: Den här dedikerade SMS-kontakten v2 har moderniserats för att ge bättre prestanda och tillförlitlighet. Den är tillgänglig i GA med början av Campaign v8.9.1. [Läs mer](#sms-connector-v2)

## Äldre SMS-koppling {#legacy-sms-connector}

Den äldre SMS-kopplingen är den MTA-baserade SMS-koppling som används i tidigare versioner av Adobe Campaign. Den här kopplingen stöds fortfarande för befintliga implementeringar, men Adobe rekommenderar starkt att du uppgraderar till v8.9.1 eller senare för att kunna utnyttja den förbättrade prestanda och tillförlitligheten hos v2-anslutningen.

Mer information om hur du kan dra nytta av v2-anslutningen finns i avsnittet [Aktivering](#activation).

Mer information om den gamla SMS-kopplingskonfigurationen och användningen finns i [Campaign Classic-dokumentationen](https://experienceleague.adobe.com/sv/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up/sms-set-up){target="_blank"}.

## SMS-anslutning v2 {#sms-connector-v2}

v2-kontakten är tillgänglig i GA från och med v8.9.1 och möjliggör SMPP-anslutningar i sändningsläge, beständiga SMPP-anslutningar och ger bättre kompatibilitet. Ett dedikerat externt SMS-konto finns tillgängligt för alla SMS-implementeringar som använder v2-anslutningen.

v2-anslutningen är aktiverad som standard för nya installationer. Om du har uppgraderat från en tidigare version med den äldre anslutningen måste du kontakta din Adobe-representant för att byta till v2-kontakten. Se avsnittet [Aktivering](#activation).

Mer information om hur du använder SMS-anslutningen v2 i Campaign v8 finns i [SMS-dokumentationen](sms.md).

>[!NOTE]
>
>v2-anslutningen är även tillgänglig i följande byggen med vissa begränsningar:
>* 8.8.1: release för alla Campaign FDA-miljöer. Inte tillgängligt för Campaign FFDA-distributioner.
>* 8.8.2: release för alla distributionstyper inklusive FFDA. Frisläppt i begränsad tillgänglighet (LA).

## Aktivering {#activation}

### Varför byta till v2-kontakten {#why-switch-v2}

I den dedikerade SMS-processen introduceras stöd för SMPP-sändningsläget, vilket minskar antalet anslutningar och förbättrar resurseffektiviteten, samtidigt som det fortfarande finns stöd för konfiguration av sändare/mottagare vid behov. Det ger betydligt större stabilitet, med snabbare återställning efter fel, beständiga anslutningar och utan beroende av lokala filer eller kommunikation mellan processer. Prestanda har också förbättrats med lägre latens, högre genomströmning och intelligent mikrobatchhantering för att balansera hastighet och tillförlitlighet. Dessutom förenklar isoleringen av SMS-processen felsökning och minimerar påverkan över flera kanaler. Dessa förbättringar gör den dedikerade kontakten till en mer robust och skalbar lösning för SMS-leverans.

### Konfiguration {#configuration}

Med Adobe Campaign Managed Cloud Services hanteras serverkonfigurationen och SMS-anslutningsmigrering av Adobe. Den här tekniska proceduren kräver direktåtkomst till serverkonfigurationsfilerna och databasåtgärder.

Om du vill aktivera och börja använda SMS-anslutningen v2 måste du först uppgradera till v8.9.1 eller senare. Kontakta Adobe eller Adobe kundtjänst. De schemalägger och utför de nödvändiga uppdateringarna för din instans.