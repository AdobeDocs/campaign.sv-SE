---
title: Skapa en tjänst med API:er
description: Lär dig skapa en tjänst med API:er
role: Developer
level: Experienced
exl-id: 91bbce9e-a618-4be2-840b-c7d021271f4e
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---

# Skapa en tjänst med API:er{#creating-a-service-api}

Tjänsterna skapas med en **POST**-begäran på tjänstresursen.

Om du vill skapa tjänsten med specifika attribut lägger du till dem i nyttolasten. I annat fall skapas den nya tjänsten med standardtjänster.

<br/>

***Exempelbegäran***

Exempelbegäran POST för att skapa en tjänst med specifika attribut.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/ \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
-i
-d {
-d "label": "My newsletter",
-d "messageType": "email",
-d "name": "email_newsletter",
-d "start": "2019-10-06"
-d }
```

Den returnerar den nyligen skapade tjänsten med de uppdaterade attributen.

```
{
    "PKey": "<PKEY>",
    "builtIn": false,
    "created": "2019-09-26 12:00:37.005Z",
    "href": "https://mc.adobe.io/<ORGANIZATION>/profileAndServices/service/@NLscZuVHxdVu9rPftvrMWFfR1zRIxQGswSOmGLrK09JTF_iWhB0JCUHEndA_vvy__k9mzOYa5NVkcWDcrK8qGh0wygahX9kRcD44kiWWSEceShn3",
    "label": "My newsletter",
    ...
}
```
