---
product: campaign
title: Interaktion
description: Interaktion
feature: Workflows, Interaction
source-git-commit: 8d9b8d3e31362c2d69ec0fc6f16ab375538d7f10
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 3%

---


# Interaktion{#interaction}

Arbetsflödena nedan installeras tillsammans med **Erbjudandemotor (interaktion)** tillägg som standard.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Fullständig aggregerad beräkning (propositionskub)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositioncp_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar <strong>Fullständig</strong> aggregat för <strong>Erbjudandeförslag</strong> kub. Den aktiveras varje dag kl. 6.00 som standard. Den här sammanställningen fångar följande dimensioner: Kanal, leverans, marknadsföringserbjudande och datum.<br /> The <strong>Erbjudandeförslag</strong> kub används sedan för att generera rapporter baserat på erbjudanden.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Fullständig mängdberäkning för MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar <strong>Fullständig</strong> aggregat för <strong>Meddelandecenter</strong> kub. Den aktiveras varje dag klockan tre som standard. Den här sammanställningen fångar följande dimensioner: Typ av kanal, datum, status och händelse.<br /> The <strong>Meddelandecenter</strong> kub används sedan för att generera rapporter baserat på händelser. <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Läs mer om kuber och aggregat i [det här avsnittet](../../v8/reporting/gs-cubes.md).

