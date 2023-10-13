---
title: Dela målgrupper med Adobe Experience Cloud lösningar
description: Lär dig dela målgrupper med Adobe Experience Cloud lösningar
feature: Audiences
role: User
level: Beginner
hide: true
hidefromtoc: true
exl-id: c4d30771-db5e-40be-8af6-50f0fab9f9af
source-git-commit: e0ec2940db3120dc8fbfd17dd2f5083bbf31232c
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 5%

---

# Dela målgrupper med Adobe Experience Cloud lösningar{#shared-audiences}


Alternativ 1: AEP-källor och -destinationer

Alternativ 2: Adobe People/AAM

Ni kan integrera **Adobe Campaign** med **Bastjänst för människor** eller Adobe Audience Manager. Då kan du:

* Importera delade målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Publiker kan importeras via listor i Adobe Campaign.

* Exportera listor i form av delade Adobe Experience Cloud-målgrupper. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. Målgrupper kan exporteras efter målgruppsanpassning i ett arbetsflöde med hjälp av en dedikerad **[!UICONTROL Update shared audience]** aktivitet.

Den här integreringen stöder två typer av Adobe Experience Cloud ID:

* **Besökar-ID**: den här typen av identifierare förenar Adobe Experience Cloud-besökare med Adobe Campaign-mottagare.
* **Deklarerat ID**: den här typen av identifierare förenar alla typer av data med element från Adobe Campaign-databasen. Den representeras i Adobe Campaign som en fördefinierad avstämningsnyckel.

  >[!NOTE]
  >
  > Deklarerad  ID-datakälla kan nu även användas med integreringen av den grundläggande tjänsten People.
  >
  >Om du använder integreringen med huvudtjänsten Kontakter och vill lägga till integreringen med Audience Manager måste du få hjälp av en Adobe Audience Manager-konsults för att undvika att förlora alla ID-synkroniseringar som samlas in när du går över till att använda den här deklarerade ID-datakällan i ett Adobe Audience Manager-sammanhang.

Se:

[https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16471.html](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16471.html)

[https://experienceleague.adobe.com/docs/core-services/interface/services/audiences/audience-library.html](https://experienceleague.adobe.com/docs/core-services/interface/services/audiences/audience-library.html)
