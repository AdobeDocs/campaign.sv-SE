---
title: Dela målgrupper med Adobe Experience Cloud lösningar
description: Lär dig dela målgrupper med Adobe Experience Cloud lösningar
feature: Audiences, Profiles
role: User
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Dela målgrupper med Adobe Experience Cloud lösningar{#shared-audiences}

Alternativ 1: AEP-källor och -destinationer

Alternativ 2: Adobe People/AAM

Du kan integrera **Adobe Campaign** med **Bastjänsten för människor** eller Adobe Audience Manager. Då kan du:

* Importera delade målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Publiker kan importeras via listor i Adobe Campaign.

* Exportera listor i form av delade Adobe Experience Cloud-målgrupper. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. Publiker kan exporteras efter målgruppsanpassning i ett arbetsflöde med en dedikerad **[!UICONTROL Update shared audience]**-aktivitet.

Den här integreringen stöder två typer av Adobe Experience Cloud ID:

* **Besökar-ID**: Den här identifieraren förenar Adobe Experience Cloud-besökare med Adobe Campaign-mottagare.
* **Deklarerat ID**: Den här identifieraren förenar alla typer av data med element från Adobe Campaign-databasen. Den fördefinierade avstämningsnyckeln i Adobe Campaign.

  >[!NOTE]
  >
  > Deklarerad ID-datakälla kan också användas med integreringen av People core service.
  >
  >Om du använder integreringen med huvudtjänsten Kontakter och vill lägga till integreringen med Audience Manager måste du få hjälp av en Adobe Audience Manager-konsults för att undvika att förlora alla ID-synkroniseringar som samlas in när du går över till att använda den här deklarerade ID-datakällan i ett Adobe Audience Manager-sammanhang.

Se:

[Adobe Audience Manager Knowledge Base](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16471.html){target="_blank"}.

[Handbok för komponenter i Adobe Experience Cloud Central Interface](https://experienceleague.adobe.com/docs/core-services/interface/services/audiences/audience-library.html){target="_blank"}.
