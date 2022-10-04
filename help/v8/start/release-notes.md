---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-utgåvan
feature: Overview
role: Admin, Developer, User
level: Beginner, Intermediate, Experienced
hidefromtoc: false
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: eb134a16e5289d6410ef9b0eae33a31839365f82
workflow-type: tm+mt
source-wordcount: '2818'
ht-degree: 29%

---

# Senaste versionen{#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign v8**.

## Version 8.4.1 {#release-8-4-1}

_30 september 2022_

**Nyheter**

<table> 
<thead>
<tr> 
<th> <strong>Adobe Campaign-integrering med Adobe Experience Platform</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td><p>Nu finns nya mål- och källanslutningar som möjliggör smidig integrering mellan Adobe Campaign och Adobe Experience Platform:</p>
<ul><li>Använd Adobe Campaign Managed Cloud Services målanslutning för att skicka Experience Platform segment till Adobe Campaign för aktivering,</li>
<li>Använd Adobe Campaign Managed Cloud Service Source Connector för att skicka Adobe Campaign leverans- och spårningsloggar till Adobe Experience Platform.</li>
</ul>
<p>Mer information finns i den <a href="../connect/ac-aep.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Twitter kanaltillgänglighet</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>The <a href="../send/twitter.md">Twitter sociala kanal</a> är nu tillgängligt med Campaign v8. Du kan:</p>
<ul> 
<li><p>Skicka meddelanden på Twitter: Med Adobe Campaign kan du skicka meddelanden direkt till ditt twitter-konto. Du kan också skicka direktmeddelanden till alla dina följare.
</p></li>
<li><p>Samla in nya kontakter: Adobe Campaign kan automatiskt återställa profildata, vilket gör att ni kan genomföra riktade kampanjer och implementera flerkanalsstrategier.
</p></li>
</ul>
<p>Lär dig hur du ansluter Campaign och Twitter i <a href="../connect/ac-tw.md">detaljerad dokumentation</a>.</p>
<p>Lär dig hur du postar tweets och skickar direktmeddelanden med Campaign i <a href="../connect/ac-tw.md">den här sidan</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Säkerhetsförbättring**

För att optimera säkerheten har säkerhetstoken tagits bort från URL:er som genererats av Campaign:

* Den här ändringen gäller endast GET-URL:er. Andra typer, inklusive POSTS-URL:er, påverkas inte.
* Om du använder anpassad kod hämtas inte säkerhetstoken längre från GET URL-säkerhetstokenparametern. Du måste generera en ny säkerhetstoken med följande JSSP-kod:

   ```getNewSecurityToken(jsspContext.getSessionToken(), jsspContext.getSecurityToken(), true);```

   Du kan också använda inloggnings-API:t för att hämta säkerhetstoken.
* Det finns ingen förändring i hanteringen av sessionstoken.

**Förbättringar**

* Efter Microsoft Internet Explorer 11 är återgivningsmotorn för HTML i konsolen nu igång **Microsoft Edge Chromium**. Dessutom installeras **Microsoft Edge WebView 2** Körning krävs nu för alla installationer av klientkonsolen.
* Förbättrad arbetsflödeskörning med hög tillgänglighet för arbetsflöde, som gör att du kan köra samtidiga arbetsflöden i olika behållare för att förhindra att tjänsten för arbetsflöde går förlorad och undvika relaterade körningsfel. **Anteckning**: Den nya funktionen lanseras endast i begränsad tillgänglighet för en uppsättning kunder.
* Sekretessförfrågningar utförs nu i batch för ett givet sekretessnamnområde. Den här förbättringen ökar körningstiden för begäranden om GDPR/sekretess-borttagning.

**Kompatibilitetsuppdateringar**

* Campaign v8 SDK har nu stöd för iOS 16 för push-meddelanden.

Se [kompatibilitetsmatrisen för Campaign](compatibility-matrix.md).

**Korrigeringar**

* Ett problem som påverkade statusuppdateringarna för leveransloggen på MID-instansen när alternativet FeatureFlag_GZIP_Compression aktiverades har åtgärdats. (NEO-49183)
* Korrigerat ett problem som kan leda till att leveranser stannar kvar i **Väntande** status även om kontaktdatum har nåtts. (NEO-48079)
* Ett problem i arbetsflöden som kunde förhindra att filer uppdaterades på servern när **Inläsning av data (fil)** aktivitet. Processen stoppades till 100 % men tog aldrig slut. (NEO-47269)
* Korrigerade ett problem under efteruppgraderingen i japanska miljöer. (NEO-46640)
* Korrigerade ett problem som kunde inträffa om en leverans nådde en exakt storlek under MTA-processen. (NEO-46097)
* Ett problem som gjorde att spårningsloggar inte kunde returnera data som var relaterade till mottagarens webbläsare har korrigerats. (NEO-46612)
* Korrigerade ett problem som ledde till personaliseringsproblem när SMS-meddelanden skickades med ett externt leveransläge. (NEO-46415)
* Ett problem som kunde generera dubbletter i spårningsloggar har korrigerats. (NEO-46409)
* Ett problem som förhindrade **[!UICONTROL Replicate Staging data]** (ffdaReplicateStagingData) tekniska arbetsflöden kan inte stoppas även om ett fel inträffar under körningen. (NEO-46280)
* För att undvika långsamhet när du skickar korrektur till dirigerade adresser grupperas nu alla efterföljande replikeringar av dirigerade medlemmar i en replikeringsbegäran. (NEO-44844)
* Korrigerade ett problem som visade ett fel när en leverans skulle förhandsgranskas i en arkiverad händelse i Message Center. (NEO-43620)
* Ett problem har korrigerats vid inmatning av data i molndatabasen i Snowflake med en kampanj **Fråga** aktivitet och **Ändra datakälla** aktivitet: processen misslyckades när det finns ett omvänt snedstreck i data. Källsträngen kunde inte escape-konverteras och data bearbetades inte korrekt på Snowflake. (NEO-45549)
* Ett problem som uppstod när **Fråga** och filtrera en tabell. När ett kolumnnamn innehöll ordet &quot;Uppdatera&quot; uppstod ett kompileringsfel med en ogiltig identifierare och följande meddelande: &quot;antal uppdaterade rader&quot;. (NEO-46485)

## Version 8.3.8 {#release-8-3-8}

_18 maj 2022_

**Nyheter**

<table> 
<thead>
<tr> 
<th> <strong>Tidskänsliga meddelanden</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>I iOS 15 har Apple lagt till en funktion för känsliga meddelanden som ger programutvecklaren kontroll över att kringgå fokusläget när ett meddelande anses vara känsligt och sedan måste nå användaren i realtid.</p>
<p>Mer information finns i den <a href="../send/push.md#send-notifications-on-ios">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Integrering av Privacy Service</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Campaign v8 kan nu integreras med Adobe Privacy Core Service. Förfrågningar om användarens information som skickas från Privacy Core Service till alla lösningar i Experience Cloud hanteras automatiskt av Campaign via ett dedikerat arbetsflöde.</p>
<p>Mer information finns i den <a href="privacy.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table>
<thead>
<tr>
<th><strong>Responshanteraren</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Med Hantering av kampanjsvar kan ni mäta framgångarna och avkastningen på era marknadsföringskampanjer eller erbjuda erbjudanden i alla kanaler: e-post, mobil, direktreklam osv.</p>
<p>Mer information finns i den <a href="../start/campaigns.md#response-manager-add-on">detaljerade dokumentationen</a>.</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Distribuerad marknadsföring</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Med Campaign Distributed Marketing kan ni implementera samarbetskampanjer mellan centrala enheter (huvudkontor, marknadsföringsavdelningar osv.) och lokala enheter (säljställen, regionala organ osv.). Genom en delad arbetsyta (kampanjpaket) kan du skapa kampanjmallar och föreslå dem för lokala enheter.</p>
<p>Mer information finns i den <a href="../start/campaigns.md#distributed-marketing-add-on">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Kompatibilitetsuppdateringar**

* Campaign v8 SDK har nu stöd för Android 12 och iOS 15 för push-meddelanden.
* Campaign v8 är nu kompatibelt med Windows 11.

Se [kompatibilitetsmatrisen för Campaign](compatibility-matrix.md).

**Förbättringar**

* Microsoft Exchange Online OAuth 2.0-autentisering för POP3 stöds nu i Campaign. [Läs mer](../config/external-accounts.md#bounce-mails-external-account)
* Kritiska korrigeringar har tillämpats för webb-API:et Microsoft Dynamics Connector.
* Den nya rättigheten Operator och group schema write (operatorWrite) har lagts till så att användare kan infoga, uppdatera och ta bort operatorer (xtk:operator) och Operator-grupper (xtk:group).

<!--* You can now enable the Email BCC (blind carbon copy) capability to store emails sent by Campaign at the delivery level, through the dedicated option in the delivery properties. [Read more](../config/email-settings.md#email-bcc)-->
<!--* To ensure better performances, a new "Split" option is now activated by default in the Routing external account. This option allows messages to be automatically split across your mid-sourcing instances in order to be delivered faster to the recipients.-->
* Flera LINE-aktiva konton kan nu konfigureras på en enda mellanleverantör.
* Antalet standardanslutningar för webbprocessen har ökat från 50 till 150.
* Campaign innehåller en uppsättning nya skyddsritningar för att förhindra att dubblettnycklar infogas i Snowflake-databasen. [Läs mer](../architecture/keys.md)

**Korrigeringar**

* Korrigerade ett problem som uppstod när frön och kontrollgrupper användes i samma återkommande leverans. (NEO-41197)
* Korrigerade ett fel i FFDA som ledde till att e-postsändning blockerades för alla mottagare som tillhör samma deliveryPart under sändningsprocessen (upp till 256) när personaliseringsblocken innehöll ett av följande tecken: `' & < > "`. Dessa tecken stöds nu i anpassningsblock (exempel: first name=&quot;Brian O&#39;Neil&quot;). (NEO-43184)
* Korrigerade ett problem som kunde leda till att spårningsarbetsflödet misslyckades när ett anpassat schema användes som målmappning. Vi ser nu till att typen för den externa länken till ett anpassat målschema är korrekt när du genererar ett wideLog-schema via målmappningsguiden. (NEO-43506)
* Korrigerade ett problem som kunde leda till att arbetsflödena för FFDA-distribution misslyckades för andra språk än engelska. (NEO-44561)

## Version 8.2.10 {#release-8-2-10}

_2 februari 2022_

**Korrigeringar**

* Korrigerade ett problem som gjorde att leveransförberedelsen misslyckades om det maximala antalet meddelanden som definierats i typologiregeln uppnåddes.
* Ett problem som uppstod när Adobe Analytics-anslutningen konfigurerades när e-postadressen innehöll ett s-tecken har åtgärdats.
* Ett fel som kan göra att tabellen deliveryMapping förlorar data från en anpassad leveransmappning har korrigerats under efteruppgraderingen.
* Korrigerade ett problem som kunde leda till att mottagare fick samma meddelande flera gånger för samma leverans när e-postadressen innehöll ett enkelt citattecken (&#39;). Den här figuren har rymts. (NEO-41198)
* Ett problem med ID-generering när korrektur med frön eller ersättningsadresser skickades har åtgärdats. (NEO-42637)
* Korrigerade ett problem som kunde förhindra dig från att skicka korrektur med adressmetoden. (NEO-40417)
* Ett problem som hindrade dig från att installera LINE-paketet har korrigerats. (NEO-42503)

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
<p>Interaktionshantering i realtid är nu tillgänglig för inkommande kanaler. Använd modulen för inkommande kampanjinteraktion för att presentera det bästa erbjudandet för era kunder när de besöker er webbplats eller kontaktar ert callcenter. Den här funktionen har Campaign v8 som ett alternativ och kräver specifik konfiguration för din instans. Kontakta Adobe och få tillgång till modulen Inkommande interaktion.</p>
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
<p>Mer information finns i den <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=en#campaign-optimization">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Universitetstjänst</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Unicity Service är en ny komponent i Cloud Database Manager. Det hjälper användarna att bevara och övervaka integriteten för unika nyckelbegränsningar i molndatabastabeller. På så sätt kan du minska risken att infoga dubblettnycklar.
<p>Eftersom molndatabasen inte tillämpar begränsningar för användargrupper, introducerar Unicity Service på programnivå, <b>en uppsättning nya skyddsräcken</b> minska risken att infoga dubbletter när data hanteras med Adobe Campaign.</p> 
<p>Unicity Service initierar ett nytt inbyggt arbetsflöde som kallas <b>ffdaUnicity</b> för att övervaka begränsningar för unicitet och varningar när dubbletter upptäcks.</p>
<p>Mer information finns i den <a href="../architecture/keys.md">detaljerade dokumentationen</a>.</p>
</td> </tr> 
</tbody> 
</table>


**Förbättringar**

* Snowflake-kontakten har förbättrats i fråga om prestanda.
* För övervaknings- och testningsändamål ska granskningsloggarna för **[!UICONTROL Replicate Staging data]** arbetsflödet innehåller nu antalet poster som har skickats till FDA-databasen (Full Federated Data Access).
* Med SQL-kodsaktiviteten kan du nu välja i vilken databas SQL-skriptet ska lagras: standarddatakällan eller ett valt externt FDA-konto.
* En uppsättning fördefinierade lagerställen finns nu tillgängliga och kan användas för att köra olika frågor parallellt, som segmentering, ETL eller toppar. [Läs mer](../config/workflows.md)

**Andra ändringar**

* The **[!UICONTROL Encrypted identifier]** fältet har lagts till i besökarschemat (`nms:visitor`). Det här fältet beräknas och ska användas för webbprogram.
* Korrigerade ett problem som gjorde att leveransanalysen misslyckades när vissa IP-tillhörigheter fanns i vissa mellanleverantörsbehållare men inte i alla. Nu lagras alla IP-tillhörigheter i databasen så att alla behållare kan komma åt tillhörigheterna som finns i alla andra behållare. (NEO-37564)
* Nu kan du importera ett paket med flera scheman och navigeringsträdsnoder.

**Korrigeringar**

* När en användare har tagits bort, i ett dataschema, `<autoStg>` attribut från ett tabelldefinitionselement eller ändrat dess värde från `true` till `false`, har den relaterade mellanlagringstabellen inte tagits bort. Problemet har åtgärdats.
* Korrigerade ett problem som orsakade ett fel när poster med ett dedikerat formulär skapades på grund av Id-hantering med en FFDA-datakälla.
* Korrigerade ett problem som kunde förhindra att erbjudanden infogades i en leverans om de hanterades av en anrikningsaktivitet i ett arbetsflöde.
* Korrigerade ett problem som kunde göra importen av paket långsammare.
* Ett problem som kunde förhindra e-postleveranser med dirigerade adresser har korrigerats.
* Korrigerade ett problem som kunde förhindra att offerter sparades i offerttabellen.
* Korrigerade ett problem som orsakade att problem med nätverkstimeout inte loggades korrekt som problem med skriptavbrott i stället för nätverksfel. Detta problem uppstod vid HTTP-begäranden som inkluderades i JavaScript-aktiviteter.
* Korrigerade ett problem som förhindrade att erbjudanden replikerades till realtidsmiljön på Snowflake.
* Korrigerade ett problem som ignorerade attributet autoStg för icke-utökade inbyggda scheman.
* Ett problem som hindrade användare från att välja **[!UICONTROL Country/Region]** när du förhandsgranskar en profil.
* Korrigerade ett problem som gjorde att datumväljaren i anpassade rapporter resulterade i ett skriptfel. (NEO-36345)
* Ett problem som gjorde att systemet kraschade när konfigurationen skulle återskapas om konfigurationsfilerna var felaktiga har åtgärdats.
* Korrigerade ett problem som hindrade marknadsförings- och kontrollinstanserna från att uppgraderas.
* Korrigerade ett problem som kunde få faktureringsarbetsflödet att krascha på marknadsinstanser.
* Korrigerade ett problem som kunde leda till dubblettnycklar i tabeller som inte är installerade i FFDA Snowflake. (NEO-38583)
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

* Efter att livscykeln har upphört har Flash tagits bort från alla relaterade Campaign-funktioner och -komponenter och ersatts med HTML5. Diagramtypen **Mätare** har tagits bort. (NEO-30330) [Läs mer](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/creating-new-reports/creating-a-chart.html)
* När du installerar klientkonsolen i Windows kontrollerar installationsprogrammet nu om det finns en överordnad registernod och skapar en om den saknas. Detta förhindrar potentiella problem när konsolen startas. (NEO-34854)
* Funktionen för att spåra signaturer har förbättrats för att förhindra att fel länkas till hur tredjepartsverktyg (e-postklienter, webbläsare osv.) hanterar specialtecken. URL-parametrar är nu kodade.

**Andra ändringar**

* Tidigare borttagna Microsoft CRM-anslutningar (Office 365 och lokala distributioner) har tagits bort från gränssnittet. [Läs mer](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/connectors/crm-connectors/crm-ms-dynamics.html#configure-acc-for-microsoft)
* Efter migreringen till Tomcat 8 har IIS-installationsskriptet uppdaterats för att åtgärda IIS-integreringsproblem. (NEO-31019)
* Ett riktlinje har lagts till för att endast tillåta att det [tekniska arbetsflödet för fakturering](https://experienceleague.adobe.com/docs/campaign-classic/using/monitoring-campaign-classic/production-procedures/monitoring-processes.html#billing-report) körs på marknadsföringsinstansen.
* Identifieringen av datakällan har förbättrats på flikarna data och schema i fönstret för arbetsflödesövergångarna **Visa population**.
* Databasindex som saknas har lagts till i följande scheman för att förhindra problem med databasuppdatering: xtk:rights, nms:dlvExclusion, nms:seedMember och nms:trackingUrl

**Felkorrigeringar**

* Ett problem som förhindrade **Snabbklickningar** från att arbeta när erbjudandena var kopplade till leveransen. (NEO-26295)
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
* Ett problem som kunde förhindra **Snabbklickning** från att visas.
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
<td> <p>The <a href="../send/line.md">LINE-kanal</a> är nu tillgängligt med Campaign v8, inklusive följande förbättringar i kombination med <a href="../send/transactional.md">transaktionsmeddelanden</a> modul:
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

* Ett problem som kunde förhindra **Snabbklickningar** rapportera från visning för specifika leveranser.
* Ett problem med **Deduplicering** arbetsflödesaktivitet som kan leda till felaktig dubblettinventering.
* Ett problem har korrigerats när en arbetsflödesfråga med filtret &quot;ID är inte tomt&quot; användes, vilket kan leda till att ett tomt objekt visas i övergångspopulationen.
* Korrigerade ett problem som förhindrade att ytterligare fält skapades i en ny målmappning.
