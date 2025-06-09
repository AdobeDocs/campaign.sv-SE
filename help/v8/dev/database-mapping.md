---
title: Mappning av kampanjdatabas
description: Mappning av kampanjdatabas
feature: Data Model, Configuration
role: Developer
level: Intermediate, Experienced
exl-id: a804d164-58bf-4b15-a48e-8cf75d793668
source-git-commit: 673298a60927902bba71fd9167c5408e538f4929
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---

# Databasmappning{#database-mapping}

SQL-mappningen i vårt exempelschema ger följande XML-dokument:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Beskrivning {#description}

Schemats rotelement är inte längre **`<srcschema>`**, utan **`<schema>`**.

Detta tar oss till en annan typ av dokument, som genereras automatiskt från källschemat, som helt enkelt kallas schema. Det här schemat kommer att användas av Adobe Campaign-programmet.

SQL-namnen bestäms automatiskt utifrån elementnamn och typ.

Namnreglerna för SQL är följande:

* tabell: sammanfogning av schemanamnrymden och namnet

  I vårt exempel anges namnet på tabellen via huvudelementet i schemat i attributet **sqltable**:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* field: name of the element before by a prefix defined as by type (&#39;i&#39; for integer, &#39;d&#39; for double, &#39;s&#39; for string, &#39;ts&#39; for dates, etc.)

  Fältnamnet anges via attributet **sqlname** för varje typ **`<attribute>`** och **`<element>`**:

  ```sql
  <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>SQL-namn kan överladdas från källschemat. Det gör du genom att fylla i attributen &quot;sqltable&quot; eller &quot;sqlname&quot; för det berörda elementet.

SQL-skriptet som skapar tabellen som genereras från det utökade schemat är följande:

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL-fältbegränsningarna är följande:

* inga null-värden i numeriska fält och datumfält
* numeriska fält initieras till 0

## XML-fält {#xml-fields}

Som standard mappas alla typer av **`<attribute>`**- och **`<element>`**-element till ett SQL-fält i datarapporten. Du kan emellertid referera till det här fältet i XML i stället för SQL, vilket betyder att data lagras i ett PM-fält (&quot;mData&quot;) i tabellen som innehåller värdena för alla XML-fält. Lagringen av dessa data är ett XML-dokument som observerar schemastrukturen.

Om du vill fylla i ett fält i XML måste du lägga till attributet **xml** med värdet &quot;true&quot; till det aktuella elementet.

**Exempel**

* Flerradskommentarfält:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Beskrivning av data i HTML-format:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  Med typen html kan du lagra HTML-innehåll i en CDATA-tagg och visa en speciell HTML-redigeringskontroll i Adobe Campaign klientgränssnitt.

Med hjälp av XML-fält kan du lägga till fält utan att behöva ändra databasens fysiska struktur. En annan fördel är att du använder mindre resurser (storlek som tilldelas SQL-fält, gräns för antalet fält per tabell osv.).
