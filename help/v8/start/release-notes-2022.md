---
title: Versionsinformation om Campaign v8 2022
description: Lista över funktioner och förbättringar i 2022 års Campaign v8-utgåvor
feature: Release Notes
exl-id: 76473fa5-48ba-42cf-8664-0dd197833a86
source-git-commit: 4fecae16b2db0f174de6d77acf5b846906073aeb
workflow-type: tm+mt
source-wordcount: '1919'
ht-degree: 12%

---

# Versionsinformation 2022{#2022-rn}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **2022 Campaign v8-utgåvorna**.

## Version 8.4.2 {#release-8-4-2}

_28 oktober 2022_

**Korrigeringar**

* Korrigerade ett problem som förhindrade att leveransindikatorn för lyckade åtgärder uppdaterades korrekt när Adobe Campaign Enhanced MTA användes. (NEO-50462)

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
<th> <strong>X-kanaltillgänglighet (tidigare Twitter)</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Den sociala <a href="../send/twitter.md">X-kanalen</a> är nu tillgänglig med Campaign v8. Du kan:</p>
<ul> 
<li><p>Skicka meddelanden på X (tidigare Twitter): Med Adobe Campaign kan du skicka meddelanden direkt till ditt X-konto. Du kan också skicka direktmeddelanden till alla dina följare.
</p></li>
<li><p>Samla in nya kontakter: Adobe Campaign kan automatiskt återställa profildata, vilket gör att ni kan genomföra riktade kampanjer och implementera strategier för flera kanaler.
</p></li>
</ul>
<p>Lär dig hur du ansluter Campaign och X i den <a href="../connect/ac-tw.md">detaljerade dokumentationen</a>.</p>
<p>Lär dig hur du skapar inlägg och skickar direktmeddelanden med Campaign på <a href="../connect/ac-tw.md">den här sidan</a>.</p>
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

* Efter livscykelns slut för Microsoft Internet Explorer 11 använder nu renderingsmotorn HTML i konsolen **Microsoft Edge Chromium**. Dessutom krävs nu installation av **Microsoft Edge WebView 2** för alla installationer av klientkonsolen.
* Förbättrad arbetsflödeskörning med hög tillgänglighet för arbetsflöde, som gör att du kan köra samtidiga arbetsflöden i olika behållare för att förhindra att tjänsten för arbetsflöde går förlorad och undvika relaterade körningsfel. **Obs!** Den här nya funktionen är endast tillgänglig för en uppsättning kunder.
* Sekretessförfrågningar utförs nu i batch för ett givet sekretessnamnområde. Den här förbättringen ökar körningstiden för begäranden om GDPR/sekretess-borttagning.

**Kompatibilitetsuppdateringar**

* Campaign v8 SDK har nu stöd för iOS 16 för push-meddelanden.

Se [kompatibilitetsmatrisen för Campaign](compatibility-matrix.md).

**Korrigeringar**

* Ett problem som påverkade statusuppdateringarna för leveransloggen på MID-instansen när alternativet FeatureFlag_GZIP_Compression aktiverades har åtgärdats. (NEO-49183)
* Korrigerade ett problem som kunde leda till att leveranserna stannar i statusen **Väntande** även om kontaktdatumet nåddes. (NEO-48079)
* Ett problem i arbetsflöden som kunde förhindra filer från att uppdateras på servern när aktiviteten **Datainläsning (fil)** användes har åtgärdats. Processen stoppades till 100 % men tog aldrig slut. (NEO-47269)
* Korrigerade ett problem under efteruppgraderingen i japanska miljöer. (NEO-46640)
* Korrigerade ett problem som kunde inträffa om en leverans nådde en exakt storlek under MTA-processen. (NEO-46097)
* Ett problem som gjorde att spårningsloggar inte kunde returnera data som var relaterade till mottagarens webbläsare har korrigerats. (NEO-46612)
* Korrigerade ett problem som ledde till personaliseringsproblem när SMS-meddelanden skickades med ett externt leveransläge. (NEO-46415)
* Ett problem som kunde generera dubbletter i spårningsloggar har korrigerats. (NEO-46409)
* Korrigerade ett problem som förhindrade det tekniska arbetsflödet **[!UICONTROL Replicate Staging data]** (ffdaReplicateStagingData) från att stoppas även om ett fel uppstod under körningen. (NEO-46280)
* För att undvika långsamhet när du skickar korrektur till dirigerade adresser grupperas nu alla efterföljande replikeringar av dirigerade medlemmar i en replikeringsbegäran. (NEO-44844)
* Korrigerade ett problem som visade ett fel när en leverans skulle förhandsgranskas i en arkiverad händelse i Message Center. (NEO-43620)
* Ett problem har korrigerats vid inmatning av data i molndatabasen i Snowflake med en Campaign **Query**-aktivitet och en **Change Data Source**-aktivitet: processen misslyckades när det finns ett omvänt snedstreck i data. Källsträngen kunde inte escape-konverteras och data bearbetades inte korrekt på Snowflake. (NEO-45549)
* Ett problem har korrigerats när aktiviteten **Fråga** användes och en tabell filtrerades. När ett kolumnnamn innehöll ordet &quot;Uppdatera&quot; uppstod ett kompileringsfel med en ogiltig identifierare och följande meddelande: &quot;number of rows updated&quot;. (NEO-46485)
* Det tekniska arbetsflödet för **databasrensning** hanterar nu även anpassade mellanlagringsscheman. (NEO-48974)
* Korrigerade ett problem som kunde göra leveransanalysen långsammare, med undantag för steget med blocklist mottagare, när stora volymer mottagare användes. (NEO-48019)
* Förbättrad stabilitet vid hantering av ogiltiga XML-strängar under SOAP. (NEO-48027)
* Korrigerade ett problem som ledde till att onödiga DeliveryParts skapades när leveransen använde kalender- och delningslägen. (NEO-48634)
* Ett prestandaproblem har korrigerats vid användning av kalenderbaserade påfyllnader. (NEO-48451)
* Korrigerade ett problem som kunde leda till ett felmeddelande på skärmen för leveranslistan efter att en ny målmappning skapades för ett anpassat schema. (NEO-49237)
* Korrigerade ett problem som kunde orsaka dataförlust om mellanlagringsarbetsflödet var felaktigt och kvarhållningsperioden gick ut. (NEO-48975)

## Version 8.3.9 {#release-8-3-9}

>[!CAUTION]
>
> klientkonsoluppgraderingen är obligatorisk. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../start/connect.md#download-ac-console).

_7 oktober 2022_

**Korrigeringar**

* Ett problem som påverkade statusuppdateringarna för leveransloggen på MID-instansen när alternativet FeatureFlag_GZIP_Compression aktiverades har åtgärdats. (NEO-49183)
* Det tekniska arbetsflödet för **databasrensning** hanterar nu även anpassade mellanlagringsscheman. (NEO-48974)
* Korrigerade ett problem som kunde leda till att leveranserna stannar i statusen **Väntande** även om kontaktdatumet nåddes. (NEO-48079, NEO-48251)
* Förbättrad stabilitet vid hantering av ogiltiga XML-strängar under SOAP. (NEO-48027)
* Korrigerade ett problem som kunde göra leveransanalysen långsammare, med undantag för steget med blocklist mottagare, när stora volymer mottagare användes. (NEO-48019)
* För att undvika långsamhet när du skickar ett korrektur till dirigerade adresser grupperas nu alla efterföljande replikeringar av dirigerade medlemmar i en replikeringsbegäran. (NEO-44844)
* Korrigerade ett problem som ledde till personaliseringsproblem när SMS-meddelanden skickades med ett externt leveransläge. (NEO-46415)
* Korrigerade ett problem som visade ett fel när en leverans skulle förhandsgranskas i en arkiverad händelse i Message Center. (NEO-43620)
* Ett problem i arbetsflöden som kunde förhindra filer från att uppdateras på servern när aktiviteten **Datainläsning (fil)** användes har åtgärdats. Processen stoppades till 100 % men tog aldrig slut. (NEO-47269)
* Korrigerade ett problem som ledde till att onödiga DeliveryParts skapades när leveransen använde kalender- och delningslägen. (NEO-48634)
* Ett prestandaproblem har korrigerats vid användning av kalenderbaserade påfyllnader. (NEO-48451)
* Korrigerade ett problem som kunde leda till ett felmeddelande på skärmen för leveranslistan efter att en ny målmappning skapades för ett anpassat schema. (NEO-49237)
* Korrigerade ett problem som kunde inträffa om en leverans nådde en viss storlek under MTA-processen. (NEO-46097)
* Ett problem som gjorde att spårningsloggar inte kunde returnera data som var relaterade till mottagarens webbläsare har korrigerats. (NEO-46612)
* Korrigerade ett problem under efteruppgraderingen i japanska miljöer. (NEO-46640)
* Ett problem har korrigerats när aktiviteten **Fråga** användes och en tabell filtrerades. När ett kolumnnamn innehöll ordet &quot;Uppdatera&quot; uppstod ett kompileringsfel med en ogiltig identifierare och följande meddelande: &quot;number of rows updated&quot;. (NEO-46485)
* Korrigerade ett problem som förhindrade det tekniska arbetsflödet **[!UICONTROL Replicate Staging data]** (ffdaReplicateStagingData) från att stoppas även om ett fel uppstod under körningen. (NEO-46280)
* Korrigerade ett problem som kunde orsaka dataförlust om mellanlagringsarbetsflödet var felaktigt och kvarhållningsperioden gick ut. (NEO-48975)
* Ett problem har korrigerats vid inmatning av data i molndatabasen i Snowflake med en Campaign **Query**-aktivitet och en **Change Data Source**-aktivitet: processen misslyckades när det finns ett omvänt snedstreck i data. Källsträngen kunde inte escape-konverteras och data bearbetades inte korrekt på Snowflake. (NEO-45549)

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
<th> <strong>Integrering av kärnPrivacy Service</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Campaign v8 kan nu integreras med Adobe Privacy Core-tjänst. Förfrågningar om användarens information som skickas från Privacy Core Service till alla lösningar i Experience Cloud hanteras automatiskt av Campaign via ett dedikerat arbetsflöde.</p>
<p>Mer information finns i den <a href="privacy.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table>
<thead>
<tr>
<th><strong>Svarshanteraren</strong><br/></th>
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
* Kritiska korrigeringar har tillämpats för webb-API:t för Microsoft Dynamics Connector.
* Den nya rättigheten Operator och group schema write (operatorWrite) har lagts till så att användare kan infoga, uppdatera och ta bort operatorer (xtk:operator) och Operator-grupper (xtk:group).
  <!--* You can now enable the Email BCC (blind carbon copy) capability to store emails sent by Campaign at the delivery level, through the dedicated option in the delivery properties. [Read more](../config/email-settings.md#email-bcc)-->
  <!--* To ensure better performances, a new "Split" option is now activated by default in the Routing external account. This option allows messages to be automatically split across your mid-sourcing instances in order to be delivered faster to the recipients.-->
* Flera LINE-aktiva konton kan nu konfigureras på en enda mellanleverantör.
* Antalet standardanslutningar för webbprocessen har ökat från 50 till 150.
* Campaign innehåller en uppsättning nya skyddsritningar för att förhindra att dubblettnycklar infogas i Snowflake-databasen. [Läs mer](../architecture/keys.md)

**Korrigeringar**

* Korrigerade ett problem som uppstod när frön och kontrollgrupper användes i samma återkommande leverans. (NEO-41197)
* Korrigerade ett fel i FFDA som ledde till att e-postsändning blockerades för alla mottagare som tillhör samma deliveryPart under sändningsprocessen (upp till 256) när anpassningsblocken innehöll ett av följande tecken: `' & < > "`. Dessa tecken stöds nu i personaliseringsblock (exempel: firstname=&quot;Brian O&#39;Neil&quot;). (NEO-43184)
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
