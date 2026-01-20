---
source-git-commit: 548b4be24e26a6970f953f92af1f89d829689592
workflow-type: tm+mt
source-wordcount: '2430'
ht-degree: 0%

---
# AC-UI Jira Tickets Analysis - arbetssammanfattning&#x200B;**Datum:** 12 januari 2026&#x200B;**Dokumenttyp:** Arbetsdokument/intern analys

&#x200B;---

## Sammanfattning

I det här dokumentet analyseras Jira-produktbiljetter från flera frågor relaterade till AC-UI-releaser (januari 2026 och november 2025). Analysen fokuserar på att identifiera dokumentationskrav, föreslå DOCAC-biljetter och framhäva öppna frågor.

**Totalt antal analyserade unika biljetter:** 19
**Biljetter som kräver dokumentation:** 14
**Biljetter som redan är dokumenterade:** 5
**Biljetter utan dokument:** 5

&#x200B;---

## &#x200B;1. Lista över analyserade biljetter

### 1.1 AC-UI-26-01-Monthly Release (januari 2026)

| Biljett-ID | Titel | Status | Prioritet | Komponenter |
|-----------|-------|--------|----------|------------|
| NEO-91565 | [Webbgränssnitt] Lägg till stöd för anpassningsfält (avancerad AEM-integrering) | Löst | Normal | ACS till ACC, PIX UI/UX |
| NEO-80973 | Dynamisk rapporttillgänglighet för alla användare av webbgränssnitt | Pågår | Normal | ACS till ACC, PIX UI/UX |
| NEO-86754 | [UX/UI] A/B-testning | Pågår | Blockera | PIX UI/UX |
| NEO-76126 | Framtagning av scheman - skapa ny tabell, utöka scheman och få åtkomst till extern DB | Pågår | Kritisk | PIX UI/UX |
| NEO-93487 | [Webbgränssnitt] Beräkningsprocess för leveransplanering som liknar den i ACS | Nytt | Kritisk | PIX UI/UX |
| NEO-92400 | Versionsförbättringar - 26 januari | Nytt | Normal | PIX UI/UX |
| NEO-88838 | Innehållsredigeraren: Använd temavariabler i fragment | Nytt | Normal | PIX UI/UX |
| NEO-92668 | [UX/UI] - webbanalys | Nytt | Normal | PIX UI/UX |
| NEO-86753 | [UX/UI] Integrering med AEM för Live-kopior/språkkopior | Nytt | Blockera | ACS till ACC, PIX UI/UX |

### 1.2 Versionsförbättringar, länkade biljetter (NEO-92400)

| Biljett-ID | Titel | Status | Prioritet | Komponenter |
|-----------|-------|--------|----------|------------|
| NEO-92942 | [Regelbyggaren] Fördefinierade filter - alternativet Delat | Löst | Normal | PIX UI/UX |
| NEO-91299 | Webbgränssnitt - kontinuerlig leveransaktivitet | Stängd | Viktigt | PIX UI/UX |
| NEO-90130 | Aktivera OOTB-filöverföring för överföring av push-meddelanden på flera språk | Stängd | Kritisk | ACS till ACC, PIX UI/UX |

### 1.3 AC-UI-25-11-Monthly Release (november 2025)

| Biljett-ID | Titel | Status | Prioritet | Komponenter |
|-----------|-------|--------|----------|------------|
| NEO-91566 | [Webbgränssnitt] - stöd för CTA-spårning i webb | Stängd | Normal | ACS till ACC, PIX UI/UX |
| NEO-91564 | [Webbgränssnitt] [AEM flerspråkig i ACC] gränssnittsstöd för AEM flerspråkiga språk | Stängd | Normal | ACS till ACC, PIX UI/UX |
| NEO-90183 | [UX/UI] Multilingual Rich Push - UI | Stängd | Blockera | PIX UI/UX |
| NEO-91567 | [Webbgränssnitt] Lägg till stöd för NRT-funktion | Löst | Normal | ACS till ACC, PIX UI/UX |
| NEO-91563 | Transactional Rest API for Profile Based Enrichment - Web UI | Löst | Normal | ACS till ACC, PIX UI/UX |
| NEO-92151 | [UI/UX] Profilbaserad anrikning transaktionsmeddelanden - fas 2 | Löst | Viktigt | ACS till ACC, PIX UI/UX |
| NEO-84916 | [UX/UI] Konfigurera och hantera godkännandeprocessen | Löst | Kritisk | PIX UI/UX |

&#x200B;---

## &#x200B;2. Biljetter som kräver dokumentation

### 2.1 HÖG PRIORITET - aktiv utveckling (AC-UI-26-01)

#### **NEO-86754: A/B-testning**- **Status:** Pågår (i spår)- **Varför dokumentation krävs:** Större ny funktion för att experimentera med e-postinnehåll med A/B-testfunktioner- **Befintlig DOCAC:** DOCAC-13104 (ny status)- **Dokumentationsomfång:**   - Skapa A/B-testexperiment i leveranser   - Definiera innehålls-/leveransvarianter   - Ange provets proportioner och skicka testvarianter   - Definiera utvärderingskriterier   - Analysera experimentresultat och välja vinnare   - God praxis och begränsningar- **Målgrupp:** Marknadsföringsanvändare, Kampanjansvariga- **Utgåva:** 8.9.1, AC-UI-26-01-Monthly- **Öppna frågor:**   - Slutgiltig verifieringsstatus för användargränssnittet/användargränssnittet?   - Finns det några begränsningar för transaktionsmeddelanden?   - Integration med Acrites förhandsgranskning av innehåll?

#### **NEO-80973: Dynamisk rapporttillgänglighet**- **Status:** Pågår (klar för granskning)- **Varför dokumentation krävs:** Utöka dynamisk rapportering till alla användare i webbgränssnittet (inte bara 8.7 ACS till ACC-kunder)- **Befintlig DOCAC:** DOCAC-11070 (stängd), DOCAC-13432 (löst - språkbegränsningar)- **Dokumentationsomfång:**   - Tillgänglighet och åtkomstkrav   - Dokumentation för språk som stöds   - Kända begränsningar jämfört med äldre rapporter   - Visning av motstridiga mätvärden med äldre rapportering   - Inställning av demomiljö- **Målgrupp:** Alla webbgränssnittsanvändare, analytiker- **Utgåva:** 8.8.1, AC-UI-26-01-Monthly- **Öppna frågor:**   - Tillgänglighetsstatus för demomiljö?   - Fullständig lista över motstridiga mätvärden med äldre rapportering?   - Språksupportmatris?

#### **NEO-76126: Schemaredigering**- **Status:** Pågår (i spår)- **Varför dokumentation krävs:** Betydande administratörsfunktion för hantering av datamodell- **Befintlig DOCAC:** DOCAC-13826 (ny status)- **Dokumentationsomfång:**   - Skapa nya tabeller   - Utöka befintliga scheman   - Åtkomst till externa databaser   - Formulärdefinition för anpassade entiteter   - Navigerings- och CRUD-åtgärder   - Fas 3-funktioner (skapa och utöka scheman) - ETA Feb end- **Målgrupp:** Administratörer, tekniska administratörer- **Utgåva:** AC-UI-26-01-Monthly- **Förfallodatum:** 28 feb 2026- **Öppna frågor:**   - När slutförs fas 2 för FF-aktivering?   - Bekräftelse av leveranstid för fas 3?   - Krav för miljökonfiguration?

#### **NEO-93487: Beräkningsprocess för leveransschema (H&amp;M)**- **Status:** Nytt- **Varför dokumentation krävs:** Kritisk kundeskalering - tidszonsbaserad leveransplanering- **Befintlig DOCAC:** Ingen identifierad- **Dokumentationsomfång:**   - Schemaläggning av leveranser baserat på användarens tidszon   - Använda beräknade formler för flertidszonsområden   - Exempel på konfiguration (t.ex. USA med flera tidszoner)   - Bästa tillvägagångssätt för globala kampanjer   - Jämförelse av funktioner med ACS- **Målgrupp:** Kampanjhanterare, marknadsföringsanvändare- **Kundpåverkan:** H&amp;M (mer än 50 marknader)- **Version:** 8.9.1, AC-UI-26-01-Monthly, 8.8.2.NEO-90300- **Öppna frågor:**   - Har du en demo planerad med PM?   - Fullständiga funktionsspecifikationer finns?   - Slutförde gränssnittsdummies?

#### **NEO-86753: AEM-integrering för Live-kopior/språkkopior**- **Status:** Nytt- **Varför dokumentation krävs:** Microsoft-specifik funktion för hantering av flerspråkigt innehåll- **Befintlig DOCAC:** DOCAC-13829 (löst)- **Dokumentationsomfång:**   - Bläddra bland leveransmallar för AEM   - Skapa Live-kopior   - Skapa språk kopierar innehållsvarianter   - Arbetsflöde och bästa praxis   - Krav för integrationsinställningar- **Målgrupp:** Marknadsförare som arbetar med AEM, Microsoft-team- **Utgåva:** AC-UI-26-01-Monthly- **Prioritet:** Blockerare- **Öppna frågor:**   - Arbetet överfördes till Himanshus team - aktuell status?   - Tidslinje för slutförande?

#### **NEO-92668: Webbanalys**- **Status:** Nytt (i spår)- **Varför dokumentation krävs:** Konfiguration av externt konto för webbanalysintegrering- **Befintlig DOCAC:** Ingen identifierad- **Dokumentationsomfång:**   - Skapa externa konton för Web Analytics   - Konfigurationsparametrar   - Integrering med leveransspårning   - Rapporteringsfunktioner- **Målgrupp:** Administratörer, marknadsföringsanalytiker- **Utgåva:** AC-UI-26-01-Monthly- **Öppna frågor:**   - Status för miljötillgänglighet?   - Nödvändiga installationssteg?

### 2.2 MEDIUM PRIORITY - Recent Delived (AC-UI-25-11)

#### **NEO-90183: Multilingual Rich Push**- **Status:** Stängt- **Varför dokumentation krävs:** Ny funktion för iOS/Android med stöd för flera språk- **Befintlig DOCAC:** DOCAC-13565 (ny status)- **Dokumentationsomfång:**   - Detaljerad konfiguration för push-meddelanden för iOS och Android   - Flerspråkiga innehållsvarianter   - Mallval   - Ytterligare fält för avancerat innehåll   - Filöverföringsfunktioner   - God praxis och begränsningar- **Målgrupp:** Marknadsföringsanvändare, Mobile Channel Manager- **Utgåva:** AC-UI-25-11-Monthly, 8.8.2- **Kund:** H&amp;M

#### **NEO-84916: Hantering av godkännandeprocesser**- **Status:** Löst- **Varför dokumentation krävs:** Större arbetsflödesfunktion för leveransvalidering- **Befintlig DOCAC:** DOCAC-13827 (ny status)- **Dokumentationsomfång:**   - Ställa in godkännantoperatörer i leveranser/kampanjer   - Konfigurera godkännande av innehåll   - Konfigurerar målgodkännande   - Hantera arbetsflöden för godkännande i olika kanaler (e-post, SMS, push iOS/Android, direktreklam, callcenter)   - Godkänn/avvisa processer   - Godkännanderapporter och spårning- **Målgrupp:** Kampanjhanterare, Administratörsanvändare- **Version:** AC-UI-25-11-Monthly- **Prioritet:** Kritisk- **Kund:** Pierre Fabre

#### **NEO-91299: Kontinuerlig leveransaktivitet**- **Status:** Stängt- **Varför dokumentation krävs:** Ny arbetsflödesaktivitet för återkommande leveransscenarier- **Befintlig DOCAC:** DOCAC-13586 (ny status), DOCAC-13808 (stängd - sammanhangsberoende hjälp)- **Dokumentationsomfång:**   - Konfiguration av kontinuerlig leveransaktivitet   - Krav för leveransmallväljare   - Bearbeta felhantering   - Integrering av arbetsflöden   - Användningsexempel- **Målgrupp:** Tekniska användare, arbetsflödesdesigners- **Version:** AC-UI-26.01.06

#### **NEO-90130: Flerspråkig överföring av push-filer (H&amp;M)**- **Status:** Stängt- **Varför dokumentation krävs:** OTB-funktionparitet med ACS för filbaserad flerspråkig push- **Befintlig DOCAC:** DOCAC-13606 (ny status)- **Dokumentationsomfång:**   - CSV-filöverföring för flerspråkiga push-meddelanden   - Filformatsspecifikationer   - Fältmappning   - Specifika konfigurationer för iOS och Android   - Typhantering av datameddelanden   - Felsökning och kända problem- **Målgrupp:** Marknadsföringsanvändare, Kampanjansvariga- **Utgåva:** AC-UI-25-10-Monthly, AC-UI-25.11.03- **Prioritet:** Kritisk- **Kund:** H&amp;M (ACS to ACC Migration)

#### **NEO-92942: Fördefinierade filter - delat alternativ**- **Status:** Löst- **Varför dokumentation krävs:** Förbättring av funktionen för regelbyggaren- **Befintlig DOCAC:** DOCAC-13697 (kodgranskningsstatus), DOCAC-13522 (stängd - hjälp)- **Dokumentationsomfång:**   - Delat alternativ för fördefinierade filter   - Hantera filtersynlighet med andra operatorer   - ACC vs Brand Journey-beteenden   - Hantering av filterlistor- **Målgrupp:** Alla användare, Frågedesigners- **Utgåva:** Huvudversion- **FF:** enable-query-filter-shared

### 2.3 LÅG PRIORITET - Förbättrad innehållsredigerare

#### **NEO-88838: Temavariabler i fragment**- **Status:** Ny (spärrad)- **Varför dokumentation krävs:** E-posta Designer-temafunktioner- **Befintlig DOCAC:** DOCAC-12941 (ny status)- **Dokumentationsomfång:**   - Använda temavariabler i e-postfragment   - Temakonfiguration   - Variabelhantering   - Bästa praxis- **Målgrupp:** E-postdesigners, marknadsföringsanvändare- **Utgåva:** AC-UI-26-01-Monthly- **Obs!** Funktionen är spärrad i väntan på granskning på ritytan

&#x200B;---

## &#x200B;3. Biljetter som inte kräver dokumentation

### 3.1 Avbruten/inte längre tillämplig

| Biljett-ID | Titel | Orsak |
|-----------|-------|--------|
| NEO-91566 | CTA tracking in webui | Inget gränssnitt förväntades; väntande information från MSFT |
| NEO-91564 | Stöd för flerspråkigt användargränssnitt i AEM | Gränssnittsarbete som hanteras av olika team |
| NEO-91567 | Stöd för NRT-funktioner | Ingen påverkan på webbgränssnittet - specifikation tillgänglig |
| NEO-91563 | API för transaktionsvila | Inget webbgränssnitt fungerar; väntande instansuppgradering |
| NEO-92151 | Profilanrikningsfas 2 | Artikeln har inga uppgifter, markerad som inte längre används |

### 3.2 Platshållare/spårningsbiljetter

| Biljett-ID | Titel | Orsak |
|-----------|-------|--------|
| NEO-92400 | Versionsförbättringar - 26 januari | Platshållare för att spåra slutförande av förbättringar |

&#x200B;---

## &#x200B;4. Föreslagna DOCAC-biljetter

### 4.1 NYA DOCAC-biljetter krävs

#### **DOCAC-XXXX: Schemaläggning av leverans med stöd för tidszon**&#x200B;**Överordnad biljett:** NEO-93487&#x200B;**Prioritet:** Kritisk&#x200B;**Målversion:** AC-UI-26-01-Monthly&#x200B;**Beskrivning:**&#x200B;Dokumentera den nya beräkningsprocessen för leveransplanering som möjliggör tidszonsbaserad leveransplanering som liknar ACS-funktionaliteten. Med den här funktionen kan marknadsförare skicka kommunikation baserat på mottagarnas tidszoner med hjälp av beräknade formler, särskilt viktigt för flertidszonsmarknader som USA.

**Omfång:**
- Konfigurationsguide för tidszonsbaserad schemaläggning
- Exempel på beräknade formler
- Marknadsscenarier för flera tidszoner
- Migreringsguide från ACS
- God praxis och begränsningar

**Kund:** H&amp;M (kritiskt för ACS till ACC-migrering)

#### **DOCAC-XXXX: Konfiguration av externt konto för Web Analytics**&#x200B;**Överordnad biljett:** NEO-92668&#x200B;**Prioritet:** Normal&#x200B;**Målversion:** AC-UI-26-01-Monthly&#x200B;**Beskrivning:**&#x200B;Dokumentera konfigurationen och användningen av den externa kontotypen för Web Analytics i webbgränssnittet.

**Omfång:**
- Steg för att skapa externa konton
- Konfigurationsparametrar
- Integrering med leveransspårning
- Rapporteringsfunktioner
- Felsökning

&#x200B;---

### 4.2 BEFINTLIGA DOCAC-biljetter att uppdatera

#### **DOCAC-13104: A/B-testning**&#x200B;**Status:** Nytt&#x200B;**Överordnad biljett:** NEO-86754&#x200B;**Åtgärd krävs:** Startdokumentation - funktion i aktiv utveckling&#x200B;**Beräknad leverans:** februari 2026 (väntar på att utvecklingsarbetet ska slutföras)

#### **DOCAC-11070 &amp; DOCAC-13432: Dynamisk rapportering**&#x200B;**Status:** Stängd/löst&#x200B;**Överordnad biljett:** NEO-80973&#x200B;**Åtgärd krävs:**- Uppdatering för allmän tillgänglighet (inte bara 8.7)- Dokumentera motstridiga mätvärden med äldre rapporter- Verifiera språksupportdokumentation

#### **DOCAC-13826: Redigering av scheman**&#x200B;**Status:** Nytt&#x200B;**Överordnad biljett:** NEO-76126&#x200B;**Åtgärd krävs:**- Fas 2-dokumentation (navigera + CRUD + formulärdefinition)- Förbered för fas 3 (skapa/utöka scheman) - ETA Feb end

#### **DOCAC-13829: AEM Live-kopior/språkkopior**&#x200B;**Status:** Löst&#x200B;**Överordnad biljett:** NEO-86753&#x200B;**Åtgärd krävs:** Kontrollera aktuell status och uppdatera efter behov

#### **DOCAC-13565: Multilingual Rich Push**&#x200B;**Status:** Nytt&#x200B;**Överordnad biljett:** NEO-90183&#x200B;**Åtgärd krävs:** Fullständig dokumentation - funktion levererad i november 2025

#### **DOCAC-13827: Godkännandeprocess**&#x200B;**Status:** Nytt&#x200B;**Överordnad biljett:** NEO-84916&#x200B;**Åtgärd krävs:** Fullständig dokumentation - funktion levererad i november 2025

#### **DOCAC-13586 &amp; DOCAC-13808: Continuous Delivery**&#x200B;**Status:** Nytt/Stängt&#x200B;**Överordnad biljett:** NEO-91299&#x200B;**Åtgärd krävs:** Fullständig huvuddokumentation (13586) - funktionen levererad

#### **DOCAC-13606: Överföring av flerspråkig push-fil**&#x200B;**Status:** Nytt&#x200B;**Överordnad biljett:** NEO-90130&#x200B;**Åtgärd krävs:** Fullständig dokumentation - funktionen levererad

#### **DOCAC-13697 &amp; DOCAC-13522: Fördefinierade delade filter**&#x200B;**Status:** Kodgranskning/stängd&#x200B;**Överordnad biljett:** NEO-92942&#x200B;**Åtgärd krävs:** Slutför dokumentation (13697)

#### **DOCAC-12941: Teman i e-post med Designer**&#x200B;**Status:** Nytt&#x200B;**Överordnad biljett:** NEO-88838&#x200B;**Åtgärd krävs:** Väntar på att funktionen ska återupptas

&#x200B;---

## &#x200B;5. Öppna Frågor och saknad information

### 5.1 Efter funktion

#### **A/B-testning (NEO-86754)**- [ ] Vilken är den slutliga UI/UX-valideringsstatusen?- [ ] Finns det specifika begränsningar för transaktionsmeddelanden?- [ ] Hur integreras detta med Acrites förhandsgranskning av innehåll (NEO-92516-blockering)?- [ ] Vilka är simulerings-/förhandsvisningsfunktionerna för varje variant?

#### **Dynamisk rapportering (NEO-80973)**- [ ] Vad är status för återaktiveringen av demomiljön?- [ ] En fullständig lista över motstridiga mätvärden med äldre rapportering?- [ ] Detaljerad matris för språkstöd?- [ ] Prestandajämförelse med äldre rapportering?

#### **Schemaredigering (NEO-76126)**- [ ] När aktiveras fas 2 FF?- [ ] Bekräftad ETA för fas 3 (skapa/utöka scheman)?- [ ] Vilka är miljökonfigurationskraven?- [ ] Finns det några begränsningar jämfört med funktionen för klientkonsolen?

#### **Schemaläggning av leverans (NEO-93487)**- [ ] Är funktionsdemo med PM schemalagd?- [ ] Är fullständiga funktionsspecifikationer tillgängliga?- [ ]-gränssnittsdummies har slutförts och granskats?- [ ] Vad är den exakta formelsyntaxen/strukturen?

#### **AEM Live/Language-kopior (NEO-86753)**- [ ] Vilken är aktuell status för Himanshus team?- [ ] Uppdaterad leveranstidslinje?- [ ] Finns det några beroenden till AEM-versionen?

#### **Webbanalys (NEO-92668)**- [ ] Vad är tillgänglighetsstatus för miljön?- [ ] Vill du slutföra installationskraven?- [ ] Analysplattformar som stöds?

#### **Temavariabler i fragment (NEO-88838)**- [ ] När kommer Acrite att besöka funktionen igen?- [ ] Planeras detta fortfarande för AC-UI-26-01?

### 5.2 Efter lansering

#### **AC-UI-26-01-Monthly (januari 2026)**- [ Bekräftelse på officiellt releasedatum för ]?- [ ] Vill du frysa?- [ ] Testar tidslinjen för slutförande?- [ ] Tidsgräns för dokumentationsleverans?

#### **Levererade funktioner november 2025**- [ ] Vilka funktioner är redan aktiverade i produktionen?- [ ] Har några kända problem eller begränsningar identifierats efter lanseringen?- [ ] har feedback tagits emot?

### 5.3 Dokumentationsprocess

- [ ] Vilka är de små och medelstora företagen för varje funktion?
- [ ] Hur ser dokumentationsgranskningen ut?
- [ ] Måldokumentationsspråk (endast EN eller flerspråkig)?
- [ ] Krav för dokumentationsplattform/format?
- [ ] Tillgänglighet för skärmbilder och demomiljö?

&#x200B;---

## &#x200B;6. Kundpåverkan och eskalering

### 6.1 Kritiska kundbiljetter

| Kund | Biljett | Funktion | Effekt |
|----------|--------|---------|--------|
| **H&amp;M** | NEO-93487 | Schemaläggning | Över 50 marknader; leveranskrav för flera tidszoner; ACS till ACC migreringsblockerare |
| **H&amp;M** | NEO-90130 | Flerspråkig överföring av push-filer | Kritiskt för migrering av ACS till ACC; minskar driftskostnaderna |
| **Pierre Fabre** | NEO-84916 | Godkännandeprocess | Krav på bestämmelser och arbetsflöde |

### 6.2 Microsoft-specifika funktioner

| Biljett | Funktion | Status | Anteckningar |
|--------|---------|--------|-------|
| NEO-86753 | AEM Live/Language-kopior | Nytt | Används flitigt av Microsoft |
| NEO-91566 | CTA Tracking | Stängt/Gäller inte längre | Väntande information från MSFT |
| NEO-91567 | NRT-funktion | Löst/ingen gränssnittseffekt | Ny ACS-funktion för MSFT |

&#x200B;---

## &#x200B;7. Dokumentationsprioriteringar och tidslinje

### 7.1 Omedelbar åtgärd krävs (januari 2026)

**HÖG PRIORITET - Levererad men inte dokumenterad:**
1. **NEO-90183** - Multilingual Rich Push (DOCAC-13565)
2. **NEO-84916** - Godkännandeprocess (DOCAC-13827)
3. **NEO-91299** - Continuous Delivery (DOCAC-13586)
4. **NEO-90130** - Överföring av flerspråkig push-fil (DOCAC-13606)

### 7.2 Pågår - utveckling pågår (februari 2026)

**VIKTIG PRIORITET:**
1. **NEO-86754** - A/B-testning (DOCAC-13104) - Förfaller: februari 2026
2. **NEO-76126** - Schemaredigering (DOCAC-13826) - Fas 2: Feb, Fas 3: Slutfeb
3. **NEO-93487** - Schemaläggning av leverans (NYTT DOCAC) - Eskalering av viktiga kunder

**NORMAL PRIORITET:**
1. **NEO-80973** - Dynamisk rapportering (uppdatering DOCAC-11070)
2. **NEO-92668** - Webbanalys (NY DOCAC)
3. **NEO-86753** - AEM Live/Language-kopior (DOCAC-13829)

### 7.3 Väntande/Framtida

1. **NEO-88838** - Temavariabler (DOCAC-12941) - Väntar på att Acrite ska återuppta

&#x200B;---

## &#x200B;8. Nästa steg

### 8.1 Documentation Team Actions1. **Prioritera levererade funktioner** utan dokumentation (Avsnitt 7.1)2. **Skapa nya DOCAC-biljetter** för NEO-93487 och NEO-926683. **Uppdatera befintliga DOCAC**-biljetter med detaljerad omfattning (avsnitt 4.2)4. **Schemalägg intervjuer med små och medelstora företag** för A/B-tester, scheman och leveransscheman5. **Samla skärmbilder** och förbered demomiljöer6. **Granska och slutför** språkbegränsningar för dynamisk rapportering

### 8.2 Informationsinsamling1. **Kontaktingenjörsleads** för statusuppdateringar om:   - A/B Testning av slutlig validering   - Schemafas 2/3-tidslinje   - Specifikationer för leveransplanering2. **Schemalägg funktionsdemonstrationer** med produkthantering3. **Samla in kundfeedback** från H&amp;M och Pierre Fabre4. **Verifiera miljötillgänglighet** för Web Analytics och Dynamic Reporting

### 8.3 Samordning1. **Synkronisera med Himanshus team** på AEM Live/Language-kopior2. **Koordinera med Acrobat-team** på temavariabelstatus3. **Följ upp Microsoft-specifika**-funktioner med kontoteam

&#x200B;---

## Dokumenthistorik

| Datum | Upphovsman | Version | Ändringar |
|------|--------|---------|---------|
| 2026-01-12 | AI Assistant | 1,0 | Inledande analys av Jira-frågor |

&#x200B;---

## Bilaga: Jira-frågor analyserade

1. `project = NEO AND fixVersion = AC-UI-26-01-Monthly and type = story order by status`
2. `issueFunction in linkedIssuesOf('key=NEO-92400', 'is implemented by')`
3. `project = NEO AND fixVersion = AC-UI-25-11-Monthly and type = story order by status`
4. `project = NEO AND fixVersion = AC-UI-25-11-Monthly and fixVersion != 8.8.2 and type = story order by status`

**Totalt antal resultat:** 19 unika biljetter analyserade

