---
title: Interagera med anpassade resurser
description: Läs mer om anpassad resurshantering med API:er/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
exl-id: 19bfeecb-da60-479c-a929-0cfb72ef59e3
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---

# Interagera med anpassade resurser {#interacting-with-custom-resources}

Med slutpunkten **/customResources** kan du visa anpassade resurser för Campaign i REST. Baserat på detta API finns det en integrering mellan anpassade entiteter och externa slutpunkter.

Slutpunkten /customResources har exakt samma beteende som slutpunkten /profileAndServices.

De anpassade resurser som visas i detta API är:

* alla enheter som inte visas under /profileAndServicesExt
* alla enheter som inte är länkade till profilen och, för dessa enheter, deras underordnade och indirekt underordnade.
* som standard alla enheter som inte är länkade till något, samt deras underordnade och indirekt underordnade.

>[!NOTE]
>De anpassade resurser som är tillgängliga under /profileAndServicesExt visas inte i API:t /customResources.


Här följer ett exempel på hur du hämtar metadata från en anpassad resurs:

```
GET /customResources/resourceType/<customResourceName>
```

När du skapar, uppdaterar eller tar bort en fil används GET, POST, PATCH och DELETE.

```
POST /customResources/<customResourceName>
```
