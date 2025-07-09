---
title: Metadatamekanism
description: Läs mer om metadatafunktionen.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
exl-id: 58ec0999-b28a-4198-8d57-729b074c6a6d
source-git-commit: 4ed5799c77c647c9f1aeabba7645fbb475d03c09
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 1%

---

# Metadatamekanism {#metadata-mechanism}

Du kan hämta metadata för resurser med **resourceType** i en GET-begäran:

`GET /profileAndServices/resourceType/<resourceName>`

Svaret returnerar huvudmetadata från resursen (alla andra fält är beskrivande eller interna):

* Noden **Innehåll** returnerar resursfälten. För varje fält i noden **content** finns följande fält:

   * &quot;apiName&quot;: namnet på attributet som används i API:erna.
   * &quot;type&quot;: det här är definitionen på högnivåtyp (sträng, tal, länk, samling, uppräkning...).
   * &quot;dataPolicy&quot;: fältets värde måste följa givna policyregler. Om regeln dataPolicy till exempel har värdet &quot;email&quot; måste värdet vara en giltig e-postadress. Under en PATCH eller en POST kan dataPolicy kontrollera värdet eller ändra värdet som ska omformas (till exempel smartCase).
   * &quot;category&quot;: anger fältets kategori i frågeredigeraren.
   * &quot;resType&quot;: Detta är den tekniska typen.

     Om&quot;type&quot; har fyllts i med värdet&quot;link&quot; eller&quot;collection&quot; är värdet resTarget namnet på resursen som länken pekar på.
Om &quot;type&quot; har slutförts med värdet &quot;enumeration&quot; läggs ett &quot;values&quot;-fält till och varje uppräkningsvärde anges i noden **values**.

* Noden **Filter** returnerar URL:en för att hämta associerade filter. Mer information om filter finns i [det här avsnittet](sorting.md#filtering).

<!-- créer une section au même niveau sur les liens -->
<!-- dans l'exemple: birthdate, email +  mettre 2 liens : un de type 1-1 , 1-N
si on prend l'exemple de l'org unit, on aura un bon exemple lien -->
<!-- plus reparler du node Data -->

<br/>

***Exempelbegäran***

Utför en GET-begäran på resursen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar den fullständiga beskrivningen av profilresursen.

```
{
...
"content": {
  "email": {...},
    ...
    },
"data": "/profileAndServices/profile/",
"filters": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/<PKEY>"
    },
"help": "Identified profiles",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/metadata",
"label": "Profiles",
"mandatory": false,
"name": "profile",
"pkgStatus": "never",
"readOnly": false,
"schema": "nms:recipient",
"type": "item"
}
```
