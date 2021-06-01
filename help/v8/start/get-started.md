---
product: Adobe Campaign
title: Kom igång med Campaign v8
description: Upptäck nyckelfunktioner, användargränssnitt och globala riktlinjer
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 04b12907-3cb1-40f1-90b8-1524d84edf2d,e3e9b514-a69d-4650-b1b1-1b76b4f3d63f
source-git-commit: 5363950db5092bc7e0a72a0823db1132a17dda33
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 43%

---

# Kom igång med Adobe Campaign{#gs-ac-v8}

Adobe Campaign är en plattform för att designa flerkanaliga kundupplevelser och en miljö för visuell kampanjsamordning, interaktionshantering i realtid och flerkanalsmarknadsföring.

Använd Campaign för att:

* **Driv personalisering och engagemang** genom en enda lättillgänglig bild av kunden
* **Integrera** kanaler för e-post, mobil, online och offline i kundresan
* **Automatisera** leverans av meningsfulla och aktuella meddelanden och erbjudanden

![](assets/ac-capabilities.png)

## Integrerad kundprofil {#integrated-customer-profile}

Profilerna är centraliserade i en kraftfull molndatabas. Det finns många sätt att förvärva profiler och bygga upp databasen: insamling online via webbformulär, manuell eller automatisk import av textfiler, replikering med företagsdatabaser eller andra informationssystem. Med Adobe Campaign kan du integrera marknadsföringshistorik, inköpsinformation, preferenser, CRM-data och alla relevanta PII-data i en enda samlad vy för att analysera och vidta åtgärder.

I Adobe Campaign är mottagarna de standardprofiler som väljs för att skicka leveranser till (e-post, SMS etc.). Tack vare mottagardata som lagras i databasen kan du filtrera det mål som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

[!DNL :bulb:] Grunderna för profilhantering beskrivs i  [det här avsnittet](audiences.md).

[!DNL :bulb:] Lär dig hur du lägger till profiler i Campaign i  [det här avsnittet](import.md).

## Målinriktad segmentering {#targeted-segmentation}

Adobe Campaign har kraftfulla och användarvänliga funktioner för segmentering och målinriktning som gör att du kan skapa mycket välriktade och differentierade erbjudanden. Med den beskrivande analysfunktionen kan du analysera information både i tidigare och senare led i marknadsföringskampanjer. Med filterhanteringen och den grafiska frågeredigeraren kan du även filtrera mottagargrupper och ta prov på eller skapa målgrupper baserat på ett obegränsat antal kriterier.

Funktionen med avancerad datahantering utökar möjligheterna för databearbetning. Den förenklar och optimerar målinriktningsprocessen genom att inkludera data som inte är modellerade i datakartläggningen.

[!DNL :bulb:] Läs mer om segmentering, målgruppsframtagning och personalisering i  [det här avsnittet](audiences.md).

## Orkestrera kampanjer över flera kanaler {#cross-channel-campaign-orchestration}

Med Adobe Campaign kan du utforma och orkestrera målinriktade och personaliserade kampanjer över flera kanaler: e-post, direktutskick, SMS och push-meddelanden. Ett enda gränssnitt erbjuder alla funktioner du behöver för att schemalägga, orkestrera, konfigurera, personalisera, automatisera, genomföra och mäta alla kampanjer och all kommunikation.

[!DNL :bulb:] Lär dig hur du utformar, schemalägger och kör en kampanj i  [det här avsnittet](campaigns.md).

## Arbetsflöden

Adobe Campaign erbjuder en omfattande grafisk miljö där du kan utforma komplexa processer som segmentering, kampanjutförande, filhantering osv. Du kan till exempel använda ett arbetsflöde för att hämta en fil från en server, expandera den och sedan importera dess poster till Adobe Campaign-databasen.

Ett arbetsflöde kan även omfatta användare genom att tilldela dem uppgifter eller låta dem godkänna utförda uppgifter. Det innebär att du kan tilldela en eller flera användare en uppgift att arbeta med innehåll eller ange mål och godkänna korrektur innan meddelandet skickas.

Arbetsflöden kan användas i olika sammanhang, till exempel:

* Målgrupper för att hantera målgrupper eller skicka meddelanden.
* Datahantering (ETL) för att hantera data.
* Importera data till Campaign-databasen.
* Tekniska processer som rensning av databaser, återställning av spårningsinformation osv.

[!DNL :bulb:] Lär dig hur du utformar och kör arbetsflöden i  [det här avsnittet](../config/workflows.md).

## Rapportering och analys {#analysis-and-reporting}

Med Adobe Campaign kan du övervaka och tolka kundernas beteende genom att gradvis berika deras data och profiler. Med rapporterings- och analysverktygen kan du ta vara på varje ny kampanj, målinrikta marknadsföringsinitiativen bättre och optimera deras effekt och med detta avkastningen på investeringen.

[!DNL :bulb:] Läs mer om rapport- och spårningsfunktioner i  [det här avsnittet](reporting.md).

## Integreringar med Adobe Experience Cloud {#adobe-experience-cloud-integrations}

Du kan kombinera leveransfunktionerna och de avancerade funktionerna för kampanjhantering i Adobe Campaign med en uppsättning lösningar som hjälper till att personalisera användarnas upplevelse. Till exempel kan du använda Adobe Experience Manager, Adobe Analytics, Adobe Target eller utlösare i Adobe Experience Cloud.

[!DNL :bulb:] Lär dig hur du kan integrera med Adobe-tjänster och -lösningar i  [det här avsnittet](../connect/integration.md).

## Mer om Campaign-funktioner {#core-capabilities-and-add-ons}

Adobe Campaign har en uppsättning funktioner som hjälper er att implementera och optimera marknadsföringsfunktionerna beroende på era behov och er arkitektur. Vissa av dem är kärnfunktioner och andra är beroende av att ett paket installeras på din konfiguration. En detaljerad produktbeskrivning finns här: [Adobe Campaign v8 Produktbeskrivning](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-classic---product-description.html).

[!DNL :bulb:] Känner du redan till Campaign Classic? Lär dig viktiga skillnader mellan Campaign Classic och Campaign v8 i [den här sidan](capability-matrix.md).

## Arbetsyta och anpassning

Kampanjarbetsytan är tillgänglig via [klientkonsolen](../dev/general-architecture.md).

[!DNL :bulb:] [Läs mer om Campaign Client Console](../start/connect.md).

Kampanjarbetsytan kan anpassas efter dina behov.

[!DNL :arrow_upper_right:]  Lär dig hur du använder arbetsytan för Campaign i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/campaign-workspace/adobe-campaign-workspace.html)

[!DNL :arrow_upper_right:]  Lär dig hur du anpassar listor i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/campaign-workspace/adobe-campaign-ui-lists.html)

Du kan även komma åt vissa funktioner via webben.

[!DNL :bulb:] [Läs mer om Campaign Web Access](../start/connect.md#web-access).


## Språk

Användargränssnittet för Campaign v8 finns på följande språk:

* Engelska (UK)
* Engelska (USA)
* Franska
* Tyska
* Japanska

Språket väljs under installationen.

>[!CAUTION]
>
>Språket kan inte ändras efter att instansen har skapats.

Språk som påverkas av datum- och tidsformat. Mer information finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/campaign-workspace/adobe-campaign-workspace.html?lang=en#date-and-time).

