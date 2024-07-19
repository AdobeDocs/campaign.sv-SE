---
title: Kom igång med Campaign-API:er
description: Kom igång med Campaign-API:er
feature: API
role: Developer
level: Intermediate, Experienced
exl-id: 50e21acd-d23d-4fdd-a8aa-23c3f209bda3
source-git-commit: 07e85c2933194a24b4275519dd7da9c3226f6a3c
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 9%

---

# Kom igång med [!DNL Campaign] API:er {#gs-ac-api}

[!DNL Adobe Campaign] innehåller en uppsättning JavaScript-funktioner som du kan använda:

* i skript - i [!DNL Adobe Campaign] arbetsflöden
* via API:er - från externa system

Du kan använda JavaScript API:er för att skriva i Campaign-molndatabasen eller läsa från databasen:

* Affärsspecifika API:er som du kan använda för varje objekt: leveranser, arbetsflöden, prenumerationer och så vidare. Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/api/business-oriented-apis.html){target="_blank"}.
* Generiska API:er för dataåtkomst för att fråga om datamodelldata. Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/api/data-oriented-apis.html){target="_blank"}.

Observera att Campaign fungerar med två databaser i sin [Enterprise-distribution](../architecture/enterprise-deployment.md): en lokal databas för meddelanden i realtid i användargränssnittet och enhetsfrågor och skriva via API:er, samt en molndatabas för kampanjkörning, rapportering, datainhämtning, batchfrågor och arbetsflödeskörning.

>[!CAUTION]
>
>* Som en Campaign-användare som övergår från Campaign Standard kan ni använda REST API:er med Campaign v8. [Läs mer](https://experienceleague.adobe.com/en/docs/experience-cloud/campaign/apis/get-started-apis){target="_blank"}.
>
>* Från och med Campaign v8.5.1 ändrades autentiseringsprocessen till Campaign v8. Tekniska operatörer måste använda Adobe Identity Management System (IMS) för att ansluta till Campaign. Lär dig hur du migrerar dina befintliga tekniska konton i [det här tekniska dokumentet](../../technotes/upgrades/ims-migration.md).
>
>* [!DNL Adobe Campaign] v8 har en begränsning av genomströmningen (TPS) för vårt API-lager. Om gränsen överskrids uppstår ett vanligt HTTP-fel (429). Som användare av hanterade Cloud Service kan du kontakta Adobe för att anpassa begränsningen för varje API.
> 

## Förhandskrav {#ac-api-prerequisites}

Innan du använder [!DNL Adobe Campaign] API:er måste du känna till följande ämnen:

* JavaScript
* SOAP
* [!DNL Adobe Campaign] datamodel

Om du vill använda API:er och interagera med [!DNL Adobe Campaign] måste du också känna till din datamodell.

>[!NOTE]
>Du kan generera en fullständig beskrivning av din datamodell. Läs mer på [den här sidan](datamodel.md).


**Relaterade ämnen**

* [God praxis för datamodell](datamodel-best-practices.md)
