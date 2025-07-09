---
title: Slutpunkter
description: Läs mer om API:ernas slutpunkter.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
exl-id: 9f6d3da6-374d-47f5-bc8f-b31b19cbb5ca
source-git-commit: 4ed5799c77c647c9f1aeabba7645fbb475d03c09
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 9%

---

# Slutpunkter {#endpoints}

Tillgängliga slutpunkter för Adobe Campaign REST API:

* **/profileAndServices**: interagerar med utanför rutfälten. Utökade fält är inte tillgängliga med den här slutpunkten.
* **/profileAndServicesExt**: interagerar med anpassade fält som lagts till under det anpassade resurstillägget för profil eller tjänster. Mer information om anpassade resurser finns i [det här avsnittet](custom-resources.md).
* **/&lt;transactionalAPI>**: interagerar med API:t för transaktionsmeddelanden (namnet på API-slutpunkten för transaktionsmeddelanden beror på instanskonfigurationen). Mer information om detta finns i [det här avsnittet](managing-transactional-messages.md).
* **/workflow/execution**: interagerar med arbetsflöden. Mer information om detta finns i [det här avsnittet](controlling-a-workflow.md).

Som standard är huvudresurserna som är tillgängliga för API:erna **profileAndServices** och **profileAndServicesExt**:

* **/profile**: interagerar med profiler från Campaign-databasen. Använd slutpunkten **/service** om du vill lägga till profiler i en tjänst. Mer information om profiler i Campaign finns i [Campaign-dokumentationen](https://helpx.adobe.com/se/campaign/standard/audiences/using/about-profiles.html).
* **/service**: hantera prenumerationstjänster. Mer information om tjänster i Campaign finns i [Campaign-dokumentationen](https://helpx.adobe.com/se/campaign/standard/audiences/using/creating-a-service.html).

>[!NOTE]
>
>Alla andra resurser som har utökats eller skapats är endast tillgängliga via API:t **ProfileAndServicesExt** . De måste vara länkade till **profilresursen** för att vara tillgängliga.
