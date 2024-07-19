---
title: Länkhantering i kampanjscheman
description: Länkhantering i Adobe Campaign-scheman
feature: Data Model, Configuration
role: Developer
level: Intermediate, Experienced
exl-id: f7047c6e-f045-4534-b117-311dd90dd92b
source-git-commit: 0f5efba364ef924447324bdd806e15e6db8d799d
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 0%

---

# Länkhantering {#links--relation-between-tables}

En länk beskriver kopplingen mellan en tabell och en annan.

Olika typer av föreningar, även kallade kardinaliteter, listas nedan.

* Kardinalitet 1-1: en förekomst av källtabellen kan ha högst en motsvarande förekomst av måltabellen.
* Kardinalitet 1-N: en förekomst av källtabellen kan ha flera motsvarande förekomster av måltabellen, men en förekomst av måltabellen kan ha högst en motsvarande förekomst av källtabellen.
* Kardinalitet N-N: en förekomst av källtabellen kan ha flera motsvarande förekomster av måltabellen och vice versa.

I användargränssnittet representeras kardinalerna med en specifik ikon.

För kopplingsrelationer med en kampanjtabell/databas:

* ![](assets/do-not-localize/join_with_campaign11.png) : Kardinalitet 1-1. Till exempel mellan en mottagare och en aktuell order. En mottagare kan bara vara relaterad till en förekomst av den aktuella ordertabellen åt gången.
* ![](assets/do-not-localize/externaljoin11.png) : Kardinalitet 1-1, extern koppling. Till exempel mellan en mottagare och deras land. En mottagare kan bara vara relaterad till en förekomst av registerlandet. Innehållet i landstabellen sparas inte.
* ![](assets/do-not-localize/join_with_campaign1n.png) : Kardinalitet 1-N. Till exempel mellan en mottagare och prenumerationstabellen. En mottagare kan vara relaterad till flera förekomster i prenumerationstabellen.

För anslutningsrelationer med FDA (Federated Database Access):

* ![](assets/do-not-localize/join_fda_11.png) : Kardinalitet 1-1
* ![](assets/do-not-localize/join_fda_1m.png) : Kardinalitet 1-N

Mer information om FDA-tabeller finns i [Åtkomst till en extern databas](../connect/fda.md).

En länk måste deklareras i schemat som innehåller sekundärnyckeln för tabellen som är länkad via huvudelementet:

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Länkarna följer följande regler:

* Definitionen av en länk anges på en **länk**-typ **`<element>`** med följande attribut:

   * **namn**: länkens namn från källtabellen
   * **mål**: målschemats namn
   * **etikett**: länketikett
   * **revLink** (valfritt): namnet på den omvända länken från målschemat (dras automatiskt som standard)
   * **integritet** (valfritt): källtabellens referensintegritet till måltabellens förekomst.
Möjliga värden är:

      * **define**: Det går att ta bort källförekomsten om den inte längre refereras av en målförekomst
      * **normal**: om du tar bort källförekomsten initieras nycklarna för länken till målförekomsten (standardläge), den här typen av integritet initierar alla sekundärnycklar
      * **egen**: Om du tar bort källförekomsten tas målförekomsten bort
      * **owncopy**: samma som **own** (vid borttagning) eller dubblerar förekomsterna (vid duplicering)
      * **neutral**: inget specifikt beteende

   * **revIntegrity** (valfritt): integritet i målschemat (valfritt, &quot;normal&quot; som standard)
   * **revCardinality** (valfritt): med värdet &quot;single&quot; fylls kardinaliteten med typen 1-1 (1-N som standard)
   * **externalJoin** (valfritt): tvingar den yttre kopplingen
   * **revExternalJoin** (valfritt): tvingar det yttre hörnet på den omvända länken

* En länk refererar till ett eller flera fält från källtabellen till måltabellen. Fälten som utgör sammanfogningen ( `<join>`-elementet) behöver inte fyllas i eftersom de automatiskt dras av som standard med målschemats interna nyckel.
* Ett index läggs automatiskt till i länkens sekundärnyckel i det utökade schemat.
* En länk består av två halvlänkar, där den första deklareras från källschemat och den andra skapas automatiskt i målschemats utökade schema.
* En join kan vara en yttre join om attributet **externalJoin** läggs till, med värdet &quot;true&quot; (stöds i PostgreSQL).

>[!NOTE]
>
>Som standard är länkar de element som deklarerats i slutet av schemat.

## Exempel: omvänd länk {#example-1}

I exemplet nedan deklarerar vi en 1-N-relation till schematabellen &quot;cus:company&quot;:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Schemat som genererats:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

Länkdefinitionen kompletteras av fälten som utgör kopplingen, dvs. primärnyckeln med XPath (&quot;@id&quot;) i målschemat och sekundärnyckeln med XPath (&quot;@company-id&quot;) i schemat.

Sekundärnyckeln läggs automatiskt till i ett element som använder samma egenskaper som det associerade fältet i måltabellen, med följande namnkonvention: namnet på målschemat följt av namnet på det associerade fältet (&quot;företag-id&quot; i vårt exempel).

Utökat schema för målet (&quot;cus:company&quot;):

```sql
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

En omvänd länk till tabellen&quot;cus:mottagare&quot; lades till med följande parametrar:

* **name**: dras automatiskt från namnet på källschemat (kan framtvingas med attributet &quot;revLink&quot; i länkdefinitionen i källschemat)
* **revLink**: namn på omvänd länk
* **mål**: nyckel för länkat schema (&quot;cus:mottagare&quot;-schema)
* **obunden**: länken deklareras som ett samlingselement för en 1-N-kardinalitet (som standard)
* **integritet**:&quot;define&quot; som standard (kan framtvingas med attributet&quot;revIntegrity&quot; i länkdefinitionen i källschemat).

## Exempel: enkel länk {#example-2}

I det här exemplet deklarerar vi en länk till schematabellen &quot;nms:address&quot;. Kopplingen är en yttre koppling och fylls i explicit med mottagarens e-postadress och fältet @address i den länkade tabellen (&quot;nms:address&quot;).

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

## Exempel: unik kardinalitet {#example-3}

I det här exemplet skapar vi en 1-1-relation till schematabellen&quot;cus:extension&quot;:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## Exempel: länk till en mapp {#example-4}

I det här exemplet deklarerar vi en länk till en mapp (&quot;xtk:folder&quot;-schema):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Standardvärdet returnerar identifieraren för den första giltiga parametertypfilen som anges i funktionen &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

## Exempel: skapa en nyckel för en länk {#example-5}

I det här exemplet skapar vi en nyckel för en länk (&quot;företag&quot; till&quot;cus:company&quot;-schema) med attributet **xlink** och ett fält i tabellen (&quot;email&quot;):

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Schemat som genererats:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

Definitionen av namnnyckeln&quot;companyEmail&quot; utökades med sekundärnyckeln för länken&quot;company&quot;. Den här nyckeln genererar ett unikt index för båda fälten.
