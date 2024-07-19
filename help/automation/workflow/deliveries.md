---
product: campaign
title: Leveranser
description: Läs mer om standardarbetsflöden för leveranser
feature: Workflows
role: User, Admin
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 5%

---


# Leveranser{#deliveries}



Arbetsflödena som anges nedan installeras som standard med modulen **Leveranser** .

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rapporteringsaggregat</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar aggregat som används i rapporter. Den aktiveras varje dag kl. 2.00 som standard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Fakturering</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Det här arbetsflödet skickar systemaktivitetsrapporten till faktureringsoperatorn via e-post. Den utlöses som standard den 25:e varje månad.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aliasrensning</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Det här arbetsflödet standardiserar uppräkningsvärden. Den utlöses varje dag klockan tre som standard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Uppdatering för leverans</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Med det här arbetsflödet kan du skapa en lista över regler för studsmeddelanden samt en lista över domäner och MX:er på plattformen. Det här arbetsflödet fungerar bara om HTTPS-porten är öppen. De här listorna uppdateras inte om inte leveransmodulen är installerad.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Databasrensning</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Det här arbetsflödet är arbetsflödet för databasunderhåll: det utför andra beräkningar än statistik och processer och tar bort föråldrade data från databasen enligt den definierade konfigurationen i distributionsassistenten. Den aktiveras varje dag klockan fyra som standard.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensning av pausade arbetsflöden</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Det här arbetsflödet analyserar pausade arbetsflöden som har allvarlighetsgraden inställd på normal och utlöser varningar och meddelanden när de har pausats för länge. Efter en månad stoppas tekniska arbetsflöden ovillkorligt. Som standard utlöses den varje måndag kl. 5.</p> <p>Mer information finns i Hantera pausade arbetsflöden </a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Erbjudandemeddelande</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Det här arbetsflödet distribuerar godkända erbjudanden till onlinemiljön samt alla kategorier i erbjudandekatalogen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Prognos</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span><br /> </td> 
   <td> Det här arbetsflödet analyserar leveranser som sparats i den preliminära kalendern (skapar preliminära loggar). Den utlöses varje dag klockan 1:00 som standard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Spärra/knip</span> <br /> </td> 
   <td> <span class="uicontrol">spårning</span> <br /> </td> 
   <td> Det här arbetsflödet utför återställning och konsolidering av spårningsinformation. Dessutom säkerställs omberäkningen av spårnings- och leveransstatistik, särskilt sådan som används i arbetsflöden för meddelandecentrets arkivering. Som standard aktiveras den en gång per timme. <br /> </td> 
  </tr> 
 </tbody> 
</table>

