---
title: Nyckelhantering i kampanjdatabasen
description: Förstå nyckelhantering i Adobe Campaign scheman
feature: Data Model, Configuration
role: Developer
level: Intermediate, Experienced
exl-id: cf1f5cfc-172f-44ec-ac97-804d15f9d628
source-git-commit: 0f5efba364ef924447324bdd806e15e6db8d799d
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Nyckelhantering {#management-of-keys}

Varje tabell som är associerad med ett dataschema måste ha minst en nyckel för att identifiera en post i en tabell.

En nyckel deklareras från huvudelementet i dataschemat.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

En nyckel kallas för primärnyckel när den är den första i schemat som ska fyllas i, eller om den innehåller attributet `internal` inställt på true.

En nyckel kan referera till ett eller flera fält i tabellen.

**Exempel**:

* Lägga till en nyckel till e-postadressen och staden:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  Schemat som genererats:

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
     <key name="email">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="location/@city"/>    
     </key>    
  
     <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Lägga till en primär eller intern nyckel i namnfältet&quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
    </element>
  </srcSchema>
  ```

  Schemat som genererats:

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
      <key name="email">      
        <keyfield xpath="@email"/>    
      </key>  
  
      <key internal="true" name="id">      
       <keyfield xpath="@id"/>    
      </key>    
  
      <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

## Primär nyckel - identifierare{#primary-key}

I samband med en [Enterprise (FFDA)-distribution](../architecture/enterprise-deployment.md) är primärnyckeln för Adobe Campaign-tabeller ett **UUID** som genereras automatiskt av databasmotorn. Nyckelvärdet är unikt i hela databasen. Innehållet i nyckeln genereras automatiskt när posten infogas.

**Exempel**

I exemplet nedan deklarerar vi en inkrementell nyckel i källschemat:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"  autopk="true" autouuid="true">
  ...
  </element>
</srcSchema>
```

Schemat som genererats:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient"  autopk="true" autouuid="true" sqltable="CusRecipient"> 

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Förutom definitionen av nyckeln har ett numeriskt fält med namnet&quot;id&quot; lagts till i det utökade schemat för att innehålla den automatiskt genererade primärnyckeln.

>[!CAUTION]
>
>När tabellen skapas infogas automatiskt en post med primärnyckeln 0. Den här posten används för att undvika yttre kopplingar, som inte gäller för volymtabeller. Som standard initieras alla sekundärnycklar med värdet 0 så att ett resultat alltid kan returneras vid kopplingen när dataobjektet inte fylls i.
