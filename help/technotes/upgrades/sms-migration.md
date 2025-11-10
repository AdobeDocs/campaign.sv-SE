---
title: Gå till den nya SMS-kopplingen v2
description: Lär dig hur du går över till den nya SMS-kopplingen v2
feature: Technote
role: Admin
hide: true
hidefromtoc: true
exl-id: 61a5a3e8-59f8-47ea-afc9-66ec243b8265
source-git-commit: 784c74aaff23dbf1f35c6e8153f90610048e1c07
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# Gå till den nya SMS-kopplingen v2

I det här dokumentet beskrivs proceduren och de viktigaste aspekterna när du migrerar från den MTA-baserade SMS-kopplingen till den nya **dedikerade SMS-processanslutningen** i Adobe Campaign v8.

## Varför ska jag byta till v2-kontakten?

I den dedikerade SMS-processen introduceras stöd för SMPP-sändningsläget, vilket minskar antalet anslutningar och förbättrar resurseffektiviteten, samtidigt som det fortfarande finns stöd för konfiguration av sändare/mottagare vid behov. Det ger betydligt större stabilitet, med snabbare återställning efter fel, beständiga anslutningar och utan beroende av lokala filer eller kommunikation mellan processer. Prestanda har också förbättrats med lägre latens, högre genomströmning och intelligent mikrobatchhantering för att balansera hastighet och tillförlitlighet. Dessutom förenklar isoleringen av SMS-processen felsökning och minimerar påverkan över flera kanaler. Dessa förbättringar gör den dedikerade kontakten till en mer robust och skalbar lösning för SMS-leverans.

## Skillnader i v1- och v2-anslutningar

Den dedikerade SMS-kopplingen i Adobe Campaign v8 introducerar flera arkitektoniska förändringar jämfört med den MTA-baserade anslutningen. En viktig skillnad är standardanvändningen av SMPP-sändningsläget, som minskar antalet anslutningar genom att kombinera funktionerna för att skicka och ta emot. Om providern inte stöder det här läget går det fortfarande att använda separata sändare- och mottagaranslutningar. Till skillnad från MTA-kopplingen har aktivering av automatiska svar ingen effekt på antalet anslutningar och alla mottagaranslutningar kan hantera alla typer av inkommande meddelanden.

Anslutningsantalet beräknas nu med en annan formel:

```
Total connections = SMS sending threads * Number of MTA child connections. 
```

Parametern sendingThreads, som definieras i serverConf, har standardvärdet 1 och bör i allmänhet förbli oförändrad om den inte särskilt optimeras för höga prestanda. Eftersom en enda process hanterar all SMS-trafik är det viktigt att hantera parallellismen genom de här parametrarna för att styra systeminläsning och -beteende.

Sändande fönster fungerar på ungefär samma sätt som MTA-anslutningen, men har ännu större inverkan på prestandan i det dedikerade läget. Större fönster minskar databasens IOPS och förbättrar dataflödet. Campaign kan effektivt hantera fönster med över 1 000 meddelanden, förutsatt att leverantören stöder detta och att användningsexemplet tillåter en liten marginal för meddelandeförlust eller dubbletter vid anslutningsproblem. På providersidan kan ett större fönster för SR-sändning också förbättra leveransrapportens genomströmning avsevärt.

MO-meddelandehantering (Mobile Originated) förblir funktionellt oförändrad, men den underliggande koden har uppdaterats. Dataflödet per anslutning är fortfarande begränsat på samma sätt, men den dedikerade anslutningen gör att det går mycket snabbare att skicka datafiler. Utan genomströmningsbegränsningar kan emellertid höghastighetssändningar överbelasta providern eller systemresurserna, vilket gör det tillrådligt att ange specifika genomströmningströsklar för MT i den externa kontokonfigurationen.

## Växlingsprocedur

För att säkerställa en smidig övergång till den dedikerade SMS-processen är det bäst att utföra åtgärden under låg eller ingen SMS-trafik. Vissa buffrade meddelanden kan gå förlorade eller lämnas i ett ogiltigt tillstånd om MTA-buffertar inte tömts helt. Det är också normalt att missa vissa SR i upp till en vecka efter bytet på grund av oförutsägbar SR-timing. Om du inte följer dessa försiktighetsåtgärder kan det leda till att meddelanden går förlorade eller dupliceras, trots inbyggda skyddsfunktioner.

Båda SMS-anslutningarna har olika format för SR-bearbetning (statusrapport). Även om båda förlitar sig på tabellen `NmsProviderMsgId`, interagerar de med den på ett annat sätt. Därför måste du rensa hela tabellen för att förhindra konflikter eller överblivna data genom att byta kopplingar. Det finns flera sätt att utföra den här rensningen. Nedan finns de SQL-frågor du kan använda:

```
TRUNCATE TABLE NmsProviderMsgId;
TRUNCATE TABLE NmsProviderMsgStatus;
```

### Steg

1. Granska inställningarna för `serverConf` (`sms > mta2`).
1. Pausa arbetsflödet för meddelandeförberedelse i realtid (om tillämpligt).
1. Pausa alla SMS-leveranser.
1. Inaktivera det externa SMS-kontot.
1. Stoppa och starta om MTA- och SMS-processerna.
1. Kontrollera att inga SMPP-anslutningar är aktiva. Kontrollera att alla leveranser är pausade, om sådana finns.
1. Radera innehållet i tabellerna `NmsProviderMsgId` och `NmsProviderMsgStatus` i databasen.
1. I det externa kontot:
   * Aktivera kryssrutan Dedikerad process
   * Justera andra inställningar: MTA-underordnade anslutningar, MT-dataflöde, fönstret Skicka
1. Aktivera det externa kontot igen och spara.
1. Återuppta SMS-leveranser.
1. Kontrollera att SMS-tjänster fungerar normalt.

>[!NOTE]
>
>Övervaka underordnade SMS-, MTA- och MTA-loggar för fel och problem.
>
>Spara tidigare externa kontoinställningar för återställningsändamål.

### Återställningsprocedur

Du kan återställa till MTA-anslutningen genom att följa samma steg som användes under den första växeln, i samma ordning. Detta inkluderar att stoppa eller pausa alla SMS-leveranser och återställa den ursprungliga externa kontokonfigurationen.

1. Om instansen använder leveranser i realtid pausar du det tekniska arbetsflöde som ansvarar för att förbereda meddelandena.
1. Pausa alla SMS-leveranser.
1. Inaktivera det externa SMS-kontot.
1. Stoppa och starta om både MTA- och SMS-processerna.
1. Se till att inga SMPP-anslutningar förblir aktiva. Om de gör det, kontrollera att alla leveranser är korrekt pausade.
1. Rensa tabellerna `NmsProviderMsgId` och `NmsProviderMsgStatus` i databasen.
1. I det externa kontot:
   * Avmarkera alternativet för dedikerad process i det externa kontot.
   * Återställ alla tidigare externa kontoinställningar: MTA-underordnade anslutningar, MT-dataflöde, fönstret Skickar
1. Återaktivera och spara det externa kontot.
1. Återuppta alla SMS-leveranser.
1. Bekräfta slutligen att SMS-tjänsterna fungerar som de ska.
