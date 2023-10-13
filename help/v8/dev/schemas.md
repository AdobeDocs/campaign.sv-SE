---
title: Arbeta med kampanjscheman
description: Kom igång med scheman
feature: Schema Extension, Configuration, Data Model
role: Developer
level: Intermediate, Experienced
exl-id: 87af72fe-6c84-4d9a-afed-015900890cce
source-git-commit: 1a0b473b005449be7c846225e75a227f6d877c88
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 4%

---

# Arbeta med scheman{#gs-ac-schemas}

Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den lyder under en grammatik som är specifik för Adobe Campaign och som kallas **schema**.

Ett schema är ett XML-dokument som är associerat med en databastabell. Den definierar datastrukturen och beskriver tabellens SQL-definition:

* Tabellens namn
* Fält
* Länkar till andra tabeller

Här beskrivs också XML-strukturen som används för att lagra data:

* Element och attribut
* Elementhierarki
* Element- och attributtyper
* Standardvärden
* Etiketter, beskrivningar och andra egenskaper.

Med scheman kan du definiera en enhet i databasen. Det finns ett schema för varje entitet.

Adobe Campaign använder datascheman för att

* Definiera hur dataobjekt i programmet kopplas till underliggande databastabeller.
* Definiera länkar mellan olika dataobjekt i programmet Campaign.
* Definiera och beskriva de enskilda fälten som ingår i varje objekt.

Om du vill få en bättre förståelse för de inbyggda tabellerna i Campaign och deras interaktion kan du läsa [det här avsnittet](datamodel.md).

>[!CAUTION]
>
>Vissa inbyggda Campaign-scheman har ett associerat schema i molndatabasen. Dessa scheman identifieras av **Xxl** och får inte ändras eller utökas.

## Syntax för scheman {#syntax-of-schemas}

Schemats rotelement är **`<srcschema>`**. Den innehåller **`<element>`** och **`<attribute>`** delelement.

Den första **`<element>`** delelement sammanfaller med entitetens rot.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Entitetens rotelement har samma namn som schemat.

![](assets/schema_and_entity.png)

The **`<element>`** -taggar definierar namnen på enhetselement. **`<attribute>`** -taggar i schemat definierar namnen på attributen i **`<element>`** -taggar som de har länkats till.

## Identifiering av ett schema {#identification-of-a-schema}

Ett dataschema identifieras med sitt namn och namnutrymme.

Med ett namnutrymme kan du gruppera en uppsättning scheman efter intresseområde. Till exempel **kus** namnutrymme används för kundspecifik konfiguration (**kunder**).

>[!CAUTION]
>
>Som standard måste namnutrymmets namn vara kortfattat och får endast innehålla tillåtna tecken i enlighet med XML-namngivningsreglerna.
>
>Identifierare får inte börja med numeriska tecken.

## Reserverade namnutrymmen {#reserved-namespaces}

Vissa namnutrymmen är reserverade för beskrivningar av de systemenheter som krävs för att Adobe Campaign-programmet ska fungera. Följande namnutrymme **får inte användas** för att identifiera ett nytt schema, i valfri kombination av versaler och gemener:

* **xxl**: reserverat för Cloud-databasscheman
* **xtk**: reserverad för plattformssystemdata
* **nl**: reserverad för programmets övergripande användning
* **nms**: reserverat för leveranser (mottagare, leverans, spårning osv.)
* **ncm**: reserverat för innehållshantering
* **temp**: reserverat för temporära scheman
* **crm**: reserverad för integrering av CRM-anslutningar

Identifieringsnyckeln för ett schema är en sträng som skapats med namnutrymmet och namnet avgränsat med ett kolon, till exempel: **nms:mottagare**.

## Skapa eller utöka kampanjscheman {#create-or-extend-schemas}

Om du vill lägga till ett fält eller något annat element i ett av de centrala dataroderna i Campaign, t.ex. mottagartabellen (nms:mottagare), måste du utöka det schemat.

![](../assets/do-not-localize/glass.png) Mer information finns i [Utöka ett schema](extend-schema.md).

Om du vill lägga till en helt ny typ av data som inte finns i Adobe Campaign (till exempel en kontraktstabell) kan du skapa ett anpassat schema direkt.

![](../assets/do-not-localize/glass.png) Mer information finns i [Skapa ett nytt schema](create-schema.md).

![](assets/schemaextension_1.png)


När du har skapat eller utökat ett schema som ska fungera i är det bästa sättet att definiera elementen för XML-innehållet i samma ordning som de visas nedan.

## Uppräkningar {#enumerations}

Uppräkningar definieras först, före huvudelementet i schemat. De gör att du kan visa värden i en lista för att begränsa vilka val användaren har för ett visst fält.

Exempel:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

När du definierar fält kan du sedan använda den här uppräkningen så här:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>Du kan också använda användarhanterade uppräkningar (vanligtvis under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) för att ange värden för ett visst fält. Detta är effektivt globala uppräkningar och ett bättre alternativ om uppräkningen kan användas utanför det specifika schema som du arbetar i.

<!--
## Index {#index} 

In the context of a [FDA Snowflake deployment](../architecture/fda-deployment.md), you need to declare indexes. Indexes are the first elements declared in the main element of the schema. 

They can be unique or not, and reference one or more fields.

Examples:

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

The **xpath** attribute points to the field in your schema that you wish to index.

>[!IMPORTANT]
>
>It is important to remember that the SQL query read performance gains provided by indexes also come with a performance hit on writing records. The indexes should therefore be used with precaution.

For more on indexes, refer to the [Indexed fields](database-mapping.md#indexed-fields) section.

-->

## Tangenter {#keys}

Alla tabeller måste ha minst en nyckel och ofta etableras de automatiskt i schemats huvudelement med hjälp av **autopk** attribut inställt på **true**.

Dessutom, när det gäller [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), använder du **@autouuid** och ange **true**.

Primärnyckeln kan också definieras med **internal** -attribut.

Exempel:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

I det här exemplet ska du inte låta **@autopk** eller **@autouuid** för att skapa en standardprimärnyckel med namnet&quot;id&quot; anger vi vår egen primärnyckel för&quot;houseid&quot;.

>[!CAUTION]
>
>När du skapar ett nytt schema eller under ett schematillägg måste du behålla samma sekvensvärde för primärnyckeln (@pkSequence) för hela schemat.

![](../assets/do-not-localize/glass.png) Läs mer om tangenter i [det här avsnittet](database-mapping.md#management-of-keys).

## Attribut (fält) {#attributes--fields-}

Med attribut kan du definiera fälten som utgör dataobjektet. Du kan använda **[!UICONTROL Insert]** i verktygsfältet för schemautgåvor om du vill släppa tomma attributmallar i XML-filen där markören finns. Läs mer i [det här avsnittet](create-schema.md).

![](assets/schemaextension_2.png)

Den fullständiga listan med attribut finns i `<attribute>` elementavsnitt i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/schema-reference/elements-attributes/attribute.html#content-model). Här är några av de vanligaste attributen: **@advanced**, **@dataPolicy**, **@default**, **@desc**, **@enum**, **@expr**, **@label**, **@length**, **@name**, **@notNull**, **@required**, **@ref**, **@xml**, **@type**.

![](../assets/do-not-localize/book.png) Mer information om respektive attribut finns i attributbeskrivningen i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/schema-reference/elements-attributes/schema-introduction.html#configuring-campaign-classic).

### Exempel {#examples}

Exempel på hur du definierar ett standardvärde:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Exempel på hur du använder ett gemensamt attribut som mall för ett fält som också är markerat som obligatoriskt:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Exempel på ett beräknat fält som är dolt med **@advanced** attribute:

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Exempel på ett XML-fält som också lagras i ett SQL-fält och som har ett **@dataPolicy** -attribut.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!CAUTION]
>
>Även om de flesta attribut är länkade enligt en 1-1-kardinalitet till ett fysiskt fält i databasen är detta inte fallet för XML-fälten eller de beräknade fälten.\
>Ett XML-fält sparas i ett PM-fält (&quot;mData&quot;) i tabellen.\
>Ett beräknat fält skapas dock dynamiskt varje gång en fråga startas, och därför finns det bara i det aktuella lagret.

## Länkar {#links}

Länkar är några av de sista elementen i huvudelementet i schemat. De definierar hur alla olika scheman i din instans relaterar till varandra.

Länkarna deklareras i schemat som innehåller **sekundärnyckel** för den tabell som den är länkad till.

Det finns tre typer av kardinalitet: 1-1, 1-N och N-N. Det är typen 1-N som används som standard.

### Exempel {#examples-1}

Ett exempel på en 1-N-länk mellan mottagartabellen (ett schema som inte är installerat) och en tabell med anpassade transaktioner:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Ett exempel på en 1-1-länk mellan det anpassade schemat &quot;Car&quot; (i &quot;cus&quot;-namnutrymmet) och mottagartabellen:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Exempel på en extern koppling mellan mottagartabellen och en adresstabell som baseras på e-postadressen och inte på en primärnyckel:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Här motsvarar &quot;xpath-dst&quot; primärnyckeln i målschemat och &quot;xpath-src&quot; den externa nyckeln i källschemat.

## Granskningskedja {#audit-trail}

Ett användbart element som du kanske vill ta med längst ned i schemat är ett spårningselement (granskningsspår).

Använd exemplet nedan för att inkludera fält som relaterar till datumet då data skapades, användaren som skapade data, datumet och författaren till den senaste ändringen för alla data i tabellen:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Uppdatera databasstrukturen {#updating-the-database-structure}

När ändringarna är klara och sparade måste alla ändringar som kan påverka SQL-strukturen tillämpas på databasen. Använd databasuppdateringsassistenten för att göra detta.

![](assets/schemaextension_3.png)

Mer information om detta finns i [det här avsnittet](update-database-structure.md).

>[!NOTE]
>
>Om ändringarna inte påverkar databasstrukturen behöver du bara generera om scheman. Det gör du genom att markera de scheman som ska uppdateras, högerklicka och välja **[!UICONTROL Actions > Regenerate selected schemas...]**.
