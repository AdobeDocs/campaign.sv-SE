---
title: Kom igång med Campaign v8
description: Har ni inte använt Campaign tidigare? Kom igång
feature: Overview
role: Admin, Developer, User
level: Beginner
exl-id: 04b12907-3cb1-40f1-90b8-1524d84edf2d,e3e9b514-a69d-4650-b1b1-1b76b4f3d63f
source-git-commit: 9bea7904ea4507083d2cf45193877e7a2539d0c7
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 39%

---

# Kom igång med Adobe Campaign{#gs-ac-v8}

Adobe Campaign är en plattform för att designa flerkanaliga kundupplevelser och en miljö för visuell kampanjsamordning, interaktionshantering i realtid och flerkanalsmarknadsföring.

Använd Campaign för att:

* **Drive** personalisering och engagemang genom en enda lättillgänglig bild av kunden
* **Integrera** e-post, mobilkanaler, online- och offlinekanaler i kundresan
* **Automatisera** leverera meningsfulla och aktuella meddelanden och erbjudanden

![](assets/ac-capabilities.png)

## Integrated Customer Profile {#integrated-customer-profile}

Profilerna är centraliserade i en kraftfull molndatabas. Det finns många sätt att skaffa profiler och bygga upp databasen: onlinesamling via webbformulär, manuell eller automatisk import av textfiler, replikering med företagsdatabaser eller andra informationssystem. Med Adobe Campaign kan du integrera marknadsföringshistorik, inköpsinformation, preferenser, CRM-data och alla relevanta PII-data i en enda samlad vy för att analysera och vidta åtgärder.

I Adobe Campaign är mottagarna de standardprofiler som väljs för att skicka leveranser till (e-post, SMS etc.). Tack vare mottagardata som lagras i databasen kan du filtrera det mål som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

![](../assets/do-not-localize/glass.png) Grunderna för profilhantering finns i [det här avsnittet](audiences.md).

![](../assets/do-not-localize/glass.png) Lär dig hur du lägger till profiler i Campaign i [det här avsnittet](import.md).

## Målinriktad segmentering {#targeted-segmentation}

Adobe Campaign har kraftfulla och användarvänliga funktioner för segmentering och målinriktning som gör att du kan skapa mycket välriktade och differentierade erbjudanden. Med den beskrivande analysfunktionen kan du analysera information både i tidigare och senare led i marknadsföringskampanjer. Med filterhanteringen och den grafiska frågeredigeraren kan du även filtrera mottagargrupper och ta prov på eller skapa målgrupper baserat på ett obegränsat antal kriterier.

Funktionen med avancerad datahantering utökar möjligheterna för databearbetning. Den förenklar och optimerar målinriktningsprocessen genom att inkludera data som inte är modellerade i datakartläggningen.

![](../assets/do-not-localize/glass.png) Läs mer om segmentering, målgruppsframtagning och personalisering i [det här avsnittet](audiences.md).

## Orkestrera kampanjer över flera kanaler {#cross-channel-campaign-orchestration}

Med Adobe Campaign kan du utforma och orkestrera målinriktade och personaliserade kampanjer över flera kanaler: e-post, direktutskick, SMS och push-meddelanden. Ett enda gränssnitt erbjuder alla funktioner du behöver för att schemalägga, orkestrera, konfigurera, personalisera, automatisera, genomföra och mäta alla kampanjer och all kommunikation.

![](../assets/do-not-localize/glass.png) Lär dig utforma, schemalägga och köra en kampanj i [det här avsnittet](campaigns.md).

## Arbetsflöden

Adobe Campaign erbjuder en omfattande grafisk miljö där du kan utforma komplexa processer som segmentering, kampanjutförande, filhantering osv. Du kan till exempel använda ett arbetsflöde för att hämta en fil från en server, expandera den och sedan importera dess poster till Adobe Campaign-databasen.

Ett arbetsflöde kan även omfatta användare genom att tilldela dem uppgifter eller låta dem godkänna utförda uppgifter. Det innebär att du kan tilldela en eller flera användare en uppgift att arbeta med innehåll eller ange mål och godkänna korrektur innan meddelandet skickas.

Arbetsflöden kan användas i olika sammanhang, till exempel:

* Målgrupper för att hantera målgrupper eller skicka meddelanden.
* Datahantering (ETL) för att hantera data.
* Importera data till Campaign-databasen.
* Tekniska processer som rensning av databaser, återställning av spårningsinformation osv.

![](../assets/do-not-localize/glass.png) Lär dig utforma och köra arbetsflöden i [det här avsnittet](../config/workflows.md).

## Rapportering och analys {#analysis-and-reporting}

Med Adobe Campaign kan du övervaka och tolka kundernas beteende genom att gradvis berika deras data och profiler. Med rapporterings- och analysverktygen kan du ta vara på varje ny kampanj, målinrikta marknadsföringsinitiativen bättre och optimera deras effekt och med detta avkastningen på investeringen.

Förutom kraftfulla och färdiga rapportmallar kan du med Adobe Campaign skapa anpassade rapporter för leverans-, kampanj-, användar- eller segmentnivå. Gör beskrivande analyser, sammanfatta avkastningen eller exportera data till Adobe Analytics och andra lösningar för ytterligare datavisualisering och analys.

Kampanjrapporteringsfunktionen gör det lättare att skapa dynamiska rapporter. Ni kan använda dra-och-släpp-variabler för att anpassa era rapporter och för att analysera hur framgångsrika era kampanjer är. Beroende på hur komplexa dina frågor och beräkningar är kan data samlas i en listvy eller nås i ett format som gör det enkelt att generera marknadsanalysrapporter.


![](../assets/do-not-localize/glass.png) Läs mer om funktionerna för rapportering och spårning i [det här avsnittet](../reporting/gs-reporting.md).

## Integreringar med Adobe Experience Cloud {#adobe-experience-cloud-integrations}

Du kan kombinera leveransfunktionerna och de avancerade funktionerna för kampanjhantering i Adobe Campaign med en uppsättning lösningar som hjälper till att personalisera användarnas upplevelse. Till exempel kan du använda Adobe Experience Manager, Adobe Analytics, Adobe Target eller utlösare i Adobe Experience Cloud.

![](../assets/do-not-localize/glass.png) Läs om hur du kan integrera med Adobes tjänster och lösningar i [det här avsnittet](../connect/integration.md).

## Mer om Campaign-funktioner {#core-capabilities-and-add-ons}

Adobe Campaign har en uppsättning funktioner som hjälper er att implementera och optimera marknadsföringsfunktionerna beroende på era behov och er arkitektur. Vissa av dem är kärnfunktioner och andra är beroende av att ett paket installeras på din konfiguration. En detaljerad produktbeskrivning finns här: [Adobe Campaign v8 - produktbeskrivning](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html).

![](../assets/do-not-localize/glass.png) Känner du redan till Campaign Classic? Läs om viktiga skillnader mellan Campaign Classic och Campaign v8 i [den här sidan](v7-to-v8.md).

**Se även**

* [Kampanjarbetsyta](campaign-ui.md)
* [Kompatibilitetsmatris för kampanj v8](compatibility-matrix.md)
* [Anslut till Campaign](connect.md)
* [Vanliga frågor och svar](campaign-faq.md)