---
title: Översikt över kampanjövervakning
description: Lär dig övervaka leveranser, arbetsflöden och din Campaign-instans
feature: Monitoring
role: User
level: Beginner
source-git-commit: c4d3a5d3cf89f2d342c661e54b5192d84ceb3a75
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 2%

---

# Översikt över kampanjövervakning {#monitor-campaign}

Adobe Campaign har en omfattande uppsättning funktioner för att övervaka processer, leveranser och miljöer för att säkerställa optimala prestanda och felsöka problem proaktivt.

>[!NOTE]
>
>Som kampanjadministratör kan du även använda [Campaign-kontrollpanelen](#control-panel) för att övervaka dina instanser, hantera prestanda och konfigurera inställningar med självbetjäningsfunktioner.

## Övervaka leveranser {#monitor-deliveries}

Att övervaka era leveranser efter att de har skickats är ett viktigt steg för att se till att era marknadsföringskampanjer är effektiva och når ut till era kunder. När du har skickat en leverans kan du övervaka dess status och spåra nyckelvärden på kontrollpanelen för leverans. Kontrollpanelen ger tillgång till leveransloggar, exkluderingsloggar, spårningsloggar och andra övervakningsfunktioner som hjälper dig att analysera leveransresultaten i alla kanaler.

**E-postleveranser** - Övervaka e-postleveransstatus, spåra nyckeltal och få tillgång till detaljerade loggar. Läs mer om [övervakning av leveranser i Campaign-gränssnittet](../send/delivery-dashboard.md), [leveransstatus](../send/delivery-statuses.md) och [övervakning av e-postleveranser](../send/send.md#email-monitoring).

**SMS-leveranser** - Spåra SMS-leveransstatus och övervaka nyckelvärden på SMS-leveransinstrumentpanelen. Läs mer om [SMS-övervakning](../send/sms/sms-monitor.md).

**Push-meddelanden** - Övervaka push-meddelandeleveranser för att se till att de når era mobilappsanvändare effektivt. Läs mer om [övervakning av push-meddelanden](../send/push.md#push-test).

**Transaktionsmeddelanden** - För meddelanden som utlöses av händelser ska du övervaka händelsebearbetningsstatus, meddelandekörning och leveransstatus. Läs mer om [övervakning av transaktionsmeddelanden](../send/delivery-execution.md#monitor-messages).

**Leveransfel** - Det är viktigt att förstå varför en leverans misslyckades för att upprätthålla en ren databas och säkerställa goda leveransfrekvenser. Leveransfel klassificeras i hårda studsar, mjuka studsar och ignorerade meddelanden. Läs mer om [leveransfel och karantän](../send/delivery-failures.md).

## Skärmleverans {#monitor-deliverability}

Med leveransövervakning kan du säkerställa att dina meddelanden når mottagarnas inkorgar och undviker skräppostfilter. Adobe Campaign har flera inbyggda verktyg för att övervaka och förbättra leveransen, inklusive leveransrapporter, inkorg-rendering, SpamAssassin-testning och sändningsstatistik. För att upprätthålla goda leveransgrader är det viktigt att du följer god praxis för leverans, som att upprätthålla en ren e-postlista, övervaka avsändarens anseende och autentisera avsändardomäner.

Läs mer om [verktyg för övervakning av levererbarhet](../send/monitoring-deliverability.md) och [god praxis för levererbarhet](../send/about-deliverability.md).

## Övervaka arbetsflöden {#monitor-workflows}

Arbetsflöden är nödvändiga för att automatisera era marknadsföringskampanjer och databearbetningar. Genom att övervaka arbetsflödeskörningen kan du:

* Säkerställ att arbetsflödena slutförs
* Identifiera och felsöka fel
* Optimera arbetsflödets prestanda

### Funktioner för arbetsflödesövervakning {#workflow-monitoring}

**Övervaka följande arbetsflödeselement:**

**Körningsstatus för arbetsflöde** - Spåra om arbetsflöden körs, pausas, misslyckas eller slutförs. [Läs mer om arbetsflödeskörning](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}

**Loggar för aktivitetskörning** - Få tillgång till detaljerade loggar för varje arbetsflödesaktivitet för att felsöka problem och optimera prestanda.

**heatmap för arbetsflöde** - Visa mönster för arbetsflödeskörning, identifiera flaskhalsar och övervaka samtidiga arbetsflöden. Workflow HeatMap är tillgängligt för Campaign-administratörer. [Läs mer om heatmap för arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/heatmap.html){target="_blank"}

**Arbetsflödeshistorik** - Spåra alla arbetsflödeskörningar och ändringar över tid för att förstå arbetsflödets beteende och prestanda.

## Övervaka instansen {#monitor-instance}

Med instansövervakning kan du säkerställa hälsan och prestandan i din Adobe Campaign-miljö.

### Granskningskedja {#audit-trail}

Med självbetjäningsgränssnittet för granskningsspår kan du övervaka ändringar som görs i Adobe Campaign-instansen. Granskningsspårning visar i realtid en omfattande lista över åtgärder och händelser som inträffar i instansen.

**Använd granskningsspår för:**

* **Spåra komponentändringar**: Övervaka vad som hände med dina arbetsflöden, scheman, alternativ och andra komponenter
* **Identifiera vem som gjorde ändringar**: Se vem som senast uppdaterade ett visst element och när
* **Förstå användaråtgärder**: Granska vad användarna gjorde i instansen för att felsöka eller granska
* **Underhåll efterlevnad**: Spåra alla konfigurationsändringar i efterlevnads- och säkerhetssyfte

Granskningsspårningen är tillgänglig via Campaign-klientkonsolen och ger detaljerad information om åtgärder som utförs av användare.

Läs mer om [Granskningsspår](../reporting/audit-trail.md)

### Prestandaövervakning {#performance-monitoring}

Campaign v8 har flera övervakningsfunktioner för att spåra instansens prestanda och säkerställa optimal funktion:

**Databasövervakning** - Övervaka databasanvändning och -kapacitet via Kontrollpanelen för att säkerställa optimala prestanda och lagringshantering. [Läs mer om databasövervakning](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/database-monitoring.html){target="_blank"}

**Övervakning av aktiva profiler** - Spåra aktiv profilanvändning mot avtalsgränserna för att upprätthålla regelefterlevnad och optimera resursallokering. [Läs mer om aktiva profiler](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html){target="_blank"}

**Arbetsflödesövervakning** - Övervaka arbetsflödets körningsstatus för att identifiera tidskrävande arbetsflöden och se till att alla tekniska arbetsflöden körs korrekt. [Läs mer om tekniska arbetsflöden](#technical-workflows)

**Leveransdataflöde och fördröjning** - Spåra leveransdataflöde (meddelanden som skickas per timme) och fördröjning för transaktionskommunikation via Kontrollpanelen. [Läs mer om genomströmningsövervakning](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/throughputs-latencies.html){target="_blank"}

>[!NOTE]
>
>För Hanterade molntjänster i Campaign v8 övervakas serverinfrastrukturen (CPU, minne, disk) och hanteras av Adobe.

### Tekniska arbetsflöden {#technical-workflows}

Tekniska arbetsflöden är viktiga processer som körs i bakgrunden för att behålla Campaign-instansen.

**Övervaka att tekniska arbetsflöden är:**

* Kör enligt schema
* Slutfördes utan fel
* Bearbetar data korrekt

**Viktiga tekniska arbetsflöden att övervaka:**

| Arbetsflöde | Syfte |
|----------|---------|
| **Spårning** | Bearbetar spårning av data från e-postleveranser |
| **Rensa** | Tar bort gamla data och loggar för att upprätthålla databasprestanda |
| **Leveransuppdatering** | Uppdaterar leveransregler och mönster för skräppostfilter |
| **Databasrensning** | Tar bort gamla loggar för leverans och spårning |

Läs mer om [tekniska arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html){target="_blank"}

### Kontrollpanelen i Campaign {#control-panel}

Campaign Control Panel ger administratörer självbetjäningsfunktioner för att övervaka och hantera Campaign-instanser.

| Övervakningstyp | Funktioner |
|-----------------|--------------|
| **Prestanda** | Spåra aktiv profilanvändning, övervaka databasanvändning och -kapacitet, visa arbetsflödeskörningsstatus, övervaka leveransflöde och fördröjning |
| **Infrastruktur** | Övervaka SFTP-lagringskapacitet, spåra konfiguration av underdomän, övervaka SSL-certifikatets förfallodatum, hantera lista över tillåtna IP-adresser |
| **Instans** | Visa version och installerade paket, övervaka systemkonfiguration, hantera auktoriserade externa domäner |

Läs mer om [Kontrollpanelen](../config/self-service.md) och [prestandaövervakning för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html?lang=sv){target="_blank"}

>[!NOTE]
>
>För Campaign v8 Managed Cloud Services övervakar och hanterar Adobe serverinfrastrukturen, operativsystemet och programlagret. Du kan använda de övervakningsfunktioner som beskrivs på den här sidan och kontrollpanelen för att övervaka instansens prestanda, arbetsflöden och leveranser.

## Spåra och rapportera {#tracking-reporting}

### Meddelandespårning {#message-tracking}

Spåra mottagarnas beteende och mät kampanjernas effektivitet:

* **Öppnar**: Spåra när mottagarna öppnar dina e-postmeddelanden
* **Klicka**: Övervaka vilka länkar mottagarna klickar på
* **Avbeställ**: Spåra avanmälningsbegäranden
* **Spegla sidvyer**: Se hur många mottagare som visar din e-post i en webbläsare

Läs mer om [meddelandespårning](../send/tracking.md)

### Leveransrapporter {#delivery-reports}

Adobe Campaign tillhandahåller en omfattande uppsättning rapporter för att analysera leveransresultaten:

* **Leveranssammanfattning**: Översikt över sändningar, leveranser och fel
* **Spårningsindikatorer**: Öppnar, klickningar och klickfrekvens
* **URL:er och klicka på strömmar**: De populäraste länkarna i dina leveranser
* **Snabbklickningar**: Visuell representation av var mottagarna klickade i e-postmeddelandet

Läs mer om [leveransrapporter](../reporting/delivery-reports.md)

### Globala rapporter {#global-reports}

Använd globala rapporter för att analysera resultatet för alla kampanjer och leveranser:

* **Leveransdataflöde**: Meddelanden skickade över tid
* **Ej levererbara och studsade**: Analys av misslyckade leveranser
* **Användaraktiviteter**: Öppnar, klickar och avslutar prenumerationen på alla kampanjer

Läs mer om [globala rapporter](../reporting/global-reports.md)

## Relaterade ämnen {#related-topics}

* [Bästa praxis för leverans](delivery-best-practices.md)
* [Karantänhantering](../send/quarantines.md)
* [Konfigurera och skicka leveranser](../send/configure-and-send.md)
* [Kom igång med rapportering](../reporting/gs-reporting.md)

