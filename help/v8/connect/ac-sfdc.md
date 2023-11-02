---
title: Arbeta med Campaign och SFDC
description: Lär dig arbeta med Campaign och Salesforce.com
feature: Salesforce Integration
role: Admin, User
level: Beginner, Intermediate
exl-id: 1e20f3b9-d1fc-411c-810b-6271360286f9
source-git-commit: f577ee6d303bab9bb07350b60cf0fa6fc9d3a163
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Arbeta med Campaign och SFDC{#crm-sfdc}

Lär dig hur du konfigurerar Campaign CRM-kopplingen för att ansluta Campaign v8 till **Salesforce.com**.

När konfigurationen är klar utförs datasynkronisering mellan system via en dedikerad arbetsflödesaktivitet. [Läs mer](crm-data-sync.md).

>[!NOTE]
>
>SFDC-versioner som stöds finns detaljerade i Campaign [Kompatibilitetsmatris](../start/compatibility-matrix.md).

Följ stegen nedan för att konfigurera ett dedikerat externt konto för att importera och exportera Salesforce-data till Adobe Campaign.

## Skapa anslutningen{#new-sfdc-external-account}

Först måste du skapa det externa Salesforce-kontot.

1. Sök i **[!UICONTROL Administration > Platform > External accounts]** noden i Campaign Explorer och skapa ett externt konto.
1. Välj **[!UICONTROL Salesforce.com]** externt konto i **Typ** -avsnitt.
1. Ange inställningar för att aktivera anslutningen.

   ![](assets/sfdc-external-account.png)

   Om du vill konfigurera det externa Salesforce CRM-kontot så att det fungerar med Adobe Campaign måste du ange följande information:

   * Ange din Salesforce-inloggning i dialogrutan **[!UICONTROL Account]** fält.
   * Ange ditt Salesforce-lösenord.
   * Du kan ignorera **[!UICONTROL Client identifier]** fält.
   * Kopiera/klistra in Salesforce **[!UICONTROL Security token]**
   * Välj **[!UICONTROL API version]**. SFDC API-versioner som stöds listas i Campaign [Kompatibilitetsmatris](../start/compatibility-matrix.md).

1. Välj **Aktivera** möjlighet att aktivera kontot i Campaign.

>[!NOTE]
>
>Om du vill godkänna konfigurationen måste du logga ut och sedan logga in på Adobe Campaign Client Console igen.

## Markera tabeller som ska synkroniseras{#sfdc-create-tables}

Nu kan du konfigurera tabeller att synkronisera.

1. Klicka på **[!UICONTROL Salesforce CRM configuration wizard...]**.
1. Markera de tabeller som ska synkroniseras och starta processen.
1. Kontrollera schemat som genererats i Adobe Campaign i **[!UICONTROL Administration > Configuration > Data schemas]** nod.

   Exempel på en **Salesforce** schema importerat i kampanj:

   ![](assets/sfdc-schemas.png)

## Synkronisera uppräkningar{#sfdc-enum-sync}

När schemat har skapats kan du synkronisera uppräkningar automatiskt från Salesforce till Adobe Campaign.

1. Öppna assistenten från  **[!UICONTROL Synchronizing enumerations...]** länk.
1. Välj den Adobe Campaign-uppräkning som matchar Salesforce-uppräkningen.
Du kan ersätta alla värden i en Adobe Campaign-uppräkning med dem i CRM: om du vill göra det väljer du **[!UICONTROL Yes]** i **[!UICONTROL Replace]** kolumn.

   ![](assets/sfdc-enum.png)

1. Klicka **[!UICONTROL Next]** och sedan **[!UICONTROL Start]** för att börja importera uppräkningarna.

1. Sök i **[!UICONTROL Administration > Platform > Enumerations]** nod för att kontrollera importerade värden. Läs mer om uppräkningar i [den här sidan](../config/ui-settings.md#enumerations).

Adobe Campaign och Salesforce.com är nu anslutna. Du kan konfigurera datasynkronisering mellan de två systemen.

Om du vill synkronisera data mellan Adobe Campaign data och SFDC skapar du ett arbetsflöde och använder **[!UICONTROL CRM connector]** aktivitet.

Läs mer om datasynkronisering [på den här sidan](crm-data-sync.md).
