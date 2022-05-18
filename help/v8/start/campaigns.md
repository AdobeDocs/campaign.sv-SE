---
title: Kom igång med marknadsföringskampanjer
description: Kom igång med marknadsföringskampanjer
feature: Audiences
role: Data Engineer
level: Beginner
exl-id: b5a6c845-13a7-4746-b856-a08a3cf80b66,c4798c8f-619e-4a60-80d7-29b9e4c61168
source-git-commit: 6de5c93453ffa7761cf185dcbb9f1210abd26a0c
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 6%

---

# Kom igång med marknadsföringskampanjer{#gs-ac-campaigns}

Adobe Campaign erbjuder en uppsättning lösningar som hjälper er att personalisera och leverera kampanjer i alla kanaler, både online och offline. Ni kan skapa, konfigurera, köra och analysera marknadsföringskampanjer. Alla marknadsföringskampanjer kan hanteras från ett enhetligt kontrollcenter. Lär dig hur du bläddrar bland och skapar marknadsföringskampanjer i det här avsnittet.

Kampanjerna omfattar åtgärder (leveranser) och processer (import eller extrahering av filer) samt resurser (marknadsföringsdokument, leveransdispositioner). De används i marknadsföringskampanjer. Kampanjer ingår i ett program och program ingår i en kampanjplan.

## Orkestrera kampanjer över flera kanaler{#cross-channel-orchestration}

Med Adobe Campaign kan du utforma och orkestrera målinriktade och personaliserade kampanjer över flera kanaler: e-post, direktutskick, SMS och push-meddelanden. Ett enda gränssnitt erbjuder alla funktioner du behöver för att schemalägga, orkestrera, konfigurera, personalisera, automatisera, genomföra och mäta alla kampanjer och all kommunikation.

![](assets/campaign-tab.png)

### Kärnkoncept{#ac-core-concepts}

Innan ni börjar implementera marknadsföringskampanjer måste ni känna till följande koncept:

* **Marknadsföringskampanj**: En kampanj centraliserar alla element som hör till en marknadsföringskampanj: leveranser, regler för målinriktning, kostnader, exportfiler, relaterade dokument osv. Varje kampanj är kopplad till ett program.

* **Program**: kan du definiera marknadsföringsåtgärder för en kalenderperiod: lansering, kanvantning, lojalitet osv. Varje program innehåller kampanjer som är länkade till en kalender, som ger en övergripande bild.

* **Plan**: marknadsföringsplanen kan innehålla flera program. Den är kopplad till en kalenderperiod, har en tilldelad budget och kan även kopplas ihop med dokument och mål.

* **Arbetsflöde för kampanj**: ett kampanjarbetsflöde innehåller aktiviteter som bygger kampanjlogiken. Använd kampanjarbetsflöden för att definiera målgrupper och skapa leveranser för alla tillgängliga kanaler.

* **Återkommande kampanjer**: återkommande kampanjer skapas från en specifik mall som definierar den arbetsflödesmall som ska köras och körningsschemat.

* **Periodiska kampanjer**: en periodisk kampanj är en kampanj som skapas automatiskt i enlighet med körningsschemat i sin mall.

## Arbetsyta för marknadsföringskampanjer{#ac-workspace}

Med Adobe Campaign kan ni skapa, konfigurera, köra och analysera alla marknadsföringskampanjer från ett enhetligt kontrollcenter.

![](assets/calendar.png)

![](../assets/do-not-localize/book.png) Upptäck hur ni får tillgång till och implementerar marknadsföringskampanjer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/about-marketing-campaigns/accessing-marketing-campaigns.html?lang=en#orchestrating-campaigns){target=&quot;_blank&quot;}


## Viktiga steg att starta{#gs-ac-start}

De viktigaste stegen för att skapa en flerkanalskampanj för marknadsföring är:

1. **Planera och utforma marknadsföringsprogram och kampanjer**

   Definiera hierarki och schema, ange budget, lägga till resurser och välj operatorer.

   ![](../assets/do-not-localize/book.png) Lär dig hur du skapar en marknadsföringsplan och konfigurerar kampanjer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/setting-up-marketing-campaigns.html?lang=en#creating-plan-and-program-hierarchy){target=&quot;_blank&quot;}

   Alla marknadsföringskampanjer är baserade på en mall som lagrar de viktigaste inställningarna och funktionerna. En inbyggd mall tillhandahålls för att skapa en kampanj för vilken ingen specifik konfiguration har definierats. Du kan skapa och konfigurera kampanjmallar och sedan skapa kampanjer utifrån dessa mallar.

   ![](../assets/do-not-localize/book.png) Lär dig hur du arbetar med kampanjmallar i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-templates.html?lang=en#orchestrating-campaigns){target=&quot;_blank&quot;}

   ![](../assets/do-not-localize/book.png) Upptäck återkommande kampanjer och hur du konfigurerar dem i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/setting-up-marketing-campaigns.html?lang=en#recurring-and-periodic-campaigns){target=&quot;_blank&quot;}

1. **Definiera målgrupper**

   Du kan skapa målgrupper i ett arbetsflöde eller välja en befintlig grupp, till exempel en mottagarlista, prenumeranter på ett nyhetsbrev, mottagare av en tidigare leverans eller något annat filtreringsvillkor.

   ![](assets/campaign-wf.png)

   ![](../assets/do-not-localize/book.png) Lär dig hur du definierar målgruppen för dina meddelanden i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-target.html?lang=en#orchestrating-campaigns){target=&quot;_blank&quot;}

1. **Skapa leveranser**

   Välj kanal(er), definiera meddelandeinnehållet och starta leveranser.

   ![](assets/campaign-dashboard.png)

   ![](../assets/do-not-localize/book.png) Lär dig skapa och starta marknadsföringskampanjer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-deliveries.html?lang=en#creating-deliveries){target=&quot;_blank&quot;}

   Du kan koppla olika dokument till en kampanj: rapport, foto, webbsida, diagram osv.

   ![](../assets/do-not-localize/book.png) Läs mer om associerade dokument i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-assets.html?lang=en#adding-documents){target=&quot;_blank&quot;}

1. **Ställ in godkännandeprocessen**

   Med Adobe Campaign kan ni skapa samverkansbaserade godkännandeprocesser för de viktigaste stegen i marknadsföringskampanjen. För varje kampanj kan ni godkänna leveransmålet, innehållet och kostnaderna. Adobe Campaign-operatörer som ansvarar för godkännande kan meddelas via e-post och kan acceptera eller avvisa godkännande från konsolen eller via en webbanslutning.

   ![](../assets/do-not-localize/book.png) Lär dig hur du ställer in och hanterar godkännanden i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-approval.html?lang=en#orchestrating-campaigns){target=&quot;_blank&quot;}


## Tillägg för distribuerad marknadsföring{#distributed-marketing-add-on}

Adobe Campaign erbjuder **Distribuerad marknadsföring** tillägg för genomförande av samverkanskampanjer mellan centrala enheter (huvudkontor, marknadsavdelningar osv.) och lokala enheter (butiker, regionala organ osv.). Detta samarbete bygger på en delad arbetsyta som kallas **[!UICONTROL List of campaign packages]**, där kampanjmallar som utformats av centrala enheter erbjuds lokala enheter.

>[!NOTE]
>
>Den här funktionen är tillgänglig från och med Campaign v8.3. Om du vill kontrollera din version kan du läsa [det här avsnittet](compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)

[](../assets/do-not-localize/book.png) Lär dig hur du konfigurerar och använder Campaign Distributed Marketing-funktioner i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/distributed-marketing/about-distributed-marketing.html){target=&quot;_blank&quot;}

## Tillägg för distribuerad marknadsföring{#response-manager-add-on}

Adobe Campaign erbjuder **Svarshantering** tillägg som gör att ni kan mäta framgången och lönsamheten för marknadsföringskampanjer eller erbjudandeförslag över olika kommunikationskanaler: e-post, mobil, direktreklam osv.

>[!NOTE]
>
>Den här funktionen är tillgänglig från och med Campaign v8.3. Om du vill kontrollera din version kan du läsa [det här avsnittet](compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)

[](../assets/do-not-localize/book.png) Lär dig hur du konfigurerar och använder svarshanteraren för Campaign i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/response-manager/about-response-manager.html){target=&quot;_blank&quot;}

