---
title: Verifierar en SMPP-anslutning
description: Lär dig hur du validerar en SMPP-anslutning
feature: SMS
role: User
level: Intermediate
exl-id: eda6934a-e48a-4932-8c88-588f661005d6
source-git-commit: 6f29a7f157c167cae6d304f5d972e2e958a56ec8
workflow-type: tm+mt
source-wordcount: '4437'
ht-degree: 0%

---

# Verifierar en SMPP-anslutning {#validate-smpp-connection}

Här är några kontroller för att se till att din SMPP-anslutning är OK.

## Saker att kontrollera innan du publicerar {#check-go-live}

Innan du publicerar måste du kontrollera att SMPP-konfigurationen är OK med listan över kontroller nedan.

>[!IMPORTANT]
>
>Denna checklista är inte fullständig. Ju fler kontroller du gör, desto bättre.

>[!NOTE]
>
>Aktivera utförliga SMPP-spårningar under kontroller, så att du och supportteamet kan förstå felen.

### Kontrollera om det finns externa kontokonflikter {#sms-external-accounts-check}

Kontrollera att du inte har kvar externa SMS-konton. Ta bort testkontona för att eliminera potentiella konflikter.

Kontrollera att ingen annan instans ansluter till det externa kontot. Se särskilt till att förproduktionsmiljön inte ansluter till det externa produktkontot.

Om du behöver ha flera konton på samma Campaign-instans som ansluter till samma leverantör, kontaktar du leverantören för att se till att de verkligen särskiljer anslutningar mellan dessa konton. Om du har flera konton med samma inloggning krävs extra konfiguration.

Kontrollera att den dedikerade processinställningen är aktiverad för alla aktiverade SMS-externa konton. Du kan inte blanda mellan de två olika kontotyperna (med och utan dedikerad process) i samma instans.

### Gör ett test i verkligheten {#real-test}

Försök skicka SMS på olika mobiler.

**Skicka SMS med alla typer av tecken**

Om du behöver skicka SMS med tecken som inte är GSM eller ASCII kan du försöka skicka meddelanden med så många tecken som möjligt. Om du ställer in en anpassad teckenmappningstabell skickar du minst ett SMS för alla möjliga data_coding-värden.

**Kontrollera att SR har bearbetats korrekt**

SMS ska markeras som mottaget i leveransloggen. Leveransloggen bör slutföras och se ut så här: *SR yourProvider stat=DELIVRD err=000|#MESSAGE#*.

Kontrollera att du har angett fältet *SMSC-implementeringsnamn* korrekt: leveransloggen får aldrig innehålla *SR Generic* i produktionsmiljöer.

**Kontrollera att flerlägesobjekt bearbetas**

Skicka några SMS för alla automatiska svarsnyckelord och kontrollera att svaret är snabbt (bara några sekunder).

Kontrollera att flerlägesobjekt infogas i databasen *nms:inSms*. Om du har anpassade TLV:er måste du se till att de också infogas korrekt och korrekt formaterade.

Kontrollera i loggen att Campaign svarar med en lyckad *DELIVER_SM_RESP (command_status=0)*.

**Gör ett inläsningstest**

Detta är särskilt viktigt om du skickar många meddelanden eller om du använder meddelanden i realtid.

Gör ett test som läser in anslutningen med 100 % i minst 5 sekunder. Du måste skicka riktiga meddelanden om leverantören inte kan ansluta till ett falskt konto för tester. Ett sätt att uppnå detta är att noggrant övervaka den första stora nog stora leveransen med utförliga SMPP-meddelanden aktiverade.

Det minsta antalet meddelanden som ska skickas kan beräknas så här:

*Maximal MT-genomströmning * Totalt antal anslutningar för sändare/mottagare * 5*

Kontrollera följande när leveransen är klar:

* Kontrollera att alla meddelanden skickades (inte nödvändigtvis mottagna)
* Det måste finnas en absolut noll-PDU med command_status som inte är 0x000000, såvida inte detta uttryckligen anges av providern som normal åtgärd
* Anslutningarna måste vara helt stabila (ingen BIND PDU) under hela leveransprocessen.
* Kontrollera att alla meddelanden har en SR och att den har bearbetats korrekt (se [Kontrollera att SR har bearbetats korrekt](#real-test)). Om en liten procentandel innehåller fel kontrollerar du att dessa var faktiska fel som returnerades av SR, inte fel under sändning eller bearbetning på Campaign-sidan.
* Om du är osäker på prestanda bör du kontrollera att fördröjning är rimlig, särskilt mellan en PDU och motsvarande RESP, eftersom en fördröjning på mer än 500 ms kan vara ett problem för hög genomströmning. Använd den fördröjningen för att kontrollera avsändande fönsterformel (mer information finns i inställningen för fönstret Skicka)

### Kontrollera PDU:er {#pdu}

Kontrollera att PDU:er är korrekt formaterade.

>[!IMPORTANT]
>
>Det här steget rekommenderas starkt vid anslutning till en leverantör som inte var ansluten till Campaign tidigare.

**BIND**

Kontrollera att PDU:er för BIND_* skickas korrekt. Det viktigaste att kontrollera är att providern alltid returnerar lyckade BIND_*_RESP PDU:er (command_status = 0).

Kontrollera att det inte finns för många BIND_* PDU:er. Om det finns för många av dem kan det tyda på att anslutningen är instabil. Se felsökningsavsnittet Problem med instabila anslutningar nedan för mer information om detta.

**INQUIRE_LINK**

Kontrollera att PDU:er för INQUIRE_LINK regelbundet utbyts när anslutningen är inaktiv.

**SUBMIT_SM/DELIVER_SM**

Skicka ett meddelande och sök sedan i loggarna efter tillhörande PDU:er SUBMIT_SM, SUBMIT_SM_RESP, DELIVER_SM och DELIVER_SM_RESP.

Med *SUBMIT_SM PDU*:

* Kontrollera att data_coding är korrekt (0 som standard).
* Kontrollera att short_message är rätt kodat: försök att avkoda det med en hexadecimal konverterare som stöder flera kodningar (det finns några tillgängliga online).
* Om du använder message_payload för långa meddelanden kontrollerar du att innehållet finns i det valfria fältet och inte i fältet short_message.

Med *SUBMIT_SM_RESP PDU*:

* Kontrollera att den lyckades (command_status = 0).
* Kontrollera att brödtexten innehåller ett korrekt formaterat ID följt av byte &#39;0&#39;.

Med *DELIVER_SM PDU*:

* Avkoda det hexadecimala fältet short_message (det finns onlineverktyg för det).
* Kontrollera med ett regex-kontrollverktyg att det regex som definieras i Extraheringsregex för ID:t i SR returnerar exakt en hämtningsgrupp och att hela ID:t hämtas i meddelandet.
* Kontrollera att det extraherade ID:t matchar det i SUBMIT_SM_RESP.
* Kontrollera att regex som är definierat i Extraheringsregex för statusen i SR returnerar innehållet i fältet stat.
* Kontrollera att regex som är definierad i Extraheringsregex för felet i SR returnerar felfältets innehåll.

Med *DELIVER_SM_RESP PDU*:

* Kontrollera att det skickades snabbt efter att du fått PDU:n DELIVER_SM (vanligtvis mindre än 1 sekund).
* Kontrollera att den lyckades (command_status = 0).

### Live-test med leverantören {#sms-live-test}

Ett bra tillvägagångssätt innan du publicerar är att göra ett direkttest med leverantören, där båda sidorna tittar på loggarna under körningen.

>[!IMPORTANT]
>
>Det här steget rekommenderas starkt när du ansluter till en leverantör som aldrig tidigare har varit ansluten till Campaign.

### Inaktivera utförliga SMPP-spår {#sms-disable-smpp}

När alla kontroller är klara är den sista åtgärden att inaktivera utförliga SMPP-spår så att inte alltför många loggar genereras.

## Felsökning av SMS {#sms-troubleshooting}

### Allmän felsökningsprocedur {#sms-general-troubleshooting}

SMS-kopplingen har tre enheter: SMPP-leverantören, Adobe och du.
Den största SMS-experten är SMPP-leverantören, så de bör vara involverade i alla SMS-trafikrelaterade problem (anslutningsproblem, förlorade meddelanden, kodningsproblem, landsspecifika regler, ...).

#### Aktivera dedikerad process {#sms-dedicated-process}

>[!IMPORTANT]
>
>Kontrollera att **[!UICONTROL Send messages through a dedicated process]** är aktiverat i alla aktiva SMS-konton.

Om du har problem med den äldre (MTA-baserad) anslutningen (dedikerad process inaktiverad) bör du överväga att migrera till den dedikerade processkopplingen. Den fungerar mycket bättre, är stabilare och ger mycket bättre återkoppling i sina loggar.

#### Konflikt mellan olika externa konton {#sms-conflict-external-accounts}

Om instansen har flera externa SMS-konton kontrollerar du att problem inte orsakas av en konflikt mellan konton.

Så här isolerar du det externa konto som orsakar problem:

1. Inaktivera alla externa konton
1. Aktivera ett externt konto
1. Försök återskapa problemet
1. Om problemet inte uppstår med det kontot inaktiverar du det och startar om till steg 2 på nästa konto. När du har markerat varje konto separat finns det två möjliga scenarier:

**Problemet uppstod på ett eller flera konton**

I så fall kan du tillämpa andra felsökningsprocedurer på varje konto separat. Det är bäst att inaktivera andra konton när du diagnostiserar ett konto, för att minska nätverkstrafiken och antalet loggar.

**Problemet uppstod inte när endast ett konto är aktivt vid något tillfälle**

Du har en konflikt mellan konton. Adobe Campaign hanterar konton individuellt, men leverantören kan behandla dem som ett enda konto.

*Du använder olika kombinationer av inloggning/lösenord för alla dina konton*
Du måste kontakta leverantören för att diagnostisera eventuella konflikter hos dem.

*Vissa av de externa kontona har samma kombination av inloggning/lösenord*
Leverantören kan inte avgöra från vilket externt konto BIND PDU:n kommer, så de behandlar alla anslutningar från flera konton som ett enda, så de dirigerar antagligen MO och SR slumpmässigt över de två kontona, vilket ger synbarligen slumpmässiga problem.

Om providern stöder flera korta koder för samma kombination av inloggning/lösenord måste du fråga var den korta koden ska placeras i BIND PDU:n. Observera att den här informationen måste placeras inuti BIND PDU:n, och inte i SUBMIT_SM, eftersom BIND PDU:n är den enda plats där MO:er kan routas korrekt.

Se avsnittet [Information i varje typ av PDU](#pdu) ovan för att veta vilka fält som är tillgängliga i BIND PDU, vanligtvis placerar du den korta koden i *address_range*, men det kräver särskild support från providern. Kontakta dem för att få veta hur de förväntar sig att skicka flera korta koder oberoende av varandra.

Adobe Campaign har stöd för att hantera flera korta koder på samma externa konto, så ofta fungerar bara ett enda konto för all trafik.

#### Ett externt konto slutade fungera {#sms-external-account-not-working}

I allmänhet är SMPP-anslutningar mycket stabila över tid, och när de har konfigurerats korrekt bör de fortsätta att fungera.

* Undersök om kopplingen nyligen har ändrats - och av vem (markera Externa konton som en grupp).
* Undersök om systemet uppgraderades och när.
* Undersök om några paket som påverkar SMS kan ha uppgraderats nyligen.

Om ingen av dessa kontroller leder till någon rotorsak kontaktar du providern. När leverantörer uppdaterar sina plattformar fungerar ibland deras koppling något annorlunda. Detta kan bryta justerade inställningar och ge upphov till regressioner.

Vi rekommenderar att du håller kontakten med leverantören. De kommunicerar ofta viktiga förändringar i förväg.

#### Problem med hosting (hosted)  {#sms-issue-hosted}

* Om problemet inträffar i en miljö med medelhög källkod måste du se till att leverans- och sändningsversionerna skapas och uppdateras på servern med mellanlagring. Om så inte är fallet är problemet inte ett SMS-problem.
* Kontrollera att mellanoperatörens namn är strikt i gemener, annars kommer leveransen att ha statusen Väntande.
* Om allt fungerar på mittservern och SMS-meddelanden skickas korrekt, men marknadsföringsinstansen inte uppdateras korrekt, har du ett problem med mellansynkronisering.

#### Problem vid anslutning till providern {#sms-issue-connection}

* Om BIND PDU returnerar en *command_status*-kod som inte är noll (vilket innebär att det finns ett fel), eller om det inte finns någon BIND_RESP PDU, frågar du providern varför detta händer.
* Kontrollera att nätverket är korrekt konfigurerat så att TCP-anslutningen kan göras till providern.
* Be leverantören kontrollera att de tillåter IP-adresser för Adobe Campaign-instansen (de flesta leverantörer kräver det).
* Kontrollera externa kontoinställningar. Fråga leverantören om du är osäker på värdet i vissa fält.
* Om anslutningen lyckas men inte fungerar kontrollerar du [utgåvorna med instabila anslutningar](#unstable-connections). nedan.
* Om det är svårt att diagnostisera anslutningsproblem kan du få mycket information genom att hämta in ett nätverk. Kontrollera att nätverksinhämtningen körs samtidigt när problemet visas så att det kan analyseras effektivt. Du bör också tänka på exakt när problemet uppstår så att det blir enklare att hitta problemet i nätverksinhämtningar.

#### Problem med instabila anslutningar {#unstable-connections}

**Diagnostisera instabila anslutningar:**

En anslutning anses vara instabil om något av följande inträffar:

* Anslutningen varar i mindre än 1 timme.
* Om du startar om SMS-processen kommer du att&quot;åtgärda&quot; saker tillfälligt. Det betyder antagligen att en instabil anslutning utlöser strypning, att SMS-processen startas om rensas och sedan inträffar den igen tills rotorsaken hittas.
* Providern skickar UNBIND PDU:er. Providern bör aldrig skicka UNBIND PDU:er i normal drift.
* *Query_link* timeout, antingen på Campaign-sidan eller på providersidan. Du kan se INQUIRE_LINK_RESP med en felkod som inte är noll i så fall.
* Det finns många BIND-PDU:er. Det får inte finnas mer än ett fåtal under en dag (det beror på antalet anslutningar). Mer än 1 BIND PDU per timme och per anslutning ska vara varningar.

**Så här åtgärdar du problem med anslutningsstabilitet:**

* Instabila anslutningar är sällan grundorsaken, det beror ofta på ett annat problem som utlöser en frånkoppling på ett eller annat sätt. Att hitta rotorsaken är prioriteten.
* Aktivera utförliga SMPP-spår. De måste se vad som händer när anslutningen startas om.
* Om providern skickar UNBIND PDU:er gör de antagligen något fel. Fråga dem varför de skickar UNBIND och det kommer antagligen att leda till grundorsaken.
* Ibland är det enda sättet att se hur anslutningen stängs att ta en nätverksinhämtning.
* Om providern stänger anslutningarna (genom att skicka antingen en TCP FIN eller ett TCP RST-paket) frågar du dem varför de gör det. Detta bör tala om orsaken till problemet.
* Om providern stänger anslutningen efter att ha skickat ett rent fel (till exempel DELIVER_SM_RESP med en felkod) måste de åtgärda sin koppling eftersom detta förhindrar att andra typer av meddelanden överförs och utlöser MTA-begränsning. Detta är särskilt viktigt i sändningsläge där stängning av anslutningen påverkar både MT och SR.
* Om det finns timeout (BIND-timeout, SUBMIT_SM-timeout) kan Campaign skicka meddelanden för snabbt för den leverantören. Försök att sänka inställningen *max MT-genomströmning* och se om den löser problemet.

#### Problem vid sändning av MT (vanlig SMS skickad till en slutanvändare)

* Kontrollera att anslutningen är stabil: en SMPP-anslutning ska vara upp minst en timme kontinuerligt. Se avsnittet Problem med instabila anslutningar ovan.
* Om du startar om SMS-processen och skickar MT-meddelanden igen under en liten tidsperiod, har du antagligen problem med detta på grund av en instabil anslutning. Se avsnittet Problem med instabila anslutningar ovan.
* Kontrollera att den breda loggen finns och att den har rätt status med rätt datum. Om det inte är det är det inte ett SMS-problem utan ett leveransproblem eller ett leveransförberedelseproblem (som ligger utanför dokumentets räckvidd).
* Kontrollera att SMS-anslutningen är bunden till providerns utrustning. Be leverantören om feedback för att säkerställa att alla system kommunicerar på rätt sätt. Se BIND_TRANSMITTER och BIND_TRANSCEIVER-PDU:er för mer information om bindningsprocessen. Du kan behöva aktivera SMPP-spår för korrekt felsökning.
* När SMPP-spårningarna är aktiverade kontrollerar du att PDU:n SUBMIT_SM innehåller rätt information (se dokumentationen ovan).
* Kontrollera att providern svarar med en SUBMIT_SM_RESP PDU med värdet OK (kod 0). Se till att PDU:n kommer med en rimlig fördröjning: allt som är längre än en sekund är misstänkt och måste diskuteras med leverantören. Det kommer vanligtvis om mindre än 100 ms.
* Om alla dessa steg fungerar kan du vara säker på att problemet ligger hos leverantören. De måste felsöka på sin plattform.
* Om det fungerar men flödet inte är konsekvent kan du försöka justera sändande fönster och sänka MT-flödet. Du måste arbeta med leverantören för att justera det. Campaign kan skicka meddelanden mycket snabbt så att det kan uppstå prestandaproblem på leverantörens utrustning.

#### MT dupliceras (samma SMS skickas flera gånger i rad)

Dubbletter orsakas ofta av återförsök. Det är normalt att ha dubbletter när du försöker skicka meddelanden igen, så du bör koncentrera dig på att eliminera grundorsaken till nya försök.

* Om dubbletter skickas med exakt 60 sekunders mellanrum (eller någon annan misstänkt &quot;vanlig&quot; period) är det antagligen ett problem på leverantörssidan, de skickar inte en SUBMIT_SM_RESP tillräckligt snabbt.
* Om du ser många BIND/UNBIND har du en instabil anslutning: se avsnittet [Problem med instabila anslutningar](#unstable-connections) för att hitta lösningar innan du försöker lösa problem med dubbla meddelanden.
* Kontrollera att alla PDU:er för SUBMIT_SM har matchande SUBMIT_SM_RESP kort därefter. Om de inte gör det eller om SUBMIT_SM_RESP är för långsamma är problemet på leverantörssidan.

Minska mängden dubbletter när ett nytt försök görs:

* Sänk ned det *sändande fönstret*. Sändande fönster ska vara tillräckligt stort för att täcka tiden för SUBMIT_SM_RESP, men inte för stort. Dess värde representerar det maximala antalet meddelanden som kan dupliceras om ett fel inträffar när fönstret är fullt.

#### Utfärda vid behandling av SR (leveranskvitton)

* SMPP-spår måste vara aktiverade för att du ska kunna utföra någon typ av SR-felsökning.
* Kontrollera att PDU:n DELIVER_SM kommer från providern och att den är korrekt formaterad.
* Kontrollera att Campaign svarar med en lyckad PDU för DELIVER_SM_RESP i rätt tid. Detta garanterar att SR har infogats i tabellen providerMsgStatus för fördröjd bearbetning i SMS-processen.

Om PDU:n DELIVER_SM inte godkänns måste du kontrollera några saker:

* Kontrollera region som är relaterad till id-extrahering och felbearbetning i det externa kontot. Du kan behöva validera dem mot innehållet i PDU:n DELIVER_SM.
* Kontrollera att fel har etablerats korrekt i tabellen bredaLogMsg (kampanjdokumentationen förklarar detta i detalj).

Om PDU:n DELIVER_SM har bekräftats av ACC-utökad SMPP-anslutning men bredaLog inte uppdateras korrekt, kontrollerar du ID-avstämningsprocessen som beskrivs i avsnittet Matchande MT-, SR- och utsändningsposter ovan.

Om du har korrigerat allt men vissa ogiltiga SR fortfarande finns i providerns buffertar kan du hoppa över dem genom att använda alternativet&quot;Ogiltigt antal ID-bekräftelser&quot;. Detta ska användas med försiktighet och återställas till 0 så fort som möjligt efter att buffertarna har tömts.

Om SR-bearbetningen är långsam kan du testa att kvalificera de vanligaste statusmeddelandena i registret BroadLogMsg.

Om endast vissa SR-meddelanden tas emot, men inte alla, kontrollerar du att inga andra system är anslutna till din leverantörs konto, till exempel ett testsystem. SR kan dirigeras på alla anslutningar, så vissa av dem kan dirigeras till det andra systemet. Leverantören kan hjälpa dig att hitta var det andra systemet som är anslutet till kontot finns.

#### Problem vid bearbetning av MO (och karantän/autosvar)

* Aktivera SMPP-spår under tester. Om du inte aktiverar TLS är det alltid bättre att göra en nätverksinhämtning när du felsöker MO för att kontrollera att PDU:er innehåller rätt information och är korrekt formaterade.
* När du hämtar nätverkstrafik eller analyserar SMPP-spår ska du se till att du fångar in hela konversationen med MO och dess MT-svar (om ett svar har konfigurerats).
* Om flerlägesobjektet (DELIVER_SM PDU) inte visas i spårningarna kan du vara säker på att problemet ligger hos leverantören. De måste felsöka på sin plattform.
* Om PDU:n DELIVER_SM visas kontrollerar du att den har bekräftats av Campaign med en lyckad PDU-fil för DELIVER_SM_RESP (kod 0). Denna RESP garanterar att all bearbetningslogik har tillämpats av Campaign (autosvar och karantän). Om så inte är fallet söker du efter ett felmeddelande i SMS-processloggarna.
* Om automatiska svar är aktiverade kontrollerar du att SUBMIT_SM har skickats till providern. Annars kommer det garanterat att hitta ett felmeddelande i SMS-processloggarna.
* Om PDU:n SUBMIT_SM MT som innehåller svaret finns i spårningarna men SMS:et inte kommer till mobiltelefonen, måste du kontakta leverantören för hjälp med felsökning eftersom problemet troligen finns på deras sida.

#### Problem vid färdigställande av leveransen, med undantag för mottagare i karantän (i karantän enligt funktionen för autosvar)

* Kontrollera att telefonnummerformatet är exakt detsamma i karantäntabellen och i leveransloggen. Om så inte är fallet, se inställningen &quot;Skicka fullständigt telefonnummer&quot; ovan om du har problem med plustecknet i det internationella telefonnummerformatet.
* Kontrollera korta koder: Undantag inträffar om den korta koden för mottagaren är densamma som den som har definierats i det externa kontot eller om den är tom (tom = valfri kortkod). Om bara en kort kod används för hela Campaign-instansen är det enklare att lämna alla&quot;korta kodsfält&quot; tomma.

#### Kodningsproblem  {#sms-encoding-issues}

Kodningsproblem uppstår ofta i SMS. Här är några grundläggande steg.

**Steg 1: Kontakta leverantören**

Leverantören är den expert som vet hur SMS fungerar. Kontakta dem och ta reda på vad som är fel. De bör kunna tala om för er om problemet ligger på deras sida eller i Campaign. Om problemet är i Campaign bör de kunna tala om för er exakt vilket fält som är felaktigt, vilket är till stor hjälp.

**Steg 2: Ta reda på vad som finns i meddelandet**

Du måste veta vad meddelandet innehåller. Den meningen låter kanske lätt, men det är den inte. Unicode tillåter så många varianter för likartade tecken att Campaign inte kan hantera alla.

Den vanligaste källan till problem är att kopiera och klistra in från en ordbehandlare, som ändrar vanliga tecken till typografiskt korrekta versioner: blanksteg har ändrats till fasta blanksteg, dubbla citattecken har ändrats till inledande och avslutande citattecken, minustecken har ändrats till olika typer av bindestreck ..

Kopiera inte och klistra in meddelandet när du testar. Skriv det alltid direkt i gränssnittet.

**Bli inte skrämd med hexadecimal**. Hexadecimal ser konstig och onaturlig ut, men har en mycket tydlig kvalitet: du kan se skillnaden mellan liknande tecken. En gemener L, en versal I, O, 0, alla olika typer av citattecken, icke-latinska kodningar eller till och med olika typer av blanksteg kan alla se likadana ut (eller visas inte alls). Hexadecimal visar allt och hjälper till att jämföra saker.

Om du vill konvertera Unicode till hexadecimal kan du använda onlineverktyg.

**När du öppnar biljetter** om kodningsproblem, oavsett om det gäller leverantören eller Campaign-stödet, **innehåller** en hexadecimal version av det du skriver och det du ser.

**Steg 3: Se vad du bör skicka**

Bestäm vilken kodning du förväntar dig ska användas och sök online efter teckentabellen. Kontrollera att de tecken du vill skicka är tillgängliga på målkodsidan. Kontrollera att fältet data_coding är korrekt och stämmer överens med vad du och providern förväntar dig.

**Steg 4: Ta reda på vad du faktiskt skickade**

Du behöver felsökningsutdata för anslutningen för att se exakt vilka byte du skickar till providern. Kodningsproblem visas i PDU:er av typen SUBMIT_SM, så se till att hämta dem. Skicka distinkta meddelanden som är enkla att hitta i loggen.

Tveka inte att skicka olika typer av specialtecken när du testar. GSM7-kodningen har till exempel utökade tecken som är mycket tydliga i hexadecimal form, så de är enkla att hitta eftersom de inte visas i någon annan kodning.

#### Prestandaproblem {#sms-performance-issues}

>[!NOTE]
>
>Prestanda är ett mycket brett ämne. I det här avsnittet finns några grundläggande kontroller att utföra innan du försöker skala eller göra andra stora projekt.

**Prestandaproblem när MT skickas**

* Kontrollera att alla inställningar i avsnittet Genomströmning och fördröjningar för det externa kontot är korrekta och att de matchar inställningarna som tillåts av providern.
* Kontrollera att det inte finns några återförsök.
* Kontrollera att leverantörens infrastruktur inte är mättad. Kontrollera om det finns RMSGQFUL- eller RTHROTTLED-fel i RESP-PDU:er.
* Kontrollera inställningarna för serverConf. Börja med standardvärden och öka parametrarna långsamt och en i taget.
* Kontrollera att SMS-processen inte startar om hela tiden när den läses in. Om den gör det kan du behöva öka *maxSMSMemoryMb*, *maxProcessMemoryAlertMb* och *maxProcessMemoryWarningMb* i filen serverConf.

**Prestandaproblem när SR** tas emot

Om providern klagar på buffertöverlagring på sin sida kan det bero på att kampanjen inte får SR tillräckligt snabbt.

* Kontrollera att instansdatabasen inte är överlastad. SR-bearbetningen är mycket beroende av databasprestanda.
* Be leverantören att öka sändningsfönstret för DELIVER_SM på sin sida. Helst ska den vara lika stor som inställningen *batchUpdateSize* i serverConf.

### Element som ska inkluderas vid kommunikation om ett SMS-problem

När du söker hjälp om ett SMS-problem (oavsett om det gäller att öppna en supportanmälan till Adobe Campaign, SMS-leverantören eller någon form av kommunikation om problemet) måste du inkludera minst följande information för att vara säker på att den är korrekt kvalificerad. Rätt kvalificerade frågor är avgörande för att lösa problem snabbare, så om man tar lite mer tid för att försöka förstå situationen och ge meningsfull information kommer det att leda till ett jättekliv i effektivitet.

* Aktivera utförliga SMPP-meddelanden när problemet uppstår. De flesta SMS-problem är praktiskt taget omöjliga att lösa utan detta.
* Om problemet är relaterat till SMS-trafik ska du kontakta leverantören först. De är de mest kunniga och deras plattform är vanligtvis lämplig för effektiv diagnos av SMS-trafikproblem i realtid.
* Ta med en kort men faktisk beskrivning av problemet.
* Ta med en beskrivning av det förväntade resultatet.
* Inkludera all feedback från leverantören.
* Inkludera relevanta loggar och/eller nätverksinhämtningar. Se till att du återskapar problemet under hämtningen när du gör hämtningar, annars blir det oanvändbart.
* Om du inkluderar loggar, kalkeringar eller hämtningar anger du exakt plats i filen när problemet uppstår, samt exakt plats för ett arbetsexempel om det finns något. Klipp eller spår kan vara stora och tröttande att titta på, så allt som hjälper dig att hitta information i dem är användbart.
* Om du refererar till meddelanden, PDU:er eller loggar måste du tydligt ange deras tidsstämpel så att de är lätta att hitta för andra.
* Försök återskapa problemet i en testmiljö. Om du är osäker på en inställning kan du testa den i testmiljön och kontrollera resultatet med SMPP-spår. Det är oftast bättre att rapportera problem som replikeras i testmiljöer än att rapportera direkt i produktionsmiljöer.
* Inkludera alla ändringar eller förbättringar som görs på plattformen: även en liten förändring kan få stor effekt. Ta även med eventuella ändringar som leverantören kan ha gjort på sin sida.

#### När är en nätverksinsamling användbar?

Nätverksinsamling behövs inte alltid. Mycket ofta räcker det med utförliga SMPP-meddelanden. Här följer några riktlinjer som hjälper dig att avgöra om en nätverksinhämtning är värd besväret:

* Anslutningsproblem, men de detaljerade meddelandena visar inga BIND_RESP PDU:er.
* Oförklarliga frånkopplingar utan felmeddelande (d.v.s. anslutningsprogrammets beteende när ett protokollfel på låg nivå identifieras).
* Providern klagar över avbindnings-/frånkopplingsprocessen.
* Det finns kodningsproblem i valfria TLV-fält.
* Trafiken misstänks vara blandad mellan olika anslutningar.

I alla andra situationer kan du försöka analysera detaljerade SMPP-meddelanden först och begära en nätverksregistrering endast om det är tydligt att information saknas i de detaljerade loggarna.

#### När är en nätverksinspelning värdelös?

I vissa fall är hämtning av nätverkstrafik värdelös eller bara slöseri med tid. Här är de vanligaste situationerna:

* TLS aktiverat: TLS-trafik krypteras per definition så den kan inte fångas in.
* Prestandaproblem: Loggar innehåller all information som behövs för att spåra prestandaproblem.
* Timingproblem (återförsökstidsinställning, frågelänk period, flödeskappning, ...)
* SR-parsning och -bearbetning: utförliga loggar ger mycket mer kontext och en bättre presentation.
* MO-behandling (automatiska svar, karantän).
* Fel som inte involverar faktisk SMPP-trafik: Förberedelse av leverans, API-problem för meddelandecenter, arbetsflödesproblem, ...
