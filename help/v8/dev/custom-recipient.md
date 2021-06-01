---
product: Adobe Campaign
title: Ändra standardmottagartabellen
description: Lär dig hur du använder en anpassad mottagartabell
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 0b71c76b-03d9-4023-84fc-3ecc0df9261b
source-git-commit: 5363950db5092bc7e0a72a0823db1132a17dda33
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 2%

---

# Använd en anpassad mottagartabell{#gs-ac-custom-recipient}

Adobe Campaign har en inbyggd profiltabell: **nmsRecipient**. Den här tabellen har ett antal fördefinierade fält och tabeller som enkelt kan utökas. Läs mer om den här tabellen i [den här sidan](datamodel.md#ootb-profiles).

Inbyggt tabelltillägg ger flexibilitet, men det går inte att ta bort vissa oanvända fält eller länkar. Därför kan det vara bra att använda en anpassad mottagartabell när datamodellen skiljer sig avsevärt från den inbyggda mottagartabellstrukturen i Campaign eller om du har ett stort antal profiler.  Den här metoden kräver dock vissa försiktighetsåtgärder när den implementeras.

Med den här funktionen kan Adobe Campaign bearbeta data från en extern databas: dessa data kommer att användas som en uppsättning profiler för leveranser. Implementeringen av den här processen inbegriper begränsningar, som:

* Ingen uppdateringsström till och från Campaign Cloud-databasen: data från den här tabellen kan uppdateras direkt via den databasmotor som är värd för den.
* Processer som körs på den befintliga databasen måste vara stabila.
* Använda en profildatabas med en icke-standardstruktur: möjlighet att leverera till profiler som sparats i olika tabeller med olika strukturer, med en enda instans.

I det här avsnittet beskrivs huvudpunkterna för att mappa befintliga tabeller i Adobe Campaign och konfigurationsinställningarna som ska användas för att köra leveranser baserat på valfri tabell. Det beskriver också hur man utformar frågegränssnitt för slutanvändare.

>[!CAUTION]
>
>Adobe Campaign-anpassning är förbehållet expertanvändare. Det kräver expertis inom indata- och schemadesign.

