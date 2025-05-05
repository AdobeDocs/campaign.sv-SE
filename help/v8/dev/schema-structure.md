---
title: Struktur för kampanjschema
description: Struktur för kampanjschema
feature: Schema Extension, Configuration, Data Model
role: Developer
level: Intermediate, Experienced
exl-id: 9c4a9e71-3fc8-4b4e-8782-0742bbeaf426
source-git-commit: 69ff08567f3a0ab827a118a089495fc75bb550c5
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 1%

---

# Schemastruktur{#schema-structure}

Grundstrukturen för en `<srcschema>` är följande:

```
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

XML-dokumentet i ett dataschema måste innehålla rotelementet **`<srcschema>`** med attributen **name** och **namespace** för att schemanamnet och dess namnområde ska kunna fyllas i.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Låt oss använda följande XML-innehåll för att illustrera strukturen i ett dataschema:

```
<recipient email="John.doe@aol.com" created="AAAA/DD/MM" gender="1"> 
  <location city="London"/>
</recipient>
```

Med motsvarande dataschema:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## Beskrivning {#description}

Startpunkten för schemat är dess huvudelement. Det är enkelt att identifiera eftersom det har samma namn som schemat och bör vara underordnat rotelementet. Beskrivningen av innehållet börjar med det här elementet.

I det här exemplet representeras huvudelementet av följande rad:

```
<element name="recipient">
```

Med elementen **`<attribute>`** och **`<element>`** som följer huvudelementet kan du definiera plats och namn för dataobjekten i XML-strukturen.

I vårt exempelschema är följande:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Följande regler måste följas:

* Varje **`<element>`** och **`<attribute>`** måste identifieras med namn via attributet **name**.

  >[!CAUTION]
  >
  >Elementets namn ska vara kortfattat, helst på engelska, och endast innehålla tillåtna tecken i enlighet med XML-reglerna för namngivning.

* Endast **`<element>`** element kan innehålla **`<attribute>`** element och **`<element>`** element i XML-strukturen.
* Ett **`<attribute>`**-element måste ha ett unikt namn i en **`<element>`**.
* Du bör använda **`<elements>`** i flerradiga datasträngar.

## Datatyper {#data-types}

Datatypen anges via attributet **type** i elementen **`<attribute>`** och **`<element>`**.

En detaljerad lista finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/schema-reference/elements-attributes/schema-introduction.html?lang=sv-SE#configuring-campaign-classic){target="_blank"}.

När det här attributet inte är ifyllt är **string** standarddatatypen om inte elementet innehåller underordnade element. Om den gör det används den bara för att strukturera elementen hierarkiskt (**`<location>`** element i vårt exempel).

Följande datatyper stöds i scheman:

* **sträng**: teckensträng. Exempel: förnamn, stad osv.

  Storleken kan anges via attributet **length** (valfritt, standardvärde 255).

* **boolesk**: Booleskt fält. Exempel på möjliga värden: true/false, 0/1, yes/no, osv.
* **byte**, **short**, **long**: heltal (1 byte, 2 byte, 4 byte). Exempel: ålder, kontonummer, antal poäng osv.
* **double**: flyttal med dubbel precision. Exempel: ett pris, en kurs, osv.
* **date**, **datetime**: datum och datum + gånger. Exempel: födelsedatum, inköpsdatum osv.
* **datetimenotz**: datum + tid utan tidszonsdata.
* **tidsintervall**: varaktighet. Exempel: tjänsteålder.
* **PM**: långa textfält (flera rader). Exempel: en beskrivning, en kommentar, osv.
* **uid**: Uniqueidentifier-fält

  >[!NOTE]
  >
  >Om du vill innehålla ett **uid**-fält måste funktionen &quot;newuid()&quot; läggas till och slutföras med standardvärdet.

Här är vårt exempelschema med de angivna typerna:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

## Egenskaper {#properties}

Elementen **`<elements>`** och **`<attributes>`** i dataschemat kan berikas med olika egenskaper. Du kan fylla i en etikett för att beskriva det aktuella elementet.

### Etiketter och beskrivningar {#labels-and-descriptions}

* Med egenskapen **label** kan du ange en kort beskrivning.

  >[!NOTE]
  >
  >Etiketten är associerad med instansens aktuella språk.

  **Exempel**:

  ```
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  Etiketten visas i indataformuläret för Adobe Campaign klientkonsol:

  ![](assets/schema_label.png)

* Med egenskapen **desc** kan du ange en lång beskrivning.

  Beskrivningen visas från indataformuläret i statusfältet i huvudfönstret i Adobe Campaign klientkonsol.

  >[!NOTE]
  >
  >Beskrivningen är associerad med instansens aktuella språk.

  **Exempel**:

  ```
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### Standardvärden {#default-values}

Med egenskapen **default** kan du definiera ett uttryck som returnerar ett standardvärde när innehåll skapas.

Värdet måste vara ett uttryck som är kompatibelt med XPath-språket. Mer information om detta finns i [det här avsnittet](#reference-with-xpath).

**Exempel**:

* Aktuellt datum: **default=&quot;GetDate()&quot;**
* Räknare: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  I det här exemplet skapas standardvärdet med hjälp av sammanfogningen av en sträng och anropet av funktionen **CounterValue** med ett kostnadsfritt räknarnamn. Det returnerade talet ökas med ett steg vid varje infogning.

  >[!NOTE]
  >
  >I Adobe Campaign klientkonsol används noden **[!UICONTROL Administration>Counters]** för att hantera räknare.

Om du vill länka ett standardvärde till ett fält kan du använda `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>`: gör att du kan förifylla fältet med ett standardvärde när du skapar entiteter. Värdet kommer inte att vara ett standard-SQL-värde.

`<sqldefault>`: ger dig ett mervärde när du skapar ett fält. Värdet visas som ett SQL-resultat. Under en schemauppdatering påverkas bara de nya posterna av det här värdet.

### Uppräkningar {#enumerations}

#### Kostnadsfri uppräkning {#free-enumeration}

Med egenskapen **userEnum** kan du definiera en kostnadsfri uppräkning för att memorera och visa de värden som anges i det här fältet. Syntaxen är följande:

**userEnum=&quot;uppräkningens namn&quot;**

Det namn som anges för uppräkningen kan väljas fritt och delas med andra fält.

Dessa värden visas i en nedrullningsbar lista från indataformuläret:

![](assets/schema_user_enum.png)

>[!NOTE]
>
>I Adobe Campaign klientkonsol används noden **[!UICONTROL Administration > Enumerations]** för att hantera uppräkningar.

#### Ange uppräkning {#set-enumeration}

Med egenskapen **enum** kan du definiera en fast uppräkning som används när listan med möjliga värden är känd i förväg.

Attributet **enum** refererar till definitionen för en uppräkningsklass som är ifylld i schemat utanför huvudelementet.

Uppräkningar gör att användaren kan välja ett värde i en nedrullningsbar lista i stället för att ange värdet i ett vanligt inmatningsfält:

![](assets/schema_enum.png)

Exempel på en uppräkningsdeklaration i dataschemat:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

En uppräkning deklareras utanför huvudelementet via elementet **`<enumeration>`**.

Uppräkningsegenskaperna är följande:

* **baseType**: typ av data som är associerade med värdena,
* **label**: beskrivning av uppräkningen,
* **namn**: uppräkningens namn,
* **standard**: uppräkningens standardvärde.

Uppräkningsvärdena deklareras i elementet **`<value>`** med följande attribut:

* **name**: namnet på värdet som lagras internt,
* **label**: etikett som visas via det grafiska gränssnittet.

#### dbenum-uppräkning {#dbenum-enumeration}

* Med egenskapen **dbenum** kan du definiera en uppräkning vars egenskaper liknar egenskaperna för egenskapen **enum**.

  Attributet **name** lagrar dock inte värdet internt, utan lagrar en kod som gör att du kan utöka de berörda tabellerna utan att ändra deras schema.

  Värdena definieras via noden **[!UICONTROL Administration>Enumerations]**.

  Den här uppräkningen används till exempel för att ange kampanjens karaktär.

  ![](assets/schema_dbenum.png)

### Exempel {#example}

Här är vårt exempelschema med egenskaperna ifyllda:

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## Samlingar {#collections}

En samling är en lista med element med samma namn och samma hierarkiska nivå.

Med attributet **unbound** med värdet &quot;true&quot; kan du fylla i ett samlingselement.

**Exempel**: definition av samlingselementet **`<group>`** i schemat.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Med projektion av XML-innehållet:

```
<group label="Group1"/>
<group label="Group2"/>
```

## Referens med XPath {#reference-with-xpath}

XPath-språket används i Adobe Campaign för att referera till ett element eller attribut som tillhör ett dataschema.

XPath är en syntax som gör att du kan hitta en nod i trädet i ett XML-dokument.

Elementen anges med sitt namn och attributen anges med namnet före tecknet&quot;@&quot;.

**Exempel**:

* **@email**: markerar e-postmeddelandet,
* **location/@city**: väljer attributet &quot;city&quot; under elementet **`<location>`**
* **../@email**: väljer e-postadressen från det överordnade elementet för det aktuella elementet
* **group`[1]/@label`**: markerar attributet &quot;label&quot; som är underordnat det första **`<group>`**-samlingselementet
* **group`[@label='test1']`**: markerar attributet &quot;label&quot; som är underordnat elementet **`<group>`** och innehåller värdet &quot;test1&quot;

>[!NOTE]
>
>En ytterligare begränsning läggs till när banan korsar ett underelement. I det här fallet måste följande uttryck placeras inom hakparenteser:
>
>* **location/@city** är inte giltig. Använd **`[location/@city]`**
>* **`[@email]`** och **@email** är likvärdiga
>

Det går också att definiera komplexa uttryck, till exempel följande aritmetiska operationer:

* **@kön+1**: lägger till 1 i innehållet i attributet **kön**,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: konstruerar en sträng genom att ta värdet för e-postadressen som lagts till i skapandedatumet mellan parenteser (för strängtypen sätter du konstanten inom citattecken).

Funktioner på hög nivå har lagts till i uttrycken för att berika detta språks potential.

Du kommer åt listan över tillgängliga funktioner via en uttrycksredigerare i Adobe Campaign klientkonsol:

![](assets/schema_function.png)

**Exempel**:

* **GetDate()**: returnerar aktuellt datum
* **Year(@created)**: returnerar året för datumet som finns i attributet&quot;created&quot;.
* **GetEmailDomain(@email)**: returnerar domänen för e-postadressen.

## Skapa en sträng via beräkningssträngen {#building-a-string-via-the-compute-string}

En **beräkningssträng** är ett XPath-uttryck som används för att konstruera en sträng som representerar en post i en tabell som är associerad med schemat. **Beräkningssträngen** används främst i det grafiska gränssnittet för att visa etiketten för en markerad post.

**Beräkningssträngen** definieras via elementet **`<compute-string>`** under huvudelementet i dataschemat. Ett **expr**-attribut innehåller ett XPath-uttryck för att beräkna visningen.

**Exempel**: beräkningssträng för mottagartabellen.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Resultat av den beräknade strängen för en mottagare: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Om schemat inte innehåller någon beräkningssträng fylls en beräkningssträng i som standard med värdena för schemats primärnyckel.
