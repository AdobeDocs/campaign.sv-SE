---
title: Inbyggd beräkning av rapportvärden
description: Inbyggd beräkning av rapportvärden
feature: Reporting
role: Data Engineer
exl-id: ad8e9f9c-df24-4a11-b8df-4b31dd54911f
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '3048'
ht-degree: 0%

---

# Inbyggd beräkning av rapportvärden {#metrics-calculation}

## Användaraktiviteter {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Öppnar <br /> </td> 
   <td> @öppnar<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-primärnyckel som är lika med 1.<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicka <br /> </td> 
   <td> @klickningar<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-typ som är lika med "Email click".<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transaktioner <br /> </td> 
   <td> @transaktioner<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-typ som är lika med Transaction.<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

Den här rapporten baseras på tabellen **[!UICONTROL Consolidated tracking]** (nms:trackingStats). Den här sammanställda tabellen används av prestandaskäl när rapporter visas i stället för tabellen **[!UICONTROL Recipient tracking logs]** (nms:trackingLogRcp) och den beräknas inte i realtid. Tabellen genereras några minuter efter att spårningsloggarna har hämtats. Om indikatorerna är aktuella blir resultatet samma som för indikatorerna i rapporten **Spårningsindikatorer**. Indikatorn @totalclicks uttrycker det totala antalet klick under en femminutersperiod.

## Ej levererbara och studsningar {#non-deliverables-and-bounces-1}

**Uppdelning efter feltyp**

Den här rapporten baseras på tabellen **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Totalt antal bearbetade meddelanden <br /> </td> 
   <td> @totalProcsed<br /> </td> 
   <td> Summan av meddelanden med statusen Klar, Skickat eller Misslyckades.<br /> </td> 
   <td> @prepare + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Okänd användare: <br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Antal alla meddelanden med statusen "Misslyckades" och en orsak som är lika med "Okänd av användare". <br /> </td> 
   <td> Count(@status=2 och msg/@errorReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Onåbar <br /> </td> 
   <td> @ej nåbar<br /> </td> 
   <td> Antal alla meddelanden med statusen "Misslyckades" och en orsak som är lika med "Inte nåbar". <br /> </td> 
   <td> Count(@status=2 och msg/@errorReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisad<br /> </td> 
   <td> @vägrade<br /> </td> 
   <td> Antal alla meddelanden med statusen"Misslyckades" och en orsak som är lika med"Avvisad". <br /> </td> 
   <td> Count(@status=2 och msg/@errorReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Ogiltig domän <br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> Antal alla meddelanden med statusen "Misslyckades" och en orsak som är lika med "Ogiltig domän". <br /> </td> 
   <td> Count(@status=2 och msg/@errorReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Konto inaktiverat <br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Antal alla meddelanden med statusen "Misslyckades" och en orsak som är lika med "Konto inaktiverat".<br /> </td> 
   <td> Count(@status=2 och msg/@errorReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Inkorgen är full<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Antal alla meddelanden med statusen "Misslyckades" och en orsak som är lika med "Inkorgen full". <br /> </td> 
   <td> Count(@status=2 och msg/@errorReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Fel <br /> </td> 
   <td> @value<br /> </td> 
   <td> Antal misslyckade meddelanden för den här typen av fel.<br /> </td> 
   <td> Count(@status=2 och msg/@errorReason="Värde för feltypen")<br /> </td> 
  </tr> 
  <tr> 
   <td> Bidrag <br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel fel av den här typen jämfört med totalt antal felmeddelanden.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning<br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel fel av den här typen jämfört med totalt antal bearbetade meddelanden.<br /> </td> 
   <td> percent(@value,@totalProcsed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Uppdelning efter domän**

I den andra delen av rapporten finns detaljerad information om hur misslyckade meddelanden per Internetdomän är fördelade i motsats till feltypen. Formeln som är länkad till indikatorn **Error** (@value) i det här fallet är: Count(@status=2 och @domain=&quot;värdet för domännamnet&quot;), d.v.s. antalet alla meddelanden som har en misslyckad status för den här domänen.

## Webbläsare {#browsers-1}

Den här rapporten baseras på tabellen **[!UICONTROL Internet Browser Statistics]** (nms:userAgentsStats).

**Global statistik**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Besökare<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Totalt antal målmottagare för den här webbläsaren som klickat i en leverans minst en gång.<br /> </td> 
   <td> Sum(@besökare)<br /> </td> 
  </tr> 
  <tr> 
   <td> Sidvyer<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Totalt antal klick på leveranslänkar som använder den här webbläsaren, för alla leveranser.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> Användningsfrekvens <br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel besökare för den här webbläsaren jämfört med totalt antal besökare.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistik per webbläsare**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Användningsfrekvens <br /> </td> 
   <td> @besökare<br /> </td> 
   <td> Procentandel av antalet besökare per dag som använder den här webbläsaren jämfört med antalet besökare som mäts på dagen med de flesta besöken.<br /> </td> 
   <td> percent(sum(@besökare),max(@besökarePåDag))<br /> </td> 
  </tr> 
  <tr> 
   <td> Global frekvens <br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel besökare för den här versionen jämfört med det totala antalet besökare som använder alla webbläsare.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Relativ vikt <br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel besökare för den här versionen jämfört med det totala antalet besökare som använder den här webbläsaren.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Delning till sociala nätverk {#sharing-to-social-networks-1}

Den här rapporten baseras på tabellerna **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) och **[!UICONTROL Web tracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Antal meddelanden att leverera<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Totalt antal meddelanden som bearbetats under leveransanalysen.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Antal slutförda leveranser <br /> </td> 
   <td> @success<br /> </td> 
   <td> Antal meddelanden som har bearbetats <br /> </td> 
   <td> sum([Indic/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> E-post<br /> </td> 
   <td> @email<br /> </td> 
   <td> Summan av alla @totalClicks för vilka URL-kategorin är lika med "e-post".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Summan av alla @totalClicks för vilka URL-kategorin är lika med "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Summan av alla @totalClicks för vilka URL-kategorin är lika med "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Summan av alla @totalClicks för vilka URL-kategorin är lika med "delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Summan av alla @totalClicks som URL-kategorin är lika med "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Summan av alla @totalClicks som URL-kategorin är lika med "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Summan av alla @totalClicks som URL-kategorin är lika med "länkad".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Resurser**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Antal resurser <br /> </td> 
   <td> @forward<br /> </td> 
   <td> Totalt antal delade meddelanden i det här sociala nätverket.<br /> </td> 
   <td> Sum(iIf([url/@category]="Value of the social network type",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Procentandel av antalet resurser i det här sociala nätverket jämfört med det totala antalet resurser.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delningsfrekvens <br /> </td> 
   <td> @rate<br /> </td> 
   <td> Antal resurser i det här nätverket jämfört med antalet meddelanden som ska levereras.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Öppnar**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Antal öppningar <br /> </td> 
   <td> @open<br /> </td> 
   <td> Totalt antal spårningsrader i webbspårningstabellen.<br /> </td> 
   <td> Antal<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Procentandel av antalet öppningar i det här sociala nätverket jämfört med det totala antalet öppningar.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Frekvens för öppningar <br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Antal öppningar i det här sociala nätverket jämfört med det totala antalet meddelanden som ska levereras.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistik om delningsaktiviteter {#statistics-on-sharing-activities-1}

Den här rapporten baseras på tabellerna **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) och **[!UICONTROL Web tracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nya kontakter<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> Antal besökare som är länkade till en mottagare.<br /> </td> 
   <td> Formel: count(@id)<br /> Filter: @mottagare-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Öppnar <br /> </td> 
   <td> @öppnad<br /> </td> 
   <td> Antal alla @ids med en URL-typ som är lika med Open.<br /> </td> 
   <td> count (Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Resurser<br /> </td> 
   <td> @shared<br /> </td> 
   <td> URL-kategorin ingår i "email", "facebook", "twitter", "delicious", "digg", "google", "linkedin" <br /> Antal alla @totalClicks med en URL-kategori som är lika med "email", "facebook", "twitter", "delicious", "digg", "google" eller "linkedin".<br /> </td> 
   <td> count (Iif([url/@category] IN (email', facebook', twitter', delicious, digg, google, linkedin), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Operativsystem {#operating-systems-1}

Den här rapporten baseras på tabellen **[!UICONTROL Internet Browser Statistics]** (nms:userAgentsStats).

**Global statistik**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Besökare<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> Dagsmedelvärde av det totala antalet mottagare som är målinriktade av operativsystemet som klickade på en leverans minst en gång.<br /> </td> 
   <td> Sum(@besökare)<br /> </td> 
  </tr> 
  <tr> 
   <td> Sidorna visade<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> Dagsgenomsnitt av det totala antalet klick på leveranslänkar per operativsystem för alla leveranser.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Användningsfrekvens <br /> </td> 
   <td> -<br /> </td> 
   <td> Uppdelning av besökare per operativsystem jämfört med totalt antal besökare.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistik per operativsystem**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Användningsfrekvens <br /> </td> 
   <td> @besökare<br /> </td> 
   <td> Procentandel av antalet besökare per dag i det här operativsystemet jämfört med antalet besökare som mäts på dagen med de flesta besöken.<br /> </td> 
   <td> percent(sum(@besökare), max(@besökareOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Global frekvens <br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel besökare per version jämfört med totalt antal besökare i alla operativsystem.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Relativ frekvens <br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel besökare per version jämfört med det totala antalet besökare som använder det här operativsystemet.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Prenumerationsspårning {#subscription-tracking-1}

Den här rapporten baseras på tabellen **[!UICONTROL Services]** (nms:service).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Registrerad <br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> Antal registrerade personer föregående dag.<br /> </td> 
   <td> sum(Iif(@skapad &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Prenumerationer<br /> </td> 
   <td> @_prenumeration<br /> </td> 
   <td> antal prenumerationer (@action = 1) föregående dag.<br /> </td> 
   <td> sum(Iif(@action = 1 och @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Avbeställer <br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> antal avbeställningar (åtgärd = 0) föregående dag.<br /> </td> 
   <td> sum(Iif(@action = 0 och @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Utveckling <br /> </td> 
   <td> -<br /> </td> 
   <td> Antal prenumerationer minus antalet prenumerationer som har avbrutits. Frekvensen beräknas i relation till det totala antalet prenumeranter.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.0 0)+ %),'')<br /> </td> 
  </tr> 
  <tr> 
   <td> Lojalitet<br /> </td> 
   <td> -<br /> </td> 
   <td> Prenumerantens lojalitetsgrad för den relaterade perioden.<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Spårningsindikatorer {#tracking-indicators-1}

Den här rapporten baseras på tabellerna **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) och **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Meddelanden att leverera<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Antal breda loggar efter målanalys.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Lyckades<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Antal meddelanden för vilka fältet "dirigeringsadress" är lika med "Nej" och med statusen "Som tagits med i beräkningen av tjänsteleverantören", "Skickat" eller "Mottaget på mobilen".<br /> </td> 
   <td> sum([Indic/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Distinkta öppningar i populationen uppnåddes <br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> Extrapolering av antalet distinkta öppningar för alla e-postmeddelanden baserat på antalet distinkta öppningar för e-postmeddelanden i html-format.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@receiveOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Totalt antal öppningar i populationen uppnåddes <br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> Extrapolering av det totala antalet öppningar för alla e-postmeddelanden baserat på det totala antalet öppningar av e-postmeddelanden i html-format.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicka på länken <br /> för att avbryta prenumerationen </td> 
   <td> @optOut<br /> </td> 
   <td> Antal alla @ids med en URL-kategori som är lika med "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicka på länken till spegelsidan <br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Antal alla @ids med en URL-kategori som är lika med "Spegelsida".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppskattning av vidarebefordran <br /> </td> 
   <td> @forward<br /> </td> 
   <td> Skillnad mellan antalet distinkta personer och antalet distinkta mottagare som klickade i e-postmeddelandet minst en gång.<br /> </td> 
   <td> @personClick - @mottagarklickning<br /> </td> 
  </tr> 
  <tr> 
   <td> Skickar<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Antal meddelanden för vilka fältet "dirigeringsadress" är lika med "Nej" och med en status som är lika med "tas med i beräkningen av mottagaren", "Skickat" eller "Mottaget på mobilen".<br /> </td> 
   <td> sum([Indic/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klagomål<br /> </td> 
   <td> @klagomål<br /> </td> 
   <td> Antal meddelanden med statusen "Misslyckades" och en orsak som är lika med "adress i blockeringslista".<br /> </td> 
   <td> Count(@status=2 och msg/@errorReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Öppnar <br /> </td> 
   <td> @receiveOpen<br /> </td> 
   <td> Antal alla @broadLog-id i alla spårningsloggar.<br /> </td> 
   <td> Motsatt ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicka <br /> </td> 
   <td> @receiveClick<br /> </td> 
   <td> Distinkt antal @broadLog-id med en URL-typ som är lika med "Email click". <br /> </td> 
   <td> Countdistans(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Raw-reaktivitet <br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel av antalet mottagare som klickade i en leverans minst en gång jämfört med antalet mottagare som öppnade en leverans minst en gång.<br /> </td> 
   <td> percent(@mottagareKlicka,@mottagareÖppna)<br /> </td> 
  </tr> 
  <tr> 
   <td> distinkta klick på populationen uppnåddes <br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Antal alla @source-id med en URL-kategori som är lika med "Email click".<br /> </td> 
   <td> Countdistans(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Ackumulerade klick<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Antal alla @ids med en URL-kategori som är lika med"E-postklick".<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Mottagaren klickar <br /> </td> 
   <td> @receiveClick<br /> </td> 
   <td> Distinkt antal av @broadLog-ids med en URL-typ som är lika med"Email click".<br /> </td> 
   <td> Countdistans(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppskattad reaktivitet <br /> </td> 
   <td> -<br /> </td> 
   <td> Förhållandet mellan antalet mottagare som klickade i en leverans minst en gång och antalet mottagare som öppnade leveransen minst en gång.<br /> </td> 
   <td> percent(@mottagareKlicka, @measuredRecipientOpen<br />) </td> 
  </tr> 
  <tr> 
   <td> Besökta sidor: <br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Antal alla @ids med en URL-typ som är lika med "Web" eller "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=4 eller [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transaktioner <br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Antal alla @ids med en URL-typ som är lika med Transaction.<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Totalt belopp <br /> </td> 
   <td> @amount<br /> </td> 
   <td> Summan av webTrackingLog/@amount med en URL-typ som är lika med Transaction. <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Genomsnittligt transaktionsbelopp <br /> </td> 
   <td> -<br /> </td> 
   <td> Förhållande mellan det totala beloppet och antalet transaktioner.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Objekt<br /> </td> 
   <td> @artikel<br /> </td> 
   <td> Summan av webTrackingLog/@articles med en URL-typ som är lika med Transaction.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Genomsnittligt antal artiklar per transaktion <br /> </td> 
   <td> -<br /> </td> 
   <td> Förhållandet mellan antalet artiklar och antalet transaktioner.<br /> </td> 
   <td> div(@artikel, @transaktion)<br /> </td> 
  </tr> 
  <tr> 
   <td> Genomsnittligt belopp per meddelande <br /> </td> 
   <td> -<br /> </td> 
   <td> Förhållande mellan det totala beloppet och antalet meddelanden som ska levereras.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> E-post<br /> </td> 
   <td> @email<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-kategori som är lika med"e-post".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-kategori som är lika med "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-kategori som är lika med "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-kategori som är lika med"delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-kategori som är lika med "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-kategori som är lika med "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-kategori som är lika med "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL:er och klickströmmar {#urls-and-click-streams-1}

Den här rapporten baseras på tabellen **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reaktivitet <br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Förhållandet mellan antalet målmottagare som klickade i en leverans minst en gång och det beräknade antalet målmottagare som öppnade en leverans minst en gång.<br /> </td> 
   <td> percent([indikatorr/@mottagarklickning], [indikatortal/@estimeradMottagareÖppna])<br /> </td> 
  </tr> 
  <tr> 
   <td> Distinkta klick<br /> </td> 
   <td> @distinktKlicks<br /> </td> 
   <td> Förhållandet mellan antalet distinkta personer som klickade i en leverans minst en gång jämfört med antalet meddelanden som levererades med framgång.<br /> </td> 
   <td> percent([Indic/@personClick], [Indic/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Ackumulerade klick<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Förhållande mellan det totala antalet klickningar av målmottagare jämfört med antalet meddelanden som levererats med lyckat resultat.<br /> </td> 
   <td> percent([Indic/@totalRecipientClick], [Indic/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicka <br /> </td> 
   <td> @_klicka<br /> </td> 
   <td> Antal alla @totalClicks med en URL-primärnyckel som skiljer sig från 1<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicka (%)<br /> </td> 
   <td> -<br /> </td> 
   <td> Procentandel av antalet klick jämfört med totalt antal klick.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Leveranssammanfattning {#delivery-summary-1}

Den här rapporten baseras på tabellen **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Inledande population <br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Totalt antal mottagare som har angetts som mål för leveransen.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Meddelanden som avvisats av regeln <br /> </td> 
   <td> @reject<br /> </td> 
   <td> Antal adresser som ignoreras under analysen enligt typologireglerna: ingen adress har angetts, i karantän, på blockeringslista osv.<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> Meddelanden att leverera<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Totalt antal meddelanden som ska levereras efter leveransanalys.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Lyckades<br /> </td> 
   <td> @success<br /> </td> 
   <td> Antal meddelanden som har bearbetats.<br /> </td> 
   <td> sum([Indic/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Fel <br /> </td> 
   <td> @error<br /> </td> 
   <td> Totalt antal kumulerade fel under leveranser och automatisk avhoppsbearbetning.<br /> </td> 
   <td> sum([Indic/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> Nya karantäner <br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Antal adresser i karantän efter leveransfel (okänd användare, ogiltig domän).<br /> </td> 
   <td> sum([Indic/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Snabbklick {#hot-clicks-1}

Den här rapporten baseras på tabellerna Delivery(nms:delivery) och **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

Den här rapporten visar meddelandeinnehållet (HTML och/eller text) med procentandelen klickningar på länkar för varje länk. Personalisering blockerar länkar för att prenumerera bort och spegelsideslänkar beaktas i det totala antalet klick, men visas inte i rapporten.

## Spårningsstatistik {#tracking-statistics-1}

Den här rapporten baseras på tabellen **[!UICONTROL Delivery]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transaktioner <br /> </td> 
   <td> @transaktioner<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-typ som är lika med Transaction.<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicka <br /> </td> 
   <td> @klickningar<br /> </td> 
   <td> Summan av alla @totalClicks med en URL-typ som är lika med"Email click".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Öppna<br /> </td> 
   <td> @öppnar<br /> </td> 
   <td> Summan av alla @totalClicks med en primär URL-nyckel som är lika med 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Leveransstatistik {#delivery-statistics-1}

Den här rapporten baseras på tabellen **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> E-postmeddelanden har bearbetats<br /> </td> 
   <td> @bearbetad<br /> </td> 
   <td> Totalt antal meddelanden med en status som är lika med "Klar", "Skickat" eller "Misslyckat".<br /> </td> 
   <td> @prepare + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Levererad<br /> </td> 
   <td> @success<br /> </td> 
   <td> Antal meddelanden som har bearbetats.<br /> </td> 
   <td> Visar/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Hårda studsar <br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Totalt antal meddelanden med en status som är lika med "Misslyckades" och en orsak som är lika med "Okänd användare".<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Mjuka studsar <br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Totalt antal meddelanden med en status som är lika med "Misslyckades" och en orsak som är lika med "Inte tillgänglig", "full inkorg", "ogiltig domän", "inaktiverat konto", "inte ansluten" eller "avvisad" <br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @vägrad<br /> </td> 
  </tr> 
  <tr> 
   <td> Öppnar <br /> </td> 
   <td> @receiveOpen<br /> </td> 
   <td> Totalt antal @broadLog-id i spårningsloggarna.<br /> </td> 
   <td> Motsatt ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicka <br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Totalt antal @source-ids som URL-kategorin är lika med"Email click". <br /> </td> 
   <td> Countdistans(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Avbeställer <br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Totalt antal @ids för vilka URL-kategorin är lika med "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Indelning av öppningar {#breakdown-of-opens-1}

Den här rapporten baseras på tabellerna **Leveranser** (nms:delivery) och **spårningsloggar** (nms:trackingLogRcp).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br /> </th> 
   <th> <strong>Fältnamn</strong> <br /> </th> 
   <th> <strong>Indikatorbeskrivning</strong> <br /> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Öppnar <br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Summan av alla @id med en primär URL-nyckel som är lika med 1 (öppen). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Andra indikatorer {#other-indicators}

Indikatorn **Skickat** (@skickat), som nås via noden **Leveranser (nms:delivery) > Indicators**, motsvarar det totala antalet SMS som skickas till tjänstprovidern. Den här indikatorn används bara för SMS-leveranser och får inte användas för andra typer av leveranser (ska inte blandas ihop med indikatorerna **@success** och **@processed**).

## Synkronisering av indikator {#indicator-synchronization}

Om vissa indikatorer inte är synkroniserade eller inte överensstämmer väljer du den aktuella leveransen i Adobe Campaign Explorer, högerklickar och väljer **[!UICONTROL Action>Recompute delivery and tracking indicators]**. Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Finish]**.

## Spårningsöppningar {#tracking-opens-}

För att Adobe Campaign ska kunna upptäcka att ett meddelande öppnas måste mottagaren hämta bilderna i e-postmeddelandet. HTML och Multipart/Alternative emails innehåller en bild på 0 pixlar som gör att du kan identifiera meddelanden som har öppnats. Eftersom meddelanden i textformat inte innehåller några bilder går det inte att se om de har öppnats eller inte. Värden som beräknas baserat på det meddelande som öppnas är alltid uppskattningar på grund av den felmarginal som är länkad till bildvisningen.

## Målgrupper/mottagare {#targeted-persons---recipients}

I vissa rapporter skiljer Adobe Campaign ut målgruppsanpassade personer och målgruppsinriktade mottagare.

Målmottagare är alla mottagare som leveransen skickades till.

Antalet personer omfattar riktade mottagare plus alla personer som e-postmeddelandet skickades till. Varje gång det finns en öppning eller ett klick i en ny webbläsare (som meddelandet ännu inte har öppnats i) läggs en annan person till i statistiken.

Om du till exempel får ett e-postmeddelande (som skickas av Adobe Campaign) på jobbet och öppnar eller klickar i det, räknas du som en målmottagare (dvs. mottagare=1, person=1). Om du vidarebefordrar det här e-postmeddelandet till två vänner är antalet målmottagare fortfarande lika med ett, medan antalet personer är lika med tre. Värdet 3 sammanfaller med varje öppet/klickning i en ny webbläsare.
