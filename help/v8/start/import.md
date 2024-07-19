---
title: Kom igång med profiler
description: Kom igång med profiler
feature: Profiles, Data Management
role: User
level: Beginner
exl-id: b0f8c057-dd4e-4284-b5a4-157986a1d95a
source-git-commit: 061197048885a30249bd18af7f8b24cb71def742
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 3%

---

# Importera data till Campaign {#ootb-profiles}

Med Campaign kan du lägga till kontakter i molndatabasen. Du kan läsa in en fil, schemalägga och automatisera flera kontaktuppdateringar, samla in data på webben eller ange profilinformation direkt i mottagartabellen.

Kom igång med [målgrupper](audiences.md)

Förstå kampanj [datamodell](../dev/datamodel.md)

## Importera profiler i ett arbetsflöde

Profilimport konfigureras i dedikerade mallar som körs via arbetsflöden via aktiviteten **Importera**. De kan upprepas automatiskt enligt ett schema, t.ex. för att automatisera datautbyte mellan olika informationssystem. Läs mer i [det här avsnittet](../../automation/workflow/recurring-import-workflow.md).

![](assets/import-wf.png)


## Kör enhetsimporter

Skapa och kör ett allmänt dataimportjobb för att läsa in kontakter i molndatabasen.

![](assets/new-import.png)

Lär dig hur du kör enhetsimportjobb för att mata in din databas i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/importing-and-exporting-data/generic-imports-exports/about-generic-imports-exports.html){target="_blank"}.

## Samla in profiler via webbprogram

Använd Campaign för att skapa webbformulär och samla in och hantera profilinformation enkelt och effektivt. Du kan dela dessa formulär på din webbplats, vilket gör det enkelt för dina kontakter att lämna sina uppgifter. Deras information skickas till Campaign för att skapa deras profil eller uppdatera deras information om de redan finns i databasen.

![](assets/web-form-page.png)

Lär dig hur du skapar webbformulär i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/about-web-forms.html){target="_blank"}.

**Relaterade ämnen**

* [Skapa målgrupper](audiences.md)
* [Deduplicera profiler](../../automation/workflow/deduplication-merge.md)
* [Förbättra profildata](../../automation/workflow/enrich-data.md)
