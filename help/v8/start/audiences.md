---
title: Arbeta med målgrupper i Campaign
description: Arbeta med målgrupper i Campaign
feature: Audiences
role: User
level: Beginner
exl-id: 07baa759-fb0b-4eba-bf8b-ec6cf21df7f8
source-git-commit: 59d33983db930b3a7dc022693d72704bda99e3a1
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 15%

---

# Arbeta med målgrupper i Campaign{#gs-ac-audiences}

Profiler är kontakter som lagras i Campaign-databasen.

I ADOBE CAMPAIGN **mottagare** är standardprofiler för att skicka leveranser (e-post, SMS, osv.). Med mottagardata som lagras i databasen kan du filtrera målet som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

Lär dig importera, uppdatera och hantera profiler och målgrupper [i det här avsnittet](../audiences/gs-audiences.md).

## Skapa listor{#create-lists}

En lista är en statisk uppsättning kontakter som kan användas för leveransåtgärder eller uppdateras under en import- eller en annan arbetsflödesåtgärd. En population som har extraherats från databasen via en fråga kan till exempel lagras som en lista.

![](../assets/do-not-localize/glass.png) Lär dig hur du skapar och hanterar listor i [den här sidan](../audiences/create-audiences.md).

## Filtrera databasen{#filter-the-database}

Med filterkonfigurationen kan du välja data från en lista **[!UICONTROL dynamically]**: När data ändras uppdateras de filtrerade data. Du kan skapa egna filter eller använda de inbyggda filtren för att definiera en målgrupp.

![](../assets/do-not-localize/glass.png) Lär dig hur du skapar och hanterar filter i [den här sidan](../audiences/create-filters.md).

## Skapa en målgrupp i ett arbetsflöde

Målinriktning kan skapas med en kombination av frågor i en grafisk sekvens i ett arbetsflöde. Ni kan skapa målgrupper som anpassas efter era behov. Om du vill visa arbetsflödesredigeraren klickar du på **[!UICONTROL Targeting and workflows]** på kampanjkontrollpanelen.

Lär dig hur du skapar en målgrupp i ett kampanjarbetsflöde i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html)


## Aktiva profiler {#active-profiles}

En aktiv profil är en profil som kunden har försökt kommunicera med under de senaste tolv månaderna via valfri kanal. Licensvärdena baseras på aktiva profiler. Läs mer i [Adobe Campaign produktbeskrivning](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Du kan övervaka antalet aktiva profiler på instansen direkt från Campaign-kontrollpanelen. Mer information finns i [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html){target="_blank"}.

>[!CAUTION]
>
>* En profil som har valts av flera leveranser räknas bara en gång.
>
>* Profiler som är inriktade på social marknadsföring på X (Twitter) räknas inte som aktiva profiler.

## Sekretess och medgivande{#privacy-and-consent}

Adobe Campaign är ett kraftfullt verktyg för att samla in och behandla stora datavolymer, inklusive personuppgifter och känsliga data. Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du erhåller och övervakar medgivande från dina mottagare.

![](../assets/do-not-localize/book.png) Lär dig hur du hanterar sekretess och samtycke i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html){target="_blank"}.

**Relaterade ämnen**

* [Utforma och genomför ett kampanjspecifikt arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/campaign-workflows.html)

* [Lär dig hur du väljer målgrupp för en kampanj](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html)

* [Kom igång med arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html)
