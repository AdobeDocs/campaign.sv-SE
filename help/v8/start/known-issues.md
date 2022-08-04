---
title: Kända fel i Campaign v8
description: Kända fel i den senaste Campaign-versionen
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 89a4ab6c-de8e-4408-97d2-8b8e574227f9
source-git-commit: 75472fd428ec218de0c48f02caf859f8ff40bdc6
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# Kända fel{#known-issues}

På den här sidan visas kända fel som identifierats i **senaste Campaign v8-utgåvan**. Dessutom listas begränsningar som följer med Campaign v8 [på den här sidan](ac-guardrails.md).


>[!NOTE]
>
>Adobe publicerar den här listan över kända problem efter eget gottfinnande. Det baseras på antalet kundrapporter, allvarlighetsgraden och möjligheten att komma runt problemet. Om ett problem som du stöter på inte visas kanske det inte uppfyller villkoren för publicering på den här sidan.

<!--
## Change Data Source activity issue #1 {#issue-1}

### Description{#issue-1-desc}

The **Change Data Source** activity is failing when transfering data from Campaign local database to Snowflake cloud database. When switching directions, the activity can generate issues.

### Reproduction steps{#issue-1-repro}

1. Connect to the client console and create a workflow.
1. Add a **Query** activity and a **Change Data Source** activity.
1. Define a query on the **email**, which is a string.
1. Run the workflow and right-click the transition to view the population: the email records are displayed replaced by `****`.
1. Check the workflow logs: the **Change Data Source** activity interprets these records as numeric values.

### Error message{#issue-1-error}

```sql
04/13/2022 10:00:18 AM              Executing change data source 'Ok' (step 'Change Data Source')
04/13/2022 10:00:18 AM              Starting 1 connection(s) on pool 'nms:extAccount:ffda tractorsupply_mkt_stage8' (Snowflake, server='adobe-acc_tractorsupply_us_west_2_aws.snowflakecomputing.com', login='tractorsupply_stage8_MKT:tractorsupply_stage8')
04/13/2022 10:00:26 AM              ODB-240000 ODBC error: {*}Numeric value '{*}******{*}{{*}}' is not recognized\{*}   File 'wkf1285541_13_1_0_47504750#458318uploadPart0.chunk.gz', line 1, character 10140   Row 279, column "WKF1285541_13_1_0"["BICUST_ID":1]   If you would like to continue loading when a
04/13/2022 10:00:26 AM              n error is encountered, use other values such as 'SKIP_FILE' or 'CONTINUE' for the ON_ERROR option. For more information on loading options, please run 'info loading_data' in a SQL client. SQLState: 22018
04/13/2022 10:00:26 AM              WDB-200001 SQL statement 'COPY INTO wkf1285541_13_1_0 (SACTIVE, SADDRESS1, SADDRESS2, BICUST_ID, SEMAIL) FROM ( SELECT $1, $2, $3, $4, $5 FROM $$@BULK_wkf1285541_13_1_0$$) FILE_FORMAT = ( TYPE = CSV RECORD_DELIMITER = '\x02' FIELD_DELIMITER = '\x01' FIEL
04/13/2022 10:00:26 AM              D_OPTIONALLY_ENCLOSED_BY = 'NONE') ON_ERROR = ABORT_STATEMENT PURGE = TRUE' could not be executed.
```

### Workaround{#issue-1-workaround}

To have the data transfered from Snowflake cloud database to Campaign local database and back to Snowflake, you must use two different **Change Data Source** activities.

### Internal reference{#issue-1-ref}

Reference: NEO-45549 
-->


## Ändra aktivitetsproblem för datakälla {#issue-2}

### Beskrivning{#issue-2-desc}

När du matar in data i molndatabasen med en Campaign **Fråga** och **Ändra datakälla** -aktiviteten misslyckas processen när det finns ett omvänt snedstreck i data. Källsträngen escape-konverteras inte och data bearbetas inte korrekt på Snowflake.

Det här problemet uppstår bara om det omvända snedstrecket finns i slutet av strängen, till exempel: `Barker\`.


### Återgivningssteg{#issue-2-repro}

1. Anslut till klientkonsolen och skapa ett arbetsflöde.
1. Lägg till en **Fråga** och konfigurera den.
1. Välj data med de egenskaper som beskrivs ovan.
1. Lägg till en **Ändra datakälla** och konfigurera den för att välja molndatabasen i Snowflake.
1. Kör arbetsflödet och kontrollera arbetsflödesloggarna för att se felet.


### Felmeddelande{#issue-2-error}

```sql
Error:
04/21/2022 4:01:58 PM     loading when an error is encountered, use other values such as 'SKIP_FILE' or 'CONTINUE' for the ON_ERROR option. For more information on loading options, please run 'info loading_data' in a SQL client. SQLState: 22000
04/21/2022 4:01:58 PM    ODB-240000 ODBC error: String '100110668547' is too long and would be truncated   File 'wkf1656797_21_1_3057430574#458516uploadPart0.chunk.gz', line 1, character 0   Row 90058, column "WKF1656797_21_1"["SCARRIER_ROUTE":13]   If you would like to continue
```

### Tillfällig lösning{#issue-2-workaround}

Tillfällig lösning är att exkludera data som innehåller omvänt snedstreck i slutet av strängen eller att ta bort dem från källfilen.

<!--
As a workaround, export the files with double quotes around the problematic values (like `Barker\`) and include a file format option `FIELD_OPTIONALLY_ENCLOSED_BY = '"'`.
-->

### Intern referens{#issue-2-ref}

Referens: NEO-45549


## Det gick inte att överföra filen på servern med datainläsningsaktiviteten (fil) {#issue-3}

### Beskrivning{#issue-3-desc}

När en fil överförs på Campaign-servern med en **Inläsning av data (fil)** stannar processen vid 100 % men aldrig avslutas.

### Återgivningssteg{#issue-3-repro}

1. Anslut till klientkonsolen och skapa ett arbetsflöde.
1. Lägg till en **Inläsning av data (fil)** och konfigurera den.
1. Välj **Överför på servern** alternativ.
1. Välj filen på den lokala datorn,
1. Klicka **Överför**


### Felmeddelande{#issue-3-error}

Processen tar aldrig slut.

### Tillfällig lösning{#issue-3-workaround}

Du kan lösa problemet genom att använda en äldre klientkonsol. Sedan kan du överföra filen till servern.

Som kampanjadministratör kan du hämta klientkonsolen Campaign v8.3.1 i [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?1_group.propertyvalues.property=.%2Fjcr%3aContent%2Fmetadata%2FDc%3Aversion&amp;1_group.propertyvalues.operation=equals&amp;1_group.propertyvalues.0_values=target-version%3AcCampaign%2F8&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;order.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=4){target=&quot;_blank&quot;}.

Lär dig hur du får åtkomst till Adobe programvarudistribution [på den här sidan](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html){target=&quot;_blank&quot;}.

Lär dig hur du uppgraderar din klientkonsol [på den här sidan](connect.md)

### Intern referens{#issue-3-ref}

Referens: NEO-47269
