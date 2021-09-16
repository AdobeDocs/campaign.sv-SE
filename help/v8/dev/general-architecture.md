---
title: Allmän arkitektur
description: Läs mer om Campaign-arkitekturen och komponenter
exl-id: 1d9ff6c5-974d-4a8a-a0d7-641685bbe26e
source-git-commit: f071fc227dac6d72873744ba56eb0b4b676de5dd
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 0%

---

# Allmän arkitektur{#general-architecture}

Den typiska driftsättningen av Adobe Campaign-lösningar består av följande komponenter:

* **Anpassad klientmiljö**

   Intuitivt grafiskt gränssnitt där användare kan kommunicera och spåra marknadsföringserbjudanden, skapa kampanjer, granska och hantera alla marknadsföringsaktiviteter, program och planer - inklusive e-post, arbetsflöden och landningssidor -, skapa och hantera kundprofiler och skapa målgrupper.

* **Utvecklingsmiljö**

   Program på serversidan som kör marknadsföringskampanjer via valda kommunikationskanaler, inklusive e-post, SMS, push-meddelanden, direktreklam, webb eller sociala, baserat på de regler och arbetsflöden som definieras i användargränssnittet.

* **Databasbehållare**

   Adobe Campaign Cloud Database lagrar all kundinformation, kampanjkomponenter, erbjudanden och arbetsflöden samt kampanjresultat i kunddatabasbehållare, baserat på relationsdatabasteknik.

## Anpassad klientmiljö {#client-env}

Programmet kan nås på olika sätt: Rich Client, Thin Client eller API Integration.

* **Klientkonsol**: Huvudanvändargränssnittet i programmet är ett inbyggt program (i Windows) som kommunicerar med Adobe Campaign-programservern med standardInternetprotokoll (SOAP, HTTP osv.). Adobe Campaign Client Console är mycket användarvänligt för ökad produktivitet och använder mycket liten bandbredd (genom att använda ett lokalt cacheminne) och är utformat för enkel driftsättning. Konsolen kan distribueras från en webbläsare, kan uppdateras automatiskt och kräver ingen specifik nätverkskonfiguration eftersom den bara genererar HTTP(S)-trafik.

   ? [Läs mer om Campaign Client Console](../start/connect.md).

* **Webbåtkomst**: delar av programmet kan nås via en enkel webbläsare med hjälp av ett HTML-användargränssnitt, inklusive rapportmodulen, godkännandesteg, instansövervakning osv.

   ? [Läs mer om Campaign Web Access](../start/connect.md).

* **Kampanj-API:er**: I vissa fall kan systemet anropas från ett externt program med hjälp av de API:er för webbtjänster som exponeras via SOAP-protokollet.

   ? [Läs mer om Campaign-API:er](../dev/api.md).

## Utvecklingsmiljö {#dev-env}

Adobe Campaign är en enda plattform med olika program för att skapa en öppen och skalbar arkitektur. Adobe Campaign-plattformen är skriven i ett flexibelt programlager och kan enkelt konfigureras efter dina behov. Den distribuerade arkitekturen säkerställer linjär skalbarhet av systemet från tusentals meddelanden till miljontals meddelanden.

Vissa Campaign-moduler fungerar kontinuerligt medan andra startas ibland för att utföra administrativa uppgifter (t.ex. konfigurera databasanslutningen) eller för att köra en återkommande uppgift (t.ex. konsolidering av spårningsinformation).

Det finns tre typer av Adobe Campaign-moduler:

* **Moduler** med flera instanser: en enda process körs för alla instanser. Detta gäller följande moduler: webb, syslogd, trackinglog och watchdog.
* **Eninstansmoduler**: en process körs per instans. Detta gäller följande moduler: mta, wfserver, inMail, sms och stat.
* **Verktygsmoduler**: Detta är moduler som körs ibland för att utföra tillfälliga eller återkommande åtgärder (rensning, konfiguration, hämtning av spårningsloggar osv.).

De viktigaste processerna är:

**Programserver**  (nlserver web)

Den här processen visar alla Adobe Campaign-funktioner via Web Services API:er (SOAP / HTTP + XML). Dessutom kan programmet dynamiskt generera webbsidor som används för HTML-baserad åtkomst (rapporter, webbformulär osv.). För att uppnå detta innehåller den här processen en Apache Tomcat JSP-server. Detta är den process som konsolen ansluter till.

**Arbetsflödesmotor**  (nlserver wfserver)

Den kör de arbetsflödesprocesser som definierats i programmet.

Den hanterar också regelbundet genomförda tekniska arbetsflöden, inklusive:

* **Spårning**: Återställer och konsoliderar spårningsloggar. Det gör att du kan hämta loggarna från omdirigeringsservern och skapa de aggregerade indikatorer som används av rapportmodulen.
* **Rensa**: Databasrengöring. Används för att rensa gamla poster och undvika att databasen växer exponentiellt.
* **Fakturering**: Automatisk sändning av en aktivitetsrapport för plattformen (databasstorlek, antal marknadsföringsåtgärder osv.).

**Delivery Server** (nlserver mta)

Adobe Campaign har inbyggd e-postsändningsfunktion. Den här processen fungerar som en MTA (SMTP mail transfer agent). Den personaliserar meddelanden från en till en och hanterar deras fysiska leverans. Den körs med leveransjobb och hanterar automatiska återförsök. När spårning är aktiverat ersätts URL-adresserna automatiskt så att de pekar på omdirigeringsservern.

Den här processen kan hantera anpassning och automatisk sändning till en tredjepartsrouter för SMS, fax och direktreklam.

**Omdirigeringsserver**  (nlserver webmdl)

För e-post hanterar Adobe Campaign automatiskt öppnings- och klickspårning (transaktionsspårning på webbplatsnivå är en ytterligare möjlighet). För att uppnå detta skrivs de URL:er som ingår i e-postmeddelandena om så att de pekar på den här modulen, som registrerar den överförda Internet-användaren innan de dirigeras om till den önskade URL:en.

För att garantera högsta tillgänglighet är denna process helt oberoende av databasen: de andra serverprocesserna kommunicerar med den endast med SOAP-anrop (HTTP, HTTP(S) och XML). Tekniskt sett implementeras den här funktionen i en tilläggsmodul för en HTTP-server (ISAPI-tillägg i IIS eller en DSO Apache-modul osv.) och finns endast i Windows.

Det finns även andra tekniska processer:

**Hantera studsmeddelanden**  (nlserver inMail)

Med den här processen kan du automatiskt hämta e-post från postlådor som konfigurerats för att ta emot studsade meddelanden som returneras om leveransen misslyckas. Dessa meddelanden genomgår sedan regelbaserad bearbetning för att fastställa orsaken till utebliven leverans (okänd mottagare, kvoten har överskridits osv.) och för att uppdatera leveransstatus i databasen.

Alla dessa åtgärder är helt automatiska och förkonfigurerade.

**SMS-leveransstatus**  (nlserver sms)

Den här processen avsöker SMS-routern för att samla in förloppsstatus och uppdatera databasen.

**Skriver loggmeddelanden**  (nlserver syslogd)

Den här tekniska processen hämtar loggmeddelanden och spårningar som genererats av andra processer och skriver dem till hårddisken. Detta gör att det finns gott om information som kan användas för diagnostik i händelse av problem.

**Skriver spårningsloggar**  (nlserver trackinglogd)

Den här processen sparar spårningsloggarna som genereras av omdirigeringsprocessen.

**Skriver inkommande händelser**  (nlserver interactiond)

Denna process gör att inkommande händelser spelas in på disken inom ramen för Interaction.

**Kontrollmoduler**  (nlserver watchdog)

Denna tekniska process fungerar som en huvudprocess som sporrar de andra. Den övervakar dem också och startar om dem automatiskt i händelse av incidenter, vilket ger maximal aktiv systemtid.

**Statistikserver**  (nlserver-status)

Den här processen innehåller statistik om antalet anslutningar, de meddelanden som skickas för varje e-postserver som meddelanden skickas till samt deras begränsningar (högsta antal samtidiga anslutningar, meddelanden per timme och/eller anslutning). Du kan också federera flera instanser eller datorer om de delar samma offentliga IP-adresser.

## Databasbehållare {#db-containers}

Adobe Campaign Cloud-databasen använder [!DNL Snowflake] som innehåller funktionell information (profiler, prenumerationer, innehåll osv.), tekniska data (leveransjobb och loggar, spårningsloggar osv.) och arbetsdata (inköp, leads) för lösningen och alla Adobe Campaign-komponenter kommunicerar med databasen för att utföra sina specifika uppgifter.

Kunder kan driftsätta Adobe Campaign med hjälp av fördefinierade databaser och scheman, och vid behov kan den fördefinierade miljön utökas. Alla data i datafilen nås av Adobe Campaign via SQL-anrop. Adobe Campaign har också en komplett uppsättning ETL-verktyg (Extract Transform and Load) för import och export av data till och från systemet.

![](assets/data-flow-diagram.png)


>[!CAUTION]
>
>Med **kampanjhanterade Cloud Services** har din miljö och den ursprungliga konfigurationen ställts in av Adobe enligt villkoren i licensavtalet. Du får inte ändra installerade inbyggda paket, inbyggda scheman eller rapporter.
>
>Om du behöver använda ett Campaign-tillägg eller en viss funktion som inte har tillhandahållits för dig måste du kontakta **Adobe kundtjänst**.