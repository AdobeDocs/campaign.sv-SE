---
title: Kom igång med Campaign-arkitekturen
description: Identifiera miljöer och grundläggande distributionsmöjligheter, inklusive hur du rapporterar om en kampanjmiljö.
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 562b24c3-6bea-447f-b74c-187ab77ae78f
source-git-commit: 618e45b6948070c6b791d2bcefa8296b297bf25e
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 2%

---

# Kom igång med Campaign-arkitekturen{#gs-ac-archi}

## Miljöer {#environments}

Campaign blir tillgängligt som enskilda instanser där varje instans representerar en komplett Campaign-miljö.

Det finns två typer av miljöer:

* **Produktionsmiljö**: är värd för de ansökningar som riktar sig till yrkesverksamma.

* **Icke-produktionsmiljö**: används för olika prestanda- och kvalitetstester innan ändringar i programmet överförs till produktionsmiljön.

Du kan exportera och importera paket från en miljö till en annan.

![](../assets/do-not-localize/book.png) Läs mer om paket i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/administration-basics/working-with-data-packages.html){target="_blank"}

## Distributionsmodeller{#ac-deployment}

Det finns två distributionsmodeller:

* **Campaign FDA [!DNL Snowflake] distribution**

   I [[!DNL Snowflake] FDA-distribution](fda-deployment.md), [!DNL Adobe Campaign] v8 är ansluten till [!DNL Snowflake] för att få åtkomst till data via funktionen för federerad dataåtkomst: kan du komma åt och bearbeta externa data och information som lagras i [!DNL Snowflake] utan att ändra strukturen på Adobe Campaign-data. PostgreSQL är den primära databasen och Snowflake är den sekundära databasen. Du kan utöka datamodellen och lagra data på Snowflake. Därefter kan ni köra ETL, segmentering och rapporter på en stor datauppsättning med enastående prestanda.

* **Driftsättning av Campaign Enterprise (FFDA)**

   När det gäller [Företagsdistribution (FFDA)](enterprise-deployment.md), [!DNL Adobe Campaign] v8 fungerar med två databaser: en lokal [!DNL Campaign] databas för användargränssnittet för meddelanden i realtid och enhetliga frågor samt skriva via API:er och ett molnbaserat [!DNL Snowflake] databas för kampanjkörning, batchfrågor och arbetsflödeskörning.

   Campaign v8 Enterprise innehåller konceptet **Fullständig federerad dataåtkomst** (FFDA): alla data är nu fjärranslutna till molndatabasen. Med den nya arkitekturen förenklar driftsättningen av Campaign v8 Enterprise (FFDA) datahanteringen: inget index krävs för molndatabasen. Du behöver bara skapa tabellerna, kopiera data så kan du börja. Cloud-databastekniken kräver inget specifikt underhåll för att garantera prestandanivån.

## Split delivery execution {#split}

>[!AVAILABILITY]
>
>Den här funktionen är endast tillgänglig för kunder med flera MID-instanskonfigurationer.

Beroende på vilket Campaign v8-paket ni har etablerats med ett visst antal mellanleverantörer som ansvarar för att utföra leveranser.

Som standard används en **[!UICONTROL Alternate]** routningsläge, vilket innebär att en leverans skickas från varje mellaninstans i taget på ett alternerande sätt.

För att få bättre prestanda både i fråga om hastighet och skala kan ni låta leveranser delas upp automatiskt mellan era instanser av mellanprodukter för att kunna levereras snabbare till mottagarna. Den här åtgärden är transparent när leveransen från marknadsföringsinstansen körs: När leveransen har skickats konsolideras alla loggar, innan de skickas tillbaka till marknadsinstansen till ett enda leveransobjekt.

Det gör du genom att lägga till ytterligare externa konton med **[!UICONTROL Split]** routningsläget skapas vid etablering för varje kanal:

* Delad leverans - e-post (splitDeliveryEmail)
* Delad leverans - SMS (splitDeliverySMS)
* Delad leverans - iOS (splitDeliveryIOS)
* Delad leverans - Android (splitDeliveryAndroid)

![](assets/splitted-delivery.png)

>[!IMPORTANT]
>
>Delat routningsläge är aktiverat som standard för kontot Delad leverans - e-post. För alla andra kanaler, externa konton, kontakta kundtjänst för att aktivera alternativet.
>
>Som standard är tröskelvärdet för att dela en leverans mellan flera mellanrum 100 kB. Du kan ändra det här värdet i alternativet &quot;NmsDelivery_MultiMidSplitThreshold&quot; i **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL Options]** -menyn.

Om du vill dela upp externa konton som standardkonto för att skicka ut leveranser måste du ändra routningsprovidern i leveransmallarna. Följ dessa steg för att göra detta:

1. Navigera till **[!UICONTROL Resources]** / **[!UICONTROL Templates]** / **[!UICONTROL Delivery templates]** och öppna leveransmallen. I det här exemplet vill vi redigera e-postleveransmallen.

   ![](assets/split-default-list.png)

1. Klicka på **[!UICONTROL Properties]** och ändra routningsprovidern till motsvarande externt konto för delad leverans.

   ![](assets/split-default-delivery.png)

1. Spara ändringarna. Alla leveranser som skickas med mallen använder nu det delade routningsläget som standard.

<!--In addition, you can select split external accounts as the default routing provider for all future delivery templates. To do this, change the value of the **[!UICONTROL xtkoption NmsBroadcast_DefaultProvider]** option to the name of the split account.

![](assets/split-default-options.png) -->

## Meddelandecenterarkitektur{#transac-msg-archi}

Transactional messaging (Message Center) är den Campaign-modul som är avsedd för hantering av utlösarmeddelanden.

![](../assets/do-not-localize/glass.png) Lär dig hur du skickar transaktionsmeddelanden i [det här avsnittet](../send/transactional.md).

Som svar på en åtgärd från en kund på en webbplats skickas en händelse till Campaign via ett REST API, och meddelandemallen fylls i med informationen eller data som tillhandahålls via API-anropet och ett transaktionsmeddelande skickas i realtid till kunden. Dessa meddelanden kan skickas individuellt eller gruppvis via e-post, SMS eller push-meddelanden.

I den här specifika arkitekturen separeras körningscellen från kontrollinstansen för att säkerställa hög tillgänglighet och lasthantering.

* The **Kontrollinstans** (eller Marketing instance) används av marknadsförare och IT-team för att skapa, konfigurera och publicera meddelandemallar. Den här instansen centraliserar också händelseövervakning och historik.

   ![](../assets/do-not-localize/glass.png) Lär dig hur du skapar och publicerar meddelandemallar i [det här avsnittet](../send/transactional.md).

* The **Körningsinstans** återtar inkommande händelser (t.ex. lösenordsåterställning eller beställningar från en webbplats) och skickar personliga meddelanden. Det kan finnas mer än en körningsinstans för att bearbeta meddelanden via belastningsutjämnaren och skala antalet händelser som ska bearbetas för maximal tillgänglighet.

>[!CAUTION]
>
>Kontrollinstansen och körningsinstansen/körningsinstanserna måste vara installerade på olika datorer. De kan inte dela samma Campaign-instans.

![](assets/messagecenter_diagram.png)

### Autentisering

Om du vill använda dessa funktioner loggar Adobe Campaign-användare in på kontrollinstansen för att skapa transaktionsmeddelandemallar, generera meddelandeförhandsvisningen med hjälp av en startlista, visa rapporter och övervaka körningsinstansen/instanserna.

* Enskild körningsinstans Vid interaktion med en körningsinstans i ett meddelandecenter på Adobe kan ett externt system först hämta en sessionstoken (som förfaller om 24 timmar) genom att göra ett API-anrop till sessionsinloggningsmetoden med hjälp av en tillhandahållen kontoinloggning och ett lösenord.
Med den sessionToken som tillhandahålls av körningsinstansen som svar på ovanstående anrop, kan det externa programmet göra SOAP api-anrop (rtEvents eller batchEvents) för att skicka kommunikation, utan att behöva inkludera kontoinloggning och lösenord i varje SOAP-anrop.

* Flera körningsinstanser I en arkitektur med flera celler och flera körningsinstanser bakom en belastningsutjämnare, går den inloggningsmetod som anropas av det externa programmet igenom belastningsutjämnaren: Därför kan ingen tokenbaserad autentisering användas. En användar-/lösenordsbaserad autentisering krävs.

![](../assets/do-not-localize/book.png) Läs mer om Transactional messaging-händelser i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/processing/event-description.html#about-transactional-messaging-datamodel){target="_blank"}
