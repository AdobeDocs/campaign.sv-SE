---
title: Kända fel i Campaign v8
description: Kända fel i den senaste Campaign-versionen
feature: Overview
role: Data Engineer
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 099d14ace04df1b98e03be283a6436f49f535958
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Kända fel{#known-issues}

På den här sidan visas kända fel som identifierats i **senaste Campaign v8-utgåvan**. Dessutom listas begränsningar som följer med Campaign v8 [på den här sidan](known-limitations.md).


>[!NOTE]
>
>Adobe publicerar den här listan över kända problem efter eget gottfinnande. Det baseras på antalet kundrapporter, allvarlighetsgraden och möjligheten att komma runt problemet. Om ett problem som du stöter på inte visas kanske det inte uppfyller villkoren för publicering på den här sidan.

## Ändra aktivitetsproblem för datakälla {#issue-1}

### Beskrivning

The **Ändra datakälla** aktiviteten misslyckas när data överförs från Campaign-databasen till molndatabasen i Snowflake. När du byter riktning kan aktiviteten ge upphov till problem.

### Återgivningssteg

1. Anslut till klientkonsolen och skapa ett arbetsflöde.
1. Lägg till en **Fråga** aktivitet och **Ändra datakälla** aktivitet.
1. Definiera en fråga på **e-post**, som är en sträng.
1. Kör arbetsflödet och högerklicka på övergången för att visa populationen: e-postposterna visas ersatta med `****`.
1. Kontrollera arbetsflödesloggarna: den **Ändra datakälla** -aktiviteten tolkar dessa poster som numeriska värden.

### Tillfällig lösning

Om du vill att data ska överföras från molndatabasen i Snowflake till den lokala Campaign-databasen och tillbaka till Snowflake måste du använda två olika **Ändra datakälla** verksamhet.

### Intern referens

Referens: NEO-45549


## Det gick inte att överföra filen på servern med datainläsningsaktiviteten (fil) {#issue-2}

### Beskrivning

Filöverföringen på Campaign-servern avbryts med 100 % förlopp men upphör aldrig.

### Återgivningssteg

1. Anslut till klientkonsolen och skapa ett arbetsflöde.
1. Lägg till en **Inläsning av data (fil)** och konfigurera den.
1. Välj **Överför på servern** alternativ.
1. Välj filen på den lokala datorn,
1. Klicka **Överför**

### Tillfällig lösning

Ingen

### Intern referens

Referens: NEO-47269