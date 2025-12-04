---
title: Ta bort prenumerationer
description: Lär dig hur du tar bort prenumerationer med API:er
role: Developer
level: Experienced
exl-id: 76e2d102-c877-41a6-af87-2f407201a572
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Ta bort prenumerationer med API:er {#mdeleting-subscriptions-api}

<!--NOTE TO WRITER: There are two duplicate headings that seem to have the same content. Delete one? Rename if different?-->

## Ta bort en serviceprenumeration för en viss profil {#deleting-service-subscription}

Detta är en procedur i tre steg.

1. Hämta prenumerations-URL:en för den önskade profilen.
1. Utför en GET-begäran på prenumerations-URL:en.
1. Utför en DELETE-begäran på den önskade tjänst-URL:en.

Om borttagningsbegäran lyckas är svarsstatusen 204 Inget innehåll.

<br/>

***Exempelbegäran***

Nedan visas exempel på nyttolaster som visar hur du kan avbryta prenumerationen på en profil från en tjänst. Utför först en GET-begäran om att hämta profilen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar prenumerations-URL:en för profilen.

```
  {
    ...
    "postalAddress":...,
    "preferredLanguage": "none",
    "subscriptions": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions/"
    },
  }
```

Utför en GET-begäran på prenumerations-URL:en.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar en lista över prenumerationer för den valda profilen, med en URL för varje prenumerationstjänst.

```
...
"service": {
  "PKey": "<PKEY>",
  "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
  "label": "Sport Newsletter",
  "name": "SVC1",
  "title": "Sport Newsletter (SVC1)"
},
...
```

Utför en DELETE-begäran på den önskade tjänst-URL:en.

```
-X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!-- + réponse -->

## Ta bort en serviceprenumeration för en viss profil

Detta är en procedur i tre steg.

1. Hämta önskad tjänst och prenumerations-URL.
1. Gör en GET-förfrågan på prenumerations-URL:en för att hämta alla profilprenumerationer.
1. Utför en DELETE-begäran på den önskade URL:en för profilprenumeration.

Om borttagningsbegäran lyckas är svarsstatusen 204 Inget innehåll.

<br/>

***Exempelbegäran***

Hämta tjänstposten.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar prenumerations-URL:en för tjänsten.

```
{
  ...
  "messageType": "email",
  "mode": "newsletter",
  "name": "SVC3",
  "subScenarioEventType": "subscriptionEvent",
  "subscriptions": {
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
  },
  "targetResource": "profile",
  ...
},
```

Utför en GET-begäran på prenumerations-URL:en.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar en lista över prenumerationer för den valda tjänsten, med en URL (href) för varje profilprenumeration.

```
{
  "PKey": "<PKEY>",
  "created": "2019-03-26 08:58:04.764Z",
  "email": "",
  "expirationDate": "",
  "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/<PKEY>",
  "metadata": "subscriptionRcp",
  "service": ...,
  "serviceName": "SVC3",
  "subscriber": ...,
  ...
}
```

Utför en DELETE-begäran på den önskade URL:en för profilprenumeration.

```
-X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!-- + réponse -->
