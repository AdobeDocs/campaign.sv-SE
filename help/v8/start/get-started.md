---
title: Kom igång med Campaign v8
description: Ny på Adobe Campaign? Hitta dokumentation om hur du får igång din programvara och var du ska börja med gränssnittet.
feature: Overview, Cross Channel Orchestration
role: User
level: Beginner
exl-id: 04b12907-3cb1-40f1-90b8-1524d84edf2d
version: Campaign v8, Campaign Classic v7
source-git-commit: a2efad26232cd380eea850a589b22b23928253e8
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 20%

---

# Kom igång med Adobe Campaign{#gs-ac-v8}

Adobe Campaign är en plattform för att designa flerkanaliga kundupplevelser och en miljö för visuell kampanjsamordning, interaktionshantering i realtid och flerkanalsmarknadsföring.

Adobe Campaign v8 är nästa generations kampanjverktyg som har byggts för olika marknadsföringskanaler som e-post, push-meddelanden, SMS och direktreklam. Den erbjuder robusta ETL- och datahanteringsfunktioner för att hjälpa till att utforma och strukturera den perfekta kampanjen. Dess orkestreringsmotor ger möjlighet till multitouch-marknadsföring med fokus på batchbaserade resor. Den levereras också tillsammans med en skalbar meddelandeserver i realtid som gör det möjligt för marknadsföringsteamen att skicka fördefinierade meddelanden baserat på en totalbelastning från alla IT-system för kommunikation som lösenordsåterställning, orderbekräftelse, e-kvitto och mycket annat.

Adobe Campaign v8 har avsevärda förbättringar vad gäller infrastruktur, säkerhet, leveransbarhet och övervakning. Det finns som en **hanterad Cloud Service** som kombinerar tjänster med proaktiv tillsyn och aktuella ändringar. Läs mer om Campaign Managed Cloud Services [på den här sidan](whats-new.md#acms-desc).

Använd Campaign för att

* **Drive**-personalisering och -engagemang via en enda lättillgänglig kundvy
* **Integrera** e-post-, mobil-, online- och offlinekanaler i kundresan
* **Automatisera** leveransen av meningsfulla och aktuella meddelanden och erbjudanden

![](assets/do-not-localize/ac-capabilities.png)

## Integrated Customer Profile {#integrated-customer-profile}

Profilerna är centraliserade i en kraftfull molndatabas. Det finns många sätt att samla in profiler och bygga upp databasen: onlinesamling via webbformulär, manuell eller automatisk import av textfiler, replikering med företagsdatabaser eller andra informationssystem. Med Adobe Campaign kan du integrera marknadsföringshistorik, inköpsinformation, preferenser, CRM-data och alla relevanta PII-data i en enda samlad vy för att analysera och vidta åtgärder.

I Adobe Campaign är mottagarna de standardprofiler som väljs för att skicka leveranser till (e-post, SMS etc.). Tack vare mottagardata som lagras i databasen kan du filtrera det mål som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

Grunderna för profilhantering beskrivs i [det här avsnittet](audiences.md).

Lär dig hur du lägger till profiler i Campaign i [det här avsnittet](import.md).

## Målinriktad segmentering {#targeted-segmentation}

Adobe Campaign har kraftfulla och användarvänliga funktioner för segmentering och målinriktning som gör att du kan skapa mycket välriktade och differentierade erbjudanden. Med den beskrivande analysfunktionen kan ni analysera information både i det övre och det nedre loppet av era marknadsföringskampanjer, och med filterhanterings- och den grafiska frågeredigeringsfunktionen kan ni filtrera era era mottagarpopulationer och sampla eller skapa målgrupper baserat på ett obegränsat antal kriterier.

Funktionen med avancerad datahantering utökar möjligheterna för databearbetning. Det förenklar och optimerar målgruppsprocessen genom att inkludera data som inte är modellerade i datamappningen.

Läs mer om segmentering och målgruppsskapande i [det här avsnittet](audiences.md).

## Samordna kampanjer i flera kanaler {#cross-channel-campaign-orchestration}

Med Adobe Campaign kan du utforma och orkestrera målinriktade och personaliserade kampanjer över flera kanaler: e-post, direktutskick, SMS och push-meddelanden. Ett enda gränssnitt ger er alla funktioner ni behöver för att schemalägga, samordna, konfigurera, personalisera, automatisera, genomföra och mäta alla kampanjer och all kommunikation.

Lär dig hur du utformar, schemalägger och kör en kampanj i [det här avsnittet](campaigns.md).

## Arbetsflöden {#wf-gsv8}

Adobe Campaign erbjuder en omfattande grafisk miljö där du kan utforma komplexa processer som segmentering, kampanjutförande, filhantering osv. Du kan till exempel använda ett arbetsflöde för att hämta en fil från en server, expandera den och sedan importera dess poster till Adobe Campaign-databasen.

Ett arbetsflöde kan även omfatta användare genom att tilldela dem uppgifter eller låta dem godkänna utförda uppgifter. Det innebär att du kan tilldela en eller flera användare en uppgift att arbeta med innehåll eller ange mål och godkänna korrektur innan meddelandet skickas.

Arbetsflöden kan användas i olika sammanhang, till exempel:

* Målgrupper för att hantera målgrupper eller skicka meddelanden.
* Datahantering (ETL) för att hantera data.
* Importera data till Campaign-databasen.
* Tekniska processer som rensning av databaser, återställning av spårningsinformation osv.

Lär dig utforma och köra arbetsflöden i [det här avsnittet](../config/workflows.md).

## Rapportering och analys {#analysis-and-reporting}

Med Adobe Campaign kan du övervaka och tolka kundernas beteende genom att gradvis berika deras data och profiler. Med rapporterings- och analysverktygen kan ni utnyttja varje ny kampanj, bättre målinrikta era marknadsföringsinitiativ och optimera deras effekt och avkastning på investeringen.

Förutom kraftfulla och färdiga rapportmallar kan du med Adobe Campaign skapa anpassade rapporter för leverans-, kampanj-, användar- eller segmentnivå. Gör beskrivande analyser, sammanfatta avkastningen eller exportera data till Adobe Analytics och andra lösningar för ytterligare datavisualisering och analys.

Kampanjrapporteringsfunktionen gör det lättare att skapa dynamiska rapporter. Ni kan använda dra-och-släpp-variabler för att anpassa era rapporter och för att analysera hur framgångsrika era kampanjer är. Beroende på hur komplexa dina frågor och beräkningar är kan data samlas i en listvy eller nås i ett format som gör det enkelt att generera marknadsanalysrapporter.


Läs mer om rapport- och spårningsfunktioner i [det här avsnittet](../reporting/gs-reporting.md).

## Adobe Experience Cloud-integreringar {#adobe-experience-cloud-integrations}

Ni kan kombinera leveransfunktionerna och de avancerade kampanjhanteringsfunktionerna i Adobe Campaign med en uppsättning lösningar som hjälper er att personalisera användarupplevelsen: t.ex. Adobe Experience Manager, Adobe Analytics, Adobe Target eller Adobe Experience Cloud.

Lär dig hur du integrerar med Adobes tjänster och lösningar i [det här avsnittet](../connect/integration.md).

## Mer om Campaign-funktioner {#core-capabilities-and-add-ons}

Adobe Campaign har en uppsättning funktioner som hjälper er att implementera och optimera marknadsföringsfunktionerna beroende på era behov och er arkitektur. Vissa av dem är kärnfunktioner och andra är beroende av att ett paket installeras på din konfiguration. En detaljerad produktbeskrivning finns här: [Adobe Campaign v8 Produktbeskrivning](https://helpx.adobe.com/se/legal/product-descriptions/adobe-campaign-managed-cloud-services.html).

Känner du redan till Campaign Classic? Lär dig viktiga skillnader mellan Campaign Classic och Campaign v8 på [den här sidan](v7-to-v8.md).

**Se även**

* [Kampanjarbetsyta](campaign-ui.md)
* [Kompatibilitetsmatris för kampanj v8](compatibility-matrix.md)
* [Anslut till Campaign](connect.md)
* [Vanliga frågor och svar](campaign-faq.md)
