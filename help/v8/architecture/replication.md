---
title: Tekniska arbetsflöden och datareplikering
description: Tekniska arbetsflöden och datareplikering
feature: Workflows, FFDA
role: Developer
level: Intermediate
exl-id: 7b145193-d4ae-47d0-b694-398c1e35eee4
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 2%

---

# Tekniska arbetsflöden och datareplikering {#wf-data-replication}

## Tekniska arbetsflöden {#tech-wf}

I samband med en [Enterprise-distribution](enterprise-deployment.md) (FFDA) levereras Adobe Campaign med en uppsättning inbyggda tekniska arbetsflöden. Tekniska arbetsflöden kör processer eller jobb som schemaläggs regelbundet på servern.

Dessa arbetsflöden utför underhållsåtgärder på databasen, utnyttjar spårningsinformationen i leveransloggarna, skapar återkommande kampanjer med mera.

En fullständig lista över tekniska arbetsflöden finns på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html){target="_blank"}.

Utöver dessa tekniska arbetsflöden förlitar sig Campaign v8 på specifika tekniska arbetsflöden för att hantera [datareplikering](#data-replication).

* **[!UICONTROL Replicate Reference tables]**
Det här arbetsflödet utför automatisk replikering av inbyggda tabeller som måste finnas i den lokala kampanjdatabasen (Postgres) och molndatabasen ([!DNL Snowflake]). Det är schemalagt att köras varje timme, varje dag. Om fältet **lastModified** finns utförs replikeringen stegvis, annars replikeras hela tabellen. Ordningen på tabellerna i arrayen nedan är den ordning som används i replikeringsarbetsflödet.
* **[!UICONTROL Replicate Staging data]**
Det här arbetsflödet replikerar mellanlagringsdata för enhetsanrop. Det är schemalagt att köras varje timme, varje dag.
* **[!UICONTROL Deploy FFDA immediately]**\
  Det här arbetsflödet utför en omedelbar distribution till molndatabasen.
* **[!UICONTROL Replicate FFDA data immediately]**
Det här arbetsflödet replikerar XS-data för ett givet externt konto.

Dessa tekniska arbetsflöden är tillgängliga från noden **[!UICONTROL Administration > Production > Technical workflows > Full FFDA Replication]** i Campaign Explorer. **De får inte ändras.**

Vid behov kan du starta datasynkronisering manuellt. Om du vill utföra detta högerklickar du på aktiviteten **Schemaläggaren** och väljer **Kör väntande aktiviteter nu**.

## Datareplikering {#data-replication}

Vissa inbyggda tabeller replikeras från den lokala databasen i Campaign till [!DNL Snowflake] Cloud-databasen via dedikerade arbetsflöden som beskrivs ovan.

Förstå vilka databaser Adobe Campaign v8 använder, varför data replikeras, vilka data som replikeras och hur replikeringsprocessen fungerar.

>[!VIDEO](https://video.tv.adobe.com/v/334460?quality=12)


### Principer för datareplikering {#data-replication-policies}

Replikeringsprinciperna baseras på tabellstorleken. Vissa tabeller replikeras i realtid, andra replikeras i timläge. Vissa tabeller får stegvisa uppdateringar när andra ersätts.

Förutom det inbyggda tekniska arbetsflödet **Replikera referenstabeller** kan du framtvinga datareplikering i dina arbetsflöden.

Du kan:

* lägg till en specifik **JavaScript-kodsaktivitet** med följande kod:

```
nms.replicationStrategy.StartReplicateStagingData("dem:sampleTable")
```

![](assets/jscode.png)


* lägg till en specifik **nlmodule**-aktivitet med följande kommando:

```
nlserver ffdaReplicateStaging -stagingSchema -instance:acc1
```

![](assets/nlmodule.png)


**Relaterade ämnen**

* [Lär dig komma igång med arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html){target="_blank"}

* [Datalagringsperioder](../dev/datamodel-best-practices.md#data-retention)
