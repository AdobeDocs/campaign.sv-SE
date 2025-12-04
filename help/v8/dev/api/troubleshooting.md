---
title: API-felsökning
description: Läs mer om vanliga problem med Campaign Standard API:er
role: Developer
level: Experienced
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# API-felsökning {#troubleshooting}

* **När du går till Adobe.io Console visas följande fel:&quot;Adobe I/O-konsolen är bara tillgänglig för att välja medlemmar i företagskonton. Kontakta systemadministratören om du anser att du bör ha åtkomst.**

Du kan bara skapa API-nycklar för de organisationer som du är administratör för. Om det här meddelandet visas och du vill skapa API-nycklar och du vill fråga en administratör i organisationen.

* **När du skickar en begäran till Adobe.io får du {&quot;error_code&quot;:&quot;403023&quot;,&quot;message&quot;:&quot;Profilen är inte giltig&quot;}**

Det innebär att det är ett problem med IMS-etableringen för din specifika Campaign-produkt: IMS-teamet måste åtgärda det.

Om du vill ha mer information kan du anropa IMS API med din token för att se hur din IMS-profil ser ut: Du måste ha en prodCtx där organisation_id är samma som den du angav i din URL för Adobe.io för att kunna dirigera din begäran.
Om IMS-etableringen saknas måste den korrigeras.

```
-X GET https://mc.adobe.io/{ORGANIZATION}/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Det returnerar följande fel.

```
{"error_code":"403023","message":"Profile is not valid"}
```

Kontrollera din IMS-profil med denna begäran.

```
-X GET https://ims-na1.adobelogin.com/ims/profile/v1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

I svaret måste värdet för ORGANIZATION_ID vara detsamma i din första GET-begäran.

```
{
  "countryCode": "FR",
  "mrktPermEmail": null,
  "projectedProductContext": [
    {
    "prodCtx": {
      "statusCode": "ACTIVE",
      "ident": "ZQ9FRQK7BF09YXAESFY9DDQP1G",
      "modDts": 1448307260000,
      "organization_id": "actest",
      "owningEntity": "6096892F54B5819E0A4C98A2@AdobeOrg",
      "serviceCode": "dma_tartan",
      "label": "Adobe Marketing Cloud",
      "serviceLevel": "standard",
      "createDts": 1421181343000,
      "deal_id": " "
      }
    }
  ]
}
```

* **När du skickar en begäran till Adobe.io får du {&quot;code&quot;:500, &quot;message&quot;:&quot;Oops. Något gick fel. Kontrollera din URI och försök igen.&quot;}**

Adobe.io deklarerar din ogiltiga URI: troligtvis är den URI du begär inte giltig. När du väljer tjänsten Campaign i Adobe.io får du en väljare med en lista över möjliga organisations_ids. Du måste kontrollera att den du väljer är den som du anger i URL:en.

* **När du skickar en begäran till Adobe.io får du {&quot;error_code&quot;:&quot;401013&quot;,&quot;message&quot;:&quot;Oauth-token är inte giltig&quot;}**

Antingen är din token ogiltig (felaktigt IMS-anrop som används för att generera en token) eller så har din token gått ut.

* **Jag kan inte se min profil när den har skapats**

Beroende på instanskonfigurationen måste den skapade profilen kopplas till en **orgUnit**. Mer information om hur du lägger till det här fältet när du skapar finns i [det här avsnittet](creating-profiles-api.md).

<!-- * (error duplicate key : quand tu crées un profile qui existe déjà , il faut faire un patch pour updater le profile plutôt qu'un POST)

With Curl
List all profiles

Create a profile

Update the mobilePhone attribute of a profile

API Calls on Service

GET the list of services

-->

<!--

How to find and use a filter?
Error codes:

* PAtch sur Age = message d'erreur :
500
Cannot update the 'age' property that is read-only
'age' property is not valid for the 'profile' resource.
-->

<!--
How to filter a list of subscribed profiles with available profile filters ? by date (by les filtres dispo sur la ressource) ?

Pattern classique :

recupérer la liste des subscriptions filtrées d'un profile
1) get sur profile
2) recup PKey
3) get sur PKey
4) get sur href des subscriptions

Comment savoir quel filtre appliquer ?

1) get sur metadata de profile
2) retourne description de la collection subscription
3) get sur la valeur du champ resTarget
4) get sur le href dans filters
5) retourne les filtres applicables sur l'url des data.

-->
