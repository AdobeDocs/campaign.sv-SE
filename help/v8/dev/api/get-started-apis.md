---
title: Kom igång med Campaign REST API:er
description: Skapa integreringar och skapa ett eget ekosystem genom att interagera Campaign med en panel med tekniker.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
exl-id: c6968252-a012-4029-bbb8-66f4f693e99b
source-git-commit: c74669a0ccdabe735eb905b7e8c1634140a7ea0b
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 47%

---

# Kom igång med Campaign REST API:er {#get-started-apis}

>[!AVAILABILITY]
>
>Den här funktionen är bara tillgänglig på begäran för alla Campaign FDA-miljöer. Det är **inte** tillgängligt för Campaign FFDA-distributioner. Kontakta din Adobe-representant för att få åtkomst.

>[!CAUTION]
>
>Innan du genomför API-anrop bör du kontrollera de begränsningar för skalor som motsvaras i licensavtalet. Se denna [sida](https://helpx.adobe.com/se/legal/product-descriptions/campaign-standard.html#ITInfrastructureResourcesbyActiveProfilesTiers) för mer information om detta.

Kampanj-REST-API:er är avsedda för att du ska kunna **skapa integreringar** för Adobe Campaign och **skapa ett eget ekosystem** genom att interagera med Adobe Campaign med den panel med tekniker som du använder.

Med Adobe Campaign REST API:er får du tillgång till följande funktioner:

<table><tr>
 <td valign="top"><a href="retrieving-profiles.md"><img width="60px" alt="villkor" src="assets/icon_profile.svg"/></a><p><a href="retrieving-profiles.md">Profiler</a></p></td>
<td valign="top"><a href="creating-a-service.md"><img width="60px" alt="villkor" src="assets/icon_services.svg"/></a><p><a href="creating-a-service.md">Tjänster och prenumerationer</a></p></td>
<td valign="top"><a href="interacting-with-custom-resources.md"><img width="60px" alt="villkor" src="assets/icon_customresources.svg"/></a><p><a href="interacting-with-custom-resources.md">Anpassade resurser</a></p></td>
<td valign="top"><a href="controlling-a-workflow.md"><img width="60px" alt="villkor" src="assets/icon_workflows.svg"/></a><p><a href="controlling-a-workflow.md">Arbetsflöden</a></p></td>
<td valign="top"><a href="managing-transactional-messages.md"><img width="60px" alt="villkor" src="assets/icon_transactionalmessage.svg"/></a><p><a href="managing-transactional-messages.md">Transaktionsmeddelanden</a></p></td>
</tr></table>

Om du vill använda Campaign REST API:er måste du ha ett Adobe I/O-konto. Detta är ett obligatoriskt första steg för att fortsätta och upptäcka API-funktionerna.
Mer information om detta finns i [det här avsnittet](setting-up-api-access.md).

De API:er vi tillhandahåller använder **standardkoncept** med ett REST-gränssnitt och JSON-nyttolaster.

Alla slutpunkter beskrivs ingående i den här dokumentationen med de allmänna synpunkterna som du bör känna till när du hanterar API:t, den fullständiga API-referensen, kodexempel och snabbstartguider. Alla exempel fungerar med Postman men du kan använda valfri REST-klient.

Om något saknas eller verkar vara felaktigt kan du fråga vår [community](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-standard/ct-p/adobe-campaign-standard-community).
