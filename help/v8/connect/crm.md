---
title: Arbeta med Campaign och CRM
description: Lär dig hur du arbetar med Campaign och CRM
feature: Overview
role: Data Engineer
level: Beginner
exl-id: c2d34ee9-4427-48e7-a8cf-0ae02a801d50
source-git-commit: 79a9d60175b06a11cf27b44275a8ba3fe11e4d3e
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 17%

---

# Koppla samman CRM med Campaign {#gs-crm}

Adobe Campaign tillhandahåller olika CRM-kopplingar för att länka din plattform i Adobe Campaign till dina tredjepartssystem. Med dessa CRM-kopplingar kan du synkronisera kontakter, konton och inköp osv. De låter dig enkelt integrera din applikation med olika tredjeparts- och företagsapplikationer.

Dessa kopplingar möjliggör snabb och enkel dataintegrering: Adobe Campaign tillhandahåller en dedikerad assistent för att samla in och välja bland tabellerna i CRM. Detta garanterar dubbelriktad synkronisering för att säkerställa att data alltid är aktuella i alla system.

De viktigaste fördelarna är:

* Enhetliga meddelanden mellan försäljning och marknadsföring: Adobe Campaign integrering med CRM ger både systemåtkomst till kundinsikter och marknadshistorik via e-post så att alla meddelanden till kunden kan dela samma enhetliga budskap.

* Holistisk bild av alla potentiella kunder och kunddata: genom att integrera Adobe Campaign med CRM-systemen kan ni dela och få tillgång till marknadshistorik via e-post för varje kontakt i CRM-systemet.

* Aktivera dina CRM-data i valfri kanal: med kontaktdata synkroniserade med Adobe Campaign kan kommunikationen skickas via valfri online- eller offlinekanal med Campaign, inklusive mobil-push, app-kommunikation, e-post eller direktreklam.


>[!NOTE]
>
>Den här funktionen är tillgänglig i Adobe Campaign via **CRM-anslutningar** dedikerat paket.

## Kompatibla system {#compatible-crm-systems-and-limitations}

CRM och versioner som stöds finns detaljerade i Campaign [Kompatibilitetsmatris](../start/compatibility-matrix.md).

![](../assets/do-not-localize/speech.png)  CRM-anslutningarna fungerar bara med en säker URL (https).

## Implementeringssteg {#crm-implementation-steps}

Lär dig steg för steg hur du ansluter Campaign och Microsoft Dynamics i [den här sidan](ac-ms-dyn.md).

Lär dig steg för steg hur du ansluter Campaign och Salesforce.com i [den här sidan](ac-sfdc.md).

Datasynkronisering mellan Adobe Campaign och CRM utförs via en dedikerad arbetsflödesaktivitet. Bygg era arbetsflöden för att automatisera synkroniseringen mellan Campaign och CRM. Du kan skapa ett arbetsflöde som importerar kontakter via Microsoft Dynamics, synkroniserar dem med befintliga Adobe Campaign-data, tar bort dubblettkontakter och sedan uppdaterar Adobe Campaign-databasen.

![](../assets/do-not-localize/book.png) Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/connectors/crm-connectors/crm-data-sync.html?lang=en#getting-started)
