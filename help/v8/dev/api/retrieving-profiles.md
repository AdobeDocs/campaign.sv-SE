---
title: Hämta profiler
description: Läs mer om hur du hämtar profiler med API:er
role: Data Engineer
level: Experienced
exl-id: 19679804-f728-49fa-b26e-8f31b67c29bf
source-git-commit: 4ed5799c77c647c9f1aeabba7645fbb475d03c09
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 4%

---

# Hämta profiler med API:er {#retrieving-profiles}

Hämtning av profiler utförs med en **GET**-begäran.

Du kan sedan förfina sökningen med filter, ordning och sidnumrering. Mer information finns i avsnittet [Ytterligare åtgärder](sorting.md).

Med Campaign Standard API:er kan du dessutom söka efter profiler som baseras på något av dessa fält: e-post, förnamn, efternamn eller andra anpassade fält. Mer information om detta finns i [det här avsnittet](#searching-field).

<br/>

***Exempelbegäranden***

* Exempelbegäran från GET om att hämta alla profiler.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
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
          },
          ...
  }
  ```

* Exempel på GET-begäran om att hämta de första 10 e-postvärdena.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10 \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Svar på begäran. Noden &quot;next&quot; returnerar den URL som ger dig tillgång till de 10 nästa e-postvärdena.

  ```
  {
  "content": [
      "amy.dakota@mail.com",
      "kristen.smith@mail.com",
      "omalley@mail.com",
      "xander.harrys@mail.com",
      "jane.summer@mail.com",
      "gloria.boston@mail.com",
      "edward.snow@mail.com",
      "dorian.simons@mail.com",
      "peter.paolini@mail.com",
      "mingam+test08@adobe.com"
  ],
  "next": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
      lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
  }
  }
  ```

## Söka efter profiler baserade på ett fält {#searching-field}

Med parametern **[!UICONTROL filterType]** kan du hämta profiler baserat på något av följande fält: e-post, förnamn, efternamn eller andra anpassade fält som har lagts till i avancerad filtrering när profilresursen utökas.

>[!NOTE]
>
>Sökningar är skiftlägeskänsliga och utförs endast med prefix. Du kan till exempel inte leta efter en profil med hjälp av efternamnets sista bokstäver.

***Exempelbegäranden***

* Exempelbegäran om att filtrera profiler baserat på förnamn.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John&filterType=firstName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Exempelbegäran om att filtrera profiler baserat på efternamn.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Miller&filterType=lastName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Exempelbegäran om att filtrera profiler baserat på e-post.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John%40gmail.com&filterType=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Exempelbegäran om att filtrera profiler baserat på det anpassade fältet &quot;Hobby&quot;.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byText?cusHobby=Dancing&filterType=Hobby \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```
