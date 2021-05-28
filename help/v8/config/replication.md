---
solution: Campaign v8
product: Adobe Campaign
title: Tekniska arbetsflöden och datareplikering
description: Tekniska arbetsflöden och datareplikering
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 7b145193-d4ae-47d0-b694-398c1e35eee4,df76e7ff-3b97-41be-abc2-640748680ff3
source-git-commit: ab7e458db5ad5696d144c17f6e89e4437a476d11
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 1%

---

# Tekniska arbetsflöden och datareplikering

## Tekniska arbetsflöden{#tech-wf}

Adobe Campaign innehåller en uppsättning inbyggda tekniska arbetsflöden. Tekniska arbetsflöden kör processer eller jobb som schemaläggs regelbundet på servern.

Dessa arbetsflöden utför underhållsåtgärder på databasen, utnyttjar spårningsinformationen i leveransloggarna, skapar återkommande kampanjer med mera.

[!DNL :arrow_upper_right:] En fullständig lista över tekniska arbetsflöden finns i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/advanced-management/about-technical-workflows.html)


Utöver dessa tekniska arbetsflöden förlitar sig Campaign v8 på specifika tekniska arbetsflöden för att hantera [datareplikering](#data-replication).

* **[!UICONTROL Replicate Reference tables]**
Det här arbetsflödet utför automatisk replikering av inbyggda tabeller som måste finnas i den lokala kampanjdatabasen (Postgres) och molndatabasen ([!DNL Snowflake]). Det är schemalagt att köras varje timme, varje dag. Om det finns ett **lastModified**-fält utförs replikeringen stegvis, annars replikeras hela tabellen. Ordningen på tabellerna i arrayen nedan är den ordning som används i replikeringsarbetsflödet.
* **[!UICONTROL Replicate Staging data]**
Det här arbetsflödet replikerar mellanlagringsdata för enhetsanrop. Det är schemalagt att köras varje timme, varje dag.
* **[!UICONTROL Deploy FFDA immediately]**\
   Det här arbetsflödet utför en omedelbar distribution till molndatabasen.
* **[!UICONTROL Replicate FFDA data immediately]**
Det här arbetsflödet replikerar XS-data för ett givet externt konto.

Dessa tekniska arbetsflöden är tillgängliga från noden **[!UICONTROL Administration > Production > Technical workflows > Full FFDA replication]** i Campaign Explorer. **De får inte ändras.**

Vid behov kan du starta datasynkronisering manuellt. Om du vill utföra detta högerklickar du på aktiviteten **Schemaläggaren** och väljer **Kör väntande aktiviteter nu**.

## Datareplikering{#data-replication}

Vissa inbyggda tabeller replikeras från den lokala databasen i Campaign till [!DNL Snowflake] Cloud-databasen via dedikerade arbetsflöden som beskrivs ovan.

Replikeringsprinciperna baseras på tabellstorleken. Vissa tabeller kommer att replikeras i realtid, andra kommer att replikeras varje timme. Vissa tabeller kommer att få stegvisa uppdateringar när andra kommer att ersättas.

Förutom det inbyggda arbetsflödet **Replikera referenstabeller** kan du framtvinga datareplikering i dina arbetsflöden.

Du kan:

* lägg till en specifik **JavaScript-kod**-aktivitet med följande kod:

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

[!DNL :arrow_upper_right:] Läs om hur du kommer igång med arbetsflöden i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/about-workflows.html?lang=en#automating-with-workflows)

[!DNL :bulb:] Få åtkomst till kvarhållningsperioder för data i  [det här avsnittet](../dev/datamodel-best-practices.md#data-retention)
