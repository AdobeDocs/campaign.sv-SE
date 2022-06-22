---
title: Kända fel i Campaign v8
description: Kända fel i den senaste Campaign-versionen
feature: Overview
role: Data Engineer
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 2705e9b23f9f8a61f799381434f7e94a226de1b9
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Kända fel{#known-issues}

På den här sidan visas kända fel som identifierats i **senaste Campaign v8-utgåvan**. Dessutom listas begränsningar som följer med Campaign v8 [på den här sidan](known-limitations.md).


>[!NOTE]
>
>Adobe publicerar den här listan över kända problem efter eget gottfinnande. Det baseras på antalet kundrapporter, allvarlighetsgraden och möjligheten att komma runt problemet. Om ett problem som du stöter på inte visas kanske det inte uppfyller villkoren för publicering på den här sidan.

## Ändra aktivitetsproblem för datakälla {#issue-1}

### Beskrivning{#issue-1-desc}

The **Ändra datakälla** aktiviteten misslyckas när data överförs från Campaign-databasen till molndatabasen i Snowflake. När du byter riktning kan aktiviteten ge upphov till problem.

### Återgivningssteg{#issue-1-repro}

1. Anslut till klientkonsolen och skapa ett arbetsflöde.
1. Lägg till en **Fråga** aktivitet och **Ändra datakälla** aktivitet.
1. Definiera en fråga på **e-post**, som är en sträng.
1. Kör arbetsflödet och högerklicka på övergången för att visa populationen: e-postposterna visas ersatta med `****`.
1. Kontrollera arbetsflödesloggarna: den **Ändra datakälla** -aktiviteten tolkar dessa poster som numeriska värden.

### Felmeddelande{#issue-1-error}

```sql
04/13/2022 10:00:18 AM              Executing change data source 'Ok' (step 'Change Data Source')
04/13/2022 10:00:18 AM              Starting 1 connection(s) on pool 'nms:extAccount:ffda tractorsupply_mkt_stage8' (Snowflake, server='adobe-acc_tractorsupply_us_west_2_aws.snowflakecomputing.com', login='tractorsupply_stage8_MKT:tractorsupply_stage8')
04/13/2022 10:00:26 AM              ODB-240000 ODBC error: {*}Numeric value '{*}******{*}{{*}}' is not recognized\{*}   File 'wkf1285541_13_1_0_47504750#458318uploadPart0.chunk.gz', line 1, character 10140   Row 279, column "WKF1285541_13_1_0"["BICUST_ID":1]   If you would like to continue loading when a
04/13/2022 10:00:26 AM              n error is encountered, use other values such as 'SKIP_FILE' or 'CONTINUE' for the ON_ERROR option. For more information on loading options, please run 'info loading_data' in a SQL client. SQLState: 22018
04/13/2022 10:00:26 AM              WDB-200001 SQL statement 'COPY INTO wkf1285541_13_1_0 (SACTIVE, SADDRESS1, SADDRESS2, BICUST_ID, SEMAIL) FROM ( SELECT $1, $2, $3, $4, $5 FROM $$@BULK_wkf1285541_13_1_0$$) FILE_FORMAT = ( TYPE = CSV RECORD_DELIMITER = '\x02' FIELD_DELIMITER = '\x01' FIEL
04/13/2022 10:00:26 AM              D_OPTIONALLY_ENCLOSED_BY = 'NONE') ON_ERROR = ABORT_STATEMENT PURGE = TRUE' could not be executed.
```

### Tillfällig lösning{#issue-1-workaround}

Om du vill att data ska överföras från molndatabasen i Snowflake till den lokala Campaign-databasen och tillbaka till Snowflake måste du använda två olika **Ändra datakälla** verksamhet.

### Intern referens{#issue-1-ref}

Referens: NEO-45549



## Det gick inte att läsa in data (fil) på grund av ett omvänt snedstreck {#issue-2}

### Beskrivning{#issue-2-desc}

När du matar in data i molndatabasen med en kampanjinläsningsaktivitet misslyckas processen när det finns ett omvänt snedstreck i källfilen. Strängen escape-konverteras inte och data bearbetas inte korrekt på Snowflake.

Det här problemet uppstår bara om det omvända snedstrecket finns i slutet av strängen, till exempel: `Barker\`.


### Återgivningssteg{#issue-2-repro}

1. Anslut till klientkonsolen och skapa ett arbetsflöde.
1. Lägg till en **Inläsning av data (fil)** och konfigurera den.
1. Välj en lokal fil med de egenskaper som beskrivs ovan.
1. Kör arbetsflödet och kontrollera arbetsflödesloggarna för att se felet.


### Felmeddelande{#issue-2-error}

```sql
Error:
04/21/2022 4:01:58 PM     loading when an error is encountered, use other values such as 'SKIP_FILE' or 'CONTINUE' for the ON_ERROR option. For more information on loading options, please run 'info loading_data' in a SQL client. SQLState: 22000
04/21/2022 4:01:58 PM    ODB-240000 ODBC error: String '100110668547' is too long and would be truncated   File 'wkf1656797_21_1_3057430574#458516uploadPart0.chunk.gz', line 1, character 0   Row 90058, column "WKF1656797_21_1"["SCARRIER_ROUTE":13]   If you would like to continue
```

### Tillfällig lösning{#issue-2-workaround}

Som en tillfällig lösning kan du exportera filerna med dubbla citattecken runt de problematiska värdena (som `Barker\`) och inkludera ett alternativ för filformat `FIELD_OPTIONALLY_ENCLOSED_BY = '"'`.

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

Ingen

### Intern referens{#issue-3-ref}

Referens: NEO-47269