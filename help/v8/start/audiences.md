---
title: Arbeta med målgrupper i Campaign
description: Arbeta med målgrupper i Campaign
feature: Audiences
role: User
level: Beginner
exl-id: 07baa759-fb0b-4eba-bf8b-ec6cf21df7f8
source-git-commit: 99cb937a475997aae714a67b1f9f91c6bae932f4
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 17%

---

# Arbeta med målgrupper i Campaign{#gs-ac-audiences}

Profiler är kontakter som lagras i Campaign-databasen.

I ADOBE CAMPAIGN **mottagare** är standardprofiler för att skicka leveranser (e-post, SMS, osv.). Med mottagardata som lagras i databasen kan du filtrera målet som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

Lär dig importera, uppdatera och hantera profiler och målgrupper [i det här avsnittet](../audiences/gs-audiences.md).

## Skapa listor{#create-lists}

En lista är en statisk uppsättning kontakter som kan användas för leveransåtgärder eller uppdateras under en import- eller en annan arbetsflödesåtgärd. En population som har extraherats från databasen via en fråga kan till exempel lagras som en lista.

Lär dig hur du skapar och hanterar listor i [den här sidan](../audiences/create-audiences.md).

## Filtrera databasen{#filter-the-database}

Med filterkonfigurationen kan du välja data från en lista **[!UICONTROL dynamically]**: När data ändras uppdateras de filtrerade data. Du kan skapa egna filter eller använda de inbyggda filtren för att definiera en målgrupp.

Lär dig hur du skapar och hanterar filter i [den här sidan](../audiences/create-filters.md).

## Skapa en målgrupp i ett arbetsflöde

Målinriktning kan skapas med en kombination av frågor i en grafisk sekvens i ett arbetsflöde. Ni kan skapa målgrupper som anpassas efter era behov. Om du vill visa arbetsflödesredigeraren klickar du på **[!UICONTROL Targeting and workflows]** på kampanjkontrollpanelen.

Lär dig hur du skapar en målgrupp i ett kampanjarbetsflöde i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html){target="_blank"}.


## Aktiva profiler {#active-profiles}


En aktiv profil är en profil som kunden har försökt kommunicera med under de senaste 12 månaderna via valfri kanal.

Enligt avtalet har var och en av instanserna i Campaign ett visst antal aktiva profiler som räknas för faktureringsändamål. Se ditt senaste kontrakt för referens om antalet köpta aktiva profiler. Läs mer i [Adobe Campaign produktbeskrivning](https://helpx.adobe.com/se/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Du kan övervaka antalet aktiva profiler på instansen direkt från Campaign-kontrollpanelen. Mer information finns i [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html){target="_blank"}.


Följande skyddsräcken och begränsningar gäller:

* En profil som har valts av flera leveranser räknas bara en gång.
* Profiler som är inriktade på social marknadsföring på X (Twitter) räknas inte som aktiva profiler.
* Antalet baseras på mottagarens primärnyckel. Om det finns en profil i två olika mottagartabeller kan den därför räknas två gånger som en aktiv profil.


## Sekretess och medgivande{#privacy-and-consent}

Adobe Campaign är ett kraftfullt verktyg för att samla in och behandla stora datavolymer, inklusive personuppgifter och känsliga data. Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du erhåller och övervakar medgivande från dina mottagare.

Lär dig hur du hanterar sekretess och samtycke i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html){target="_blank"}.

**Relaterade ämnen**

* [Utforma och genomför ett kampanjspecifikt arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/campaign-workflows.html){target="_blank"}

* [Lär dig hur du väljer målgrupp för en kampanj](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html){target="_blank"}

* [Kom igång med arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html){target="_blank"}
