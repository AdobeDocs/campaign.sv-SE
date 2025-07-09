---
title: Måste läsas
description: Måste läsas innan API:er används.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
exl-id: 9e2d1b59-55a5-4715-adfb-35191a9df536
source-git-commit: 4ed5799c77c647c9f1aeabba7645fbb475d03c09
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Must-Read {#must-read}

## Tekniska krav

* Adobe Campaign API:er får endast användas på servern.
* Kontakta alltid Adobe tekniska kontakt om användningsfallet som du vill implementera är anpassat till den skala som tillåts av Adobe Campaign API:er.
* Du måste ha specifik behörighet för att konfigurera en AdobeIO-åtkomst. Kontakta Adobe Support om du har problem.

## Rättigheter och tillgång

* Som standard använder Adobe Campaign API:er administratörskontexten och därför gäller inte organisationsenheterna och rollerna.
* Adobe Campaign-API:erna exkluderas från rollkontexten.
* Om du vill konfigurera API:erna med en eller flera organisationsenheter bör du kontrollera med din tekniska kontakt till Adobe först.

## Resursrepresentation

Alla API-resurser är tillgängliga i **JSON** med ett URL-tillägg eller i ett HTTP Accept Header:

`GET /profileAndServices/<resourceName>.json`

>[!NOTE]
>
>Utan tillägg i URL:en är formatet **json** som standard för innehållstypen.

<br/>

***begär exempel***

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile.json \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

## Primärnyckel och URL:er

* Försök inte att skapa en URL själv. Alla URL:er returneras av API:t. Det går dock att skapa en URL utifrån det översta resursnamnet.

* Värdena för den automatiska primärnyckeln (PKey) som illustrerar exemplen är inte avsedda att fungera i en annan specifik distribution. De produceras av Adobe Campaign API.

* Automatiska primärnyckelvärden som genererats av Adobe Campaign får aldrig lagras i en extern databas eller webbplats. Du måste generera specifika nyckelfält i databasdefinitionen och använda dem under utvecklingen.

## Anpassade tangenter {#custom-keys}

Om profilresursen har utökats med ett anpassat nyckelfält kan du använda det här fältet som en nyckel i stället för den automatiska primärnyckel som genererats av Adobe Campaign:

`GET /.../profileAndServicesExt/profile/<customKey>`

Det går inte att ändra anpassade nycklar med hjälp av en PATCH-åtgärd om nyckelvärdet skiljer sig från originalnyckeln, eller om du använder din egen affärsnyckel som URI i stället för den som tillhandahålls av Adobe.

Använd endast en anpassad nyckel för **profilresurser på den översta nivån**. URL:er returneras av API:t och bör aldrig skapas av dig själv.

<br/>

***Exempelbegäran***

Om du vill hämta prenumerationer för en profil med hjälp av en anpassad nyckel utför du en GET-åtgärd på den anpassade nyckeln.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/<customKey> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Utför en GET-förfrågan på den prenumerations-URL som returneras.

```
-X GET <SUBSCRIPTION_URL> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar en lista med prenumerationer för profilen.

```
"service": {
"PKey": "<PKEY>",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
"label": "Sport Newsletter",
"name": "SVC1",
"title": "Sport Newsletter (SVC1)"
}
```
