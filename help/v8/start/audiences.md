---
product: Adobe Campaign
title: Kom igång med målgrupper
description: Kom igång med målgrupper
feature: Målgrupper
role: Data Engineer
level: Beginner
exl-id: 07baa759-fb0b-4eba-bf8b-ec6cf21df7f8
source-git-commit: 0566d40370a3e14d5205861509f7c1ae8cb4b22d
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 19%

---

# Kom igång med målgrupper{#gs-ac-audiences}

## Arbeta med profiler{#gs-ac-profiles}

Profiler är kontakter som lagras i Campaign-databasen, inklusive kunder, prenumeranter och potentiella kunder. Det finns många sätt att förvärva profiler och bygga upp databasen: insamling online via webbformulär, manuell eller automatisk import av textfiler, replikering med företagsdatabaser eller andra informationssystem. Med Adobe Campaign kan ni införliva marknadsföringshistorik, inköpsinformation, preferenser, CRM-data och alla relevanta PI-data i en samlad vy för att analysera och vidta åtgärder. Profilerna innehåller all information som krävs för att målinrikta, kvalificera och spåra individer.

En profil är en post i tabellen **nmsRecipient** eller en extern tabell som lagrar alla profilattribut, t.ex. förnamn, efternamn, e-postadress, cookie-ID, kund-ID, mobilidentifierare eller annan information som är relevant för en viss kanal. Andra tabeller som är länkade till mottagartabellen innehåller profilrelaterade data, till exempel leveransloggtabellen som innehåller poster för alla leveranser som skickas till mottagare. Läs mer om inbyggda profiler och mottagartabeller i [det här avsnittet](../dev/datamodel.md#ootb-profiles).

I Adobe Campaign är **mottagare** standardprofiler för att skicka leveranser (e-post, SMS osv.). Med mottagardata som lagras i databasen kan du filtrera målet som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

Profiler kan grupperas i listor eller samlas in genom att fråga databasen.


Om du vill fylla i Campaign med profildata kan du:

* [importera datafiler ](import.md) från en extern datakälla, t.ex. ett CRM-system
* [skapa webbformulär ](../dev/webapps.md) så att kunderna kan ange sin egen information och skapa en egen profil
* [mappa till en extern ](../connect/fda.md) databas där profiler lagras
* ange profiler manuellt med hjälp av klientkonsolen enligt nedan:

![](assets/create-profile.png)


[!DNL :arrow_upper_right:] Lär dig hur du hanterar profiler i  [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/profile-management/about-profiles.html){target=&quot;_blank&quot;}.


## Sekretess och medgivande

Adobe Campaign är ett kraftfullt verktyg för att samla in och behandla stora datavolymer, inklusive personuppgifter och känsliga data. Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du erhåller och övervakar medgivande från dina mottagare.

[!DNL :arrow_upper_right:] Lär dig hur du hanterar sekretess och samtycke i  [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-and-recommendations.html){target=&quot;_blank&quot;}.

## Skapa listor

En lista är en statisk uppsättning profiler som kan användas för leveransåtgärder eller uppdateras under importåtgärder eller under arbetsflödeskörning. En grupp som har extraherats från databasen via en fråga kan till exempel innehålla en lista.

[!DNL :arrow_upper_right:] Lär dig hur du skapar och hanterar listor i  [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/profile-management/creating-and-managing-lists.html){target=&quot;_blank&quot;}.

## Fråga databasen

Använd aktiviteten **Fråga** i ett arbetsflöde för att fråga databasen, segmentera data och skapa komplexa målgrupper.

[!DNL :arrow_upper_right:] Läs mer om Campaign-frågor i  [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/targeting-data.html){target=&quot;_blank&quot;}.

[!DNL :arrow_upper_right:] Alla målinriktningsaktiviteter listas i  [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/about-targeting-activities.html){target=&quot;_blank&quot;}.

## Skapa en målgrupp i ett arbetsflöde

Målinriktning kan skapas med en kombination av frågor i en grafisk sekvens i ett arbetsflöde. Ni kan skapa målgrupper som anpassas efter era behov. Om du vill visa arbetsflödesredigeraren klickar du på fliken **[!UICONTROL Targeting and workflows]** på kontrollpanelen för kampanjer.

[!DNL :arrow_upper_right:] Lär dig hur du skapar en målgrupp i ett kampanjarbetsflöde i  [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-target.html?lang=en#building-the-main-target-in-a-workflow){target=&quot;_blank&quot;}.


## Aktiva profiler{#active-profiles}

Enligt avtalet har var och en av instanserna i Campaign ett visst antal aktiva profiler som räknas för faktureringsändamål. Se ditt senaste avtal som referens om antalet köpta aktiva profiler.

**En** informationspost (t.ex.: en post i  [mottagartabellen ](../dev/datamodel.md) eller en extern tabell som innehåller ett cookie-ID, Kund-ID, mobilidentifierare eller annan information som är relevant för en viss kanal) som representerar en slutkund, potentiell kund eller lead. Profiler anses vara aktiva om de har riktats eller kommunicerats via någon kanal under de senaste tolv månaderna.

<!--
You can monitor the number of active profiles used on your instances directly from Campaign Control Panel. 

[!DNL :arrow_upper_right:] For more on this, refer to the [Control Panel documentation](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/active-profiles-monitoring.html).
-->

**Dokumentation** för närliggande ämnen i Campaign Classic v7:

[!DNL :arrow_upper_right:] [Utforma och kör ett kampanjspecifikt arbetsflöde](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/building-a-workflow.html){target=&quot;_blank&quot;}

[!DNL :arrow_upper_right:] [Lär dig hur du väljer publik för en kampanj](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-target.html){target=&quot;_blank&quot;}

[!DNL :arrow_upper_right:] [Kom igång med arbetsflöden](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/introduction/about-workflows.html){target=&quot;_blank&quot;}
