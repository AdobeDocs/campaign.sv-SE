---
product: Adobe Campaign
title: Kom igång med profiler
description: Kom igång med profiler
feature: Profiler
role: Data Engineer
level: Beginner
exl-id: b0f8c057-dd4e-4284-b5a4-157986a1d95a
source-git-commit: 5363950db5092bc7e0a72a0823db1132a17dda33
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 2%

---

# Importera data till Campaign {#ootb-profiles}

Med Campaign kan du lägga till kontakter i molndatabasen. Du kan läsa in en fil, schemalägga och automatisera flera kontaktuppdateringar, samla in data på webben eller ange profilinformation direkt i mottagartabellen.

[!DNL :bulb:] Kom igång med  [](audiences.md)
[!DNL :bulb:] målgrupperFörstå Campaign- [datamodellen](../dev/datamodel.md)

## Importera profiler i ett arbetsflöde

Profilimport konfigureras i dedikerade mallar som körs via arbetsflöden via aktiviteten **Importera**. De kan upprepas automatiskt enligt ett schema, t.ex. för att automatisera datautbyte mellan olika informationssystem. Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/import-export-workflows.html).

![](assets/import-wf.png)

Läs mer i Campaign Classic v7-dokumentationen:

[!DNL :arrow_upper_right:] [Kom igång med import och export](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/get-started-data-import-export.html)

[!DNL :arrow_upper_right:] [Bästa praxis för import och export](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/best-practices/import-export-best-practices.html)

[!DNL :arrow_upper_right:] [Konfigurera och köra en import](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/generic-imports-exports/executing-import-jobs.html)

## Kör enhetsimporter

Skapa och kör ett allmänt dataimportjobb för att läsa in kontakter i molndatabasen.

![](assets/new-import.png)

[!DNL :arrow_upper_right:] Lär dig hur du kör enhetsimportjobb för att mata in din databas i  [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/generic-imports-exports/about-generic-imports-exports.html).

## Samla in profiler via webbprogram

Använd Campaign för att skapa webbformulär och samla in och hantera profilinformation enkelt och effektivt. Du kan dela dessa formulär på din webbplats, vilket gör det enkelt för dina kontakter att lämna sina uppgifter. Deras information skickas till Campaign för att skapa deras profil eller uppdatera deras information om de redan finns i databasen.

![](assets/web-form-page.png)

[!DNL :arrow_upper_right:] Lär dig hur du skapar webbformulär i  [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/about-web-forms.html).

**Relaterade ämnen**

* [Skapa målgrupper](audiences.md)
* [Deduplicera profiler](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html)
* [Förbättra profildata](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/enriching-data.html)
