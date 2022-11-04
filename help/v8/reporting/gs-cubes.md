---
title: Kom igång med Adobe Campaign analysrapporter
description: Lär dig hur du skapar kuber
feature: Reporting
role: Data Engineer
level: Beginner
source-git-commit: bead34ec59f6f3dca0fbec8460d58ec7da2ed76f
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 13%

---

# Kom igång med rapporter om kampanjanalyser {#gs-cube}

Adobe Campaign har ett intuitivt dataundersökningsverktyg för att skapa dynamiska rapporter.

Använd funktioner för marknadsanalys för att analysera och mäta data, beräkna statistik, förenkla och optimera framtagning och beräkning av rapporter. Du kan skapa rapporter och skapa målpopulationer och lagra dem i listor som kan användas i Adobe Campaign för målinriktning eller segmentering.

Du kan utöka databasens undersöknings- och analyskapacitet samtidigt som det blir enklare för slutanvändarna att konfigurera rapporter och tabeller. Allt de behöver göra är att välja en befintlig (helt konfigurerad) kub när de skapar sin rapport eller tabell för att bearbeta beräkningar, mått och statistik.

Kuber används för att generera vissa inbyggda rapporter, inklusive [leveransrapporter](delivery-reports.md) (leveransspårning, klickningar, öppningar osv.).

När de har skapats och konfigurerats används kuber i frågeformulär för rapportering och webbapplikationer. De kan användas och ändras i pivottabeller.

Använd modulen Campaign Marketing Analytics för att:

1. Skapa kuber och indikatorer

   * sammanställa och lagra data i en arbetstabell för att på förhand beräkna indikatorer baserat på användarnas behov,
   * minska datavolymen i de olika beräkningar som används för rapporter och frågor, vilket avsevärt optimerar beräkningstiderna för indikatorn,
   * förenkla tillgången till data, göra det möjligt för användarna att hantera data (oavsett om de är i förväg aggregerade eller inte) beroende på olika dimensioner.

   Mer information finns i [Skapa indikatorer](cube-indicators.md).

1. Skapa pivottabeller och utforska data

   * utforska beräknade data, konfigurerade mått,
   * välja vilka data som ska visas samt dess visningsläge,
   * personalisera de åtgärder och indikatorer som används,
   * erbjuder interaktiva analysverktyg till användare med icke-teknisk bakgrund.

   Mer information finns i [Använd kuber för att utforska data](cube-tables.md).

1. Bygg en fråga med data som beräknas och aggregeras i en kub.
1. Identifiera populationer och referera till dem i listor.

## Terminologi {#terminology}

Specifika termer när du arbetar med kuber visas nedan.

* **Kub** - En kub är en representation av flerdimensionell information: ger slutanvändarna strukturer som utformats för interaktiv dataanalys.

* **Faktatabell/schema** - Faktatabellen (eller faktchemat) innehåller rådata eller elementära data som analyserna ska baseras på. Dessa är huvudsakligen stora volymtabeller (möjligen med länkade tabeller) med potentiellt långa beräkningar. En faktatabell kan till exempel vara: sändningstabellen, inköpstabellen osv.

* **Dimension** - Med Dimensioner kan du gruppera data i grupper: När de har skapats fungerar dimensionerna som analysaxlar. I de flesta fall definieras flera nivåer för en viss dimension. För en tidsdimension är nivåerna till exempel månader, dagar, timmar, minuter och så vidare. Den här nivåuppsättningen representerar dimensionshierarkin och möjliggör olika nivåer av dataanalys.

* **Bindning** - För vissa fält kan du definiera bindning till gruppvärden och göra det enklare att läsa information. Bindning används på nivåer. Vi rekommenderar att du definierar bindning när det kan finnas många olika värden.

* **Mät** - De vanligaste måtten är summa, genomsnitt, maximum, minimum, standardavvikelse osv. Mått kan beräknas: Antagandegraden för ett erbjudande är förhållandet mellan antalet gånger det presenterades och antalet gånger det accepterades.
