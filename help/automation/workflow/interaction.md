---
product: campaign
title: Interaktion
description: Interaktion
feature: Workflows, Interaction
role: User, Admin
version: Campaign v8, Campaign Classic v7
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 1%

---


# Interaktion{#interaction}

Arbetsflödena som anges nedan installeras som standard med tillägget **Erbjudandemotor (interaktion)**.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Fullständig aggregeringsberäkning (propositionscp-kub)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmsproposicp_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar sammanställningen <strong>Fullständig</strong> för kuben <strong>Erbjudandeerbjudande</strong>. Den aktiveras varje dag kl. 6.00 som standard. Sammanställningen innehåller följande dimensioner: kanal, leverans, marknadsföringserbjudande och datum.<br /> Kuben <strong>Erbjudandeerbjudande</strong> används sedan för att generera rapporter baserat på erbjudanden.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Fullständig mängdberäkning för MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar sammanställningen <strong>Fullständig</strong> för kuben <strong>Meddelandecenter</strong>. Den aktiveras varje dag klockan tre som standard. Den här sammanställningen fångar följande dimensioner: Kanal, Datum, Status och Händelsetyp.<br /> Kuben <strong>Message center</strong> används sedan för att generera rapporter baserat på händelser. <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Läs mer om kuber och aggregat i [det här avsnittet](../../v8/reporting/gs-cubes.md).

