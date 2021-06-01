---
product: Adobe Campaign
title: Kom igång med marknadsföringskampanjer
description: Kom igång med marknadsföringskampanjer
feature: Målgrupper
role: Data Engineer
level: Beginner
exl-id: b5a6c845-13a7-4746-b856-a08a3cf80b66,c4798c8f-619e-4a60-80d7-29b9e4c61168
source-git-commit: 5363950db5092bc7e0a72a0823db1132a17dda33
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 7%

---

# Kom igång med marknadsföringskampanjer{#gs-ac-campaigns}

Adobe Campaign erbjuder en uppsättning lösningar som hjälper er att personalisera och leverera kampanjer i alla kanaler, både online och offline. Ni kan skapa, konfigurera, köra och analysera marknadsföringskampanjer. Alla marknadsföringskampanjer kan hanteras från ett enhetligt kontrollcenter. Lär dig hur du bläddrar bland och skapar marknadsföringskampanjer i det här avsnittet.

Kampanjerna omfattar åtgärder (leveranser) och processer (import eller extrahering av filer) samt resurser (marknadsföringsdokument, leveransdispositioner). De används i marknadsföringskampanjer. Kampanjer ingår i ett program och program ingår i en kampanjplan.

## Orkestrera kampanjer över flera kanaler

Med Adobe Campaign kan du utforma och orkestrera målinriktade och personaliserade kampanjer över flera kanaler: e-post, direktutskick, SMS och push-meddelanden. Ett enda gränssnitt erbjuder alla funktioner du behöver för att schemalägga, orkestrera, konfigurera, personalisera, automatisera, genomföra och mäta alla kampanjer och all kommunikation.

### Kärnkoncept

Innan ni börjar implementera marknadsföringskampanjer måste ni känna till följande koncept:

* **Marknadsföringskampanj**: En kampanj centraliserar alla element som hör till en marknadsföringskampanj: leveranser, regler för målinriktning, kostnader, exportfiler, relaterade dokument osv. Varje kampanj är kopplad till ett program.

* **Program**: kan du definiera marknadsföringsåtgärder för en kalenderperiod: lansering, kanvantning, lojalitet osv. Varje program innehåller kampanjer som är länkade till en kalender, som ger en övergripande bild.

* **Planera**: marknadsföringsplanen kan innehålla flera program. Den är kopplad till en kalenderperiod, har en tilldelad budget och kan även kopplas ihop med dokument och mål.

* **Kampanjarbetsflöde**: ett kampanjarbetsflöde innehåller aktiviteter som bygger kampanjlogiken. Använd kampanjarbetsflöden för att definiera målgrupper och skapa leveranser för alla tillgängliga kanaler.

* **Återkommande kampanjer**: återkommande kampanjer skapas från en specifik mall som definierar den arbetsflödesmall som ska köras och körningsschemat.

* **Periodiska kampanjer**: en periodisk kampanj är en kampanj som skapas automatiskt i enlighet med körningsschemat i sin mall.

## Arbetsyta för marknadsföringskampanjer

Med Adobe Campaign kan ni skapa, konfigurera, köra och analysera alla marknadsföringskampanjer från ett enhetligt kontrollcenter.

[!DNL :arrow_upper_right:] Upptäck hur ni får tillgång till och implementerar marknadsföringskampanjer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/about-marketing-campaigns/accessing-marketing-campaigns.html?lang=en#orchestrating-campaigns)


## Viktiga steg att starta

De viktigaste stegen för att skapa en flerkanalskampanj för marknadsföring är:

1. **Planera och utforma marknadsföringsprogram och kampanjer**

   Definiera hierarki och schema, ange budget, lägga till resurser och välj operatorer.

   [!DNL :arrow_upper_right:] Lär dig hur du skapar en marknadsföringsplan och konfigurerar kampanjer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/setting-up-marketing-campaigns.html?lang=en#creating-plan-and-program-hierarchy)

   Alla marknadsföringskampanjer är baserade på en mall som lagrar de viktigaste inställningarna och funktionerna. En inbyggd mall tillhandahålls för att skapa en kampanj för vilken ingen specifik konfiguration har definierats. Du kan skapa och konfigurera kampanjmallar och sedan skapa kampanjer utifrån dessa mallar.

   [!DNL :arrow_upper_right:] Lär dig hur du arbetar med kampanjmallar i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-templates.html?lang=en#orchestrating-campaigns)

   [!DNL :arrow_upper_right:] Upptäck återkommande kampanjer och hur du konfigurerar dem i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/setting-up-marketing-campaigns.html?lang=en#recurring-and-periodic-campaigns)

1. **Definiera målgrupper**

   Du kan skapa målgrupper i ett arbetsflöde eller välja en befintlig grupp, till exempel en mottagarlista, prenumeranter på ett nyhetsbrev, mottagare av en tidigare leverans eller något annat filtreringsvillkor.

   [!DNL :arrow_upper_right:] Lär dig hur du definierar målgruppen för dina meddelanden i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-target.html?lang=en#orchestrating-campaigns)

1. **Skapa leveranser**

   Välj kanal(er), definiera meddelandeinnehållet och starta leveranser.

   [!DNL :arrow_upper_right:] Läs om hur du skapar och startar leveranser av marknadsföringskampanjer i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-deliveries.html?lang=en#creating-deliveries)

   Du kan koppla olika dokument till en kampanj: rapport, foto, webbsida, diagram osv.

   [!DNL :arrow_upper_right:] Läs mer om associerade dokument i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-assets.html?lang=en#adding-documents)

1. **Ställ in godkännandeprocessen**

   Med Adobe Campaign kan ni skapa samverkansbaserade godkännandeprocesser för de viktigaste stegen i marknadsföringskampanjen. För varje kampanj kan ni godkänna leveransmålet, innehållet och kostnaderna. Adobe Campaign-operatörer som ansvarar för godkännande kan meddelas via e-post och kan acceptera eller avvisa godkännande från konsolen eller via en webbanslutning.

   [!DNL :arrow_upper_right:] Läs om hur du konfigurerar och hanterar godkännanden i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-approval.html?lang=en#orchestrating-campaigns)

