---
title: Kom igång med Campaign-arkitekturen
description: Identifiera miljöer och grundläggande distributionsmöjligheter, inklusive hur du rapporterar om en kampanjmiljö.
feature: Architecture, Deployment
role: Developer
level: Beginner
exl-id: 562b24c3-6bea-447f-b74c-187ab77ae78f
source-git-commit: 7465cacc74b8b7df38c5eb10d2928749c70a87ea
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 1%

---

# Kom igång med Campaign-arkitekturen{#gs-ac-archi}

## Miljöer {#environments}

Campaign blir tillgängligt som enskilda instanser där varje instans representerar en komplett Campaign-miljö.

Det finns två typer av miljöer:

* **Produktionsmiljö**: är värd för program för affärsanvändare.

* **Icke-produktionsmiljö**: används för olika prestanda- och kvalitetstester innan ändringar i programmet överförs till produktionsmiljön.

Du kan exportera och importera paket från en miljö till en annan.

Läs mer om paket i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/administration-basics/working-with-data-packages.html){target="_blank"}

## Distributionsmodeller {#ac-deployment}

Det finns två distributionsmodeller tillgängliga: **Campaign FDA-distribution** (P1-P3) och **Campaign Enterprise (FFDA)-distribution** (P4).

### Campaign FDA-distribution {#ac-deployment-fda}

I [FDA-distributionen](fda-deployment.md) kan [!DNL Adobe Campaign] v8 anslutas till [!DNL Snowflake] för att komma åt data via funktionen för federerad dataåtkomst: du kan komma åt och bearbeta externa data och information som lagras i din [!DNL Snowflake]-databas utan att ändra strukturen för Adobe Campaign-data. PostgreSQL är den primära databasen, och du kan använda Snowflake som den sekundära databasen för att utöka din datamodell och lagra dina data i Snowflake. Därefter kan ni köra ETL, segmentering och rapporter på en stor datauppsättning med enastående prestanda.


![](assets/P1-P3-architecture.png){zoomable="yes"}

>[!NOTE]
>
>I den här distributionsmodellen är den sekundära databasen [!DNL Snowflake] endast tillgänglig på begäran. Kontakta din Adobe Transition Manager om du vill uppdatera din distribution med [!DNL Snowflake].
>

### Driftsättning av Campaign Enterprise (FFDA) {#ac-deployment-ffda}

I kontexten för en [Enterprise (FFDA)-distribution](enterprise-deployment.md) fungerar [!DNL Adobe Campaign] v8 med två databaser: en lokal [!DNL Campaign]-databas för användargränssnittet för meddelanden i realtid och enhetliga frågor och skrivningar via API:er, och en Cloud [!DNL Snowflake]-databas för kampanjkörning, gruppfrågor och arbetsflödeskörning.

Campaign v8 Enterprise innehåller konceptet **FDA (Full Federated Data Access)**: alla data finns nu på fjärrbasis i molndatabasen. Med den här nya arkitekturen förenklar driftsättningen av Campaign v8 Enterprise (FFDA) datahanteringen: inget index krävs för molndatabasen. Du behöver bara skapa tabellerna, kopiera data så kan du börja. Cloud-databastekniken kräver inget specifikt underhåll för att garantera prestandanivån.

![](assets/P4-architecture.png){zoomable="yes"}


## Split delivery execution {#split}

>[!AVAILABILITY]
>
>Den här funktionen är endast tillgänglig för kunder med flera MID-instanser (Middle-sourcing).

Beroende på vilket Campaign v8-paket ni har etablerats med ett visst antal mellanleverantörer som ansvarar för att utföra leveranser.

Som standard använder de externa kontona för alla kanaler ett **[!UICONTROL Alternate]**-routningsläge, vilket innebär att en leverans skickas från varje MID-instans i taget på ett alternerande sätt.

För att få bättre prestanda både i fråga om hastighet och skala kan ni låta leveranser delas upp automatiskt mellan era instanser av mellanprodukter för att kunna levereras snabbare till mottagarna. Den här åtgärden är transparent när leveransen från marknadsinstansen körs: när leveransen har skickats konsolideras alla loggar, innan de skickas tillbaka till marknadsinstansen till ett enda leveransobjekt.

För att göra detta skapas ytterligare externa konton med routningsläget **[!UICONTROL Split]** vid etablering för varje kanal:

* Delad leverans - e-post (splitDeliveryEmail)
* Delad leverans - SMS (splitDeliverySMS)
* Delad leverans - iOS (splitDeliveryIOS)
* Delad leverans - Android (splitDeliveryAndroid)

![](assets/splitted-delivery.png)

>[!IMPORTANT]
>
>Delat routningsläge är aktiverat som standard för kontot Delad leverans - e-post. För alla andra kanaler ska du kontakta din Adobe Transition Manager för att aktivera alternativet.
>
>Som standard är tröskelvärdet för att dela upp en leverans mellan flera MID-instanser 100 kB. Du kan ändra det här värdet i alternativet &quot;NmsDelivery_MultiMidSplitThreshold&quot; på menyn **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL Options]** .

Om du vill dela upp externa konton som standardkonto för att skicka ut leveranser måste du ändra routningsprovidern i leveransmallarna. Följ dessa steg för att göra detta:

1. Navigera till mappen **[!UICONTROL Resources]** / **[!UICONTROL Templates]** / **[!UICONTROL Delivery templates]** och öppna önskad leveransmall. I det här exemplet vill vi redigera e-postleveransmallen.

   ![](assets/split-default-list.png)

1. Klicka på knappen **[!UICONTROL Properties]** och ändra routningsprovidern till motsvarande externt konto för delad leverans.

   ![](assets/split-default-delivery.png)

1. Spara ändringarna. Alla leveranser som skickas med mallen använder nu det delade routningsläget som standard.

<!--In addition, you can select split external accounts as the default routing provider for all future delivery templates. To do this, change the value of the **[!UICONTROL xtkoption NmsBroadcast_DefaultProvider]** option to the name of the split account.

![](assets/split-default-options.png) -->

## Meddelandecenterarkitektur{#transac-msg-archi}

Transactional messaging (Message Center) är den Campaign-modul som är avsedd för hantering av utlösarmeddelanden.

Lär dig hur du skickar transaktionsmeddelanden i [det här avsnittet](../send/transactional.md).

Som svar på en åtgärd från en kund på en webbplats skickas en händelse till Campaign via ett REST API, och meddelandemallen fylls i med informationen eller data som tillhandahålls via API-anropet och ett transaktionsmeddelande skickas i realtid till kunden. Dessa meddelanden kan skickas individuellt eller gruppvis via e-post, SMS eller push-meddelanden.

I den här specifika arkitekturen separeras körningscellen från kontrollinstansen för att säkerställa hög tillgänglighet och lasthantering.

* **Kontrollinstansen** (eller Marketing-instansen) används av marknadsförare och IT-team för att skapa, konfigurera och publicera meddelandemallar. Den här instansen centraliserar också händelseövervakning och historik.

  Lär dig hur du skapar och publicerar meddelandemallar i [det här avsnittet](../send/transactional.md).

* **Körningsinstansen** hämtar inkommande händelser (t.ex. lösenordsåterställning eller beställningar från en webbplats) och skickar personliga meddelanden. Det kan finnas mer än en körningsinstans för att bearbeta meddelanden via belastningsutjämnaren och skala antalet händelser som ska bearbetas för maximal tillgänglighet.

>[!CAUTION]
>
>Kontrollinstansen och körningsinstansen/körningsinstanserna måste vara installerade på olika datorer. De kan inte dela samma Campaign-instans.

![](assets/messagecenter_diagram.png)

### Autentisering

Om du vill använda dessa funktioner loggar Adobe Campaign-användare in på kontrollinstansen för att skapa transaktionsmeddelandemallar, generera meddelandeförhandsvisningen med hjälp av en startlista, visa rapporter och övervaka körningsinstansen/instanserna.

* Enkel körningsinstans
När du interagerar med en körningsinstans i Adobe Message Center kan ett externt system först hämta en sessionstoken (som förfaller om 24 timmar) genom att anropa sessionsinloggningsmetoden med hjälp av en tillhandahållen kontoinloggning och ett lösenord.
Med den sessionToken som tillhandahålls av körningsinstansen som svar på ovanstående anrop kan det externa programmet göra SOAP API-anrop (rtEvents eller batchEvents) för att skicka kommunikation, utan att behöva ta med kontouppgifterna för inloggning och lösenord i varje SOAP-anrop.

* Flera körningsinstanser
I en arkitektur för körning av flera celler med flera körningsinstanser bakom en belastningsutjämnare, går den inloggningsmetod som anropas av det externa programmet igenom belastningsutjämnaren: av den anledningen går det inte att använda en tokenbaserad autentisering. En användar-/lösenordsbaserad autentisering krävs.

Läs mer om Transactional Messaging-händelser på [den här sidan](../send/event-processing.md).
