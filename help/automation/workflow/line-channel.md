---
product: campaign
title: LINE-kanal
description: LINE-kanal
feature: Workflows
role: User
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 11%

---


# LINE-kanal{#line-channel}

Arbetsflödena nedan installeras tillsammans med **LINE-kanal** som standard. Mer information om den här modulen finns i [den här sidan](../../v8/send/line.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Uppdatering av åtkomsttoken för LINE V2</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar åtkomsttoken till LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ta bort blockerade LINE-användare</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Det här arbetsflödet säkerställer att LINE V2-användarnas data tas bort efter att de har blockerat LINE-kontot i 180 dagar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID till LineUserID-migrering</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Det här arbetsflödet genererar användar-ID:t för LINE V2 för migrering från LINE V1 till LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

