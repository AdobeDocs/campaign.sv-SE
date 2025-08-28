---
title: Arbeta med målgrupper i Campaign
description: Arbeta med målgrupper i Campaign
feature: Audiences
role: User
level: Beginner
exl-id: 07baa759-fb0b-4eba-bf8b-ec6cf21df7f8
version: Campaign v8, Campaign Classic v7
source-git-commit: b24e05f152bc299ea7953856bfa71950b5cc9837
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 11%

---


# Arbeta med målgrupper i Campaign{#gs-ac-audiences}

Profiler representerar de kontakter som lagras i din Adobe Campaign-databas. Som standard är **mottagare** de primära profiler som används för att skicka leveranser som e-post, SMS eller direktreklam. Med mottagardata som lagras i databasen kan ni definiera och filtrera målgrupperna samt personalisera leveransinnehållet. Förutom mottagare finns det andra profiltyper för specifika ändamål. Med dirigerade profiler kan du till exempel testa leveranser innan de skickas till den verkliga målgruppen.

Lär dig hur du importerar, uppdaterar och hanterar profiler och målgrupper [i det här avsnittet](../audiences/gs-audiences.md).

## Skapa listor{#create-lists}

En lista är en statisk uppsättning kontakter som kan användas för leveransåtgärder eller uppdateras under en import- eller en annan arbetsflödesåtgärd. En population som har extraherats från databasen via en fråga kan till exempel lagras som en lista.

Lär dig skapa och hantera listor på [den här sidan](../audiences/create-audiences.md).

## Filtrera databasen{#filter-the-database}

Med filterkonfigurationen kan du välja data från en lista **[!UICONTROL dynamically]**: när data ändras uppdateras filtrerade data. Du kan skapa egna filter eller använda de inbyggda filtren för att definiera en målgrupp.

Lär dig hur du skapar och hanterar filter på [den här sidan](../audiences/create-filters.md).

## Skapa en målgrupp i ett arbetsflöde

Målinriktning kan skapas med en kombination av frågor i en grafisk sekvens i ett arbetsflöde. Ni kan skapa målgrupper som anpassas efter era behov. Om du vill visa arbetsflödesredigeraren klickar du på fliken **[!UICONTROL Targeting and workflows]** på kontrollpanelen för kampanjer.

Lär dig hur du skapar en målgrupp i ett kampanjarbetsflöde på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=sv-SE){target="_blank"}.


## Aktiva profiler {#active-profiles}

En aktiv profil är en profil som kunden har försökt kommunicera med under de senaste 12 månaderna via valfri kanal.

Enligt avtalet har var och en av instanserna i Campaign ett visst antal aktiva profiler som räknas för faktureringsändamål. Se ditt senaste kontrakt för referens om antalet köpta aktiva profiler. Läs mer i [Adobe Campaign produktbeskrivning](https://helpx.adobe.com/se/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Du kan övervaka antalet aktiva profiler på instansen direkt från Campaign-kontrollpanelen. Mer information finns i dokumentationen för [Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=sv-SE){target="_blank"}.


Följande skyddsräcken och begränsningar gäller:

* En profil som har valts av flera leveranser räknas bara en gång.
* Profiler som är inriktade på social marknadsföring på X (Twitter) räknas inte som aktiva profiler.
* Antalet baseras på mottagarens primärnyckel. Om det finns en profil i två olika mottagartabeller kan den därför räknas två gånger som en aktiv profil.

## Sekretess och medgivande{#privacy-and-consent}

Adobe Campaign är ett kraftfullt verktyg för att samla in och behandla stora datavolymer, inklusive personuppgifter och känsliga data. Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du erhåller och övervakar medgivande från dina mottagare.

Lär dig hur du hanterar sekretess och samtycke i [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html){target="_blank"}.

