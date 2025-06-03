---
title: Kända fel i Campaign v8
description: Kända fel i den senaste Campaign-versionen
feature: Overview
role: Data Engineer
level: Beginner
hide: true
hidefromtoc: true
exl-id: 89a4ab6c-de8e-4408-97d2-8b8e574227f9
source-git-commit: 41e39e046ec77de8b5e657ba76645898ff1cd2d7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Kända fel{#known-issues}

På den här sidan visas kända fel som identifierats i **de senaste Campaign v8-versionerna**. Dessutom visas begränsningar som kommer med Campaign v8 [på den här sidan](ac-guardrails.md).


>[!NOTE]
>
>Adobe publicerar den här listan över kända fel efter eget gottfinnande. Det baseras på antalet kundrapporter, allvarlighetsgraden och möjligheten att komma runt problemet. Om ett problem som du stöter på inte visas kanske det inte uppfyller villkoren för publicering på den här sidan.

## Campaign v8.3.8{#8.3-issues}

### Ändra aktivitetsproblem för Source Data {#issue-2}

#### Beskrivning{#issue-2-desc}

När du matar in data i Snowflake molndatabas med Campaign **Query** och en **Change Data Source** -aktivitet misslyckas processen när det finns ett omvänt snedstreck i data. Källsträngen escape-konverteras inte och data bearbetas inte korrekt i Snowflake.

Problemet uppstår bara om det omvända snedstrecket finns i slutet av strängen, till exempel: `Barker\`.


#### Återgivningssteg{#issue-2-repro}

1. Anslut till klientkonsolen och skapa ett arbetsflöde.
1. Lägg till en **Query**-aktivitet och konfigurera den.
1. Välj data med de egenskaper som beskrivs ovan.
1. Lägg till en **Ändra data för Source**-aktivitet och konfigurera den så att den väljer Snowflake molndatabas.
1. Kör arbetsflödet och kontrollera arbetsflödesloggarna för att se felet.


#### Felmeddelande{#issue-2-error}

```sql
Error:
04/21/2022 4:01:58 PM     loading when an error is encountered, use other values such as 'SKIP_FILE' or 'CONTINUE' for the ON_ERROR option. For more information on loading options, please run 'info loading_data' in a SQL client. SQLState: 22000
04/21/2022 4:01:58 PM    ODB-240000 ODBC error: String '100110668547' is too long and would be truncated   File 'wkf1656797_21_1_3057430574#458516uploadPart0.chunk.gz', line 1, character 0   Row 90058, column "WKF1656797_21_1"["SCARRIER_ROUTE":13]   If you would like to continue
```

#### Tillfällig lösning{#issue-2-workaround}

Tillfällig lösning är att exkludera data som innehåller omvänt snedstreck i slutet av strängen eller att ta bort dem från källfilen.


#### Intern referens{#issue-2-ref}

Referens: NEO-45549


### Det gick inte att överföra filen på servern med datainläsningsaktiviteten (fil) {#issue-3}

#### Beskrivning{#issue-3-desc}

När en fil överförs på Campaign-servern med en **datainläsningsaktivitet (fil)** stoppas processen vid 100 % men avslutas aldrig.

#### Återgivningssteg{#issue-3-repro}

1. Anslut till klientkonsolen och skapa ett arbetsflöde.
1. Lägg till en **datainläsningsaktivitet (fil)** och konfigurera den.
1. Välj alternativet **Överför på servern**.
1. Välj filen på den lokala datorn,
1. Klicka på **Överför**


#### Felmeddelande{#issue-3-error}

Processen tar aldrig slut.

#### Tillfällig lösning{#issue-3-workaround}

Du kan lösa problemet genom att använda en äldre klientkonsol. Sedan kan du överföra filen till servern.

Som kampanjadministratör kan du hämta Campaign v8.3.1-klientkonsolen i [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?1_group.propertyvalues.property=.%2Fjcr%3aContent%2Fmetadata%2FDc%3Aversion&amp;1_group.propertyvalues.operation=equals&amp;1_group.propertyvalues.0_values=target-version%3AcCampaign%2F8&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;order.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=4){target="_blank"}.

Lär dig hur du får åtkomst till Adobe programdistribution [på den här sidan](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html){target="_blank"}.

Lär dig hur du uppgraderar din klientkonsol [på den här sidan](connect.md)

#### Intern referens{#issue-3-ref}

Referens: NEO-47269

