---
product: campaign
title: Kampanjwebbkomponenter och version 100 i webbläsarna Chrome Firefox och Edge
description: Kampanjwebbkomponenter och version 100 i webbläsarna Chrome, Firefox och Edge
hide: true
hidefromtoc: true
exl-id: 912ad71e-2b23-4b16-b5f9-47d547fc83d5
source-git-commit: b71197027d9521fd648a0c2657b6b76a1aa7fc9a
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# 3-siffrig webbläsarversion påverkar webbkomponenterna i Campaign {#version-100}

Google och Mozilla varnar för att Chrome och Firefox kan bryta ned vissa webbplatser på grund av kommande 3-siffriga versioner.

Chrome v100 är inställd för release den **29 mars 2022** och Firefox v100 på **3 maj 2022**.

Microsoft släppte Edge v100 tidigare i mars 2022.

Ändringen av versionsnumret från 2 till 3 siffror kan orsaka vissa problem när du besöker webbplatser som inte är förberedda för den här ändringen. Vissa webbsidor kan sluta visas korrekt i de nya webbläsarversionerna.

Kompatibiliteten för större webbplatser har testats i förväg. Om det uppstår problem med webbplatser som inte kan åtgärdas innan versionerna släpps har företagen planer för säkerhetskopiering som är klara att säkerställa att webbplatserna inte påverkas.

Potentiella problem eller funktionsförlust på webbplatsen kommer från användaragentsträngen som webbläsare skickar till webbplatser du besöker: användaragenten är en sträng som skickas av webbläsaren till webbplatsen för att tala om vilken webbläsare och version du använder samt tillhörande teknik. När webbläsaren skickar en begäran till en webbplats identifieras den med användaragentsträngen innan innehållet som du begärde hämtas. Data i användaragentsträngen hjälper webbplatsen att leverera innehållet i ett format som passar din webbläsare. Versionen av användaragenten ökas så att den matchar webbläsarens versionsnummer. Att gå från 2 till 3 siffror kan orsaka problem.

## Påverkas du?{#version-100-impact}

Adobe rekommenderar att du testar dina Campaign-webbprogram, inklusive webbformulär och enkäter, så att de fortfarande fungerar bra med de nya webbläsarversionerna.

Den här rekommendationen gäller alla webbprogram, särskilt om du har inkluderat JavaScript-kod.

Du måste kontrollera med alla webbläsare, mobiler och datorer.

## Hur testar man?{#version-100-test}

Du kan konfigurera webbläsarna så att de rapporterar versionen som 100 just nu, och sedan rapportera och korrigera eventuella problem du stöter på.

Med de här inställningarna skickar webbläsaren den nya användaragentsträngen till webbplatser, vilket anger att webbläsaren är v100. Om du stöter på problem med dina webbformulär bör du skapa ett fel för webbläsarredigeraren. Överväg att återskapa dessa webbformulär innan uppdateringarna är allmänt tillgängliga.

### Testa med Firefox 100{#test-firefox-100}

Om du vill testa dina webbsidor med Mozilla Firefox 100 kan du simulera den kommande användaragentändringen i dina webbprogram genom att manuellt ändra användaragentsträngen.

1. Öppna Firefox, ange `about:config` i adressfältet och tryck på Retur.
1. Sök efter `general.useragent.override`.
1. Välj String och klicka sedan på plustecknet (+).

   ![](assets/force-user-agent-firefox.png)

1. Ange följande text i fältet:

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Klicka på den blå bockmarkeringsknappen för att spara inställningen.
1. Stäng och starta om webbläsaren.

Gå tillbaka till `about:config` och söka efter `general.useragent.override` igen.  När den visas klickar du på papperskorgsikonen för att ta bort inställningen och startar om webbläsaren.

### Testa med Chrome 100{#test-chrome-100}

Om du vill testa Google Chrome 100-användaragenten i dina egna webbprogram kan du aktivera det här testet genom att följa de här stegen:

1. Öppna Chrome, ange `chrome://flags` i adressfältet och tryck på Retur.
1. Sök `Force major version to 100 in User-Agent` i sökfältet och aktivera det så som visas nedan.

   ![](assets/force-user-agent-chrome.png)

1. Starta om webbläsaren.
1. Stäng `chrome://flags` -fliken.

Om du vill ändra användaragenten tillbaka till standardinställningen följer du bara den här processen och ändrar flaggans inställning till `Default` och starta om webbläsaren.


### Testa med Microsoft Edge 100{#test-ms-edge-100}

Från och med v97 kan webbplatsägare emulera den här versionen genom att aktivera experimentflaggan  `#force-major-version-to-100` in `edge://flags`.

1. Öppna Microsoft Edge, ange `edge://flags` i adressfältet och tryck på Retur.
1. Sök efter `force-major-version-to-100` och aktivera enligt nedan.

   ![](assets/force-user-agent-edge.png)

1. Starta om webbläsaren.
1. Stäng `edge://flags` -fliken.

Om du vill ändra användaragenten tillbaka till standardinställningen följer du bara den här processen och ändrar flaggans inställning till `Default` och starta om webbläsaren.
