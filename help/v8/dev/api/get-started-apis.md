---
title: Kom igång med Campaign REST API:er
description: Skapa integreringar och skapa ett eget ekosystem genom att interagera Campaign med en panel med tekniker.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
exl-id: c6968252-a012-4029-bbb8-66f4f693e99b
source-git-commit: 115b7b6824f3736e03f9fb87898f1264f9bab636
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 40%

---

# Kom igång med Campaign REST API:er {#get-started-apis}

Kampanj-REST-API:er är avsedda för att du ska kunna **skapa integreringar** för Adobe Campaign och **skapa ett eget ekosystem** genom att interagera med Adobe Campaign med den panel med tekniker som du använder.

>[!AVAILABILITY]
>
>* Den här funktionen är bara tillgänglig på begäran för alla [Campaign FDA-miljöer](../../architecture/fda-deployment.md). Det är **inte** tillgängligt för [Enterprise-distributioner (FFDA)](../../architecture/enterprise-deployment.md). Kontakta din Adobe-representant för att få åtkomst.
>
>* Innan du genomför API-anrop bör du kontrollera de begränsningar för skalor som motsvaras i licensavtalet. Mer information finns i produktbeskrivningen för [Adobe Campaign v8](https://helpx.adobe.com/se/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.


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

