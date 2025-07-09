---
title: Skapa profiler med API:er
description: Lär dig mer om hur du skapar profiler med API:er.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
exl-id: 69e8d034-6bdd-4b82-bcd7-1ef4be0a59b3
source-git-commit: 4ed5799c77c647c9f1aeabba7645fbb475d03c09
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Skapa profiler med API:er {#creating-profiles-api}

Profiler skapas med en **POST**-begäran på profilresursen.

>[!CAUTION]
>
>Om du vill associera en <b>orgUnit</b> med den skapade profilen måste du utöka profilresursen med det här fältet och, efter att tillägget har publicerats, utföra en POST-begäran på slutpunkten <b>ProfileAndServicesExt</b> .
>
>Mer information om profilens resurstillägg finns i <a href="https://helpx.adobe.com/se/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">Kampanjdokumentationen</a>.

<br/>

***Exempelbegäran***

Exempelbegäran POST om att skapa en profil med e-postmeddelandet&quot;john.doe@mail.com&quot;.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"email":"john.doe@mail.com"}'
```

Den returnerar den nyligen skapade profilen med e-postadressen&quot;john.doe@mail.com&quot;.

```
{
    "PKey": "<PKEY>",
    "firstName": "John",
    "lastName":"Doe",
    "birthDate": "1980-10-24",
    "email": "john.doe@mail.com",
    ...
}
```
