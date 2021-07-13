---
product: Adobe Campaign
title: Arbeta med Campaign och CRM
description: 'Lär dig hur du arbetar med Campaign och CRM '
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: c61d8aa8e0a68ccc81a6141782f860daf061bc61
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 22%

---

# Koppla samman CRM med Campaign {#gs-crm}

Adobe Campaign tillhandahåller olika CRM-kopplingar för att länka din plattform i Adobe Campaign till dina tredjepartssystem. Med dessa CRM-kopplingar kan du synkronisera kontakter, konton och inköp osv. De låter dig enkelt integrera din applikation med olika tredjeparts- och företagsapplikationer.

Dessa kopplingar möjliggör snabb och enkel dataintegrering: Adobe Campaign tillhandahåller en dedikerad assistent för att samla in och välja bland tabellerna i CRM. Detta garanterar dubbelriktad synkronisering för att säkerställa att data alltid är aktuella i alla system.

>[!NOTE]
>
>Den här funktionen är tillgänglig i Adobe Campaign via **CRM-anslutningarna** dedikerade paket.

## Kompatibla system {#compatible-crm-systems-and-limitations}

CRM och versioner som stöds finns detaljerade i Campaign [Kompatibilitetsmatrisen](../start/compatibility-matrix.md).

? CRM-anslutningarna fungerar bara med en säker URL (https).

## Implementeringssteg {#crm-implementation-steps}

↗️ Lär dig steg för steg hur du ansluter Campaign och Microsoft Dynamics i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/connectors/crm-connectors/crm-ms-dynamics.html?lang=en#microsoft-dynamics-implementation-steps)

↗️ Lär dig steg för steg hur du ansluter Campaign och Salesforce i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/connectors/crm-connectors/crm-sfdc.html?lang=en#getting-started)


Datasynkronisering mellan Adobe Campaign och CRM utförs via en dedikerad arbetsflödesaktivitet. Bygg era arbetsflöden för att automatisera synkroniseringen mellan Campaign och CRM. Du kan skapa ett arbetsflöde som importerar kontakter via Microsoft Dynamics, synkroniserar dem med befintliga Adobe Campaign-data, tar bort dubblettkontakter och sedan uppdaterar Adobe Campaign-databasen.

↗️ Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/connectors/crm-connectors/crm-data-sync.html?lang=en#getting-started)

