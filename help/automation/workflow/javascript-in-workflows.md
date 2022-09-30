---
product: campaign
title: Exempel på JavaScript-kod i arbetsflöden
description: De här exemplen visar hur du kan använda JavaScript-kod i ett arbetsflöde
feature: Workflows
exl-id: 3412e3de-1c88-496e-8fda-ca9fc9b18e69
source-git-commit: 2ce1ef1e935080a66452c31442f745891b9ab9b3
workflow-type: tm+mt
source-wordcount: '1756'
ht-degree: 2%

---

# Exempel på JavaScript-kod i arbetsflöden{#javascript-in-workflows}

I följande exempel visas hur du kan använda JavaScript-kod i ett arbetsflöde:

* [Skriv till databasen](#write-example)
* [Fråga databasen](#read-example)
* [Utlösa ett arbetsflöde med en statisk SOAP-metod](#trigger-example)
* [Interagera med databasen med en icke-statisk SOAP-metod](#interact-example)

[Läs mer](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) om statiska och icke-statiska SOAP-metoder.

I de här exemplen används tillägget ECMAScript för XML (E4X). Med det här tillägget kan du kombinera JavaScript-anrop och XML-mallar i samma skript.

Följ de här stegen för att testa de här exemplen:

1. Skapa ett arbetsflöde och lägg till de här aktiviteterna i arbetsflödet:
   1. Starta aktivitet
   1. JavaScript-kodaktivitet
   1. Avsluta aktivitet

   [Läs mer](build-a-workflow.md) om att bygga arbetsflöden.

1. Lägg till JavaScript-koden i en aktivitet. [Läs mer](advanced-parameters.md).
1. Spara arbetsflödet.
1. Testa exemplen:
   1. Starta arbetsflödet. [Läs mer](start-a-workflow.md).
   1. Öppna journalen. [Läs mer](monitor-workflow-execution.md#displaying-logs).

## Exempel 1: skriva till databasen{#write-example}

Om du vill skriva till databasen kan du använda den statiska `Write` på `xtk:session` schema:

1. Skapa en skrivbegäran i XML.

1. Skriv posten:

   1. Ring `Write` på `xtk:session` schema.

      >[!IMPORTANT]
      > Om du använder Adobe Campaign v8 rekommenderar vi att du använder mellanlagringsmekanismen med **Inmatning** och **Datauppdatering/borttagning** API:er för `Write` i en Snowflake-tabell. [Läs mer](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

   1. Skicka XML-koden som ett argument för skrivbegäran.

### Steg 1: skapa en skrivbegäran

Du kan lägga till, uppdatera och ta bort poster.

#### Infoga en post

På grund av `insert` är standardåtgärden, du behöver inte ange den.

Ange den här informationen som XML-attribut:

* Schemat för tabellen som ska ändras
* Tabellfälten som ska fyllas i

Exempel:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Uppdatera en post

Använd `_update` operation. .

Ange den här informationen som XML-attribut:

* Schemat för tabellen som ska ändras
* Registerfälten som ska uppdateras
* Nyckelargumentet som krävs för att identifiera den post som ska uppdateras

Exempel:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### Ta bort en post

Använd `DeleteCollection` -metod. [Läs mer](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Ange den här informationen:

* Schemat för tabellen som ska ändras
* The `where` -sats som krävs för att identifiera den post som ska uppdateras, i form av ett XML-element

Exempel:

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### Steg 2: skriva posten

Anropa den icke-statiska `Write` på `xtk:session` schema:

```javascript
xtk.session.Write(myXML)
```

Inget värde returneras för den här metoden.

Lägg till den fullständiga koden i en JavaScript-kodsaktivitet i arbetsflödet:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

I den här videon visas hur du skriver till databasen:
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Exempel 2: fråga databasen{#read-example}

Om du vill fråga databasen kan du använda den icke-statiska `xtk:queryDef` förekomstmetod:

1. Skapa en fråga i XML.
1. Skapa ett frågeobjekt.
1. Kör frågan.

### Steg 1: skapa en fråga

Ange XML-koden för en `queryDef` enhet.

Syntax:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Ange den här informationen:

* Schemat för tabellen som ska läsas
* Åtgärden
* De kolumner som ska returneras, i en `select` sats
* Villkoren i `where` sats
* filtreringsvillkoren i en `orderBy` sats

Du kan använda följande åtgärder:

| Åtgärd | Resultat |
| --- | --- |
| `select` | Noll eller fler element returneras som en samling. |
| `getIfExists` | Ett element returneras. Om det inte finns något matchande element returneras ett tomt element. |
| `get` | Ett element returneras. Om det inte finns något matchande element returneras ett fel. |
| `count` | Antalet matchande poster returneras i form av ett element med en `count` -attribut. |

Skriv `select`, `where`och `orderBy` satser som XML-element:

* `select` sats

   Ange de kolumner som ska returneras. Om du till exempel vill markera personens förnamn och efternamn skriver du följande kod:

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Med `nms:recipient` schema, element returneras i det här formuläret:

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` sats

   Om du vill ange villkor använder du en `where` -sats. Du kan till exempel välja de poster som finns i **Utbildning** kan du skriva den här koden:

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   När du kombinerar flera uttryck ska du använda den booleska operatorn i det första uttrycket. Om du till exempel vill markera alla personer som heter Isabel Garcia kan du skriva följande kod:

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` sats

   Om du vill sortera resultatmängden anger du `orderBy` -sats som ett XML-element med `sortDesc` -attribut. Om du till exempel vill sortera efternamnen i stigande ordning kan du skriva följande kod:

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Steg 2: skapa ett frågeobjekt

Om du vill skapa en enhet från XML-koden använder du `create(`*`content`*`)` metod:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Prefix the `create(`*`content`*`)` med schemat för den entitet som ska skapas.

The *`content`* argument är ett strängargument och är valfritt. Det här argumentet innehåller XML-koden som beskriver entiteten.

### Steg 3: köra frågan

Följ de här stegen:

1. Ring `ExecuteQuery` på `queryDef` enhet:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Bearbeta resultaten:
   1. Iterera över resultaten av `select` -åtgärd, med hjälp av en slingkonstruktion.
   1. Testa resultaten med `getIfExists` operation.
   1. Räkna resultaten med `count` operation.

#### Resultat av en `select` operation

Alla matchningar returneras som en samling:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Om du vill iterera igenom resultaten använder du `for each` slinga:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

Slingan innehåller en lokal mottagarvariabel. För varje mottagare som returneras i mottagarsamlingen skrivs mottagarens e-post ut. [Läs mer](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) om `logInfo` funktion.

#### Resultat av en `getIfExists` operation

Varje matchning returneras som ett element:

```xml
<recipient id="52,378,079">
```

Om det inte finns någon matchning returneras ett tomt element:

```xml
<recipient/>
```

Du kan referera till primärnyckelnoden, till exempel `@id` attribute:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Resultatet av en `get` operation

En matchning returneras som ett element:

```xml
<recipient id="52,378,079">
```

Om det inte finns någon matchning returneras ett fel.

>[!TIP]
>
>Om du vet att det finns en matchning använder du `get` operation. I annat fall använder du `getIfExists` operation. Om du använder den här bästa metoden visar felen oväntade problem. Om du använder `get` -åtgärd, använd inte `try…catch` -programsats. Problemet hanteras av arbetsflödets felhanteringsprocess.

#### Resultatet av en `count` operation

An element with the `count` attribut returneras:

```xml
<recipient count="200">
```

Om du vill använda resultatet läser du `@count` attribute:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

För `select` lägger du till den här koden i en JavaScript-kodsaktivitet i arbetsflödet:

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

På grund av `select` är standardåtgärden, du behöver inte ange den.

I den här videon visas hur du läser från databasen:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Utlösa ett arbetsflöde {#trigger-example}

Du kan starta arbetsflöden programmatiskt, till exempel i tekniska arbetsflöden eller för att bearbeta information som en användare har angett på en webbprogramsida.

Arbetsflöde som utlöser arbete genom användning av händelser. Du kan använda dessa funktioner för händelser:

* Om du vill publicera en händelse kan du använda den statiska `PostEvent` -metod. [Läs mer](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Om du vill ta emot en händelse kan du använda **[!UICONTROL External signal]** aktivitet. [Läs mer](external-signal.md).

Du kan utlösa arbetsflöden på olika sätt:

* Du kan aktivera ett arbetsflöde infogat, det vill säga från huvudskriptet för en **[!UICONTROL JavaScript code]** aktivitet.
* Du kan utlösa ett arbetsflöde när ett annat har slutförts:
   * Lägg till ett initieringsskript i **[!UICONTROL End]** det inledande arbetsflödets aktivitet.
   * Lägg till **[!UICONTROL External signal]** aktiviteten i början av målarbetsflödet.

      När det inledande arbetsflödet är klart bokförs en händelse. Den utgående övergången aktiveras och händelsevariablerna fylls i. Händelsen tas sedan emot av målarbetsflödet.

      >[!TIP]
      >
      >Ett tips är att när du lägger till ett skript i en aktivitet måste du omsluta aktivitetsnamnet med t.ex. två bindestreck `-- end --`. [Läs mer](workflow-best-practices.md) om arbetsflöden.

Syntax för `PostEvent` metod:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

I det här exemplet skickas en kort text till **signal** verksamhet **wkfExampleReceiver** arbetsflöde:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Eftersom den sista parametern är inställd på `false`, **wkfExampleReceiver** arbetsflödet aktiveras varje gång det inledande arbetsflödet slutförs.

När du startar arbetsflöden bör du tänka på följande principer:

* The `PostEvent` kommandot körs asynkront. Kommandot placeras i serverkön. Metoden returneras efter att händelsen har bokförts.
* Målarbetsflödet måste startas. Annars skrivs ett fel till loggfilen.
* Om målarbetsflödet är pausat visas `PostEvent` kommandot står i kö tills arbetsflödet återupptas.
* Den utlösta aktiviteten kräver inte att en aktivitet pågår.

I den här videon visas hur du använder statiska API-metoder:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

I den här videon visas hur du utlöser arbetsflöden:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interagera med databasen {#interact-example}

I följande exempel visas hur du utför dessa åtgärder:

* Använd `get` och `create` metoder för scheman att använda icke-statiska SOAP-metoder
* Skapa metoder som utför SQL-frågor
* Använd `write` metod för att infoga, uppdatera och ta bort poster

Följ de här stegen:

1. Definiera frågan:

   * Hämta en entitet med `create` -metoden i motsvarande schema, till exempel `xtk:workflow` schema. [Läs mer](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Använd `queryDef` metod för att skicka en SQL-fråga.

1. Kör frågan med `ExecuteQuery` -metod. [Läs mer](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Använd `for each` -slinga för att hämta resultaten.

### Syntax för `queryDef` metod med en `select` sats

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### `Create` method

#### Exempel 1: markera poster och skriva till journalen

De interna namnen på de arbetsflöden som finns i **wfExamples** -mappen är markerad. Resultaten sorteras efter internt namn, i stigande ordning och skrivs till journalen.

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### Exempel 2: ta bort poster

Förnamn, efternamn, e-postadress och ID för alla mottagare som heter Chris Smith markeras. Resultaten sorteras efter e-post, i stigande ordning och skrivs till journalen. A `delete` används för att ta bort de markerade posterna.

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### Exempel 3: markera poster och skriva till journalen

I det här exemplet används en icke-statisk metod. E-postadressen och födelseåret för alla mottagare vars information lagras i **1234** och vars e-postdomännamn börjar med adobe markeras. Resultaten sorteras efter födelsedatum i fallande ordning. Mottagarens e-post skrivs till journalen.

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### `Write` method

Du kan infoga, uppdatera och ta bort poster. Du kan använda `Write` på alla scheman i Adobe Campaign. Eftersom den här metoden är statisk behöver du inte skapa något objekt. Du kan använda följande åtgärder:

* The `update` operation
* The `insertOrUpdate` åtgärd, med `_key` argument för att identifiera den post som ska uppdateras

   Om du inte anger **Mottagare** om det finns en matchning uppdateras posten i en undermapp. Annars skapas posten i roten **Mottagare** mapp.

* The `delete` operation

>[!IMPORTANT]
> Om du använder Adobe Campaign v8 rekommenderar vi att du använder mellanlagringsmekanismen med **Inmatning** och **Datauppdatering/borttagning** API:er för `Write` i en Snowflake-tabell. [Läs mer](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

#### Exempel 1: infoga eller uppdatera en post

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### Exempel 2: ta bort poster

I det här exemplet kombineras en statisk metod och en icke-statisk metod.

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

I den här videon visas hur du använder icke-statiska API-metoder:
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

I den här videon visas ett exempel på hur en icke-statisk API-metod används i ett arbetsflöde:
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Relaterade ämnen

### API-dokumentation

* [Exempel på SOAP-anrop](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* Metoder:
   * [Skapa](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Skriv](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [funktionen logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)
