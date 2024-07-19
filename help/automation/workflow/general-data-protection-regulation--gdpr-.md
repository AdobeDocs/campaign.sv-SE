---
product: campaign
title: Arbetsflöden för dataskyddsförordningen
description: Läs mer om arbetsflödena i förordningen om skydd av personuppgifter
role: User
feature: Workflows, Privacy
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 2%

---


# Skyddsförordningen för personuppgifter{#general-data-protection-regulation-gdpr}


Arbetsflödena som beskrivs nedan installeras som standard med modulen **Sekretessdataskydd** . Mer information om den här modulen finns i [artikeln](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Samla in sekretessförfrågningar</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> Det här arbetsflödet genererar mottagarens data som lagras i Adobe Campaign och gör dem tillgängliga för hämtning på sekretesförfrågningens skärm.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ta bort data för sekretessförfrågningar</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> Det här arbetsflödet tar bort mottagarens data som lagras i Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensa sekretessbegäran</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> Det här arbetsflödet raderar filer för åtkomstbegäran som är äldre än 90 dagar.<br /> </td> 
  </tr> 
 </tbody> 
</table>

