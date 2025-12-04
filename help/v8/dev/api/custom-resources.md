---
title: Anpassade resurser
description: Läs mer om anpassad resurshantering med API:er/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
exl-id: d7b2231d-46ff-4966-9ea7-27a775e5236b
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 2%

---

# Anpassade resurser {#custom-resources}

Adobe Campaign levereras med en fördefinierad datamodell, där data definieras med olika resurser. Du kan utöka datamodellen som tillhandahålls genom att utöka resurserna för att lägga till egna anpassade fält eller anpassade tabeller, till exempel köp- eller produkttabeller.

Anpassade resurser är tillgängliga via API:er med slutpunkten **/profileAndServicesExt** och det anpassade resursnamnet.

`https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/`

>[!NOTE]
>
>Använd alltid prefixet <b>&quot;cus&quot;</b> före resursens namn för resurser som inte är färdiga.

Du kan utföra vilken åtgärd som helst med anpassade resurser, förutsatt att de är länkade till profiltabellen. Låt oss titta på tabellstrukturen nedan:

![Alt-text](assets/cusresources.png)

I så fall är alla resurser från tabellerna **Transaction**, **TransactionDetails** och **Product** tillgängliga så länge de är länkade till tabellen **Profile** .

<br/>

***Exempelbegäran***

Exempel på GET-begäran om åtkomst till den utökade profilenAndServicesExt-resursen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
```

Den returnerar listan med alla länkade anpassade resurser. Du kan sedan använda resurs-URL:erna för att utföra alla API-åtgärder som beskrivs i den här dokumentationen.

```
{
"apiName": "resourceType",
"cusProduct": {
        "content": ...,
        "data": "/profileAndServicesExt/cusProduct/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusProduct/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
"cusTransaction": {
        "content": ...,
        "data": "/profileAndServicesExt/cusTransaction/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusTransaction/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
    ...
}
```
