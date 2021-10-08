---
title: 'Kom igång med API:er i Campaign '
description: 'Kom igång med API:er i Campaign '
feature: Overview
role: Data Engineer
level: Beginner
source-git-commit: 391eac2f5e4d4c8c5d4dadd3394798361640e1d8
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 5%

---

# Kom igång med [!DNL Campaign] API:er{#gs-ac-api}

[!DNL Adobe Campaign] innehåller en uppsättning JavaScript-funktioner som du kan använda:

* i skript - i [!DNL Adobe Campaign]-arbetsflöden
* via API:er - från externa system

Du kan använda JavaScript-API:er för att skriva i Campaign-molndatabasen eller läsa från databasen:

* Affärsspecifika API:er där du kan agera på varje objekt: leveranser, arbetsflöden, prenumerationer och så vidare. Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/api/business-oriented-apis.html).
* Generiska API:er för dataåtkomst för att fråga om datamodelldata. Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/api/data-oriented-apis.html).

Campaign v8 fungerar med två databaser: en lokal databas för användargränssnittet för meddelanden i realtid och enhetliga frågor och skrivningar via API:er samt en molndatabas för kampanjkörning, rapportering, datainhämtning, batchfrågor och arbetsflödeskörning.

>[!CAUTION]
>
>[!DNL Adobe Campaign] v8 har en begränsning av genomströmningen (TPS) för vårt API-lager. Om gränsen överskrids uppstår ett vanligt HTTP-fel (429). Som användare av hanterade Cloud Services kan du kontakta Adobe för att anpassa begränsningen för varje API.

## Förhandskrav

Innan du använder [!DNL Adobe Campaign] API:er måste du känna till följande:

* JavaScript
* SOAP-protokoll
* [!DNL Adobe Campaign] datamodell

Om du vill använda API:er och interagera med [!DNL Adobe Campaign] måste du också känna till din datamodell.

>[!NOTE]
>Du kan generera en fullständig beskrivning av din datamodell. Läs mer i [den här sidan](datamodel.md).

## [!DNL Campaign] API-mellanlagringsmekanism

Med [!DNL Campaign] Cloud-databasen rekommenderas inte snabba enhetsanrop på grund av prestanda (fördröjning och samtidighet). Gruppåtgärd är alltid att föredra. För att garantera optimala prestanda för API:er fortsätter Campaign att hantera API-anrop på lokal databasnivå.

![](../assets/do-not-localize/glass.png) [API-mellanlagringsmekanismen beskrivs på den här sidan](staging.md)

## Nya API:er

Det finns nya API:er tillgängliga för att hantera datasynkronisering mellan den lokala databasen [!DNL Campaign] och molndatabasen. En ny mekanism har också introducerats för att hantera API-anrop på lokal databasnivå för att undvika fördröjning och öka den övergripande prestandan.

![](../assets/do-not-localize/glass.png) [Nya API:er finns på den här sidan](new-apis.md)

**Relaterade ämnen**

* [God praxis för datamodell](datamodel-best-practices.md)
