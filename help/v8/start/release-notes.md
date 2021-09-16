---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-utgåvan
feature: Overview
role: Data Engineer
level: Beginner
hidefromtoc: false
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471,a9d18e75-18e7-491e-bfc4-671c3600396e
source-git-commit: f071fc227dac6d72873744ba56eb0b4b676de5dd
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 4%

---

# Senaste versionen{#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **den senaste Campaign v8-utgåvan**.

## Version 8.1.20 {#release-8-1-20}

_7 september 2021_

**Säkerhetsförbättringar**

* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot kataloggenombrottsangrepp. (NEO-28547)

**Förbättringar**

* Efter att livscykeln upphört har Flash tagits bort från alla relaterade Campaign-funktioner och -komponenter och ersatts med HTML5. Diagramtypen **Mätare** har tagits bort. (NEO-30330) [Läs mer](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/creating-new-reports/creating-a-chart.html)
* När du installerar klientkonsolen i Windows kontrollerar installationsprogrammet nu om det finns en överordnad registernod och skapar en om den saknas. Detta förhindrar potentiella problem när konsolen startas. (NEO-34854)
* Funktionen för att spåra signaturer har förbättrats för att förhindra att fel länkas till hur tredjepartsverktyg (e-postklienter, webbläsare osv.) fungerar hantera specialtecken. URL-parametrar är nu kodade.

**Andra ändringar**

* Tidigare borttagna Microsoft CRM-anslutningar (Office 365- och On-Local-distributioner) har tagits bort från gränssnittet. [Läs mer](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/connectors/crm-connectors/crm-ms-dynamics.html#configure-acc-for-microsoft)
* Efter migreringen till Tomcat 8 har IIS-installationsskriptet uppdaterats för att åtgärda IIS-integreringsproblem. (NEO-31019)
* Ett skyddsförslag har lagts till för att endast tillåta att det [tekniska arbetsflödet](https://experienceleague.adobe.com/docs/campaign-classic/using/monitoring-campaign-classic/production-procedures/monitoring-processes.html#billing-report) för fakturering körs på marknadsinstansen.
* Identifieringen av datakällan har förbättrats på flikarna data och schema i arbetsflödesövergångarnas **Visa ifyllning**-fönster.
* Databasindex som saknas har lagts till i följande scheman för att förhindra problem med databasuppdatering: xtk:rights, nms:dlvExclusion, nms:seedMember, nms:trackingUrl

**Felkorrigeringar**

* Korrigerade ett problem som gjorde att **Hot Click**-rapporten inte fungerade när erbjudandena länkades till leveransen. (NEO-26295)
* Korrigerade ett problem med aktiviteten **Delarbetsflöde** när körningen inte genererade någon utdatatabell. (NEO-36242)
* Åtgärdade olika problem vid export av **Beskrivande analys**-rapporten till PDF. (NEO-25847)
* Korrigerade ett problem som kan leda till att leveranser misslyckas när en extern e-postleverans används. (NEO-37435)
* Ett fel har korrigerats vid anslutning till Microsoft CRM med webb-API. Felmeddelandet har tagits bort eftersom funktioner inte påverkades.
* Ett problem med borttagning av dubbletter i spårningsloggar när mittservern angavs som relä mellan spårnings- och marknadsföringsservrar har åtgärdats. (NEO-36285)
* Korrigerade en regression som förhindrade att Vault användes som ett specifikt kodarkiv.
* Korrigerade ett problem som förhindrade dig från att använda variabler i en **arbetsflödesaktivitet för berikning** när den inkommande övergången kom från en FDA-datakälla.
* Korrigerade ett problem med FFDA som förhindrar korrekt replikering av operatörsgrupper och behörigheter.
* Korrigerade ett problem som kunde leda till att en felaktig avprenumerationslänk skickades via leveransen.
* Ett problem med replikeringshantering som påverkar efteruppgraderingens varaktighet har korrigerats.
* Korrigerade ett fel som kunde förhindra att **snabbklickningen** visades.
* Korrigerade ett problem som kunde leda till trasiga URL:er i e-postmeddelanden.

## Version 8.1.14 {#release-8-1-14}

_23 juli 2021_

**Nyheter**

<table>
<thead>
<tr>
<th><strong>Ny arbetsflödesaktivitet: Ändra datakälla</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Med den nya arbetsflödesaktiviteten <b>Ändra datakälla</b> kan du ändra datakällan för arbetsflödets arbetsregister. Detta ger större flexibilitet vid datahantering över olika datakällor (FDA, FFDA och lokal databas).</p>
<p>I Adobe Campaign-arbetsflöden hanteras data med hjälp av fungerande (eller tillfälliga) tabeller. När arbetsflödet körs delar arbetsregister data mellan arbetsflödesaktiviteter. Som standard skapas arbetstabeller i samma databas som källan för de data som vi vill fråga efter.</p>
<p>Med Campaign v8 lagras huvudprofiltabellen direkt i molndatabasen. Om du frågar i tabellen Profiler skapas även en fungerande tabell i molndatabasen. I vissa fall kan det vara bra att flytta arbetstabellen till en annan datakälla för att kunna utföra vissa åtgärder.</p>
<p>Mer information finns i den <a href="../config/workflows.md#change-data-source-activity">detaljerade dokumentationen</a>.</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Tillgänglighet för LINE-kanal</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../send/line.md">LINE-kanalen</a> är nu tillgänglig med Campaign v8, inklusive följande förbättringar i kombination med <a href="../send/transactional.md">transaktionsmeddelandemodulen</a>:
<ul> 
<li><p>Korrigerade ett problem som kunde förhindra besökare från att riktas mot en radleverans. 
</p></li>
<li><p>Korrigerade ett problem som kunde orsaka fel när besökare hämtades från körningsinstansen till marknadsinstansen.
</p></li>
<li><p>Korrigerade problem under bearbetning av realtidshändelser.</p></li>
</ul>
</td> 
</tr> 
</tbody> 
</table>

**Andra förbättringar**

* Korrigerade ett problem som kunde förhindra att **Hot Click**-rapporten visas för specifika leveranser.
* Korrigerade ett problem med arbetsflödesaktiviteten **Deduplicering** som kunde resultera i en felaktig dubblettinventering.
* Ett problem har korrigerats när en arbetsflödesfråga med filtret &quot;ID är inte tomt&quot; användes, vilket kan leda till att ett tomt objekt visas i övergångspopulationen.
* Korrigerade ett problem som förhindrade att ytterligare fält skapades i en ny målmappning.
