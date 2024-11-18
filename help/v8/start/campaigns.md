---
title: Kom igång med kampanjer
description: Kom igång med kampanjer
feature: Cross Channel Orchestration
role: User
level: Beginner
exl-id: b5a6c845-13a7-4746-b856-a08a3cf80b66
source-git-commit: 8d6c3e03f9b7533f7f325b755e3b6d4f74b63a8d
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 2%

---

# Kom igång med kampanjer {#gs-ac-campaigns}

Adobe Campaign erbjuder en uppsättning lösningar som hjälper er att personalisera och leverera kampanjer i alla kanaler, både online och offline. Ni kan skapa, konfigurera, köra och analysera marknadsföringskampanjer. Alla marknadsföringskampanjer kan hanteras från ett enhetligt kontrollcenter. Lär dig att hitta och skapa marknadsföringskampanjer i det här avsnittet.

Kampanjerna omfattar åtgärder (leveranser) och processer (import eller extrahering av filer) samt resurser (marknadsföringsdokument, leveransdispositioner). De används i marknadsföringskampanjer. Kampanjer ingår i ett program och program ingår i en kampanjplan.

## Samordna kampanjer i flera kanaler{#cross-channel-orchestration}

Med Adobe Campaign kan du utforma och orkestrera målinriktade och personaliserade kampanjer över flera kanaler: e-post, direktutskick, SMS och push-meddelanden. Ett enda gränssnitt ger er alla funktioner ni behöver för att schemalägga, samordna, konfigurera, personalisera, automatisera, genomföra och mäta alla kampanjer och all kommunikation.

![](assets/campaign-tab.png)

### Kärnkoncept{#ac-core-concepts}

Innan ni börjar implementera marknadsföringskampanjer måste ni känna till följande koncept:

* **Marknadsföringskampanj**: En kampanj centraliserar alla element som hör till en marknadsföringskampanj: leveranser, målgruppsregler, kostnader, exportfiler, relaterade dokument osv. Varje kampanj är kopplad till ett program.

* **Program**: Med ett program kan du definiera marknadsföringsåtgärder för en kalenderperiod: start, skanning, lojalitet osv. Varje program innehåller kampanjer som är länkade till en kalender, som ger en övergripande bild.

* **Planera**: marknadsföringsplanen kan innehålla flera program. Den är kopplad till en kalenderperiod, har en tilldelad budget och kan även kopplas ihop med dokument och mål.

* **Kampanjarbetsflöde**: Ett kampanjarbetsflöde innehåller aktiviteter för att skapa kampanjlogiken. Använd kampanjarbetsflöden för att definiera målgrupper och skapa leveranser för alla tillgängliga kanaler.

* **Återkommande kampanjer**: återkommande kampanjer skapas från en specifik mall som definierar den arbetsflödesmall som ska köras och körningsschemat.

* **Periodiska kampanjer**: En periodisk kampanj är en kampanj som skapas automatiskt i enlighet med körningsschemat för dess mall.

## Arbetsyta för marknadsföringskampanjer{#ac-workspace}

Med Adobe Campaign kan ni skapa, konfigurera, köra och analysera alla marknadsföringskampanjer från ett enhetligt kontrollcenter.

![](assets/calendar.png)

Upptäck hur du får åtkomst till och implementerar marknadsföringskampanjer i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html){target="_blank"}.

## Viktiga steg att starta{#gs-ac-start}

De viktigaste stegen för att skapa en flerkanalskampanj för marknadsföring är:

1. **Planera och utforma marknadsföringsprogram och kampanjer**

   Definiera hierarki och schema, ange budget, lägga till resurser och välj operatorer.

   Lär dig hur du skapar en marknadsföringsplan och konfigurerar kampanjer på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html){target="_blank"}.

   Alla marknadsföringskampanjer är baserade på en mall som lagrar de viktigaste inställningarna och funktionerna. En inbyggd mall tillhandahålls för att skapa en kampanj för vilken ingen specifik konfiguration har definierats. Du kan skapa och konfigurera kampanjmallar och sedan skapa kampanjer utifrån dessa mallar.

   Lär dig hur du arbetar med kampanjmallar på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-templates.html){target="_blank"}.

   Upptäck återkommande kampanjer och hur du konfigurerar dem på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/recurring-periodic-campaigns.html){target="_blank"}.

1. **Definiera målgrupper**

   Du kan skapa målgrupper i ett arbetsflöde eller välja en befintlig grupp, till exempel en mottagarlista, prenumeranter på ett nyhetsbrev, mottagare av en tidigare leverans eller något annat filtreringsvillkor.

   ![](assets/campaign-wf.png)

   Lär dig hur du definierar publik för dina meddelanden på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html){target="_blank"}.

1. **Skapa leveranser**

   Välj kanal(er), definiera meddelandeinnehållet och starta leveranser.

   ![](assets/campaign-dashboard.png)

   Lär dig hur du skapar och startar leveranser av marknadsföringskampanjer på [den här sidan](../../automation/campaigns/marketing-campaign-deliveries.md).

   Du kan associera olika dokument med en kampanj: rapport, foto, webbsida, diagram osv. Läs mer om associerade dokument på [den här sidan](../../automation/campaigns/marketing-campaign-assets.md).

1. **Konfigurera godkännandeprocessen**

   Med Adobe Campaign kan ni skapa samverkansbaserade godkännandeprocesser för de viktigaste stegen i marknadsföringskampanjen. För varje kampanj kan ni godkänna leveransmålet, innehållet och kostnaderna. Adobe Campaign-operatörer som ansvarar för godkännande kan meddelas via e-post och kan acceptera eller avvisa godkännande från konsolen eller via en webbanslutning.

   Lär dig hur du konfigurerar och hanterar godkännanden på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html#campaign-orchestration){target="_blank"}.


## Tillägg för distribuerad marknadsföring{#distributed-marketing-add-on}

Adobe Campaign erbjuder ett **Distributed Marketing**-tillägg för att implementera samarbetskampanjer mellan centrala enheter (huvudkontor, marknadsföringsavdelningar osv.) och lokala enheter (butiker, regionala byråer osv.). Samarbetet baseras på en delad arbetsyta som kallas **[!UICONTROL List of campaign packages]**, där kampanjmallar som utformats av centrala entiteter erbjuds lokala entiteter.

>[!NOTE]
>
>Den här funktionen är tillgänglig från och med Campaign v8.3. Mer information om hur du kontrollerar versionen finns i [det här avsnittet](compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)

Lär dig hur du konfigurerar och använder Campaign Distributed Marketing-funktioner på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html){target="_blank"}.

## Tillägget Svarshantering{#response-manager-add-on}

Adobe Campaign erbjuder ett **Response Management**-tillägg som gör att du kan mäta framgången och lönsamheten för marknadsföringskampanjer eller erbjuda förslag över kommunikationskanaler: e-post, mobil, direktreklam osv.

>[!NOTE]
>
>Den här funktionen är tillgänglig från och med Campaign v8.3. Mer information om hur du kontrollerar versionen finns i [det här avsnittet](compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion)

[](../assets/do-not-localize/book.png) Lär dig hur du konfigurerar och använder kampanjsvarshanteraren i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/response-manager/about-response-manager.html){target="_blank"}.
