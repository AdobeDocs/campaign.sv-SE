---
product: campaign
title: SQL-datahantering
description: Läs mer om arbetsflödesaktiviteten för SQL Data Management
feature: Workflows
Role: User
level: Experienced
exl-id: a1e08d57-0387-4802-b447-f6d9ad87072a
source-git-commit: 64b24d7a72c2cdee841ea301ca46b0204f1fccaa
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 1%

---

# SQL-datahantering{#sql-data-management}

Med aktiviteten **SQL Data Management** kan du skriva egna SQL-skript för att skapa och fylla i arbetsregister.

## Förhandskrav {#prerequisites}

Innan du konfigurerar aktiviteten bör du kontrollera att följande krav är uppfyllda:

* Aktiviteten är endast tillgänglig för fjärrdatakällor.
* Det utgående schemat måste finnas i databasen och vara länkat till en FDA-databas.


## Konfigurera SQL Data Management-aktiviteten {#configuring-the-sql-data-management-activity}

1. Ange aktiviteten **[!UICONTROL Label]**.
1. Markera **[!UICONTROL External account]** som ska användas och markera sedan **[!UICONTROL Outbound schema]** som är länkad till det här externa kontot.

   >[!CAUTION]
   >
   >Det utgående schemat är fast och kan inte redigeras.

1. Lägg till SQL-skriptet.

   >[!CAUTION]
   >
   >Det är SQL-skriptskrivarens ansvar att se till att SQL-skriptet fungerar och att dess referenser (fältnamn, osv.) följer det utgående schemat.

   Om du vill läsa in en befintlig SQL-kod väljer du alternativet **[!UICONTROL The SQL script is contained in an entity stored in the database]**. SQL-skript måste skapas och lagras på menyn **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** .

   I annat fall skriver eller kopierar och klistrar du in SQL-skriptet i det dedikerade området.

   ![](assets/sql_datamanagement.png)

   Med aktiviteten kan du använda följande variabler i skriptet:

   * **activity.tableName**: SQL-namn för utgående arbetstabell.
   * **task.inkommandeTransitionByName(&#39;name&#39;).tableName**: SQL-namnet på arbetstabellen som medföljer den inkommande övergången som ska användas (övergången identifieras med sitt namn).

     >[!NOTE]
     >
     >Värdet (&#39;name&#39;) motsvarar fältet **[!UICONTROL Name]** i övergångsegenskaperna.

1. Om SQL-skriptet redan innehåller kommandon för att skapa en utgående arbetstabell avmarkerar du alternativet **[!UICONTROL Automatically create work table]**. I annat fall skapas en arbetstabell automatiskt när arbetsflödet körs.
1. Klicka på **[!UICONTROL Ok]** för att bekräfta aktivitetskonfigurationen.

Aktiviteten är nu konfigurerad. Den är klar att köras i arbetsflödet.

>[!CAUTION]
>
>När aktiviteten har utförts är antalet utgående övergångsposter endast vägledande. Det kan variera beroende på SQL-skriptets komplexitet.
>  
>Om aktiviteten startas om körs hela skriptet från början, oavsett dess körningsstatus.

## SQL-skriptexempel {#sql-script-samples}

>[!NOTE]
>
>Skriptexemplen i det här avsnittet ska köras under PostgreSQL.

Med skriptet nedan kan du skapa en arbetstabell och infoga data i samma arbetstabell:

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

Nedan kan du utföra en CTAS-åtgärd (CREATE TABLE AS SELECT) och skapa ett arbetstabellindex:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

Nedanför skript kan du sammanfoga två arbetsregister:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```
