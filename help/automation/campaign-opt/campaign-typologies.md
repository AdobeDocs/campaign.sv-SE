---
product: campaign
title: Kom igång med olika kampanjtyper
description: Lär dig konfigurera och implementera kampanjtyper
feature: Typology Rules
exl-id: 7832ffe1-eb65-4b37-9fc5-1374516755d9
source-git-commit: 7fe079c5473fa164405753c2be6cc8be16329f58
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 16%

---

# Kom igång med olika kampanjtyper{#about-campaign-typologies}

**Kampanjoptimering** är Adobe Campaign-modulen som gör att du kan styra, filtrera och övervaka leveransen. För att undvika konflikter mellan kampanjer kan Adobe Campaign testa olika kombinationer genom att tillämpa särskilda begränsningsregler. Detta garanterar att de skickade meddelandena uppfyller kundernas behov och förväntningar och företagets kommunikationspolicy.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#typologies-video)

>[!NOTE]
>
>Beroende på vilket erbjudande du erbjuder kan Campaign Optimization inkluderas eller läggas till. Kontrollera licensavtalet.

## Typologiregler och typologi {#typology-rules}

Campaign innehåller som standard inbyggda typologier och typologiregler.

En typologi är en uppsättning verifieringsregler som tillämpas på alla meddelanden under leveransanalysen.

En kampanjtypologi kan innehålla flera typologiregler, men en leverans kan bara referera till en typologi.

Inbyggda typologiregler och typologier finns i **[!UICONTROL Administration > Campaign management > Typology management]** nod i Campaign Explorer.

För varje typologi **[!UICONTROL Rules]** kan du lägga till, ta bort eller visa de typologiregler som ska användas.

![](assets/campaign_opt_rules_tab.png)

När de har skapats grupperas typologireglerna i kampanjen **typologier** som refereras i leveranser. [Läs mer](#apply-typologies).


Campaign innehåller en uppsättning standardinställningar **Filtrering** och **Kontroll** regler:

* **Filtrering** -regler används för att utesluta delar av målet baserat på kriterier. [Läs mer](filtering-rules.md).
* **Kontroll** gör att du kan kontrollera giltigheten för meddelanden innan de skickas. [Läs mer](control-rules.md).

Kampanjoptimeringstillägget innehåller ytterligare två typer av **typologiregler**:

* **Tryck** regler som gör att ni kan kontrollera reklamtrötthet. [Läs mer](pressure-rules.md).
* **Kapacitet** regler som gör att du kan begränsa lasterna för att garantera optimala bearbetningsförhållanden. [Läs mer](consistency-rules.md#controlling-capacity).


>[!NOTE]
>
>Om du använder **Interaktion** för att hantera erbjudanden kan man också skapa **Erbjudandepresentation** typologiregler för att styra flödet av erbjudandeförslag med hjälp av presentationsregler. [Läs mer](../../v8/interaction/interaction-offer.md#offer-presentation).


## Viktiga steg för att skapa och använda typografi {#apply-typologies}

Följ stegen nedan för att skapa och använda en typologi för dina leveranser:

1. Skapa typologiregler och skapa en typologi som refererar till dem i den.
Detaljerade steg visas i följande avsnitt:

   * [Filtreringsregler](filtering-rules.md)
   * [Kontrollregler](control-rules.md)
   * [Tryckregler](pressure-rules.md)
   * [Kapacitetsregler](consistency-rules.md)

1. Konfigurera leveransen för att använda den typologi du skapade. [Läs mer](apply-rules.md#apply-a-typology-to-a-delivery).
1. Testa och kontrollera beteendet med kampanjsimuleringar. [Läs mer](campaign-simulations.md).

Vid färdigställande av leveransen utesluts mottagarna när kriteriet är uppfyllt. Du kan kontrollera loggar för att övervaka uteslutningar.

Exempel på användningsområden för regler för trycktypologi finns i [den här sidan](pressure-rules.md#use-cases-on-pressure-rules).

## Självstudievideor {#typologies-video}

### Konfigurera trötthetshantering med hjälp av typologiregler

I den här videon förklaras hur du implementerar trötthetshantering i Adobe Campaign genom att utnyttja typologiregler.

>[!VIDEO](https://video.tv.adobe.com/v/333787?quality=12)

### Ställa in trötthetshantering med fördefinierade filter

Trötthetshanteringen styr frekvens och antal meddelanden för att undvika överbelastning av mottagaren. Om du inte har kampanjoptimeringsmodulen i din kampanjinstans kan du konfigurera ett fördefinierat filter som filtrerar målpopulationen efter antalet meddelanden som tas emot I den här videon förklaras hur du implementerar trötthetshantering i Adobe Campaign med hjälp av filter.

>[!VIDEO](https://video.tv.adobe.com/v/333778?quality=12)
