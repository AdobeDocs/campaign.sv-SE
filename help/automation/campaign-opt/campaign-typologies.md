---
product: campaign
title: Kom igång med olika kampanjtyper
description: Lär dig konfigurera och implementera kampanjtyper
feature: Typology Rules
source-git-commit: 72467caf94e652ede70c00f1ea413012fc4c7e1f
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 18%

---

# Kom igång med olika kampanjtyper{#about-campaign-typologies}

Kampanjoptimering är Adobe Campaign-modulen som gör att ni kan styra, filtrera och övervaka leveransen. För att undvika konflikter mellan kampanjer kan Adobe Campaign testa olika kombinationer genom att tillämpa särskilda begränsningsregler. Detta garanterar att de skickade meddelandena uppfyller kundernas behov och förväntningar och företagets kommunikationspolicy.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#typologies-video)

>[!NOTE]
>
>Beroende på vilket erbjudande du erbjuder kan Campaign Optimization inkluderas eller läggas till. Kontrollera licensavtalet.

## Typologiregler och typologi {#typology-rules}

Med Adobe Campaign kan du designa och använda fyra typer av **typologiregler**:

* **Filtrering** regler som gör att du kan utesluta delar av målet baserat på kriterier. [Läs mer](filtering-rules.md).
* **Tryck** regler som gör att ni kan kontrollera reklamtrötthet. [Läs mer](pressure-rules.md).
* **Kapacitet** regler som gör att du kan begränsa lasterna för att garantera optimala bearbetningsförhållanden. [Läs mer](consistency-rules.md#controlling-capacity).
* **Kontroll** regler som gör att du kan kontrollera giltigheten för meddelanden innan de skickas. [Läs mer](control-rules.md).

När de har skapats grupperas typologireglerna i kampanjen **typologier** som refereras i leveranser. [Läs mer](#apply-typologies).

En kampanjtypologi kan innehålla flera typologiregler, men en leverans kan bara referera till en typologi.

Inbyggda typologiregler och typologier finns i **[!UICONTROL Administration > Campaign management > Typology management]** nod i Campaign Explorer.

För varje typologi **[!UICONTROL Rules]** kan du lägga till, ta bort eller visa de typologiregler som ska användas.

![](assets/campaign_opt_rules_tab.png)

## Viktiga steg för att tillämpa typografi {#apply-typologies}

De viktigaste stegen för att skapa och tillämpa en typologi på dina leveranser är följande:

1. Skapa typologiregler och skapa en typologi som refererar till dem i den.
Detaljerade steg visas i följande avsnitt:
   * [Tryckregler](pressure-rules.md)
   * [Filtreringsregler](filtering-rules.md)
   * [Kapacitetsregler](consistency-rules.md)
   * [Kontrollregler](control-rules.md)

1. Konfigurera leveransen för att använda den typologi du skapade. [Läs mer](apply-rules.md#apply-a-typology-to-a-delivery).
1. Testa och kontrollera beteendet med kampanjsimuleringar. [Läs mer](campaign-simulations.md).

Vid färdigställande av leveransen utesluts mottagarna när kriteriet är uppfyllt. Du kan kontrollera loggar för att övervaka uteslutningar.

Exempel på användningsområden för regler för trycktypologi finns i [den här sidan](pressure-rules.md#use-cases-on-pressure-rules).

## Självstudievideor {#typologies-video}

### Konfigurera trötthetshantering med hjälp av typologiregler

I den här videon förklaras hur du implementerar trötthetshantering i Adobe Campaign genom att utnyttja typologiregler.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Ställa in trötthetshantering med fördefinierade filter

Trötthetshanteringen styr frekvens och antal meddelanden för att undvika överbelastning av mottagaren. Om du inte har kampanjoptimeringsmodulen i din kampanjinstans kan du konfigurera ett fördefinierat filter som filtrerar målpopulationen efter antalet meddelanden som tas emot I den här videon förklaras hur du implementerar trötthetshantering i Adobe Campaign med hjälp av filter.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)


