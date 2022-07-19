---
product: campaign
title: Erbjudandemotor
description: Erbjudandemotor
feature: Workflows, Interaction
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 4%

---

# Erbjudandemotor{#offer-engine}

The **[!UICONTROL Offer engine]** Med -aktivitet kan du definiera ett anrop till erbjudandemotorn före en leverans.

Denna aktivitet fungerar enligt samma princip som anrikningsaktiviteten med ett motoranrop genom att anrika den inkommande populationsinformationen med ett erbjudande som beräknas av motorn, före leverans.

![](assets/int_offerengine_activity2.png)

När du har konfigurerat frågan (se [section](query.md)):

1. Lägg till och öppna en **[!UICONTROL Offer engine]** aktivitet.
1. Fyll i de olika tillgängliga fälten för att ange anrop till motoriska parametrar (erbjudandeutrymme, kategori eller tema, kontaktdatum, antal erbjudanden som ska behållas). Motorn beräknar automatiskt erbjudandena som ska läggas till enligt dessa parametrar.

   >[!CAUTION]
   >
   >Om du använder den här aktiviteten lagras endast de offertförslag som används i leveransen.

   ![](assets/int_offerengine_activity1.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Se [Flerkanalsleveranser](cross-channel-deliveries.md).
