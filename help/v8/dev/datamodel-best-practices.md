---
solution: Campaign v8
product: Adobe Campaign
title: Bästa praxis för datamodell
description: Lär dig mer om de bästa sätten att använda Campaign-datamodelltillägg
source-git-commit: 583a8f6a03b00e1eafa6d408c9949e60a6f8158d
workflow-type: tm+mt
source-wordcount: '2681'
ht-degree: 4%

---

# Bästa praxis för datamodell{#data-model-best-practices}

I det här dokumentet beskrivs viktiga rekommendationer när du utformar din Adobe Campaign-datamodell.

Adobe Campaign-systemet är mycket flexibelt och kan byggas ut utöver den ursprungliga implementeringen. Men även om möjligheterna är oändliga är det viktigt att fatta kloka beslut och bygga starka grunder för att börja utforma din datamodell.

Om du vill ha en bättre förståelse för de inbyggda tabellerna i Campaign och hur de relaterar till varandra kan du läsa [det här avsnittet](datamodel.md).

[!DNL :bulb:] Läs  [det här ](schemas.md) avsnittet för att komma igång med Campaign-scheman.

[!DNL :bulb:] Lär dig hur du konfigurerar tilläggsscheman för att utöka Adobe Campaign-databasens konceptuella datamodell på  [den här sidan](extend-schema.md).

## Datamodellarkitektur {#data-model-architecture}

Adobe Campaign är ett kraftfullt kanalövergripande kampanjhanteringssystem som kan hjälpa er att anpassa era online- och offlinestrategier för att skapa personaliserade kundupplevelser.

### Kundfokuserad metod {#customer-centric-approach}

De flesta e-postleverantörer kommunicerar med kunderna via en listcentrerad strategi, men Adobe Campaign förlitar sig på en relationsdatabas för att få en bredare bild av kunderna och deras attribut.

Gå till **[!UICONTROL Admin > Configuration > Data schemas]**, markera en resurs i listan och klicka på fliken **[!UICONTROL Documentation]** om du vill få åtkomst till beskrivningen av varje tabell.


>[!NOTE]
>
>Adobe Campaign tillåter att en [anpassad mottagartabell](custom-recipient.md) skapas. I de flesta fall bör du dock använda den inbyggda [mottagartabellen](datamodel.md#ootb-profiles) som redan har fördefinierade ytterligare tabeller och funktioner.

### Data för Adobe Campaign {#data-for-campaign}

Vilka data ska skickas till Adobe Campaign? Det är viktigt att kunna avgöra vilka data som krävs för era marknadsföringsaktiviteter.

>[!NOTE]
>
>Adobe Campaign är varken ett data warehouse eller ett rapportverktyg. Därför ska du inte importera alla möjliga kunder och tillhörande information till Adobe Campaign, eller importera data som bara ska användas för att skapa rapporter.

Om du vill avgöra om ett attribut behövs eller inte i Adobe Campaign, frågar du dig själv om det skulle ingå i någon av dessa kategorier:

* Attribut som används för **segmentering**
* Attribut som används för **datahanteringsprocesser** (t.ex. aggregerad beräkning)
* Attribut som används för **personalisering**

Om du inte hamnar i något av dessa behöver du troligen inte det här attributet i Adobe Campaign.

### Val av datatyper {#data-types}

Följ de bästa metoderna nedan för att konfigurera data i Adobe Campaign för att säkerställa att din systemarkitektur och prestanda är bra.

* Inom stora tabeller kan du infoga strängar eller numeriska fält och lägga till länkar till referenstabeller (när du arbetar med värdelista).
* Med attributet **expr** kan du definiera ett schemaattribut som ett beräkningsfält i stället för ett fysiskt uppsättningsvärde i en tabell. Detta kan ge åtkomst till informationen i ett annat format (t.ex. för ålder och födelsedatum) utan att båda värdena behöver lagras. Detta är ett bra sätt att undvika att duplicera fält. I mottagartabellen används till exempel ett uttryck för domänen, som redan finns i e-postfältet.
* När uttrycksberäkningen är komplex bör du dock inte använda attributet **expr** eftersom beräkningen kan påverka frågeprestanda.
* Typen **XML** är ett bra sätt att undvika att skapa för många fält. Men det tar också upp diskutrymme när en CLOB-kolumn används i databasen. Det kan även leda till komplexa SQL-frågor och kan påverka prestanda.
* Längden för ett **strängfält**-fält ska alltid definieras med kolumnen. Som standard är maxlängden i Adobe Campaign 16 kB, men Adobe rekommenderar att du håller fältet kortare om du redan vet att storleken inte kommer att överskrida en kortare längd.
* Det går bra att ha ett fält som är kortare i Adobe Campaign än i källsystemet om du är säker på att storleken i källsystemet var för stor och inte skulle nås. Detta kan betyda en kortare sträng eller ett mindre heltal i Adobe Campaign.

### Val av fält {#choice-of-fields}

Ett fält måste lagras i en tabell om det har ett syfte att målinrikta eller personalisera. Det innebär att om ett fält inte används för att skicka ett anpassat e-postmeddelande eller används som ett kriterium i en fråga, tar det upp diskutrymme i onödan.


### Val av nycklar {#choice-of-keys}

Förutom **autouid** och **autopk** som är definierad som standard i de flesta tabeller bör du överväga att lägga till några logiska nycklar eller affärsnycklar (kontonummer, klientnummer osv.). Den kan användas senare för import/avstämning eller datapaket. Mer information finns i [Identifierare](#identifiers).

Effektiva nycklar är viktiga för prestanda. Med Snowflake kan du infoga numeriska eller strängbaserade datatyper som nycklar för tabeller.

<!-- ### Dedicated tablespaces {#dedicated-tablespaces}

The tablespace attribute in the schema allows you to specify a dedicated tablespace for a table.

The installation wizard allows you to store objects by type (data, temporary).

Dedicated tablespaces are better for partitioning, security rules, and allow fluid and flexible administration, better optimization, and performance. -->

## Identifierare {#identifiers}

Adobe Campaign-resurser har tre identifierare och det går att lägga till ytterligare en identifierare.

I följande tabell beskrivs dessa identifierare och deras syfte.

| Identifierare | Beskrivning | Bästa praxis |
|--- |--- |--- |
| ID | <ul><li>ID är den fysiska primärnyckeln för en Adobe Campaign-tabell. För inbyggda tabeller är det ett UUID (Universally Unique ID)</li><li>Den här identifieraren måste vara unik. </li><li>Ett UUID kan vara synligt i en schemadefinition.</li></ul> | <ul><li>Automatiskt genererade identifierare bör inte användas som referens i ett arbetsflöde eller i en paketdefinition.</li><li>ID:t i en tabell är ett UUID och den här typen ska inte ändras.</li></ul> |
| Namn (eller internt namn) | <ul><li>Den här informationen är en unik identifierare för en post i en tabell. Värdet kan uppdateras manuellt, vanligtvis med ett genererat namn.</li><li>Den här identifieraren behåller sitt värde när den distribueras i en annan instans av Adobe Campaign och får inte vara tom.</li></ul> | <ul><li>Byt namn på den post som genererats av Adobe Campaign om objektet ska distribueras från en miljö till en annan.</li><li>När ett objekt har ett namnutrymmesattribut (*schema* till exempel), kommer detta gemensamma namnutrymme att utnyttjas för alla anpassade objekt som skapas. Vissa reserverade namnutrymmen bör inte användas: *nms*, *xtk* osv.  Observera att vissa namnutrymmen bara är interna. [Läs mer](schemas.md#reserved-namespaces).</li><li>När ett objekt inte har något namnutrymme (*arbetsflöde* eller *leverans* till exempel) läggs det här namnutrymmesbegreppet till som ett prefix för ett internt namnobjekt: *namespaceMyObjectName*.</li><li>Använd inte specialtecken som blanksteg&quot;, halvkolumn &quot;:&quot; eller bindestreck &quot;-&quot;. Alla dessa tecken ersätts med understrecket&quot;_&quot; (tillåtet tecken). &quot;abc-def&quot; och &quot;abc:def&quot; skulle till exempel lagras som &quot;abc_def&quot; och skrivas över varandra.</li></ul> |
| Etikett | <ul><li>Etiketten är affärsidentifieraren för ett objekt eller en post i Adobe Campaign.</li><li>Det här objektet tillåter mellanslag och specialtecken.</li><li>Det garanterar inte att ett register är unikt.</li></ul> | <ul><li>Vi rekommenderar att du bestämmer en struktur för objektetiketterna.</li><li>Detta är den mest användarvänliga lösningen för att identifiera en post eller ett objekt för en Adobe Campaign-användare.</li></ul> |

Adobe Campaign primärnyckel är ett automatiskt genererat UUID för alla inbyggda tabeller. Ett UUID kan också användas för anpassade tabeller.

Även om antalet ID:n är oändligt bör du ta hand om databasens storlek för att säkerställa optimala prestanda. Om du vill förhindra problem måste du justera inställningarna för instansrensning. Mer information finns i [det här avsnittet](#data-retention).


## Anpassade interna nycklar {#custom-internal-keys}

Primärnycklar krävs för alla tabeller som skapas i Adobe Campaign.

De flesta organisationer importerar poster från externa system. Även om den fysiska nyckeln för mottagartabellen är attributet &quot;id&quot;, är det möjligt att fastställa en anpassad nyckel dessutom.

Denna anpassade nyckel är den faktiska primärnyckeln för posten i det externa system som matar Adobe Campaign.

När du skapar en anpassad tabell finns det två alternativ:
* En kombination av autogenererad nyckel (id) och intern nyckel (anpassad). Det här alternativet är intressant om systemnyckeln är en sammansatt nyckel eller inte ett heltal. Med Snowflake får heltal och strängbaserade nycklar högre prestanda i stora tabeller och med andra tabeller.
* Använda primärnyckeln som extern systemprimärnyckel. Den här lösningen är vanligtvis att föredra eftersom den förenklar import och export av data, med en konsekvent nyckel mellan olika system. **Automatisk** redigering bör inaktiveras om nyckeln heter&quot;id&quot; och förväntas fyllas med externa värden (inte autogenererade).

>[!CAUTION]
>
>Ett autouid ska inte användas som referens i arbetsflöden.


## Länkar och kardinalitet {#links-and-cardinality}

### Länkar {#links}

Se upp för den&quot;egna&quot; integriteten i stora tabeller. Om du tar bort poster som har stora tabeller med &quot;egen&quot; integritet kan instansen eventuellt stoppas. Tabellen är låst och borttagningarna görs en i taget. Därför är det bäst att använda&quot;neutral&quot; integritet i underordnade tabeller som har stora volymer.

Att deklarera en länk som en extern koppling är inte bra för prestandan. Posten med noll-id emulerar den externa kopplingsfunktionen. Det är inte nödvändigt att deklarera externa kopplingar om länken använder **autouid**.

Även om det är möjligt att ansluta en tabell i ett arbetsflöde rekommenderar Adobe att du definierar gemensamma länkar mellan resurser direkt i datastrukturdefinitionen.

Länken ska definieras i enlighet med de data som finns i tabellerna. En felaktig definition kan påverka data som hämtas via länkar, t.ex. oväntat duplicering av poster.

Namnge länken konsekvent med tabellnamnet: länknamnet bör hjälpa till att förstå vad den distinkta tabellen är.

Namnge inte en länk med ID som suffix. Ge det till exempel namnet&quot;transaktion&quot; i stället för&quot;transaktionId&quot;.

Som standard skapar Adobe Campaign en länk med den externa tabellens primärnyckel. För större tydlighet är det bättre att uttryckligen definiera kopplingen i länkdefinitionen.

### Kardinalitet {#cardinality}

När du utformar en länk måste du se till att målposten är unik när en 1-1-relation har deklarerats. Annars kan join returnera flera poster när bara en förväntas. Detta resulterar i fel under leveransförberedelsen när frågan returnerar fler rader än förväntat. Ange länknamnet till samma namn som målschemat.

Definiera en länk med en kardinalitet (1-N) i schemat på (1) sidan. Relationen mottagare (1) - (N)-transaktion ska till exempel definieras i transaktionsschemat.

Observera att en länks omvända kardinalitet är (N) som standard. Det går att definiera en länk (1-1) genom att lägga till attributet revCardinality=&#39;single&#39; till länkdefinitionen.

Om den omvända länken inte ska vara synlig för användaren kan du dölja den med länkdefinitionen revLink=&#39;_NONE_&#39;. Ett bra exempel för detta är att definiera en länk från mottagaren till den senaste transaktionen som har slutförts. Du behöver bara se länken från mottagaren till den sista transaktionen och ingen omvänd länk krävs för att kunna visas från transaktionsregistret.

Länkar som utför en extern koppling (1-0..1) bör användas med försiktighet eftersom det påverkar systemets prestanda.

## Datalagring {#data-retention}

Adobe Campaign är varken ett data warehouse eller ett rapportverktyg. För att Adobe Campaign-lösningen ska fungera väl bör databastillväxten därför förbli under kontroll. För att uppnå detta kan det vara bra att följa några av de bästa metoderna nedan.

När det gäller lagring har inbyggda loggtabeller i Campaign förinställda lagringsperioder vilket generellt begränsar datalagringen till sex månader eller mindre.

Följande är standardvärden gällande lagring för inbyggda tabeller. Var medveten om att lagringskonfigurationen ställs in av Adobes tekniska administratörer under implementeringen och att värdena kan variera för varje implementering baserat på kundens krav.

* **Konsoliderad spårning**: 1 år
* **Leveransloggar**: 6 månader
* **Spårningsloggar**: 1 år
* **Raderade leveranser**: 1 vecka
* **Importavvisanden**: 6 månader
* **Besökarprofiler**: 1 månad
* **Erbjudandeförslag**: 1 år
* **Händelser**: 1 månad
* **Statistik över händelsebearbetning**: 1 månader
* **Arkiverade händelser**: 1 år
* **Ignorerade pipeline-händelser**: 1 månad

>[!CAUTION]
>
>Anpassade tabeller rensas inte med standardrensningsprocessen. Även om detta kanske inte är nödvändigt den första dagen, glöm inte att skapa en rensningsprocess för dina anpassade tabeller eftersom detta kan leda till prestandaproblem.

Det finns några lösningar som minimerar behovet av arkivering i Adobe Campaign:
* Exportera data i en data warehouse utanför Adobe Campaign.
* Generera aggregerade värden som använder mindre utrymme samtidigt som de är tillräckliga för er marknadsföringspraxis. Du behöver t.ex. inte den fullständiga kundtransaktionshistoriken i Adobe Campaign för att hålla reda på de senaste köpen.

Du kan deklarera attributet &quot;deleteStatus&quot; i ett schema. Det är effektivare att markera posten som borttagen och sedan skjuta upp borttagningen i rensningsaktiviteten.

[!DNL :speech_balloon:] Som användare av hanterade Cloud Services kan du kontakta Adobe konsulter eller tekniska administratörer för att få veta mer om bevarande eller om du behöver ange bevarande för anpassade tabeller.

## Prestanda {#performance}

Följ de bästa metoderna nedan för att få bättre prestanda när som helst.

### Allmänna rekommendationer {#general-recommendations}

* Undvik åtgärder som &quot;CONTAINS&quot; i frågor. Om du vet vad som förväntas och vill filtreras efter använder du samma villkor med &quot;EQUAL TO&quot; eller andra specifika filteroperatorer.
* Försök att se till att processer som import och export går utanför kontorstid.
* Se till att det finns ett schema för alla dagliga aktiviteter och att schemat följs.
* Om en eller flera av de dagliga processerna misslyckas och om det är obligatoriskt att köra den samma dag, ska du se till att det inte finns några processkonflikter som körs när den manuella processen startar, eftersom detta kan påverka systemets prestanda.
* Kontrollera att ingen av de dagliga kampanjerna körs under importprocessen eller när någon manuell process körs.
* Använd en eller flera referenstabeller i stället för att duplicera ett fält i varje rad. När du använder nyckel/värde-par bör du välja en numerisk nyckel.
* En kort sträng kan fortfarande användas. Om referenstabeller redan finns på plats i ett externt system, kommer dataintegreringen med Adobe Campaign att underlättas om du återanvänder samma.

### En-till-många-relationer {#one-to-many-relationships}

* Datadesign påverkar användbarhet och funktionalitet. Om du utformar din datamodell med många 1:N-relationer blir det svårare för användarna att skapa meningsfull logik i programmet. En-till-många-filterlogik kan vara svår för icke-tekniska marknadsförare att konstruera och förstå på ett korrekt sätt.
* Det är bra att ha alla viktiga fält i en tabell eftersom det gör det enklare för användarna att skapa frågor. Ibland kan det också vara bra för prestanda att duplicera vissa fält mellan tabeller om det kan undvika en koppling.
* Vissa inbyggda funktioner kan inte referera till 1:N-relationer, t.ex. offertviktningsformel och Leveranser.

## Stora tabeller {#large-tables}

Adobe Campaign förlitar sig på databasmotorer från tredje part. Beroende på vilken provider som används kan optimering av prestanda för större tabeller kräva en viss design.

Nedan följer några vanliga metodtips som bör följas när du utformar din datamodell med stora tabeller och komplexa kopplingar.

* När du använder ytterligare anpassade mottagartabeller måste du ha en dedikerad loggtabell för varje leveransmappning.
* Minska antalet kolumner, särskilt genom att identifiera de som inte används.
* Optimera datamodellens relationer genom att undvika komplexa kopplingar, till exempel kopplingar på flera villkor och/eller flera kolumner.
* För hörnnycklar kan du använda numeriska värden eller strängbaserade värden.
* Minska så mycket du kan av djupet för loggbevarande. Om du behöver mer detaljerad historik kan du sammanställa beräkningar och/eller hantera anpassade loggtabeller för att lagra större historik.

### Storlek på tabeller {#size-of-tables}

Tabellstorleken är en kombination av antalet poster och antalet kolumner per post. Båda kan påverka prestanda för frågor.

* En **tabell med liten storlek** påminner om leveranstabellen.
* En **medelstor tabell** är samma som storleken på mottagartabellen. Det finns en post per kund.
* En **tabell med stor storlek** påminner om den allmänna loggtabellen. Det finns många poster per kund.
Om din databas till exempel innehåller 10 miljoner mottagare innehåller den stora loggtabellen cirka 100 till 200 miljoner meddelanden och leveranstabellen innehåller några tusen poster.

Antalet rader påverkar även prestandan. Adobe Campaign-databasen är inte utformad för att lagra historiska data som inte aktivt används för målinriktning eller personalisering - det här är en operativ databas.

Om du vill förhindra prestandaproblem som har att göra med det stora antalet rader sparar du bara de nödvändiga posterna i databasen. Alla andra poster bör exporteras till tredje part data warehouse och tas bort från Adobe Campaign databas.

Här följer några tips om tabellstorlek:

* Designa stora tabeller med färre fält och mer numeriska data.
* Använd inte en stor kolumntyp för att lagra små tal som booleska värden.
* Ta bort oanvända kolumner från tabelldefinitionen.
* Spara inte historiska eller inaktiva data i Adobe Campaign-databasen (export och rensning).
