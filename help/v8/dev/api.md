---
title: 'Kom igång med API:er i Campaign '
description: 'Kom igång med API:er i Campaign '
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 50e21acd-d23d-4fdd-a8aa-23c3f209bda3
source-git-commit: 6de5c93453ffa7761cf185dcbb9f1210abd26a0c
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 7%

---

# Kom igång med [!DNL Campaign] API:er{#gs-ac-api}

[!DNL Adobe Campaign] innehåller en uppsättning JavaScript-funktioner som du kan använda:

* i skript - in [!DNL Adobe Campaign] arbetsflöden
* via API:er - från externa system

Du kan använda JavaScript-API:er för att skriva i Campaign-molndatabasen eller läsa från databasen:

* Affärsspecifika API:er där du kan agera på varje objekt: leveranser, arbetsflöden, prenumerationer och så vidare. Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/api/business-oriented-apis.html).
* Generiska API:er för dataåtkomst för att fråga om datamodelldata. Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/api/data-oriented-apis.html).

Campaign v8 fungerar med två databaser: en lokal databas för användargränssnittet för meddelanden i realtid och enhetliga frågor och skrivningar via API:er samt en molndatabas för kampanjkörning, rapportering, datainhämtning, batchfrågor och arbetsflödeskörning.

>[!CAUTION]
>
>[!DNL Adobe Campaign] v8 har en begränsning av genomströmningen (TPS) för vårt API-lager. Om gränsen överskrids uppstår ett vanligt HTTP-fel (429). Som användare av hanterade Cloud Services kan du kontakta Adobe för att anpassa begränsningen för varje API.

## Förhandskrav

Innan du använder [!DNL Adobe Campaign] API:er måste du känna till följande:

* JavaScript
* SOAP-protokoll
* [!DNL Adobe Campaign] datamodell

För att kunna använda API:er och interagera med [!DNL Adobe Campaign]måste du också känna till din datamodell.

>[!NOTE]
>Du kan generera en fullständig beskrivning av din datamodell. Läs mer i [den här sidan](datamodel.md).


**Relaterade ämnen**

* [God praxis för datamodell](datamodel-best-practices.md)