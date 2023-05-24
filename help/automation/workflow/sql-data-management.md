---
product: campaign
title: SQL-datahantering
description: Läs mer om arbetsflödesaktiviteten för SQL Data Management
feature: Workflows
exl-id: a1e08d57-0387-4802-b447-f6d9ad87072a
source-git-commit: 77ec01aaba1e50676bed57f503a9e4e8bb1fe54c
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 1%

---

# SQL-datahantering{#sql-data-management}

The **SQL Data Management** kan du skriva egna SQL-skript för att skapa och fylla i arbetstabeller.

## Förhandskrav {#prerequisites}

Innan du konfigurerar aktiviteten bör du kontrollera att följande krav är uppfyllda:

* Aktiviteten är endast tillgänglig för fjärrdatakällor.
* Det utgående schemat måste finnas i databasen och vara länkat till en FDA-databas.


## Konfigurera SQL Data Management-aktiviteten {#configuring-the-sql-data-management-activity}

1. Ange aktiviteten **[!UICONTROL Label]**.
1. Välj **[!UICONTROL External account]** som du vill använda väljer du **[!UICONTROL Outbound schema]** länkad till det här externa kontot.

   >[!CAUTION]
   >
   >Det utgående schemat är fast och kan inte redigeras.

1. Lägg till SQL-skriptet.

   >[!CAUTION]
   >
   >Det är SQL-skriptets skrivares ansvar att se till att SQL-skriptet fungerar och att dess referenser (fältnamn, etc.) är i enlighet med det utgående schemat.

   Om du vill läsa in en befintlig SQL-kod väljer du **[!UICONTROL The SQL script is contained in an entity stored in the database]** alternativ. SQL-skript måste skapas och lagras i **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** -menyn.

   I annat fall skriver eller kopierar och klistrar du in SQL-skriptet i det dedikerade området.

   ![](assets/sql_datamanagement.png)

   Med aktiviteten kan du använda följande variabler i skriptet:

   * **activity.tableName**: SQL-namn för utgående arbetstabell.
   * **task.inkommandeTransitionByName(&quot;name&quot;).tableName**: SQL-namn för arbetsregistret som medföljer den inkommande övergången som ska användas (övergången identifieras med sitt namn).

      >[!NOTE]
      >
      >Värdet (&#39;name&#39;) motsvarar värdet **[!UICONTROL Name]** från övergångsegenskaperna.

1. Om SQL-skriptet redan innehåller kommandon för att skapa en utgående arbetstabell avmarkerar du **[!UICONTROL Automatically create work table]** alternativ. I annat fall skapas en arbetstabell automatiskt när arbetsflödet körs.
1. Klicka **[!UICONTROL Ok]** för att bekräfta aktivitetskonfigurationen.

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
