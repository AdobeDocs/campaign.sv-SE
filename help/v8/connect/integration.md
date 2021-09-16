---
title: Koppla samman Campaign med era lösningar
description: Lär dig hur ni kan koppla Campaign till era lösningar
feature: Overview
role: Data Engineer
level: Beginner
exl-id: d1d57aa8-b811-470f-a8a6-18da3a700f1a
source-git-commit: f071fc227dac6d72873744ba56eb0b4b676de5dd
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 10%

---

# Koppla samman Campaign med era lösningar{#gs-ac-connectors}

Du kan koppla din Campaign-instans till Adobe Experience Cloud lösningar för att kombinera funktioner.

Adobe Campaign har flera kopplingar som gör att du kan kommunicera med externa program, ansluta till databasmotorer, dela och synkronisera data.

## Utnyttja Adobe lösningar {#gs-ac-integration}

Modernisera implementeringen och utnyttja alla Adobe Experience Cloud-funktioner.

? Som användare av hanterade Cloud Services ska du [kontakta Adobe](../start/campaign-faq.md#support) för att ansluta Campaign till Adobe Experience Cloud tjänster och lösningar.

Campaign v8 kan kommunicera med:


* [Adobe Experience Cloud Real-Time CDP](../connect/ac-rtcdp.md)
* [Adobe Journey Orchestration](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=en).

   Se det fullständiga användningsexemplet [här](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=sv).

* [Adobe Analytics](../connect/ac-aa.md)
* [Adobe Experience Manager](../connect/ac-aem.md)
* [Adobe Experience Cloud-utlösare](../connect/ac-triggers.md)
* [Adobe Target](../connect/ac-at.md)

Du kan också kombinera dina **målgrupper** och **resurser** mellan olika Experience Cloud-lösningar med funktioner för resursdelning och målgruppsdelning.

↗️ Läs mer om **målgruppsdelning** mellan Campaign- och Experience Cloud-lösningar i [dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/audience-sharing/sharing-audiences-with-adobe-experience-cloud.html?lang=en#integrating-with-adobe-experience-cloud)

↗️ Läs mer om **Resursdelning** mellan Campaign- och Experience Cloud-lösningar i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/asset-sharing/sharing-assets-with-adobe-experience-cloud.html?lang=en#integrating-with-adobe-experience-cloud)

## CRM-kopplingar{#gs-crm-connectors}

Du kan ansluta din Adobe Campaign-plattform till dina **CRM-system från tredje part** och synkronisera data: kontakter, konton, inköp osv.

Aktivera dina CRM-data för kommunikation över flera kanaler: Lär dig hur du skickar kontakter från CRM-systemet till Adobe Campaign och delar kampanjdata från Adobe Campaign till CRM-systemet.
CRM-anslutningar möjliggör snabb och enkel dataintegrering: Adobe Campaign tillhandahåller en dedikerad assistent för att samla in och välja bland tabellerna i CRM. Detta garanterar dubbelriktad synkronisering för att säkerställa att data alltid är aktuella i alla system.

? Lär dig hur du integrerar Campaign med Microsoft Dynamics 365 och Salesforce.com i [den här sidan](crm.md)

## Federerad dataåtkomst (FDA){#gs-fda}

Använd FDA Connector (Federated Data Access) för att ansluta Campaign till en eller flera **externa databaser** och bearbeta information som lagras i dem utan att påverka data i Campaign Cloud-databasen.

? Läs mer i [den här sidan](fda.md)


<!-- 
 ## Integrate with social media

Use the **Managing social networks (Social Marketing)** option to interact with customers and prospects via Twitter.

* Send messages - Use Adobe Campaign Social Marketing to send messages on Twitter. Adobe Campaign lets you post messages directly to your twitter account. You can also send direct messages to all your followers.

* Collect new contacts - Adobe Campaign Social Marketing also makes it easy to acquire new contacts via Facebook: contact users and ask them if they want to share their profile information. If they accept, Adobe Campaign automatically recovers the data, which enables you to carry out targeting campaigns and, when possible, to implement cross-channel strategies.

💡 Learn how to set up and use Campaign Social Marketing in [this section](../connect/ac-tw.md) -->