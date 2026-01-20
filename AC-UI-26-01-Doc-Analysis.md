---
source-git-commit: 548b4be24e26a6970f953f92af1f89d829689592
workflow-type: tm+mt
source-wordcount: '1522'
ht-degree: 0%

---
# AC-UI-26-01 - Dokumentationsanalys

## Innehåll för nästa release

I det här dokumentet analyseras JIRA-produkter för månadsutgåvorna AC-UI-26-01 och AC-UI-25-11 för att planera dokumentationsåtgärder.

### JIRA-filter

1. **[Artiklar om AC-UI-26-01-Monthly &#x200B;](https://jira.corp.adobe.com/issues/?jql=project%20%3D%20NEO%20AND%20fixVersion%20%3D%20AC-UI-26-01-Monthly%20and%20type%20%3D%20story%20order%20by%20status)** - huvudversioner
2. **[NEO-92400-förbättringar](https://jira.corp.adobe.com/issues/?jql=issueFunction%20in%20linkedIssuesOf(%27key%3DNEO-92400%27%2C%20%27is%20implemented%20by%27))** - Versionsförbättringar länkade problem
3. **[AC-UI-25-11-Monthly Stories](https://jira.corp.adobe.com/issues/?jql=project%20%3D%20NEO%20AND%20fixVersion%20%3D%20AC-UI-25-11-Monthly%20and%20type%20%3D%20story%20order%20by%20status)** - föregående release Carryover
4. **[AC-UI-25-11 Exklusive 8.8.2](https://jira.corp.adobe.com/issues/?jql=project%20%3D%20NEO%20AND%20fixVersion%20%3D%20AC-UI-25-11-Monthly%20and%20fixVersion%20!%3D%208.8.2%20and%20type%20%3D%20story%20order%20by%20status)** - filtrerad föregående version

&#x200B;---

## 🟢 Skapa DOCAC

### [NEO-91565](https://jira.corp.adobe.com/browse/NEO-91565) - Lägg till stöd för anpassningsfält (avancerad AEM-integrering)**Status:** Löst\**Dokument krävs:** Ja\**Befintlig DOCAC:** Ingen\**Åtgärd:** Skapa DOCAC

**Omfång:**
- Dokumentstöd för personaliseringsfält i avancerad AEM-integrering
- Arbetsflöde och konfigurationssteg för användargränssnittet
- AEM flerspråkiga integreringsfunktioner

**Funktionsbeskrivning:**
Stöd för att lägga till personaliseringsfält i leveranser med avancerad AEM-integrering, vilket gör det möjligt att infoga dynamiskt innehåll från Campaign-data i AEM-skapade e-postmallar.

**Kontext:** ACS till ACC-paritet, MSFT-specifikt krav

**Referenser:** [AEM flerspråkig wiki](https://wiki.corp.adobe.com/pages/viewpage.action?pageId=2988189953)

&#x200B;---

### [NEO-93487](https://jira.corp.adobe.com/browse/NEO-93487) - Beräkningsprocess för leveransplanering (ACS-paritet)**Status:** Nytt\**Dokument krävs:** Ja\**Befintlig DOCAC:** Ingen\**Åtgärd:** Skapa DOCAC

**Omfång:**
- Beräkningsprocess för dokumentleveransplanering för push-meddelanden
- Tidszonsbaserade planeringsformler
- Filöverföring för mål med flera tidszoner

**Funktionsbeskrivning:**
Möjliggör OOTB-filbaserad leveransplanering med beräknade sändningstider baserat på mottagarnas tidszon, vilket möjliggör enkel leverans över flera tidszoner med optimerade sändningstider per region.

**Kontext:** Kunddriven (H&amp;M), ACS till ACC-paritetskrav

**Referenser:** [ACS-dokumentation](https://experienceleague.adobe.com/sv/docs/campaign-standard/using/testing-and-sending/scheduling-messages/computing-the-sending-date)

&#x200B;---

## 🔄 Uppdatera DOCAC

### [NEO-80973](https://jira.corp.adobe.com/browse/NEO-80973) - Tillgänglighet för dynamisk rapportering för alla användare i webbgränssnittet&#x200B;**Status:** Pågår\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-11070](https://jira.corp.adobe.com/browse/DOCAC-11070) (stängd), [DOCAC-13432](https://jira.corp.adobe.com/browse/DOCAC-13432) (löst)\**Åtgärd:** Granska DOCAC

**Omfång:**
- Uppdatera tillgänglighetsinformation (nu för alla användare av webbgränssnittet, inte bara 8.7)
- Begränsningar för dokumentspråk
- Förtydliga hur motstridiga mätvärden visas med äldre rapporter

**Funktionsbeskrivning:**
Dynamisk rapportering är nu tillgängligt för alla som använder Campaign Web UI (tidigare begränsat till 8.7 ACS till ACC-kunder), vilket ger avancerade analysfunktioner och anpassade rapporteringsfunktioner med ett gränssnitt av ACS-typ.

**Kontext:** Funktionsexpansion, serverdelsberoende (8.8.1)

**Referenser:** [Wiki - rapportjämförelse](https://wiki.corp.adobe.com/display/~kumarvishal/Reports+-+Client+console+vs+WebUI)

&#x200B;---

### [NEO-86754](https://jira.corp.adobe.com/browse/NEO-86754) - A/B-testning&#x200B;**Status:** Pågår\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-13104](https://jira.corp.adobe.com/browse/DOCAC-13104) (ny)\**Åtgärd:** Uppdatera DOCAC

**Omfång:**
- Komplett dokumentation för arbetsflöde för A/B-testning
- Installation av innehållsexperiment och variantkonfiguration
- Exempel på definition av proportioner och kriterier för val av vinnare
- Insamling och utvärdering av statistik

**Funktionsbeskrivning:**
Innehållsexperiment och A/B-tester för e-postleveranser, vilket gör det möjligt för marknadsförare att testa olika innehållsvarianter, definiera urvalsstorlekar, samla in prestandastatistik och automatiskt skicka den vinnande varianten till de återstående mottagarna.

**Kontext:** Europa-projekt, Microsoft-krav, funktionsflagga aktiverad

**Referenser:** [Wiki](https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3017705719), [Figma mocks](https://www.figma.com/design/4EfXEaA6OIV0D8rauuXSWX/A-B-Testing)

&#x200B;---

### [NEO-76126](https://jira.corp.adobe.com/browse/NEO-76126) - Skapa scheman (skapa ny tabell, utöka scheman, få åtkomst till extern DB)**Status:** Pågår\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-13826](https://jira.corp.adobe.com/browse/DOCAC-13826) (ny)\**Åtgärd:** Uppdatera DOCAC

**Omfång:**
- Arbetsflöde för redigering av dokumentschema (endast 3 alternativ: skapa tabell, utöka schema, få åtkomst till extern DB)
- Formulärdefinition för anpassade entiteter
- Navigera och CRUD-åtgärder i anpassade scheman
- Funktioner i fas 2 och fas 3

**Funktionsbeskrivning:**
Schemaredigeringsfunktioner i webbgränssnittet gör att administratörer kan skapa nya databastabeller, utöka befintliga scheman med anpassade fält och ansluta till externa databaser - vilket är nödvändigt för datamodellanpassning.

**Kontext:** Microsoft-krav, Europa-projekt, fasad leverans (fas 2 aktiv, fas 3 feb-slut)

**Referenser:** [PRD](https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=neolane&title=AC+Web+UI+-+Schemas+PRD), [Figma](https://www.figma.com/design/lZkJso2HvXPbNjG0TmQTrC/Schemas)

&#x200B;---

### [NEO-92668](https://jira.corp.adobe.com/browse/NEO-92668) - Webbanalys&#x200B;**Status:** Nytt\**Dokument krävs:** Ja\**Befintlig DOCAC:** Ingen\**Åtgärd:** Skapa DOCAC

**Omfång:**
- Konfiguration av externt webbanalyskonto
- Inställning och autentisering av integrering
- Analysdataanvändning i kampanjer

**Funktionsbeskrivning:**
Integrering med Web Analytics möjliggör anslutning till webbanalysplattformar för spårning och rapportering av kampanjresultat och webbplatsbesökares beteende.

**Kontext:** Kundförfrågan (P2E-RSC), väntande miljötillgänglighet

**Referenser:** Inga angivna

&#x200B;---

### [NEO-86753](https://jira.corp.adobe.com/browse/NEO-86753) - AEM-integration för Live-kopior/språkkopior&#x200B;**Status:** Nytt\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-13829](https://jira.corp.adobe.com/browse/DOCAC-13829) (löst)\**Åtgärd:** Granska DOCAC

**Omfång:**
- Bläddra bland leveransmallar för AEM
- Skapa live-kopior och språkversioner med ett klick
- Arbetsflöde för att skapa flerspråkiga innehållsvarianter

**Funktionsbeskrivning:**
Smidig integrering med AEM som gör det möjligt att skapa kopior på Live och språkversioner från AEM mallar, vilket förenklar framtagning av flerspråkiga kampanjer för AEM-användare.

**Kontext:** Microsoft-krav, arbete överfört till Himanshus team

**Referenser:** [ACS-dokumentation](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/working-with-campaign-and-experience-manager/creating-multilingual-email-aem.html?lang=sv-SE)

&#x200B;---

### [NEO-88838](https://jira.corp.adobe.com/browse/NEO-88838) - Innehållsredigeraren: Använd temavariabler i fragment&#x200B;**Status:** Nytt\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-12941](https://jira.corp.adobe.com/browse/DOCAC-12941) (ny)\**Åtgärd:** Uppdatera DOCAC

**Omfång:**
- Temavariabler i e-postdesigner (Beta)
- Använda teman i fragment
- Aktivera Acriter-funktionen

**Funktionsbeskrivning:**
Stöd för användning av temavariabler i innehållsfragment, vilket möjliggör enhetlig branding- och designsystemanvändning i alla e-postkomponenter med centraliserad temahantering.

**Kontext:** Spärrad, Acrite-funktionen som ska omprövas

**Referenser:** [ATU-5460](https://jira.corp.adobe.com/browse/ATU-5460)

&#x200B;---

## ➕ Skapa DOCAC (förbättringar)

### [NEO-92942](https://jira.corp.adobe.com/browse/NEO-92942) - Fördefinierade filter - Delat alternativ&#x200B;**Status:** Löst\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-13697](https://jira.corp.adobe.com/browse/DOCAC-13697) (kodgranskning), [DOCAC-13522](https://jira.corp.adobe.com/browse/DOCAC-13522) (stängd - hjälp)\**Åtgärd:** Granska DOCAC

**Omfång:**
- Delat alternativ för fördefinierade filter
- Filtersynlighet med andra operatorer (beteendet ACC kontra Brand Journey)
- Hantering av delade filter

**Funktionsbeskrivning:**
Fördefinierade filter kan nu markeras som&quot;delade&quot; för att göra dem synliga för andra operatorer, med olika beteende för ACC (standard) och Brand Journey (användarspecifik filtrering).

**Kontext:** Förbättrad regelbyggare, funktionsflagga: enable-query-filter-shared

**Referenser:** Relaterat till [NEO-88441](https://jira.corp.adobe.com/browse/NEO-88441)

&#x200B;---

### [NEO-91299](https://jira.corp.adobe.com/browse/NEO-91299) - Kontinuerlig leveransaktivitet&#x200B;**Status:** Stängt\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-13586](https://jira.corp.adobe.com/browse/DOCAC-13586) (ny), [DOCAC-13808](https://jira.corp.adobe.com/browse/DOCAC-13808) (stängd - sammanhangsberoende hjälp)\**Åtgärd:** Uppdatera DOCAC

**Omfång:**
- Arbetsflödesaktivitet för kontinuerlig leverans
- Konfiguration av leveransmallväljare
- Automatisk generering av utgående övergång
- Målinställningar (ingen innehållsåtkomst)

**Funktionsbeskrivning:**
Kontinuerlig leveransaktivitet för arbetsflöden möjliggör återkommande leveranskörning från mallar, vilket automatiskt genererar utgående övergångar för arbetsflödessamordning utan att något innehåll ändras.

**Kontext:** Funktionsflagga: enable-continuous-delivery

**Referenser:** Relaterad episk [NEO-67972](https://jira.corp.adobe.com/browse/NEO-67972)

&#x200B;---

### [NEO-90130](https://jira.corp.adobe.com/browse/NEO-90130) - Aktivera OTB-filöverföring för flerspråkiga push-meddelanden&#x200B;**Status:** Stängt\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-13606](https://jira.corp.adobe.com/browse/DOCAC-13606) (ny)\**Åtgärd:** Uppdatera DOCAC

**Omfång:**
- Filöverföring för flerspråkiga push-meddelanden (iOS och Android)
- CSV-format och fältmappning
- Stort stöd för flera språk

**Funktionsbeskrivning:**
OOTB-filöverföring för att skapa flerspråkiga push-meddelandeleveranser via CSV-import, matcha ACS-funktioner och möjliggör effektiv konfiguration av flerspråkiga kampanjer.

**Kontext:** Kunddriven (H&amp;M), ACS till ACC-paritet, kritisk för migrering

**Referenser:** [ACS-dokumentation](https://experienceleague.adobe.com/sv/docs/campaign-standard/using/communication-channels/push-notifications/generating-csv-multilingual-push)

&#x200B;---

## ❌ har avbrutits/gäller inte längre

### [NEO-91566](https://jira.corp.adobe.com/browse/NEO-91566) - Stöd för CTA-spårning i webbui&#x200B;**Status:** Stängd (gäller inte längre)\**Dokument krävs:** Nej\**Befintlig DOCAC:** [DOCAC-13821](https://jira.corp.adobe.com/browse/DOCAC-13821) (ny)\**Åtgärd:** Stäng DOCAC

**Orsak:** Ny ACS-funktion som stöder MSFT - inte startad, väntande information från MSFT, inget användargränssnitt förväntades

**Kontext:** Microsoft-specifikt, CTA-spårningskrav

&#x200B;---

### [NEO-91564](https://jira.corp.adobe.com/browse/NEO-91564) - Stöd för flerspråkigt gränssnitt för AEM&#x200B;**Status:** Stängd (gäller inte längre)\**Dokument krävs:** Nej\**Befintlig DOCAC:** [DOCAC-13822](https://jira.corp.adobe.com/browse/DOCAC-13822) (ny)\**Åtgärd:** Stäng DOCAC

**Orsak:** Gränssnittet hanteras av Himanshus team (en annan artikel)

**Kontext:** Microsoft-krav, arbete har överförts

&#x200B;---

### [NEO-91567](https://jira.corp.adobe.com/browse/NEO-91567) - Lägg till stöd för NRT-funktionen&#x200B;**Status:** Löst (gäller inte längre)\**Dokument krävs:** Nej\**Befintlig DOCAC:** [DOCAC-13824](https://jira.corp.adobe.com/browse/DOCAC-13824) (ny)\**Åtgärd:** Stäng DOCAC

**Orsak:** Ny ACS-specifik funktion för MSFT - specifikation tillgänglig men ingen påverkan på webbgränssnittet

**Kontext:** Microsoft-krav, transaktionsmeddelanden

&#x200B;---

### [NEO-91563](https://jira.corp.adobe.com/browse/NEO-91563) - Transactional Rest API for Profile Based Enrichment&#x200B;**Status:** Löst (gäller inte längre)\**Dokument krävs:** Nej\**Befintlig DOCAC:** [DOCAC-13825](https://jira.corp.adobe.com/browse/DOCAC-13825) (ny)\**Åtgärd:** Stäng DOCAC

**Orsak:** Inget webbgränssnitt fungerar, väntande uppgraderad instans, build upgrade mandatory for release

**Kontext:** REST API-slutpunktsfunktion

&#x200B;---

### [NEO-92151](https://jira.corp.adobe.com/browse/NEO-92151) - Profilbaserad Enrichment Transactional Messaging Phase 2&#x200B;**Status:** Löst (gäller inte längre)\**Dokument krävs:** Nej\**Befintlig DOCAC:** [DOCAC-13823](https://jira.corp.adobe.com/browse/DOCAC-13823) (ny)\**Åtgärd:** Stäng DOCAC

**Orsak:** Artikeln har inga aktiviteter, markerad som &quot;gäller inte längre&quot;

**Kontext:** Microsoft-krav, Europa-projekt

&#x200B;---

## 🟢 Documentation Ready (from AC-UI-25-11)

### [NEO-90183](https://jira.corp.adobe.com/browse/NEO-90183) - Multilingual Rich Push - UI&#x200B;**Status:** Stängt\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-13565](https://jira.corp.adobe.com/browse/DOCAC-13565) (ny)\**Åtgärd:** Granska DOCAC

**Omfång:**
- Omfattande push-fält för flerspråkiga leveranser
- Stöd för iOS och Android
- Konfiguration av mallar och innehåll

**Funktionsbeskrivning:**
Stöd för push-meddelanden med flerspråkiga funktioner som gör att marknadsförarna kan skapa förbättrade push-meddelanden med bilder, knappar och multimedia för både iOS och Android på flera språk.

**Kontext:** Kundstyrd (H&amp;M), levererad i 25-11, backend-arbete slutfört

**Referenser:** [Wiki](https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=neolane&title=Rich+push+fields+in+multilingual)

&#x200B;---

### [NEO-84916](https://jira.corp.adobe.com/browse/NEO-84916) - Konfigurera och hantera godkännandeprocessen&#x200B;**Status:** Löst\**Dokument krävs:** Ja\**Befintlig DOCAC:** [DOCAC-13827](https://jira.corp.adobe.com/browse/DOCAC-13827) (ny)\**Åtgärd:** Uppdatera DOCAC

**Omfång:**
- Konfigurera valideringsoperatorer i leverans/kampanj
- Inställningar för godkännandearbetsflöde
- Godkännandeprocess för innehåll och mål
- Flerkanalsstöd (e-post, SMS, push, direktreklam, callcenter, anpassad)

**Funktionsbeskrivning:**
Hantering av godkännandeprocesser möjliggör valideringsarbetsflöden för leveransinnehåll och målinriktning, med operatörstilldelning och spårning av godkännanden i alla leveranskanaler.

**Kontext:** Kunddriven (Pierre Fabre), Microsoft-krav, fullständig och testad dev

**Referenser:** [Klassisk dokumentation](https://experienceleague.adobe.com/sv/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-approval), [Figma mocks](https://www.figma.com/design/r2vpqXoVyI3aucKgkt8TLN/Approvals)

&#x200B;---

## 📊 Sammanfattning efter åtgärd

| Åtgärd | Antal |
|--------|-------|
| 🟢 Skapa DOCAC | 3 |
| 🔄 Uppdatera DOCAC | 6 |
| ✅ Granska DOCAC | 3 |
| ❌ Stäng DOCAC | 5 |
| **Totalt** | **17** |

&#x200B;---

## ⚠️ Öppna frågor

1. NEO-93487 - Eskalering av H&amp;M - kräver omedelbar åtgärd vid schemaläggning av beräkningsprocessen
2. NEO-92668 - Web Analytics - Väntar på miljötillgänglighet innan dokumentation kan slutföras
3. NEO-76126 - Schema fas 3 - ETA Feb end, need separate documentation story
4. NEO-88838 - Temavariabler - är spärrade i väntan på funktionsrevision i Acrite
5. Dynamisk rapportering - förtydliga motstridiga mätvärden med hjälp av äldre rapporter

&#x200B;---

## 🔗 relaterade e-postmeddelanden

- NEO-85263 - ACS to ACC (EUROPA) parent epic
- NEO-67972 - Förbättrat arbetsflöde
- NEO-87980 - avancerad AEM-integrering
- NEO-90199 - Dynamisk rapporteringsberedskap
- NEO-63067 - Innehållsexperimenterande UX/UI
- NEO-67726 - A/B-testning och innehållsexperiment
- NEO-85274 - Schema och form (fas 2)
- NEO-87993 - Schema och form (fas 3)
