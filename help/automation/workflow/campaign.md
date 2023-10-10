---
product: campaign
title: Campaign
description: Campaign
feature: Workflows
role: User, Admin
topic-tags: technical-workflows
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 3%

---


# Campaign{#campaign}

Arbetsflödena nedan installeras tillsammans med **Campaign** som standard.

>[!CAUTION]
>
>Dessa arbetsflöden MÅSTE startas för att kampanjprocesserna ska kunna köras på kampanjnivå.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kostnadsberäkning</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> Det här arbetsflödet startar beräkningen av utgifts- och kostnadsrader för budgetar, planer, program, kampanjer, leveranser och uppgifter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock: Beställningar och larm</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Det här arbetsflödet startar lagerberäkning på orderraderna och hanterar varningsaviseringströsklar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Jobb för leveranser i kampanjer</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Det här arbetsflödet utlöser de godkända leveranserna och påbörjar efterbearbetning av tjänsteleverantören för en extern leverans. Dessutom skickas meddelanden och påminnelser om godkännande.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kampanjjobb</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> Det här arbetsflödet hanterar jobben för marknadsföringskampanjer (lanserar målinriktning, filextrahering osv.). Det skapar också arbetsflöden för återkommande och periodiska kampanjer.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Jobb för tjänsteleverantörer</span> <br /> </td> 
   <td> <span class="uicontrol">providerMgt</span> <br /> </td> 
   <td> Det här arbetsflödet börjar bearbeta providern (e-post till routern och efterbearbetning) när leveranser har godkänts. <br /> </td> 
  </tr> 
 </tbody> 
</table>

