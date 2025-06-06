---
title: Versionsinformation om Campaign v8 2021
description: Lista över funktioner och förbättringar i 2021 års Campaign v8-utgåvor
feature: Release Notes
hide: true
hidefromtoc: true
exl-id: 5ac6bda9-86c8-4200-b285-6fee2a29039d
source-git-commit: e4f6c70ecdcf7414b5f49a43933cfd1c967a0905
workflow-type: tm+mt
source-wordcount: '1581'
ht-degree: 37%

---

# Versionsinformation 2021{#2021-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **2021 Campaign v8-utgåvorna**.

## Version 8.2.8 {#release-8-2-8}

_28 oktober 2021_

<table>
<thead>
<tr>
<th><strong>Inkommande interaktion</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Interaktionshantering i realtid är nu tillgänglig för inkommande kanaler. Använd modulen Kampanjinkommande interaktion för att presentera det bästa erbjudandet för era kunder när de besöker er webbplats eller kontaktar ert callcenter. Den här funktionen har Campaign v8 som ett alternativ och kräver en specifik konfiguration för din instans. Kontakta Adobe för att få tillgång till modulen Inkommande interaktion.</p>
<p>Mer information finns i den <a href="../interaction/interaction-architecture.md">detaljerade dokumentationen</a>.</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Kampanjoptimering</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Modulen Kampanjoptimering är nu tillgänglig. Med den här modulen kan du styra, filtrera och övervaka leveransen. För att undvika konflikter mellan kampanjer kan Adobe Campaign testa olika kombinationer genom att tillämpa särskilda begränsningsregler. Detta garanterar att de skickade meddelandena uppfyller kundernas behov och förväntningar och företagets kommunikationspolicy.</p>
<p>Mer information finns i den <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=sv-SE#campaign-optimization">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Unistadstjänst</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Unicity Service är en ny komponent i Cloud Database Manager. Det hjälper användarna att bevara och övervaka integriteten för unika nyckelbegränsningar i molndatabastabeller. På så sätt kan du minska risken att infoga dubblettnycklar.
<p>Eftersom molndatabasen inte tillämpar begränsningar för användargrupper, introduceras i Unicity Service på programnivå, <b>en uppsättning nya skyddsfunktioner</b> minskar risken för att infoga dubbletter när data hanteras med Adobe Campaign.</p> 
<p>Unicity Service initierar ett nytt inbyggt arbetsflöde med namnet <b>ffdaUnicity</b> som övervakar begränsningar för unicitet och varningar när dubbletter identifieras.</p>
<p>Mer information finns i den <a href="../architecture/keys.md">detaljerade dokumentationen</a>.</p>
</td> </tr> 
</tbody> 
</table>


**Förbättringar**

* Snowflake Connector har förbättrats i fråga om prestanda.
* För övervaknings- och testningsändamål innehåller granskningsloggarna för arbetsflödet **[!UICONTROL Replicate Staging data]** nu antalet poster som har skickats till databasen FFDA (Full Federated Data Access).
* Med SQL-kodaktiviteten kan du nu välja i vilken databas SQL-skriptet ska lagras: standarddatakällan eller ett valt aktivt FDA-externt konto.
* En uppsättning fördefinierade lagerställen finns nu tillgängliga och kan användas för att köra olika frågor parallellt, som segmentering, ETL eller toppar. [Läs mer](../config/workflows.md)

**Andra ändringar**

* Fältet **[!UICONTROL Encrypted identifier]** har lagts till i besökarschemat (`nms:visitor`). Det här fältet beräknas och ska användas för webbprogram.
* Korrigerade ett problem som gjorde att leveransanalysen misslyckades när vissa IP-tillhörigheter fanns i vissa mellanleverantörsbehållare men inte i alla. Nu lagras alla IP-tillhörigheter i databasen så att alla behållare kan komma åt tillhörigheterna som finns i alla andra behållare. (NEO-37564)
* Nu kan du importera ett paket med flera scheman och navigeringsträdsnoder.

**Korrigeringar**

* När en användare har tagit bort attributet `<autoStg>` från ett tabelldefinitionselement eller ändrat dess värde från `true` till `false` i ett datarema, togs den relaterade mellanlagringstabellen inte bort. Problemet har åtgärdats.
* Korrigerade ett problem som orsakade ett fel när poster med ett dedikerat formulär skapades på grund av Id-hantering med en FFDA-datakälla.
* Korrigerade ett problem som kunde förhindra att erbjudanden infogades i en leverans om de hanterades av en anrikningsaktivitet i ett arbetsflöde.
* Korrigerade ett problem som kunde göra importen av paket långsammare.
* Ett problem som kunde förhindra e-postleveranser med dirigerade adresser har korrigerats.
* Korrigerade ett problem som kunde förhindra att offerter sparades i tabellen för offertförslag.
* Korrigerade ett problem som orsakade att problem med nätverkstimeout inte loggades korrekt som problem med skriptavbrott i stället för nätverksfel. Detta problem uppstod vid HTTP-begäranden som inkluderades i JavaScript-aktiviteter.
* Korrigerade ett problem som förhindrade att erbjudanden replikerades till Snowflake-miljön.
* Korrigerade ett problem som ignorerade attributet autoStg för icke-utökade inbyggda scheman.
* Ett problem som gjorde att användare inte kunde välja länken **[!UICONTROL Country/Region]** när de förhandsvisade en profil har korrigerats.
* Korrigerade ett problem som gjorde att datumväljaren i anpassade rapporter resulterade i ett skriptfel. (NEO-36345)
* Ett problem som gjorde att systemet kraschade när konfigurationen skulle återskapas om konfigurationsfilerna var felaktiga har åtgärdats.
* Korrigerade ett problem som hindrade marknadsförings- och kontrollinstanserna från att uppgraderas.
* Korrigerade ett problem som kunde få faktureringsarbetsflödet att krascha på marknadsinstanser.
* Korrigerade ett problem som kunde leda till dubblettnycklar i färdiga tabeller i FFDA Snowflake. (NEO-38583)
* Korrigerade ett problem som kunde leda till att tillfälliga scheman för arbetsflöden förlorades när två dedupliceringsaktiviteter redigerades den ena efter den andra. (NEO-34063)
* Korrigerade ett problem som returnerade felaktiga resultat när funktionerna Amazon Redshift HoursDiff och MinutesDiff kördes när tidskomponenten skulle extraheras.(NEO-31673)
* Ett problem som kunde förhindra användare från att logga in på konsolen på grund av ett proxykonfigurationsproblem har åtgärdats. (NEO-38388)
* Korrigerade ett regressionsproblem som förhindrade funktionen **Rensa mappen** från att fungera som den ska. (NEO-37459)
* Korrigerade ett problem som kunde förhindra dig från att förhandsgranska mobila leveranser som var kopplade till ett arbetsflöde.
* Korrigerade ett problem som kunde förhindra arbetsflödesaktiviteten **Läslista** från att fungera när listan identifierades i databasen med ett negativt ID. (NEO-39607)

## Version 8.1.20 {#release-8-1-20}

_7 september 2021_

**Säkerhetsförbättringar**

* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot katalogbläddringsattacker. (NEO-28547)

**Förbättringar**

* Efter att livscykeln har upphört har Flash tagits bort från alla relaterade Campaign-funktioner och -komponenter och ersatts med HTML5. Diagramtypen **Mätare** har tagits bort. (NEO-30330) [Läs mer](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/creating-new-reports/creating-a-chart.html?lang=sv-SE)
* När du installerar klientkonsolen i Windows kontrollerar installationsprogrammet nu om det finns en överordnad registernod och skapar en om den saknas. Detta förhindrar potentiella problem när konsolen startas. (NEO-34854)
* Funktionen för att spåra signaturer har förbättrats för att förhindra fel som har att göra med hur tredje parts verktyg (e-postklienter, webbläsare osv.) hanterar specialtecken. URL-parametrar är nu kodade.

**Andra ändringar**

* Tidigare borttagna Microsoft CRM-anslutningar (Office 365 och lokala distributioner) har tagits bort från gränssnittet. [Läs mer](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/connectors/crm-ms-dynamics.html?lang=sv-SE#configure-acc-for-microsoft)

* Efter migreringen till Tomcat 8 har IIS-installationsskriptet uppdaterats för att åtgärda IIS-integreringsproblem. (NEO-31019)
* Ett riktlinje har lagts till för att endast tillåta att det [tekniska arbetsflödet för fakturering](https://experienceleague.adobe.com/docs/campaign-classic/using/monitoring-campaign-classic/production-procedures/monitoring-processes.html?lang=sv-SE#billing-report) körs på marknadsföringsinstansen.
* Identifieringen av datakällan har förbättrats på flikarna data och schema i fönstret för arbetsflödesövergångarna **Visa population**.
* Databasindex som saknas har lagts till i följande scheman för att förhindra problem med databasuppdatering: xtk:rights, nms:dlvExclusion, nms:seedMember och nms:trackingUrl

**Felkorrigeringar**

* Ett problem som gjorde att rapporten **Hot Click** inte fungerade när erbjudanden länkades till leveransen har åtgärdats. (NEO-26295)
* Korrigerade ett problem med aktiviteten **Delarbetsflöde** när körningen inte genererade en utdatatabell. (NEO-36242)
* Korrigerade olika problem vid export av rapporten **Beskrivande analys** som en PDF-fil. (NEO-25847)
* Korrigerade ett problem som kan leda till att leveranser misslyckas när en extern e-postleverans används. (NEO-37435)
* Korrigerade ett fel vid anslutning till Microsoft CRM med webb-API. Felmeddelandet har tagits bort eftersom funktioner inte påverkades.
* Korrigerade ett problem med borttagning av dubbletter i spårningsloggar när mittservern angavs som relä mellan spårnings- och marknadsföringsservrar. (NEO-36285)
* Korrigerade en regression som förhindrade att Vault användes som ett specifikt kodarkiv.
* Korrigerade ett problem som förhindrade dig från att använda variabler i arbetsflödesaktiviteten **Berikning** när den inkommande övergången kom från en FDA-datakälla.
* Korrigerade ett problem med FFDA som förhindrar korrekt replikering av operatörsgrupper och behörigheter.
* Korrigerade ett problem som kunde leda till att en felaktig avprenumerationslänk skickades via leveransen.
* Ett problem med replikeringshantering som påverkar efteruppgraderingens varaktighet har korrigerats.
* Ett problem som kunde förhindra att **snabbklickningen** visades har korrigerats.
* Korrigerade ett problem som kunde leda till brutna URL:er i e-postmeddelanden.

## Version 8.1.14 {#release-8-1-14}

_23 juli 2021_

**Nyheter**

<table>
<thead>
<tr>
<th><strong>Ny arbetsflödesaktivitet: ändra datakälla</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Med den nya arbetsflödesaktiviteten <b>Ändra datakälla</b> kan du ändra datakällan för arbetsflödets arbetstabell. Detta ger större flexibilitet vid datahantering över olika datakällor (FDA, FFDA och lokal databas).</p>
<p>I Adobe Campaign-arbetsflöden hanteras data med hjälp av arbets- (eller tillfälliga) tabeller. När arbetsflödet körs delar arbetstabeller data mellan arbetsflödesaktiviteter. Som standard skapas arbetstabeller i samma databas som källan för de data som vi ställer frågor på.</p>
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
<td> <p><a href="../send/line.md">LINE-kanalen</a> är nu tillgänglig med Campaign v8, inklusive följande förbättringar i kombination med modulen <a href="../send/transactional.md">transaktionsmeddelanden</a>:
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

* Korrigerade ett problem som kunde förhindra att rapporten **Hot Click** visas för specifika leveranser.
* Ett problem med arbetsflödesaktiviteten **Deduplicering** har korrigerats, vilket kan leda till en felaktig dubblettinventering.
* Ett problem har korrigerats när en arbetsflödesfråga med filtret &quot;ID är inte tomt&quot; användes, vilket kan leda till att ett tomt objekt visas i övergångspopulationen.
* Korrigerade ett problem som förhindrade att ytterligare fält skapades i en ny målmappning.
