---
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-utgåvan
feature: Overview
role: Admin, Developer, User
level: Beginner, Intermediate, Experienced
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471
source-git-commit: 441310dc1cdcb96296c0cbe5bf3fb7cd1502709f
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 18%

---

# Senaste versionen{#latest-release}

Adobe Campaign uppdateras regelbundet. Denna regelbundna uppdateringsfrekvens syftar till att ge dig den senaste och bästa produkten, hålla din miljö säker och förbättra din upplevelse med produkten. Adobe rekommenderar varmt alla kunder att uppgradera till den senaste versionen.

Som användare av hanterade Cloud Services uppgraderas din instans av Adobe i varje ny version. Adobe kommer att kontakta dig och uppgradera dina miljöer. Campaign Client Console **måste uppgraderas till samma version** som kampanjservrar. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../start/connect.md#upgrade-ac-console).

Som kund kan du dessutom kontrollera att du använder de senaste versionerna av de system som stöds i [Kompatibilitetsmatris](compatibility-matrix.md).

## Version 8.5 {#release-8-5}

_30 juni 2023_

**Nyheter**

<table> 
<thead>
<tr> 
<th> <strong>Förbättrad push-meddelandetjänst</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td><p>Campaign v8.5 introducerar vår senaste tjänst för push-meddelanden, som bygger på ett robust ramverk som bygger på modern spetsteknik. Den här tjänsten är utformad för att låsa upp nya nivåer av skalbarhet, så att dina meddelanden kan nå en större publik med smidig effektivitet. Med vår förbättrade infrastruktur och våra optimerade processer kan ni förvänta er större skalbarhet och tillförlitlighet, så att ni kan engagera och kommunicera med era mobilappsanvändare som aldrig förr. Den här funktionen är bara tillgänglig för en viss kundgrupp (begränsad tillgänglighet).</p>
<p>Mer information finns i den <a href="../send/push-data-collection.md">detaljerade dokumentationen</a>.</p>

</td> 
</tr> 
</tbody> 
</table>

**Kompatibilitetsuppdateringar**

* 32-bitarsversionen av klientkonsolen är nu inaktuell. Från och med 8.6 är klientkonsolen endast tillgänglig i 64 bitar. Uppgraderingen till 64-bitarsversionen av klientkonsolen är smidig. Mer information om hur du uppgraderar ditt operativsystem finns i [technote](../../technotes/upgrades/console.md).
* Nu kan du ansluta Campaign v8-instansen till din externa Azure synapse-databas. Den här anslutningen hanteras via ett nytt externt konto. Läs mer i [Kompatibilitetsmatris för kampanj](../start/compatibility-matrix.md#federated-data-access-fdafederateddataaccessfda).

**Förbättringar**

* SMS-genomströmningen har förbättrats avsevärt genom att man implementerar en rad optimeringar, vilket ger snabbare och effektivare SMS-kommunikation.
* Nu kan du använda Adobe Experience Platform Destination-anslutningen för att synkronisera profilattribut, som avanmälningsdata mellan Adobe Experience Platform- och Campaign v8-databasen.
* Förberedelsen av leveransen har optimerats.
* Ett nytt nyckelbaserat autentiseringsalternativ har lagts till för det externa SFTP-kontot, tillsammans med den befintliga autentiseringsmetoden för användare/lösenord. Användarna kan nu autentisera säkert med en privat nyckel, förbättra säkerheten och tillhandahålla en alternativ autentiseringsmekanism för SFTP-åtkomst. Läs mer i [det här avsnittet](../config/external-accounts.md).

**Säkerhetsförbättringar**

* Från och med Campaign v8.5 har autentiseringsprocessen till Campaign v8 förbättrats. Tekniska operatörer måste använda Adobe Identity Management System (IMS) för att ansluta till Campaign. Lär dig hur du migrerar dina befintliga tekniska konton i [den här tekniken](../../technotes/upgrades/ims-migration.md).
* Du kan inte längre skapa operatorer från Campaign Client Console. Användargränssnittet har uppdaterats i enlighet med detta. Nu måste du använda Adobe Admin Console. [Läs mer](../start/gs-permissions.md).
* Flera tredjepartsverktyg har uppdaterats för att optimera säkerheten.

**Korrigeringar**

* Korrigerade ett problem som kunde leda till att specialtecken i HTML-innehållet i en leverans kodades felaktigt i flera webbläsare. (NEO-60081)
* Ett problem som kunde förhindra dig från att spara en rapport för en Campaign v8 Enterprise-distribution (FFDA) har åtgärdats. (NEO-56836)
* Ett problem har korrigerats när data infogades eller uppdaterades i ett anpassat FFDA-schema via en aktivitet i arbetsflödet Uppdatera data. (NEO-54708)
* Ett problem som gjorde att det inte gick att ta bort adresser i tabellen nms:address i FFDA i databasrensningsarbetsflödet har åtgärdats. (NEO-54460)
* Ett problem med faktureringsarbetsflödet som kunde misslyckas med felet &quot;Kompileringsminnet är slut&quot; har åtgärdats. (NEO-51137)
* Ett problem som kunde förhindra GPG-dekrypteringen från att fungera korrekt i arbetsflödesaktiviteten för datainläsning (fil) har åtgärdats. (NEO-50257)
* Korrigerade ett problem som förhindrade funktionen `JSPContext.sqlExecWithOneParam` från att arbeta. (NEO-50066)
* Korrigerade ett problem som ledde till leveransfel när icke-utskrivbara tecken användes i anpassningsfält. (NEO-48588)
* Ett problem som kunde orsaka leveransfel vid infogning av dynamiska Adobe Target-bilder har åtgärdats. (NEO-62689)
* Ett problem har korrigerats som förhindrar att webbläsare lägger till extra mellanslag när villkorsstyrt innehåll används i en leverans. (NEO-62132)
* Ett problem som gjorde att ett popup-fönster öppnades när du klickade på en bild i e-postredigeraren har åtgärdats. (NEO-60752)
* Korrigerade ett problem som kan leda till ett fel och förhindra att du rullar när du redigerar innehållet i en leverans. (NEO-61364)
* Adobe Analytics Connector exporterar nu mätvärden med rätt kanaltyp. Den har tidigare alltid angetts som en e-postkanal. (NEO-26340)


## Version 8.4.5 {#release-8-4-5}

_3 april 2023_

**Korrigeringar**

* Korrigerade ett problem som kunde leda till ett duplicerat nyckelbegränsningsfel om flera godkännandearbetsflöden hade angetts till samma schema. (NEO-48968)
* Korrigerade ett regressionsfel som introducerades av NEO-54474 (8.4.4) som ledde till att formategenskapen för body-taggen ändrades när en bild överfördes till Digital Content Editor (DCE). (NEO-57697)
* Korrigerade ett problem som kunde leda till ett fel när data exporterades med en CRM-koppling om den tillfälliga tabellen hade en primärnyckel definierad som lång i stället för uuid. (NEO-54153)
* Korrigerade ett regressionsproblem som introducerades i 8.4.1 som kunde leda till fel vid paketexport, FDA över HTTP och rapportering. (NEO-57731)
* Ett regressionsproblem som introducerades i 8.3.8 som kunde förhindra att leveransstatusen uppdateras korrekt för leveranser med negativa ID:n har åtgärdats. (NEO-54675)
* Ett problem med booleska fält vid import av data med Big Query-kopplingen (NEO-49181) har korrigerats


## Version 8.4.4 {#release-8-4-4}

_8 mars 2023_

**Säkerhetsförbättring**

* För att förbättra säkerheten har Tomcat uppdaterats från version 8.5.81 till 8.5.85. (NEO-50530)

**Korrigeringar**

* Korrigerade ett problem som kunde förhindra dig från att skrolla i fliken **Redigera** i Redigeraren för digitalt innehåll (DCE). (NEO-54474)
* Ett fel som kan leda till att webbservern kraschar har åtgärdats under replikeringen. (NEO-53670)


## Version 8.4.3 {#release-8-4-3}


_27 januari 2023_

**Förbättringar**

* Ett problem med synkronisering av leveransindikator mellan marknadsföringsservern och mellanleverantörsservern har korrigerats. (NEO-50724) <!--OKKKK-->
* Korrigerade ett problem som kunde leda till ett fel vid export av ett arbetsflöde. (NEO-50555) <!--OKKKK-->
* Ett problem som uppstod när ett tidigare utökat schema skulle utökas har åtgärdats. (NEO-49118) <!--OKKKK-->
* Ett problem har korrigerats vid användning av två anrikningsaktiviteter med samma identifierare i länkdefinitionen. (NEO-48851)
* Åtgärdade två fel vid leveransförberedelse. Förberedelsen kan misslyckas om antalet potentiella erbjudanden som manipuleras är för högt. Det andra problemet uppstod när bild-URL:erna definierades som URL:er att spåra i en textformatsleverans. (NEO-48807) <!--OKKKK-->
* Korrigerade ett problem som kunde leda till ett arbetsflödesfel där ett arbetsflöde skulle skriva över det lagerställenamn som definierats i det externa kontot för andra konton än FFDA. (NEO-43209) <!--OKKKK-->
* Förbättrad säkerhet för webbprogram för att förhindra DDoS-attacker. (NEO-50757) <!--OKKKK-->
* Hanteringen av konsoliderade spårningsdata har förbättrats i **[!UICONTROL Consolidated tracking]** (nms:trackingStats) FFDA-tabell för att undvika dubbletter. (NEO-46409)
* Ett problem med en logisk operator i arbetsflödesfrågor när en användare användes har korrigerats `enableIf` i ett logiskt operatorvillkor. Det föregående logiska villkoret skrevs över. (NEO-45815)  <!--OKKKK-->
* Genereringen av aktiva profiler har optimerats i faktureringsarbetsflödet för att förbättra prestandan. (NEO-47658) <!--OKKKK-->
* Korrigerade ett problem med import av HTML-fil när bildnoder (img) innehöll URL:er med personaliseringsfält. (NEO-48396)
* Ett problem med Snowflake (alla distributioner) när sorteringsparametern i en **Dela** arbetsflödesaktivitet. (NEO-45899) <!--OKKKK-->
* Korrigerade ett problem som orsakade ett fel när en användare med läsbehörighet i mappen nmsDeliveryMapping försökte köra en kampanj eller ett arbetsflöde. (NEO-48230)
* Korrigerade ett prestandaproblem på fliken HTML för en leverans som kan uppstå för stor HTML-kod. (NEO-47440)
<!-- * Fixed an issue which could lead to a "Character set mismatch" error when using certain functions such as `to_nclob` with an Oracle unicode database where NChar was not enabled. (NEO-49361)
* Fixed an issue which prevented users from inserting a Time datatype in a **Data Update** workflow activity on MSSQL. (NEO-47763)-->
* Ett problem som hindrade användare från att använda **Sammanfoga markerade rader** arbetsflödesalternativ. (NEO-48488)
* Korrigerade ett fel på Snowflake FDA-anslutningen som ledde till att poster utelämnades när alternativet &quot;0 eller 1 enkel kardinalitetsanslutning&quot; användes under anrikningen. (NEO-48737)
* Återstående referenser till log4j-biblioteket har tagits bort från Campaign-installationen i Windows. (NEO-44851)
* Korrigerade ett problem som kan leda till ett fel när indikatorn **Mottagare som har öppnat** (estimatedRecipientOpen) lades till i ytterligare data för arbetsflödesaktiviteten **Fråga**. (NEO-46665)
* Hanteringen av spårnings-URL:er har förbättrats i arbetsflöden med flera leveranser för att förbättra prestandan. (NEO-50894) <!--OKKKK-->
* Korrigerade ett problem som kunde göra så att replikering av scheman som använder Xtkfolder misslyckades. (NEO-46787) <!--OKKKK-->
* Korrigerat en felorsak som kan göra att den anpassade kolumnen&quot;lastModified&quot; tas bort i NmsSubscription-tabellen. (NEO-48402)


