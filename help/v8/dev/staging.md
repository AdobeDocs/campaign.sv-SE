---
product: Adobe Campaign
title: Mellanlagringsmekanism för kampanj-API
description: Mellanlagringsmekanism för kampanj-API
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: 99a1381a0d5cef38eb708dbe6e3e8029e6ff3953
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 2%

---

# Mellanlagringsmekanism för kampanj-API

I Campaign Cloud-databasen rekommenderas inte att enhetsanrop görs med avseende på prestanda (fördröjning och samtidighet). Grupperingsåtgärd är alltid att föredra. För att förbättra prestandan omdirigeras API:er för inmatning till den lokala databasen.

Kampanjmellanlagring är aktiverat som standard för vissa inbyggda scheman. Vi kan även aktivera det i alla anpassade scheman. Mellanlagringsmekanism i ett nötskal:

* Dataschemastrukturen dupliceras till den lokala mellanlagringstabellen
* Nya API:er som är dedikerade för dataöverföring flödar direkt in i den lokala mellanlagringstabellen. [Läs mer](new-apis.md)
* Ett schemalagt arbetsflöde utlöses varje timme och data synkroniseras tillbaka till molndatabasen. [Läs mer](../config/replication.md).

Vissa inbyggda scheman är som standard mellanlagrade, till exempel nmsSubscriptionRcp, nmsAppSubscriptionRcp och nmsRecipient.

API:er för Campaign Classic v7 är fortfarande tillgängliga men kan inte utnyttja den här nya mellanlagringsmekanismen: API-anrop flödar direkt till molndatabasen. Adobe rekommenderar att du använder den nya mellanlagringsmekanismen så mycket som möjligt för att minska det övergripande trycket och latensen i Campaign Cloud-databasen.

>[!CAUTION]
>
>* Med den här nya mekanismen är datasynkronisering för kanalalternativ, prenumerationer, avregistreringar eller mobilregistrering nu **asynkron**.
   >
   >
* Mellanlagring gäller endast för scheman som lagras i molndatabasen. Aktivera inte mellanlagring för replikerade scheman. Aktivera inte Mellanlagring för lokala scheman. Aktivera inte mellanlagring på ett mellanlagrat schema

>



## Implementeringssteg{#implement-staging}

Följ stegen nedan för att implementera Campaign-mellanlagringsmekanismen för en specifik tabell:

1. Skapa ett anpassat exempelschema i Campaign Cloud-databasen. Ingen mellanlagring har aktiverats i det här steget.

   ```
   <srcSchema _cs="Sample Table (dem)" created="YYYY-DD-MM"
           entitySchema="xtk:srcSchema" img="xtk:schema.png" label="Sample Table"
           lastModified="YYYY-DD-MM HH:MM:SS.TZ" mappingType="sql" md5="XXX"
           modifiedBy-id="0" name="sampleTable" namespace="dem" xtkschema="xtk:srcSchema">
   <element autopk="true" autouuid="true" dataSource="nms:extAccount:ffda" label="Sample Table"
           name="sampleTable">
       <attribute label="Test Col 1" length="255" name="testcol1" type="string"/>
       <attribute label="Test Col 2" length="255" name="testcol2" type="string"/>
   </element>
   </srcSchema>
   ```

   [!DNL :bulb:] Läs mer om hur du skapar anpassade scheman på  [den här sidan](create-schema.md).

1. Spara och uppdatera databasstrukturen.  [Läs mer](update-database-structure.md)

1. Aktivera mellanlagringsmekanismen i schemadefinitionen genom att lägga till parametern **autoStg=&quot;true&quot;**.

   ```
   <srcSchema _cs="Sample Table (dem)" "YYYY-DD-MM"
           entitySchema="xtk:srcSchema" img="xtk:schema.png" label="Sample Table"
           lastModified="YYYY-DD-MM HH:MM:SS.TZ" mappingType="sql" md5="XXX"
           modifiedBy-id="0" name="sampleTable" namespace="dem" xtkschema="xtk:srcSchema">
   <element autoStg="true" autopk="true" autouuid="true" dataSource="nms:extAccount:ffda" label="Sample Table"
           name="sampleTable">
       <attribute label="Test Col 1" length="255" name="testcol1" type="string"/>
       <attribute label="Test Col 2" length="255" name="testcol2" type="string"/>
   </element>
   </srcSchema>
   ```

1. Spara ändringen. Det finns ett nytt mellanlagringsschema, som är en lokal kopia av det ursprungliga schemat.

   ![](assets/staging-mechanism.png)

1. Uppdatera databasstrukturen. Mellanlagringstabellen skapas i den lokala Campaign-databasen.
