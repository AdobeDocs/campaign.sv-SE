---
title: Rekommendationer och begränsningar
description: Rekommendationer och begränsningar vid migrering till Campaign v8 REST API:er.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
mini-toc-levels: 1
exl-id: 45acebb1-9325-4e26-8fe9-cc73f745d801
source-git-commit: 4ed5799c77c647c9f1aeabba7645fbb475d03c09
workflow-type: tm+mt
source-wordcount: '1050'
ht-degree: 1%

---

# Rekommendationer och begränsningar {#limitations}

## Behörigheter och säkerhet {#permissions}

### Mappning av produktprofiler

I Campaign Standard fick du förhöjd administratörsrollåtkomst till API:er oavsett din tilldelade produktprofil. I Campaign v8 introduceras en annan uppsättning produktprofiler, vilket kräver mappning från produktprofiler för Campaign Standard till Campaign v8.

Med migreringen läggs två produktprofiler till i dina befintliga eller redan skapade tekniska konton: Administratör och Meddelandecenter (för åtkomst till transaktionsprogrammeringsgränssnitt). Granska mappningen av produktprofiler och tilldela den produktprofil som behövs om du inte vill att Admin-produktprofilen ska mappas till ditt tekniska konto.

### Klient-ID

Efter migreringen, för framtida integreringar, rekommenderas att du använder ditt **Campaign v8-klientorganisations-ID** i REST-URL:er och ersätter ditt tidigare Campaign Standard-klientorganisations-ID.

### Nyckelanvändning

Hanteringen av PKey-värden skiljer sig mellan Campaign Standard och Campaign v8. Om du lagrade PKeys med Campaign Standard bör du se till att implementeringen dynamiskt skapar efterföljande API-anrop med PKeys eller hrefs från tidigare API-anrop.

## Tillgängliga API:er {#deprecated}

För närvarande är REST API:erna som listas nedan tillgängliga:

* **Profiler**
* **Tjänster och prenumerationer**
* **Anpassade resurser**
* **Arbetsflöden**
* **Transaktionsmeddelanden**

>[!AVAILABILITY]
>
>För närvarande är REST API:t för **transaktionsmeddelanden** inte tillgängligt.
>
>REST-API:erna som anges nedan är inaktuella och kan inte användas:
>* Marknadsföringshistorik
>* Organisationsenheter
>* Integritetshantering

## Filtrering

* Om du vill använda dina filter i REST API-nyttolaster måste du redigera dem i Campaign v8 och ange ett namn att använda i dina nyttolaster. Om du vill göra det kommer du åt filtrets ytterligare parametrar på fliken **[!UICONTROL Parameters]** och anger önskat namn i fältet **[!UICONTROL Filter name in REST API]**.

  ![](assets/api-filtering.png)


* Det by-prefix som krävs för att använda anpassade filter behövs inte längre. Filternamnet ska användas som det är i dina förfrågningar.

  Exempel:

  `GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/<customFilterName>?<customFilterparam>=<customFilterValue>`

## Ignorerade databasfält

Vissa fält från databasen tas bort under migreringen. När du använder ett släppt fält returnerar REST-API:er tomma värden. I framtiden kommer alla borttagna fält att bli inaktuella och tas bort.

## POST med länkade resurser

När du använder följande body-format för begäran, där &quot;vehikelägare&quot; representerar länken till &quot;nms:mottagare&quot;:

```
{
    "vehicleNumber": "20009",
    "vehicleName": "Model E",
    "vehicleOwner":{
        "firstName":"tester 11",
        "lastName":"Smith 11"
    }
}
```

Länkinformationen ignoreras. Följaktligen genereras en ny post under&quot;cusVehicle&quot; som endast innehåller värdena&quot;VehicleNumber&quot; och&quot;VehicleName&quot;. Länken är emellertid fortfarande null, vilket resulterar i att&quot;vehikelägare&quot; ställs in på null.

I Campaign v8 inträffar ett fel när samma frågetexakthjälpstruktur används och&quot;vehikeln&quot; är kopplad till en profil. Det här felet inträffar eftersom egenskapen &quot;firstName&quot; inte känns igen som giltig för &quot;cusVehicle&quot;. En begärandetext som bara innehåller attributen utan länkfunktionerna utan några problem.

## PATCH

* Campaign v8 stöder inte PATCH med en tom begärandetext: den returnerar statusen 204 Inget innehåll.
* Även om Campaign Standard har stöd för PATCH för element/attribut i ett schema, bör du tänka på att PATCH-åtgärder på plats inte stöds i Campaign v8. Om du försöker köra en PATCH på plats uppstår ett internt 500-serverfel med ett felmeddelande som anger att zipCode-egenskapen inte är giltig för profile-resursen.

## REST-svar

I avsnittet nedan visas mindre skillnader mellan Campaign Standard och v8 REST-svar.

* För enstaka GET-poster inkluderar svaret href i svaret.
* När Campaign v8 efterfrågas med attributet tillhandahåller den Count och Pagination i svaret.
* Efter POST-åtgärder returneras värden från länkade resurser i svaret.

## Felkoder och meddelanden

I avsnittet nedan listas skillnaderna mellan felkoder och meddelanden för Campaign Standard och Campaign v8.

| Scenario | Campaign Standard | Campaign v8 |
|  ---  |  ---  |  ---  |
| Använd en ogiltig PKey i begärandetexten | 500 - Attributet O5iRp40EGA är okänt (se definitionen av schemat Profiler (nms:receive). XTK-170036 Det gick inte att parsa uttrycket &#39;@id = @O5iRp40EGA&#39;. | 404 - Det gick inte att dekryptera PKey. (PKey=@jkledsen) |
| Använd en ogiltig PKey i URI | 500 - Attributet O5iRp40EGA är okänt (se definitionen av schemat Profiler (nms:receive). XTK-170036 Det gick inte att parsa uttrycket &#39;@id = @O5iRp40EGA&#39;. | 404 - Det gick inte att dekryptera PKey. (PKey=@jkledsen) Slutpunkten stöds inte. (endpoint=rest/profileAndServices/profile/@jkledsen) |
| Använda två olika raw-nycklar i URI:n och begärandetexten | 500 - RST-360011 Ett fel har inträffat - kontakta administratören. RST-360012 Inkonsekvent åtgärd för resursen service - Det går inte att uppdatera nyckeln SVC3 till SVC4. | 500 - Ett fel har inträffat. Kontakta administratören. |
| Använda PKey i URI:n och en annan PKey i begärandetexten | 500 - Det finns redan en tjänst med samma nyckel, SVC4. PGS-220000 PostgreSQL-fel: FEL: Dubblettnyckelvärdet bryter mot den unika begränsningen &quot;nmsservice_name&quot; DETAIL: Key (sname)=(SVC4) finns redan. | 500 - Ett fel har inträffat. Kontakta administratören. |
| Använda ett icke-befintligt raw-id i URI | 404 - RST-360011 Ett fel har inträffat. Kontakta administratören. Det gick inte att hitta dokumentet med sökvägen Service från nyckeln adobe_nl:0 (dokument med schemat service och namnet adobe_nl) | 404 - Det går inte att hitta dokumentet med sökvägen Service från nyckeln adobe_nl (dokument med schemat service och namnet adobe_nl) |
| Använda ett icke-befintligt raw-id i begärandetexten | 404 - RST-360011 Ett fel har inträffat. Kontakta administratören. Det gick inte att hitta dokumentet med sökvägen Service från nyckeln adobe_nl (dokument med schemat service och namnet adobe_nl) | 404 - Det går inte att hitta dokumentet med sökvägen Service från nyckeln adobe_nl (dokument med schemat service och namnet adobe_nl) |
| - | 500 - RST-360011 Ett fel har inträffat - kontakta administratören. | 500 - Ett fel har inträffat. Kontakta administratören. |
| Infoga en profil/tjänst med ett ogiltigt enum-värde för kön (eller något annat) | 500 - RST-360011 Ett fel har inträffat - kontakta administratören. Värdet invalid är inte giltigt för nms:recipient:kön-uppräkningen i fältet @kön | 500 -Ett fel har inträffat - kontakta administratören. |

## Profil - tidszon

Med Campaign Standard visas tidszonen som en del av JSON-svaret för REST-API-anrop för **profileAndServices/profile**.

Med Campaign v8 visas tidszonen endast för användaren som en del av **profileAndServicesExt/profile** REST API-anrop. Det ingår inte i **profileAndServices/profile** REST API-anrop eftersom det läggs till i ett utökat schema.

## Arbetsflöden - Extern signalutlösare

Campaign Standard Workflow GET API returnerar parameternamn som arbetsflödesinstansvariabler och deras datatyper (boolesk, sträng osv.). Detta används för att skapa korrekt formaterad JSON-begärandetext när signalen aktiveras via ett POST API-anrop.

Campaign v8 stöder inte variabler för annonsarbetsflödesinstanser, men förväntar sig att utvecklare ska veta vad de är. Efter migreringen måste parameterinformationen i POST-begärandetexten konstrueras utan att parameterinformationen i GET API-svaret är tillgänglig.

<!--## Transactional messages

* With Campaign Standard, a POST request returns empty fields for elements and attributes in the request body. With Campaign v8, the response returns values that match the ones in the request body instead.

* When publishing an event configuration, the API preview panel displays the REST URL alongside the request body syntax.

    Since Campaign v8 does not support event configuration fields definition (event creation is just adding a value to eventType enumeration), there is no API preview panel when adding an event type. The REST URL is displayed  in the transactional message user interface once an event transactional message is published.-->
