---
title: Datareplikering
description: Tekniska arbetsflöden och datareplikering
feature: Workflows, FFDA
role: Developer
level: Intermediate
exl-id: 7b145193-d4ae-47d0-b694-398c1e35eee4
source-git-commit: b8f774ce507cff67163064b6bd1341b31512c08f
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 2%

---


# Datareplikering {#wf-data-replication}

## Princip

I samband med en [Enterprise-distribution](enterprise-deployment.md) (FFDA) säkerställer datareplikering att de två databaserna Campaign-databasen (PostgreSQL) och Cloud-databasen ([!DNL Snowflake]) fungerar parallellt och förblir synkroniserade i realtid.

Molndatabasen ([!DNL Snowflake]) är optimerad för hantering av stora datagrupper, till exempel uppdatering av 1 miljon adresser. Samtidigt passar Campaigns lokala databas (PostgreSQL) bättre för åtgärder som utförs på enskilda eller små volymer, som att uppdatera en enda dirigeringsadress. Synkroniseringen sker automatiskt och transparent i bakgrunden, så att data i den lokala Campaign-databasen (PostgreSQL) dupliceras i molndatabasen ([!DNL Snowflake]) i realtid, vilket synkroniserar båda databaserna. Datasynkronisering innefattar scheman, tabeller och data.

➡️ [Upptäck hur datareplikering fungerar i video](#video)

## Replikeringslägen {#modes}

Datareplikering kan ske i olika lägen beroende på användningsfallet.

* **Replikering direkt** hanterar fall där duplicering i realtid är nödvändig. Den förlitar sig på specifika tekniska trådar för att omedelbart återge data för användning som att skapa en diffusion eller uppdatera en dirigeringsadress.
* **Schemalagd replikering** används när omedelbar synkronisering inte krävs. Schemalagd replikering använder specifika [tekniska arbetsflöden](#workflows) som körs varje timme för att synkronisera data, till exempel typologiregler.

## Replikeringsprinciper

Replikeringsprinciper definierar hur mycket data som replikeras från en Campaign-lokal databastabell (PostgreSQL). Dessa profiler beror på tabellens storlek och det specifika användningsfallet. Vissa tabeller kommer att ha inkrementella uppdateringar när andra kommer att replikeras helt. Det finns tre huvudtyper av replikeringsprinciper:

* **XS**: Den här principen används för tabeller med relativt små storlekar. Hela tabellen replikeras i en bild. Med inkrementell replikering undviker du upprepade gånger samma data genom att använda en tidsstämpelpekare för att replikera endast de senaste ändringarna.
* **SingleRow**: Den här principen replikerar bara en rad i taget. Det används vanligtvis för direktreplikering av aktuella Campaign-objekt och relaterade objekt.
* **Några rader**: Den här principen är utformad för att replikera en begränsad delmängd med data med hjälp av frågedefinitioner eller filter. Det används för större tabeller där selektiv replikering är nödvändig.

## Replikeringsarbetsflöden {#workflows}

Campaign v8 förlitar sig på specifika tekniska arbetsflöden för att hantera schemalagd datareplikering. Dessa tekniska arbetsflöden är tillgängliga från noden **[!UICONTROL Administration > Production > Technical workflows > Full FFDA Replication]** i Campaign Explorer. **De får inte ändras.**

Tekniska arbetsflöden kör processer eller jobb som schemaläggs regelbundet på servern. En fullständig lista över tekniska arbetsflöden finns på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html){target="_blank"}.

Tekniska arbetsflöden som säkerställer datareplikering är följande:

| Tekniskt arbetsflöde | Beskrivning |
|------|-----------|
| **[!UICONTROL Replicate Reference tables]** (ffdaReplicateReferenceTables) | Utför automatisk replikering av inbyggda tabeller som måste finnas i Campaign-databasen (PostgreSQL) och molndatabasen ([!DNL Snowflake]). Det är schemalagt att köras varje timme, varje dag. Om fältet **lastModified** finns utförs replikeringen stegvis, annars replikeras hela tabellen. |
| **[!UICONTROL Replicate Staging data]** (ffdaReplicateStagingData) | Replikerar mellanlagringsdata för enhetsanrop. Det är schemalagt att köras varje timme, varje dag. |
| **[!UICONTROL Deploy FFDA immediately]** (ffdaDeploy) | Utför en omedelbar distribution till molndatabasen. |
| **[!UICONTROL Replicate FFDA data immediately]** (ffdaReplicate) | Replikerar XS-data för ett givet externt konto. |

Vid behov kan du starta datasynkronisering manuellt. Om du vill göra det högerklickar du på aktiviteten **Schemaläggaren** och väljer **Kör väntande aktiviteter nu**.

Förutom det inbyggda tekniska arbetsflödet **Replikera referenstabeller** kan du framtvinga datareplikering i dina arbetsflöden med någon av dessa metoder

+++Hur datareplikering framtvingas

* Lägg till en specifik **JavaScript-kodsaktivitet** med följande kod:

  ```
  nms.replicationStrategy.StartReplicateStagingData("dem:sampleTable")
  ```

  ![](assets/jscode.png)

* Lägg till en specifik **nlmodule**-aktivitet med följande kommando:

  ```
  nlserver ffdaReplicateStaging -stagingSchema -instance:acc1
  ```

  ![](assets/nlmodule.png)

+++

<br/>

>[!NOTE]
>
>Replikering direkt hanteras av specifika tekniska trådar i stället för arbetsflöden. Konfigurationen för det här läget hanteras i filen serverConf.xml. Du kan konfigurera serverConf.xml så att den matchar specifika användningsfall, som att begära att XS-tabeller replikeras stegvis i stället för helt. Kontakta din Adobe-representant om du vill veta mer.

## API:er

API:er möjliggör replikering av både anpassade och körklara data från Campaign-databasen (PostgreSQL) till molndatabasen ([!DNL Snowflake]). Med dessa API:er kan du kringgå fördefinierade arbetsflöden och anpassa replikeringen efter specifika krav, som att replikera anpassade tabeller.

Exempel:

```
var dataSource = "nms:extAccount:ffda";
var xml = xtk.builder.CopyXxlData(
    <params dataSource={dataSource} policy="xs">
        <srcSchema name="cus:recipient"/>
    </params>
);
```

## Replikeringsköer

När stora volymer replikeringsbegäranden inträffar samtidigt kan prestandaproblem uppstå i molndatabasen ([!DNL Snowflake]) på grund av lås på tabellnivå under MERGE-åtgärder. För att minimera detta centraliserade arbetsflöden för replikering grupperas begäranden i köer.

Varje kö hanteras av ett tekniskt arbetsflöde, som hanterar replikering för en viss tabell och kör väntande begäranden som en enda MERGE-åtgärd. Dessa arbetsflöden aktiveras var 20:e sekund för att bearbeta nya replikeringsbegäranden:

| Tekniskt arbetsflöde | Beskrivning |
|------|-----------|
| **Replikera nmsDelivery-kö** (ffdaReplicateQueueDelivery) | Kö för tabellen `nms:delivery`. |
| **Replikeringskön nmsDlvExclusion** (ffdaReplicateQueueDlvExclusion) | Kö för tabellen `nms:dlvExclusion`. |
| **Replikera kön nmsDlvMidRemoteIdRel** (fdaReplicateQueueDlvMidRemoteIdRel) | Kö för tabellen `nms:dlvRemoteIdRel`. |
| **Replikera kön nmsTrackingUrl** (ffdaReplicateQueueTrackingUrl)<br/>**Replikera kön nmsTrackingUrl i samtidighet** (ffdaReplicateQueueTrackingUrl_2) | Köer i samtidighet för tabellen `nms:trackingUrl`, använder två arbetsflöden för att förbättra effektiviteten genom att behandla begäranden baserat på olika prioriteringar. |

## Självstudiekurs {#video}

I den här videon visas de viktigaste begreppen för databaser som används i Adobe Campaign v8, varför data replikeras, vilka data som replikeras och hur replikeringsprocessen fungerar.

>[!VIDEO](https://video.tv.adobe.com/v/334460?quality=12)

Ytterligare självstudiekurser för Campaign v8-klientkonsolen finns [här](https://experienceleague.adobe.com/en/docs/campaign-learn/tutorials/overview).
