---
title: Allmän arkitektur
description: Läs mer om Adobe Campaigns arkitektur och komponenter. Läs mer om hur du anpassar din klientkonsol och miljö.
feature: Architecture, Deployment
role: Admin, Developer
level: Beginner
exl-id: 1d9ff6c5-974d-4a8a-a0d7-641685bbe26e
source-git-commit: 061197048885a30249bd18af7f8b24cb71def742
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 1%

---

# Allmän arkitektur{#general-architecture}

Den typiska driftsättningen av Adobe Campaign-lösningar består av följande komponenter:

* **Anpassad klientmiljö**

  Intuitivt grafiskt gränssnitt där användare kan kommunicera och spåra marknadsföringserbjudanden, skapa kampanjer, granska och hantera alla marknadsföringsaktiviteter, program och planer - inklusive e-post, arbetsflöden och landningssidor -, skapa och hantera kundprofiler och skapa målgrupper.

* **Utvecklingsmiljö**

  Program på serversidan som kör marknadsföringskampanjer via valda kommunikationskanaler, inklusive e-post, SMS, push-meddelanden, direktreklam, webb eller sociala, baserat på de regler och arbetsflöden som definieras i användargränssnittet.

* **Databasbehållare**

  Adobe Campaign Cloud Database lagrar all information, alla kampanjkomponenter, erbjudanden, arbetsflöden och kampanjresultat i databasbehållare, baserat på relationsdatabasteknik.

## Anpassad klientmiljö {#client-env}

Programmet kan nås på olika sätt: webbanvändargränssnitt, klientkonsol (RIA-klient), webbåtkomst (tunn klient) eller API-integrering.

[Läs mer om Campaign-användargränssnittet](../start/campaign-ui.md).

## Utvecklingsmiljö {#dev-env}

Adobe Campaign är en enda plattform med olika program för att skapa en öppen och skalbar arkitektur. Adobe Campaign-plattformen är skriven i ett flexibelt programlager och kan enkelt konfigureras efter dina behov. Den distribuerade arkitekturen säkerställer linjär skalbarhet av systemet från tusentals meddelanden till miljontals meddelanden.

Vissa Campaign-moduler fungerar kontinuerligt medan andra startas ibland för att utföra administrativa uppgifter (t.ex. konfigurera databasanslutningen) eller för att köra en återkommande uppgift (t.ex. konsolidering av spårningsinformation).

Det finns tre typer av Adobe Campaign-moduler:

* **Moduler med flera instanser**: en enda process körs för alla instanser. Detta gäller följande moduler: web, syslogd, trackinglogd och watchdog.
* **Eninstansmoduler**: en process körs per instans. Detta gäller följande moduler: mta, wfserver, inMail, sms och stat.
* **Verktygsmoduler**: Det här är moduler som körs ibland för att utföra tillfälliga eller återkommande åtgärder (rensning, konfiguration, hämtning av spårningsloggar osv.).

De viktigaste processerna är:

* **Programserver** (webbserver) - Den här processen visar alla Adobe Campaign-funktioner via webbtjänstens API:er (SOAP/HTTP + XML). Dessutom kan man dynamiskt generera de webbsidor som används för HTML-baserad åtkomst (rapporter, webbformulär etc.). För att uppnå detta innehåller den här processen en Apache Tomcat JSP-server. Detta är den process som konsolen ansluter till.

* **Arbetsflödesmotor** (nlserver wfserver) - Den här processen kör de arbetsflödesprocesser som definierats i programmet. Den hanterar också regelbundet genomförda tekniska arbetsflöden, inklusive:

   * **Spårning**: Återställer och konsoliderar spårningsloggar, så att du kan hämta loggarna från omdirigeringsservern och skapa de aggregerade indikatorer som används av rapportmodulen.
   * **Rensa**: Rensar databasen och tömmer gamla poster så att databasen inte växer exponentiellt.
   * **Fakturering**: Skickar en aktivitetsrapport för plattformen (databasens storlek, antal marknadsföringsåtgärder osv.).

* **Leveransserver** (nlserver mta) - Adobe Campaign har inbyggd e-postsändningsfunktion. Den här processen fungerar som en MTA (SMTP mail transfer agent). Den personaliserar meddelanden från en till en och hanterar deras fysiska leverans. Den körs med leveransjobb och hanterar automatiska återförsök. När spårning är aktiverat ersätts URL-adresserna automatiskt så att de pekar på omdirigeringsservern. Den här processen kan hantera anpassning och automatisk sändning till en tredjepartsrouter för SMS, fax och direktreklam.

* **Omdirigeringsserver** (nlserver webmdl) - För e-post hanterar Adobe Campaign automatiskt öppnings- och klickspårning (transaktionsspårning på webbplatsnivå är en ytterligare möjlighet). För att uppnå detta skrivs de URL:er som ingår i e-postmeddelandena om så att de pekar på den här modulen, som registrerar den överförda Internet-användaren innan de dirigeras om till den önskade URL:en.

  För att garantera högsta tillgänglighet är den här processen helt oberoende av databasen: de andra serverprocesserna kommunicerar med den endast med SOAP-anrop (HTTP, HTTP(S) och XML). Tekniskt sett implementeras den här funktionen i en tilläggsmodul för en HTTP-server (ISAPI-tillägg i IIS eller en DSO Apache-modul osv.) och är endast tillgänglig i Windows.

Det finns även andra tekniska processer:

* **Hantera studsmeddelanden** (nlserver inMail) - Med den här processen kan du automatiskt hämta e-post från postlådor som konfigurerats för att ta emot studsmeddelanden som returneras om leveransen misslyckas. Dessa meddelanden genomgår sedan regelbaserad bearbetning för att fastställa orsaken till utebliven leverans (okänd mottagare, kvoten har överskridits osv.) och för att uppdatera leveransstatusen i databasen. Alla dessa åtgärder är helt automatiska och förkonfigurerade.

* **SMS-leveransstatus** (nlserver sms) - Den här processen avsöker SMS-routern för att samla in förloppsstatus och uppdatera databasen.

* **Skriver loggmeddelanden** (nlserver syslogd) - Den här tekniska processen hämtar loggmeddelanden och spårningar som genererats av de andra processerna och skriver dem till hårddisken. Detta gör att det finns gott om information som kan användas för diagnostik i händelse av problem.

* **Skriver spårningsloggar** (nlserver trackinglog) - Den här processen sparar spårningsloggarna som genererats av omdirigeringsprocessen på disken.

* **Skriver inkommande händelser** (interaktion på servern) - Den här processen garanterar att inkommande händelser spelas in på disken inom ramen för Interaction.

* **Kontrollerande moduler** (nlserver watchdog) - Den här tekniska processen fungerar som en primär process som skapar de andra. Den övervakar dem också och startar om dem automatiskt i händelse av incidenter, vilket ger maximal aktiv systemtid.

* **Statistikserver** (nlserver-status) - Den här processen underhåller statistik om antalet anslutningar, meddelanden som skickas för varje e-postserver som meddelanden skickas till samt deras begränsningar (högsta antal samtidiga anslutningar, meddelanden per timme/och/eller anslutning). Du kan också federera flera instanser eller datorer om de delar samma offentliga IP-adresser.


## Databasbehållare {#db-containers}

I sin [Enterprise (FFDA)-distribution](enterprise-deployment.md) är Adobe Campaign Cloud-databasen beroende av [!DNL Snowflake] som innehåller funktionell information (profiler, prenumerationer, innehåll osv.), tekniska data (leveransjobb och loggar, spårningsloggar osv.) och arbetsdata (inköp, leads) för lösningen, och alla Adobe Campaign-komponenter kommunicerar med databasen för att utföra sina specifika uppgifter.

Du kan distribuera Adobe Campaign med hjälp av fördefinierade databaser och scheman, och om det behövs kan den fördefinierade miljön utökas. Alla data i datafilen nås av Adobe Campaign via SQL-anrop. Adobe Campaign har också en komplett uppsättning ETL-verktyg (Extract Transform and Load) för import och export av data till och från systemet.

![](assets/data-flow-diagram.png)


>[!CAUTION]
>
>Med **Kampanjhanterade molntjänster** har din miljö och den inledande konfigurationen angetts av Adobe, i enlighet med villkoren i licensavtalet. Du får inte ändra installerade inbyggda paket, inbyggda scheman eller rapporter.
>
>Om du behöver använda ett Campaign-tillägg eller en viss funktion som inte har etablerats för dig måste du kontakta **Adobe kundtjänst**.

## Databaslagring {#db-storage}

Total lagringskvot delas mellan huvuddatabasen och den (valfria) sekundära Snowflake-databasen. Var data lagras bör fastställas vid implementering eller uppgradering, beroende på kundspecifika användningsfall.

Lär dig hur du övervakar databasanvändningen i [dokumentationen på Kontrollpanelen för kampanj](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/database-monitoring/database-monitoring.html?lang=sv-SE){target="_blank"}.