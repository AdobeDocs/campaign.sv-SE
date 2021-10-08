---
title: Kom igång med Campaign-arkitekturen
description: Upptäck miljöer och grunderna om driftsättning
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 562b24c3-6bea-447f-b74c-187ab77ae78f
source-git-commit: 9e07353859e63b71abb61526f40675f18837bc59
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Kom igång med Campaign-arkitekturen{#gs-ac-archi}

## Miljö

Campaign blir tillgängligt som enskilda instanser där varje instans representerar en komplett Campaign-miljö.

Tre typer av miljöer tillgängliga med Campaign Cloud Service:

* **Produktionsmiljö**: är värd för de ansökningar som riktar sig till yrkesverksamma.

* **Scenmiljö**: används för olika prestanda- och kvalitetstester innan ändringar i programmet överförs till produktionsmiljön.

* **Utvecklingsmiljö**: ger utvecklare möjlighet att implementera Campaign under samma körningsförhållanden som scen- och produktionsmiljöerna.

Du kan exportera och importera paket från en miljö till en annan.

![](../assets/do-not-localize/book.png) Läs mer om paket i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/administration-basics/working-with-data-packages.html)

## Driftsättning via mid-sourcing{#mid-sourcing-deployment}

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/architecture.png)

* Modulerna för exekvering och studshantering är inaktiverade på instansen.

* Programmet är konfigurerat för att utföra meddelandekörning på en fjärrserver med &quot;mellanlagring&quot; som drivs med SOAP-anrop (via HTTP eller HTTPS).

>[!NOTE]
>
> Campaign v8 bygger på en hybridarkitektur. Om du går över från Campaign Classic v7 bör du tänka på att alla leveranser går via servern för mellanlagring.
> Därför är intern routning **inte möjlig** i Campaign v8, och det externa kontot har inaktiverats i enlighet med detta.

## Meddelandecenterarkitektur{#transac-msg-archi}

Transactional messaging (Message Center) är den Campaign-modul som är avsedd för hantering av utlösarmeddelanden.

![](../assets/do-not-localize/glass.png) Lär dig hur du skickar transaktionsmeddelanden i  [det här avsnittet](../send/transactional.md).

Som svar på en åtgärd från en kund på en webbplats skickas en händelse till Campaign via ett REST API, och meddelandemallen fylls i med informationen eller data som tillhandahålls via API-anropet och ett transaktionsmeddelande skickas i realtid till kunden. Dessa meddelanden kan skickas individuellt eller gruppvis via e-post, SMS eller push-meddelanden.

I den här specifika arkitekturen separeras körningscellen från kontrollinstansen för att säkerställa hög tillgänglighet och lasthantering.

* **Kontrollinstansen** (eller marknadsföringsinstansen) används av marknadsförare och IT-team för att skapa, konfigurera och publicera meddelandemallar. Den här instansen centraliserar också händelseövervakning och historik.

   ![](../assets/do-not-localize/glass.png) Lär dig hur du skapar och publicerar meddelandemallar i  [det här avsnittet](../send/transactional.md).

* **Körningsinstansen** hämtar inkommande händelser (lösenordsåterställning eller order från en webbplats till exempel) och skickar personliga meddelanden. Det kan finnas mer än en körningsinstans för att bearbeta meddelanden via belastningsutjämnaren och skala antalet händelser som ska bearbetas för maximal tillgänglighet.

>[!CAUTION]
>
>Kontrollinstansen och körningsinstansen/körningsinstanserna måste vara installerade på olika datorer. De kan inte dela samma Campaign-instans.

![](assets/messagecenter_diagram.png)

### Autentisering

Om du vill använda dessa funktioner loggar Adobe Campaign-användare in på kontrollinstansen för att skapa transaktionsmeddelandemallar, generera meddelandeförhandsvisningen med hjälp av en startlista, visa rapporter och övervaka körningsinstansen/instanserna.

* Enkel körningsinstans
När du interagerar med en körningsinstans i ett meddelandecenter på Adobe kan ett externt system först hämta en sessionstoken (som förfaller om 24 timmar) genom att anropa sessionsinloggningsmetoden med en tillhandahållen kontoinloggning och ett lösenord.
Med den sessionToken som tillhandahålls av körningsinstansen som svar på ovanstående anrop, kan det externa programmet göra SOAP api-anrop (rtEvents eller batchEvents) för att skicka kommunikation, utan att behöva inkludera kontoinloggning och lösenord i varje SOAP-anrop.

* Flera körningsinstanser
I en arkitektur för körning av flera celler med flera körningsinstanser bakom en belastningsutjämnare, går den inloggningsmetod som anropas av det externa programmet igenom belastningsutjämnaren: Därför kan ingen tokenbaserad autentisering användas. En användar-/lösenordsbaserad autentisering krävs.

![](../assets/do-not-localize/book.png) Läs mer om Transactional Messaging-händelser i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/processing/event-description.html#about-transactional-messaging-datamodel)