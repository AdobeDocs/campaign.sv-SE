---
product: Adobe Campaign
title: Versionsinformation om Campaign v8
description: Senaste Campaign v8-utgåvan
feature: Översikt
role: Data Engineer
level: Beginner
hidefromtoc: true
exl-id: 7cf8111d-9f3a-46a4-813a-d4e43a1d1471,a9d18e75-18e7-491e-bfc4-671c3600396e
source-git-commit: 9e745f7fb8fd20f35025c06ff621a9da5002190e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Senaste versionen{#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **den senaste Campaign v8-utgåvan**.

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
<td> <p>LINE-kanalen är nu tillgänglig med Campaign v8. Följande förbättringar har gjorts när du använder LINE med Message Center:
</p>
<ul> 
<li><p>Korrigerade ett problem som kunde förhindra besökare från att riktas mot en radleverans. 
</p></li>
<li><p>Korrigerade ett problem som kunde orsaka fel när besökare hämtades från körningsinstansen till marknadsinstansen.
</p></li>
<li><p>Korrigerade problem vid bearbetning av realtidshändelser i samband med radleveranser med Message Center.</p></li>
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
