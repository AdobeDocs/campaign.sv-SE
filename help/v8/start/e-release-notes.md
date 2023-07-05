---
title: Versionsinformation om tidig kampanj v8
description: Tidig Campaign v8-version
feature: Overview
role: Admin, Developer, User
level: Beginner, Intermediate, Experienced
hide: true
hidefromtoc: true
exl-id: a45f7b22-44c7-4dad-af0a-ae8f683ae3d9
source-git-commit: 958d2e8acdb9edee74f55bc3ea808f5072bf8f4d
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 7%

---

# Tidig versionsinformation {#e-new-release}

Den här sidan beskriver de förbättringar och korrigeringar som ingår i nästa Campaign v8-version. Innehållet kan ändras utan föregående meddelande fram till releasedatum. Den officiella versionsinformationen finns här [page](../start/release-notes.md).

## Version 8.5.1 {#release-8-5}

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
<td><p>Campaign 8.5.1 introducerar vår senaste tjänst för push-meddelanden på v8, som bygger på ett robust ramverk som bygger på modern spetsteknik. Den här tjänsten är utformad för att låsa upp nya nivåer av skalbarhet, så att dina meddelanden kan nå en större publik med smidig effektivitet. Med vår förbättrade infrastruktur och våra optimerade processer kan ni förvänta er större skalbarhet och tillförlitlighet, så att ni kan engagera och kommunicera med era mobilappsanvändare som aldrig förr. Den här funktionen är bara tillgänglig för en viss kundgrupp (begränsad tillgänglighet).</p>
</td> 
</tr> 
</tbody> 
</table>

**Kompatibilitetsuppdateringar**

* 32-bitarsversionen av klientkonsolen är nu inaktuell. Från och med 8.6 är klientkonsolen endast tillgänglig i 64 bitar. Uppgraderingen till 64-bitarsversionen av klientkonsolen är smidig. Mer information om hur du uppgraderar ditt operativsystem finns i [technote](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/console.html).
* Nu kan du ansluta Campaign v8-instansen till din externa Azure synapse-databas. Den här anslutningen hanteras via ett nytt externt konto.

**Förbättringar**

* SMS-genomströmningen har förbättrats avsevärt genom att man implementerar en rad optimeringar, vilket ger snabbare och effektivare SMS-kommunikation.
* Från och med Campaign v8.5.1 har autentiseringsprocessen till Campaign v8 förbättrats. Tekniska operatörer måste använda Adobe Identity Management System (IMS) för att ansluta till Campaign.
* Nu kan du använda anslutningarna Mål och Källa för att synkronisera profilattribut som avanmälningsdata mellan Adobe Experience Platform- och Campaign v8-databasen
* Förberedelsen av leveransen har optimerats.
* Ett nytt nyckelbaserat autentiseringsalternativ har lagts till för det externa SFTP-kontot, tillsammans med den befintliga autentiseringsmetoden för användare/lösenord. Användarna kan nu autentisera säkert med en privat nyckel, förbättra säkerheten och tillhandahålla en alternativ autentiseringsmekanism för SFTP-åtkomst.

**Säkerhetsförbättringar**

* Du kan inte längre skapa operatorer från klientkonsolen. Nu måste du använda Admin Console. [Läs mer](../start/gs-permissions.md).
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
