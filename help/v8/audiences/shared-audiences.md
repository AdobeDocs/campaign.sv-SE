---
title: Dela målgrupper med Adobe Experience Cloud lösningar
description: Lär dig dela målgrupper med Adobe Experience Cloud lösningar
feature: Audiences, Profiles
role: User
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 65f4da979f0c5884797af0c3a835d948672b4a7c
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Dela målgrupper med Adobe Experience Cloud lösningar{#shared-audiences}

Alternativ 1: AEP-källor och -destinationer

Alternativ 2: Adobe-AAM

Ni kan integrera **Adobe Campaign** med **Bastjänst för människor** eller Adobe Audience Manager. Då kan du:

* Importera delade målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Publiker kan importeras via listor i Adobe Campaign.

* Exportera listor i form av Adobe Experience Cloud delade målgrupper. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. Målgrupper kan exporteras efter målgruppsanpassning i ett arbetsflöde med hjälp av en dedikerad **[!UICONTROL Update shared audience]** aktivitet.

Den här integreringen stöder två typer av Adobe Experience Cloud ID:

* **Besökar-ID**: den här identifieraren förenar Adobe Experience Cloud-besökare med Adobe Campaign-mottagare.
* **Deklarerat ID**: den här identifieraren förenar alla typer av data med element från Adobe Campaign-databasen. Det är den fördefinierade avstämningsnyckeln i Adobe Campaign.

   >[!NOTE]
   >
   > Deklarerad ID-datakälla kan också användas med integreringen av People core service.
   >
   >Om du använder integreringen med huvudtjänsten Kontakter och vill lägga till integreringen med Audience Manager måste du få hjälp av en Adobe Audience Manager-konsults för att undvika att förlora alla ID-synkroniseringar som samlas in när du går över till att använda den här deklarerade ID-datakällan i ett Adobe Audience Manager-sammanhang.

Se:

[https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16471.html](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16471.html)

[https://experienceleague.adobe.com/docs/core-services/interface/services/audiences/audience-library.html](https://experienceleague.adobe.com/docs/core-services/interface/services/audiences/audience-library.html)
