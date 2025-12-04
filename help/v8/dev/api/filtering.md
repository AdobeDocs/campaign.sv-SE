---
title: Filtrering
description: Lär dig hur du utför filtreringsåtgärder.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
exl-id: cdb050b7-d327-42f7-b534-d32d988c8ffb
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Filtrering {#filtering}

## Hämtar filtermetadata

Det finns filter för varje resurs. Om du vill identifiera de filter som är associerade med en resurs måste du utföra en GET-begäran på resursens metadata. Denna begäran returnerar URL:en där alla filter har definierats för en given resurs. Mer information om metadata finns i [det här avsnittet](metadata-mechanism.md).

Om du vill identifiera metadata för ett filter och avgöra hur det ska användas, måste du utföra en GET-begäran på den tidigare returnerade URL:en.

<br/>

***Exempelbegäran***

Exempelnyttolasterna nedan visar hur du hämtar filtermetadata för byText för profilresursen. Utför först en GET-begäran på resursmetadata för profilen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar den URL där filtren beskrivs.

```
{
"filters": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/<PKEY>/filters/"
    }
  }
```

Utför en GET-begäran på URL:en. Den returnerar listan med filter för profilresursen, med metadata för varje filter.

```
{
"birthday": {
        "PKey": "@FL-CbDFXbnHbXcVpeCGWL46VXJLn1LqxLMPagt2vz8sCxQ52lvB15KiUaxXkxJYQw-tZXYrgUWG6K8QcB4gxVY9RKoba5bRFY3294YFshDmorRr8",
        "category": "0150_profile",
        "condition": ...,
        "data": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/birthday?type=$value&precision=$value&operator=$value&day=$value&month=$value&includeStart=$value&endDay=$value&endMonth=$value&includeEnd=$value&relativeValue=$value&nextUnitsValue=$value&previousUnitsValue=$value",
        "formType": "webPage",
        "fragmentName": "",
        "label": "Birthday",
}
```

## Metadatastruktur för filter

Samma metadatastruktur är tillgänglig för varje filter:

* Fälten **@formType** och **@webPage** är tekniska fält.
* Fältet **data** innehåller ett exempel på hur du använder filtret.
* Noden **metadata** beskriver filterparametrarna.
* Noden **condition** beskriver vad filtret är avsett att göra. Filterparametrarna som beskrivs i metadatanoden används för att skapa filtervillkor. Om **enabledIf** är true används **expr** för varje filtervillkor.

<br/>

Exempel på metadatastruktur för filter:

```
"byText": {
        "PKey": "...",
        "category": "99_none",
        "condition": ...,
        "data": "/profileAndServices/profile/byText?text=$value",
        "formType": "none",
        "fragmentName": "",
        "label": "By name or email",
    }
```

## Använda filter

Filtrering utförs med följande begäran:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/<resourceName>/by<filterName>?<filterParam>=<filterValue>`

Det går att kombinera flera filter i en enda begäran:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/<resourceName>/<filter1name>/<filter2name>?<filter1param>=<filter1value>&<filter2param>=<filter2value>`

<br/>

***Exempelbegäranden***

* Exempelbegäran från GET om att hämta tjänstresurserna med typen &quot;email&quot;.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel?channel=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Svar på begäran.

  ```
  {
      "content": [
          {
              "PKey": "<PKEY>",
              "created": "2019-09-25 23:20:35.000Z",
              "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/@I_FIiDush4OQPc0mbOVR9USoh36Tt5CsD35lATvQjdWlXrYc0lFkvle2XIwZUbD8GqTVvSp8AfWFUvjkGMe1fPe5nok",
              "label": "Marketing Newsletter",
              "lastModified": "2019-09-25 23:20:35.000Z",
              "limitedDuration": false,
              "messageType": "email",
              "mode": "newsletter",
              ...
          },
          ...
      ],
      ...
  }
  ```

* Exempel på GET-begäran om att hämta profilresurserna som innehåller &quot;Doe&quot; i
e-post- eller efternamnsfälten (filtret byText söker i både e-post- och efternamnsfälten).

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Doe \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Svar på begäran.

  ```
  {
      "content": [
          {
              "PKey": "<PKEY>",
              "firstName": "John",
              "lastName":"Doe",
              "birthDate": "1980-10-24",
              ...
          }
          ...
      ],
      ...
  }
  ```

* Exempelbegäran från GET om att hämta tjänstresurserna med typen&quot;email&quot; och etiketten&quot;sport&quot;.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/byText?channel=email&text=sport \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Svar på begäran.

  ```
  {
      "content": [
          {
              "PKey": "<PKEY>",
              "created": "2019-09-26 09:36:01.014Z",
              "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
              "label": "sport",
              "lastModified": "2019-09-26 09:36:01.014Z",
              "limitedDuration": false,
              "messageType": "email",
              "mode": "newsletter",
              "name": "SVC13",
              ...
          }
      ],
      ...
  }
  ```

## Egna filter

Om du vill använda ett eget filter måste du skapa och anpassa det i Adobe Campaign Standard-gränssnittet. Det anpassade filtret fungerar sedan på samma sätt som utanför rutfiltren:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/by<customFilterName>?<customFilterparam>=<customFilterValue>`

Mer information finns i Campaign Standard-dokumentationen:

* [Konfigurerar filterdefinitionen](https://helpx.adobe.com/campaign/standard/developing/using/configuring-filter-definition.html).
* [Använd skiftläge: Anropar en resurs med en sammansatt identifieringsnyckel](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/adding-or-extending-a-resource/uc-calling-resource-id-key.html).

<br/>

***Exempelbegäran***

Exempel på GET-begäran om att hämta profilresurserna med transaktionsbelopp på 100$ eller mer. Observera att filtret&quot;byAmount&quot; först har definierats i Adobe Campaign Standard-gränssnittet och länkats till den anpassade tabellen&quot;Transaction&quot;.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byAmount?amount_parameter=100 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!--
Response to the request.

```

{
    "content": [
        {
            "PKey": "<PKEY>",
            "builtIn": false,
            "created": "2019-09-26 09:36:01.014Z",
            "desc": "",
            "end": "",
            "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>",
            ...
        }
    ],
}

```

-->

<!-- exemple à vérifier de bout en bout-->

<!--+category = query editor
privacy ?
displayFOrmat ?
pour faire un POST sur une enum, il faut lui passer le @name décrit dans le noeud values, chaque @name a une correspondance en format = au format définit par le resType
-->





<!--
 if link ou collection.* resName +
* resTarget tout ca, ca va ensemble : le système de lien, resTarget va donner la ressource targetée par le lien. type
resType = type technique (long..) resType = link alors unbound='false' ou 'true'
If type = enumeration alors champ "values" rajouté et les valeurs sont dans values
pour faire un POST sur une enum, il faut lui passer le @name décrit dans le noeud values, chaque @name a une correspondance en format = au format définit par le resType
ail faut que la valeur poster soit conforme ,elle doit valider la dataPolicy . La dataPolicy peut soit controler la valeur (email invalide), soit transformé (cas du smartCase par exemple)
type dans les metadata = type de haut-niveau (nombre, text)
-->
