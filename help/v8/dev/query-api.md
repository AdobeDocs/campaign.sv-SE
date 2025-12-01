---
title: Fråga databasen med queryDef
description: Lär dig hur du använder metoderna queryDef och NLWS för att fråga Campaign-databasen
feature: API
role: Developer
level: Intermediate, Experienced
hide: true
hidefromtoc: true
exl-id: 0fd39d6c-9e87-4b0f-a960-2aef76c9c8eb
source-git-commit: ceab90331fab0725962a2a98f338ac3dc31a2588
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 0%

---

# Fråga databasen med queryDef {#query-database-api}

[!DNL Adobe Campaign] innehåller kraftfulla JavaScript-metoder för interaktion med databasen med `queryDef` och objektet `NLWS`. Med dessa SOAP-baserade metoder kan du läsa in, skapa, uppdatera och fråga data med JSON, XML eller SQL.

>[!NOTE]
>
>Den här dokumentationen innehåller dataorienterade API:er för programmässig sökning i databasen. Information om REST API:er finns i [Kom igång med REST API:er](api/get-started-apis.md). Om du vill skapa visuella frågor läser du [Arbeta med frågeredigeraren](../start/query-editor.md).

## Vad är NLWS? {#what-is-nlws}

`NLWS` (Neolane Web Services) är det globala JavaScript-objekt som används för att komma åt [!DNL Adobe Campaign]s SOAP-baserade API-metoder. Scheman är egenskaper för objektet `NLWS`, vilket gör att du kan interagera med Campaign-entiteter programmatiskt.

Enligt [Campaign-JSAPI-dokumentationen](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html){target="_blank"} är &quot;scheman&quot; globala objekt av typen &quot;NLWS&quot;.&quot; Syntaxen för att komma åt schemametoder följer det här mönstret:

```javascript
NLWS.<namespace><SchemaName>.<method>()
```

**Exempel:**

* `NLWS.nmsRecipient` - Åtkomstmetoder för mottagarschemat (`nms:recipient`)
* `NLWS.nmsDelivery` - Åtkomstmetoder för leveransschemat (`nms:delivery`)
* `NLWS.xtkQueryDef` - Använd queryDef-metoder för att fråga databasen

Vanliga API-metoder är:

* `load(id)` - Läs in en entitet med dess ID. [Läs mer](https://experienceleague.adobe.com/developer/campaign-api/api/f-load.html){target="_blank"}
* `create(data)` - Skapa en ny entitet
* `save()` - Spara ändringar i en entitet

**Exempel från officiell dokumentation:**

```javascript
var delivery = NLWS.nmsDelivery.load("12435")
```

>[!NOTE]
>
>**Alternativ syntax:** För bakåtkompatibilitet kan du även se syntaxen med gemener i vissa dokument (t.ex. `nms.recipient.create()`, `xtk.queryDef.create()`). Båda syntaxerna fungerar, men `NLWS` är den standard som beskrivs i den officiella Campaign-JSAPI-referensen.

## Förhandskrav {#prerequisites}

Innan du använder metoderna queryDef och NLWS bör du känna till följande:

* JavaScript
* [!DNL Adobe Campaign] datamodell och scheman
* XPath-uttryck för navigering i schemaelement

**Om Campaign-datamodellen:**

Adobe Campaign levereras med en fördefinierad datamodell som består av tabeller som är sammanlänkade i en molndatabas. Den grundläggande strukturen omfattar följande:

* **Mottagartabell** (`nmsRecipient`) - Huvudregister som lagrar marknadsföringsprofiler
* **Leveranstabell** (`nmsDelivery`) - lagrar leveransåtgärder och mallar med parametrar för att utföra leveranser
* **Loggar tabeller** - Lagra körningsloggar:
   * `nmsBroadLogRcp` - Leveransloggar för alla meddelanden som skickas till mottagare
   * `nmsTrackingLogRcp` - Spårningsloggar för mottagarnas reaktioner (öppningar, klickningar)
* **Tekniska tabeller** - Lagra systemdata som operatorer (`xtkGroup`), sessioner (`xtkSessionInfo`), arbetsflöden (`xtkWorkflow`)

Om du vill komma åt schemabeskrivningar i Campaign-gränssnittet går du till **Administration > Konfiguration > Datamodeller**, markerar en resurs och klickar på fliken **Dokumentation** .

## Metoder för entitetsschema {#entity-schema-methods}

Varje schema i [!DNL Adobe Campaign] (t.ex. `nms:recipient`, `nms:delivery`) levereras med metoder som är tillgängliga via objektet `NLWS`. Dessa metoder är ett praktiskt sätt att interagera med databasenheter.

### Statiska metoder {#static-methods}

Statiska SOAP-metoder nås genom att en metod anropas i det objekt som representerar schemat. `NLWS.xtkWorkflow.PostEvent()` anropar till exempel en statisk metod.

### Icke-statiska metoder {#non-static-methods}

Om du vill använda icke-statiska SOAP-metoder måste du först hämta en entitet med metoderna `load` eller `create` i motsvarande scheman. Läs mer i [Kampanjens JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html){target="_blank"}.

### Läsa in, spara och skapa enheter {#load-save-create}

**Läs in en entitet med ID och uppdatera den:**

```javascript
// Load a delivery by @id and save
var delivery = NLWS.nmsDelivery.load("12435");
delivery.label = "New label";
delivery.save();
```

**Skapa en mottagare med JSON:**

```javascript
// Create via JSON, edit via JS and save
var recipient = NLWS.nmsRecipient.create({
  x: { // the key 'x' doesn't matter
    email: 'john.doe@example.com',
  }
});
recipient.folder_id = 1183;
recipient.firstName = 'John';
recipient.lastName = 'Doe';
recipient.save();
```

**Skapa en mottagare med XML:**

```javascript
// Create via XML and save
var recipient = NLWS.nmsRecipient.create(
  <recipient
    email="support@adobe.com"
    lastName="Adobe"
    firstName="Support"
  />
);
recipient.save();
```

## QueryDef - översikt {#querydef-overview}

Schemat `xtk:queryDef` innehåller metoder för att skapa och köra databasfrågor. Du kan använda `NLWS.xtkQueryDef.create()` för att skapa frågor med JSON- eller XML-syntax.

**Tillgängliga åtgärder:**

* `select` - Hämta flera poster
* `get` - Hämta en enskild post (SQL `LIMIT 1`)
* `getIfExists` - Hämta en enskild post, returnera null om den inte hittas
* `count` - Antal poster som matchar villkor

Läs mer om queryDef-metoder i [Kampanjens JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/s-xtk-queryDef.html){target="_blank"}.

## Fråga med JSON {#query-json}

Använd `NLWS.xtkQueryDef.create()` för att skapa frågor med JSON-syntax. Åtgärden `get` hämtar en enskild post (SQL `LIMIT 1`) medan `select` hämtar flera poster.

**Hämta en enskild mottagare:**

```javascript
var email = "contact@example.com";
var query = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: "nms:recipient", 
    operation: "get", // "get" does a SQL "LIMIT 1"
    select: { 
      node: [{expr: "@id"}, {expr: "@email"}, {expr: "@firstName"}] 
    },
    where: { 
      condition: [
        {expr: "@email = '" + email + "'"}, // filter by email
      ],
    }
  }
});

var res = query.ExecuteQuery(); 
// res is an XML object such as <recipient id="1234" email="contact@example.com" firstName="John"/>
var recipient = NLWS.nmsRecipient.load(res.$id); // conversion to a JavaScript object
recipient.email = "newemail@example.com";
recipient.save();
```

**Använd `getIfExists` för att undvika undantag:**

Om posten kanske inte finns använder du `operation: "getIfExists"` i stället för `get` för att undvika undantag:

```javascript
var query = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: "nms:recipient", 
    operation: "getIfExists",
    select: { node: [{expr: "@id"}] },
    where: { 
      condition: [{expr: "@email = 'nonexistent@example.com'"}]
    }
  }
});

var res = query.ExecuteQuery();
if (res) {
  logInfo("Recipient found: " + res.$id);
} else {
  logInfo("Recipient not found");
}
```

## Markera flera poster {#select-multiple}

Använd åtgärden `select` för att hämta flera poster. Du kan lägga till villkor, ordning och begränsningar.

**Frågearbetsflöden med filter och ordning:**

```javascript
var query = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: "xtk:workflow", 
    operation: "select", 
    select: {
      node: [
        {expr: "@id"},
        {expr: "@label"},
        {expr: "@internalName"}
      ] 
    }, 
    where: {
      condition: [
        {expr: "[folder/@name]='nmsTechnicalWorkflow'"},
        {expr: "@production = 1"}
      ]
    }, 
    orderBy: {
      node: {expr: "@internalName", sortDesc: "false"}
    }
  }
});

var res = query.ExecuteQuery();

var workflows = res.getElementsByTagName("workflow");
for each (var w in workflows) {
  logInfo(w.getAttribute("internalName"));
}
```

**Frågeleveranser med XML-syntax:**

```javascript
var q = NLWS.xtkQueryDef.create(
  <queryDef schema="nms:delivery" operation="select" lineCount="3">
    <select>
      <node expr="@id"/>
      <node expr="@label"/>
      <node expr="@created"/>
    </select>
    <where>
      <condition expr="@label NOT LIKE '%Proof%'" bool-operator="AND"/>
      <condition expr="@created &lt;= '2024-12-01'" bool-operator="AND"/>
    </where>
    <orderBy>
      <node expr="@lastModified" sortDesc="true"/>
    </orderBy>    
  </queryDef>
);

var deliveries = q.ExecuteQuery();
for each(var delivery in deliveries.delivery) {
  logInfo(delivery.@id + ": " + delivery.@label);
}
```

>[!NOTE]
>
>**Resultatgränser:** Kampanjen begränsar automatiskt frågeresultaten för att förhindra minnesproblem:
>* Standardgränsen varierar beroende på sammanhang (vanligen 200-10 000 poster)
>* Använd `lineCount` för att explicit ange maximalt antal resultat
>* För stora datauppsättningar (>1 000 poster) använder du arbetsflöden i stället för queryDef. Arbetsflödena är utformade för att bearbeta miljontals rader effektivt.

Läs mer om [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html){target="_blank"} och [fråga om bästa praxis](https://opensource.adobe.com/acc-js-sdk/xtkQueryDef.html){target="_blank"}.

## Fråga om övergångsdata för arbetsflöde {#workflow-transition-data}

När du arbetar med JavaScript-aktiviteter i arbetsflöden kan du hämta data från inkommande övergångar med `vars.targetSchema` och `vars.tableName`.

**Fråga efter mottagardata från en arbetsflödesövergång:**

```javascript
// Query data from the incoming transition
var query = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: vars.targetSchema, // The schema from the previous activity
    operation: 'select', 
    lineCount: 999999999, // Override default 10,000 limit
    select: { 
      node: [
        {expr: '@id'},
        {expr: '@email'},
        {expr: '@firstName'},
        {expr: '@lastName'}
      ]
    },
  }
});

var records = query.ExecuteQuery(); // Returns a DOMElement

for each(var record in records.getElements()) {
  logInfo("Processing: " + record.$id + " - " + record.$email);
  
  // Clean email address
  var cleanedEmail = record.$email.replace(/\s+/g, '').toLowerCase();
  
  // Update using parameterized query to prevent SQL injection
  sqlExec(
    "UPDATE " + vars.tableName + " SET sEmail=$(sz) WHERE iId=$(l)", 
    cleanedEmail, 
    record.$id
  );
}
```

>[!CAUTION]
>
>Använd alltid parametriserade frågor med `$(sz)` för strängar och `$(l)` för heltal för att förhindra SQL-injektionsproblem. Läs mer i [Kampanjens JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/f-sqlExec.html){target="_blank"}.

## Räkna poster {#count-records}

Använd `Count(@id)` med ett alias för att räkna poster.

**Antal hypoteser som körs:**

```javascript
var jobCount = NLWS.xtkQueryDef.create(
  <queryDef schema="nms:remaHypothesis" operation="get">
    <select>
      <node expr="Count(@id)" alias="@count"/>
    </select>
    <where>
      <condition expr={"@status=" + HYPOTHESIS_STATUS_RUNNING}/>
    </where>
  </queryDef>
);

var iJobCount = parseInt(jobCount.ExecuteQuery().@count);
logInfo("Running jobs: " + iJobCount);
```

**Antal med flera villkor:**

```javascript
var xmlQuery = <queryDef schema="nms:trackingLogRcp" operation="select">
  <select>
    <node expr="DateOnly(@logDate)" groupBy="1"/>
    <node expr="count(@id)" alias="@count"/>
    <node expr="countDistinct([@broadLog-id])" alias="@distinctCount"/>
  </select>
  <where>
    <condition expr={"@logDate IS NOT NULL AND @logDate &lt; #" + today + "# AND [@url-id] &lt;&gt; 1"}/>
  </where>
</queryDef>;

var result = NLWS.xtkQueryDef.create(xmlQuery).ExecuteQuery();
```

## Fördelning av värden {#distribution-values}

Hämta värdefördelningen för ett specifikt fält, vilket är användbart för att analysera datamönster.

**Distribution av landskoder:**

```javascript
/**
 * @class DistributionOfValues
 * @param {string} schema - The schema name (e.g., 'nms:recipient')
 * @param {string} field - The field to analyze (e.g., '@country')
 */
function DistributionOfValues(schema, field) {
  this.queryDef = {
    operation: 'select', 
    lineCount: 200, 
    schema: schema,
    select: {
      node: [
        {alias: '@expr', expr: field, groupBy: 'true', noSqlBind: 'true'},
        {alias: '@count', expr: 'COUNT()', label: 'Count'},
      ]
    },
    orderBy: {
      node: [{expr: 'COUNT()', sortDesc: 'true'}]
    },
  };
  
  /**
   * Execute the query and return results
   * @return {Array} XML list of results
   */
  this.get = function() {
    this.results = NLWS.xtkQueryDef.create({queryDef: this.queryDef}).ExecuteQuery();
    return this.results.getElements();
  };
}

// Usage example
var d = new DistributionOfValues('nms:recipient', '@country');

// Optional: Add additional filters
d.queryDef.where = {
  condition: [{expr: 'DateOnly(@created) = #2024-12-01#'}]
};

// Execute and display results
for each(var result in d.get()) {
  logInfo(result.$expr + ': ' + result.$count);
}
```

## Frågeuppräkningar med analys {#analyze-enumerations}

Alternativet `analyze` returnerar användarvänliga namn för uppräkningsvärden. I stället för bara numeriska värden returnerar Campaign också strängvärdet och etiketten med suffixen&quot;Namn&quot; och&quot;Etikett&quot;.

**Frågeleveransmappning med uppräkningsanalys:**

```javascript
var query = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: "nms:deliveryMapping",
    operation: "get",
    select: {
      node: [
        {expr: "@id"},
        {expr: "@name"},
        {expr: "[storage/@exclusionType]", analyze: true}  // Analyze enumeration
      ]
    },
    where: {
      condition: [{expr: "@name='mapRecipient'"}]
    }
  }
});

var mapping = query.ExecuteQuery();

// Result includes:
// - exclusionType: 2 (numeric value)
// - exclusionTypeName: "excludeRecipient" (string value)
// - exclusionTypeLabel: "Exclude recipient" (display label)
logInfo("Type: " + mapping.$exclusionType);
logInfo("Name: " + mapping.$exclusionTypeName);
logInfo("Label: " + mapping.$exclusionTypeLabel);
```

Läs mer om alternativet [Analysera](https://opensource.adobe.com/acc-js-sdk/xtkQueryDef.html#the-analyze-option){target="_blank"}.

## Sidnumrering {#pagination}

Använd `lineCount` och `startLine` för att paginera genom stora resultatuppsättningar.

**Hämta poster på sidor:**

```javascript
// Get records 3 and 4 (skip first 2)
var query = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: "nms:recipient",
    operation: "select",
    lineCount: 2,     // Number of records per page
    startLine: 2,     // Starting position (0-indexed)
    select: {
      node: [
        {expr: "@id"},
        {expr: "@email"}
      ]
    },
    orderBy: {
      node: [{expr: "@id"}]  // Critical: Always use orderBy for pagination
    }
  }
});

var recipients = query.ExecuteQuery();
```

>[!CAUTION]
>
>**Pagination kräver orderBy:** Utan en `orderBy` -sats är det inte säkert att frågeresultaten är i konsekvent ordning. Efterföljande anrop kan returnera olika sidor eller dubblettposter. Inkludera alltid `orderBy` när sidnumrering används.

Läs mer om [sidnumrering](https://opensource.adobe.com/acc-js-sdk/xtkQueryDef.html#pagination){target="_blank"}.

## Dynamisk frågekonstruktion {#dynamic-queries}

Bygg frågor dynamiskt genom att lägga till villkor programmatiskt.

**Lägg till villkor i en befintlig fråga:**

```javascript
var xmlQuery = <queryDef schema="nms:delivery" operation="select">
  <select>
    <node expr="@id"/>
    <node expr="@label"/>
  </select>
  <where/>
</queryDef>;

// Dynamically add conditions
if (includeProofs) {
  xmlQuery.where.appendChild(
    <condition expr="@label LIKE '%Proof%'"/>
  );
}

if (startDate) {
  xmlQuery.where.appendChild(
    <condition expr={"@created >= #" + Format.toISO8601(startDate) + "#"}/>
  );
}

var result = NLWS.xtkQueryDef.create(xmlQuery).ExecuteQuery();
```

**Skapa select och where-satser i slingor:**

```javascript
// Build select dynamically
var select = <select/>;
var fields = ["@id", "@label", "@created"];
for each(var field in fields) {
  select.appendChild(<node expr={field}/>);
}

// Build where dynamically
var where = <where/>;
var conditions = [
  "@status = 1",
  "@type = 'email'"
];
for each(var condition in conditions) {
  where.appendChild(<condition expr={condition}/>);
}

// Create complete query
var xmlQuery = <queryDef operation="select" schema="nms:delivery"/>;
xmlQuery.appendChild(select);
xmlQuery.appendChild(where);

var result = NLWS.xtkQueryDef.create(xmlQuery).ExecuteQuery();
```

## Avancerade queryDef-metoder {#advanced-methods}

Efter `ExecuteQuery()` innehåller queryDef flera specialiserade metoder för avancerade användningsfall.

### BuildQuery - Generera SQL utan att köra {#build-query}

Använd `BuildQuery()` för att generera SQL-satsen utan att köra den. Detta är användbart när du vill felsöka, logga eller skicka frågor till externa system.

```javascript
var query = NLWS.xtkQueryDef.create(
  <queryDef schema="nms:recipient" operation="select">
    <select>
      <node expr="@id"/>
      <node expr="@email"/>
    </select>
    <where>
      <condition expr="@email IS NOT NULL"/>
    </where>
  </queryDef>
);

// Get the generated SQL
var sql = query.BuildQuery();
logInfo("Generated SQL: " + sql);
// Output: "SELECT iRecipientId, sEmail FROM NmsRecipient WHERE sEmail IS NOT NULL"
```

Läs mer om [BuildQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-BuildQuery.html){target="_blank"}.

### BuildQueryEx - Hämta SQL med formatsträng {#build-query-ex}

`BuildQueryEx()` returnerar både SQL-frågan och en formatsträng som är kompatibel med funktionen `sqlSelect()`.

```javascript
var query = NLWS.xtkQueryDef.create(
  <queryDef schema="nms:recipient" operation="select">
    <select>
      <node expr="@id"/>
      <node expr="@email"/>
      <node expr="@firstName"/>
    </select>
  </queryDef>
);

var [sql, format] = query.BuildQueryEx();
logInfo("SQL: " + sql);
logInfo("Format: " + format);

// Use with sqlSelect
var results = sqlSelect(format, sql);
```

Läs mer om [BuildQueryEx](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-BuildQueryEx.html){target="_blank"}.

### Markera alla - Lägg till alla fält som ska markeras {#select-all}

Metoden `SelectAll()` lägger automatiskt till alla fält från schemat till select-satsen, så att du inte kan visa varje fält manuellt.

```javascript
var query = NLWS.xtkQueryDef.create(
  <queryDef schema="nms:recipient" operation="select">
    <select/>
    <where>
      <condition expr="@id = 12345"/>
    </where>
  </queryDef>
);

// Add all fields to the select
query.SelectAll(false);

var result = query.ExecuteQuery();
// Result contains all recipient fields
```

Läs mer om [SelectAll](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-SelectAll.html){target="_blank"}.

### Uppdatera - massuppdateringsposter {#mass-update}

Med metoden `Update()` kan du utföra massuppdateringar för poster som matchar dina frågevillkor utan att läsa in varje post separat.

```javascript
// Mass update example: set a field value for all matching records
var updateQuery = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: "nms:recipient",
    operation: "update",
    where: {
      condition: [{expr: "@country = 'US'"}]
    },
    set: {
      node: [{expr: "@blackList", value: "0"}]
    }
  }
});

// Execute mass update
updateQuery.Update();
logInfo("Mass update completed");
```

>[!CAUTION]
>
>Massuppdateringar påverkar alla poster som matchar where-satsen. Testa alltid var du befinner dig med en urvalsfråga först för att kontrollera vilka poster som påverkas.

Läs mer om [Uppdatering](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-Update.html){target="_blank"}.

### GetInstanceFromModel - frågemallsinstanser {#get-instance-from-model}

Använd `GetInstanceFromModel()` för att hämta data från instanser som skapats från mallar.

```javascript
var query = NLWS.xtkQueryDef.create(
  <queryDef schema="nms:delivery" operation="select">
    <select>
      <node expr="@id"/>
      <node expr="@label"/>
    </select>
    <where>
      <condition expr="@isModel = 1"/>
    </where>
  </queryDef>
);

// Get instance data from template
var instance = query.GetInstanceFromModel("nms:delivery");
```

Läs mer om [GetInstanceFromModel](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-GetInstanceFromModel.html){target="_blank"}.

## Gruppåtgärder {#batch-operations}

Bearbeta flera poster batchvis för att förbättra prestandan.

**Leveransetiketter för batchuppdatering:**

```javascript
// Query all deliveries to update
var query = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: vars.targetSchema,
    operation: 'select', 
    lineCount: 999999999,
    select: { 
      node: [{expr: '@id'}]
    },
    where: {
      condition: [{expr: "@label LIKE '%OLD%'"}]
    }
  }
});

var records = query.ExecuteQuery();

// Process each record
for each(var record in records.getElements()) {
  var delivery = NLWS.nmsDelivery.load(record.$id);
  var oldLabel = delivery.label.toString();
  var newLabel = oldLabel.replace(/OLD/g, 'NEW');
  
  logInfo("Updating: " + oldLabel + " => " + newLabel);
  
  delivery.label = newLabel;
  delivery.save();
}

logInfo("Updated " + records.getElements().length + " deliveries");
```

## SQL-körning i råformat {#raw-sql}

För komplexa åtgärder kan du köra råa SQL direkt.

**Kör parametriserad SQL:**

```javascript
var dbEngine = instance.engine;

// Using parameterized query (recommended)
dbEngine.exec(
  "UPDATE NmsUserAgentStats SET iVisitorsOfTheDay=$(l) WHERE tsDate=$(dt)", 
  visitorCount,
  Format.parseDateTimeInter(dateString)
);
```

**Fråga med sqlSelect:**

```javascript
// Execute SELECT query and parse results
var xml = sqlSelect(
  "collection,@id,@email", 
  "SELECT iId as id, sEmail as email FROM " + vars.tableName + " WHERE iStatus = 1"
);

logInfo(xml.toXMLString()); // "<select><collection id="1" email="..."/></select>"

for each(var record in xml.collection) {
  logInfo('ID: ' + record.@id + ', Email: ' + record.@email);
  
  // Load full object if needed
  if (vars.targetSchema == "nms:recipient") {
    var recipient = NLWS.nmsRecipient.load(record.@id);
    recipient.lastName = recipient.lastName.toUpperCase();
    recipient.save();
  }
}
```

>[!CAUTION]
>
>När du använder rå SQL:
>
>* Validera och sanera användarindata
>* Använd parametriserade frågor med `$(sz)`, `$(l)`, `$(dt)` osv.
>* Observera skillnaderna mellan lokala databaser och molndatabaser i [FFDA-distributioner](../architecture/enterprise-deployment.md)

## Bästa praxis {#best-practices}

När du arbetar med queryDef- och NLWS-metoder:

* **Använd arbetsflöden för stora datamängder** - QueryDef är inte utformad för databearbetning i stora volymer. För datauppsättningar med fler än 1 000 poster använder du arbetsflöden som kan hantera miljontals rader effektivt. Läs mer i [dokumentationen för Campaign SDK](https://opensource.adobe.com/acc-js-sdk/xtkQueryDef.html){target="_blank"}
* **Använd parametriserade frågor** - Använd alltid bundna parametrar (`$(sz)`, `$(l)`) med `sqlExec` för att förhindra SQL-injektion
* **Ange explicita gränser** - Använd `lineCount` för att kontrollera resultatstorleken. Standardgränserna för kampanjen varierar beroende på sammanhang (200-10 000 poster)
* **Använd orderBy med pagination** - Inkludera alltid en `orderBy` -sats när du använder `startLine` och `lineCount` för att säkerställa konsekvent sidnumrering
* **Använd getIfExists** - Använd `operation: "getIfExists"` när det inte finns några poster för att undvika undantag
* **Använd Analysera för uppräkningar** - Lägg till `analyze: true` för att välja noder för att få användarvänliga uppräkningsnamn och etiketter
* **Optimera frågor** - Lägg till lämpliga `where` villkor för att begränsa resultatuppsättningar
* **Gruppbearbetning** - Bearbeta flera poster i grupper för att undvika minnesproblem och timeout
* **FFDA-medvetenhet** - I [Enterprise-distributioner (FFDA)](../architecture/enterprise-deployment.md) ska du vara medveten om att [!DNL Campaign] fungerar med två databaser



## Praktiska användningsområden {#use-cases}

### Felsök och logga frågor {#debug-queries}

Använd `BuildQuery()` för att inspektera den genererade SQL-filen innan körning:

```javascript
var query = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: "nms:recipient",
    operation: "select",
    select: { node: [{expr: "@id"}, {expr: "@email"}] },
    where: { condition: [{expr: "@blackList = 0"}] }
  }
});

// Log the SQL for debugging
var sql = query.BuildQuery();
logInfo("About to execute: " + sql);

// Now execute
var results = query.ExecuteQuery();
```

### Duplicera en post med SelectAll {#duplicate-record}

Använd `SelectAll()` för att kopiera alla fält när poster dupliceras:

```javascript
// Query the original record
var query = NLWS.xtkQueryDef.create(
  <queryDef schema="nms:delivery" operation="get">
    <select/>
    <where>
      <condition expr="@id = 12345"/>
    </where>
  </queryDef>
);

// Select all fields for duplication
query.SelectAll(true); // true indicates duplication mode

var original = query.ExecuteQuery();

// Create a new delivery from the original
var newDelivery = NLWS.nmsDelivery.create(original);
newDelivery.label = original.@label + " (Copy)";
newDelivery.save();
```

### Validera före massuppdatering {#validate-mass-update}

Förhandsgranska alltid berörda poster innan du utför massuppdateringar:

```javascript
// Step 1: Preview what will be updated
var previewQuery = NLWS.xtkQueryDef.create({
  queryDef: {
    schema: "nms:recipient",
    operation: "select",
    select: { node: [{expr: "@id"}, {expr: "@email"}] },
    where: { condition: [{expr: "@country = 'US' AND @blackList = 1"}] }
  }
});

var preview = previewQuery.ExecuteQuery();
var count = preview.getElementsByTagName("recipient").length;
logInfo("About to update " + count + " recipients");

// Step 2: If count looks correct, proceed with mass update
if (count > 0 && count < 10000) {
  sqlExec("UPDATE NmsRecipient SET iBlackList = 0 WHERE sCountryCode = 'US' AND iBlackList = 1");
  logInfo("Mass update completed for " + count + " recipients");
} else {
  logWarning("Update cancelled: count is " + count);
}
```

## Syntaxreferens för frågedefinition {#querydef-reference}

Fullständig struktur för objektet `queryDef`:

```javascript
{
  queryDef: {
    schema: 'nms:recipient',           // Required: target schema
    operation: 'select',                // select|get|getIfExists|count
    lineCount: 100,                    // Maximum records to return
    startLine: 0,                      // Offset for pagination
    select: {
      node: [
        {
          expr: '@id',                 // XPath expression
          alias: '@myAlias',           // Optional alias
          label: 'ID',                 // Optional label
          groupBy: 'true',             // Group by this field
          noSqlBind: 'true'            // No SQL binding on constants
        }
      ]
    },
    where: {
      condition: [
        {
          expr: '@email IS NOT NULL',  // Condition expression
          boolOperator: 'AND',         // AND|OR
          setOperator: 'EXISTS',       // EXISTS|NOT EXISTS|IN|NOT IN
          enabledIf: '',               // Enabling condition
          ignore: false,               // Ignore this condition
          sql: '',                     // Native SQL expression
          'filter-name': ''            // Predefined filter name
        }
      ]
    },
    orderBy: {
      node: [
        {
          expr: '@lastModified',       // Field to sort by
          sortDesc: 'true'             // true for DESC, false for ASC
        }
      ]
    },
    groupBy: {
      node: [
        {expr: '@country'}             // Group by field
      ]
    }
  }
}
```

## Relaterade ämnen {#related-topics}

* [Kom igång med Campaign-API:er](api.md)
* [Campaign JavaScript SDK - Query API](https://opensource.adobe.com/acc-js-sdk/xtkQueryDef.html){target="_blank"}
* [queryDef API Reference](https://experienceleague.adobe.com/developer/campaign-api/api/s-xtk-queryDef.html){target="_blank"}
* [Kampanj-JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/p-1.html){target="_blank"}
* [Arbeta med scheman](schemas.md)
* [Arbeta med frågeredigeraren](../start/query-editor.md)

