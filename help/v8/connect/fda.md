---
title: Arbeta med Campaign och externa databaser (FDA)
description: Lär dig hur du arbetar med Campaign och externa databaser
feature: Federated Data Access
role: Data Engineer
level: Beginner
exl-id: 0259b3bd-9dc2-44f9-a426-c4af46b00a4e
source-git-commit: ca9275017e36dae2f0152e0ff365541d7cab96de
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 1%

---

# Federerad dataåtkomst (FDA){#gs-fda}

Använd FDA Connector (Federated Data Access) för att ansluta Campaign till en eller flera **externa databaser** och bearbeta information som lagras i dem utan att påverka data i Campaign Cloud-databasen. Sedan kan du komma åt externa data utan att ändra strukturen på Adobe Campaign-data.

![](../assets/do-not-localize/speech.png)   Som användare av hanterade Cloud Services [kontakta Adobe](../start/campaign-faq.md#support) för att ansluta externa databaser till Campaign.


>[!NOTE]
>
>* Kompatibla databaser för Federated Data Access listas i [Kompatibilitetsmatris](../start/compatibility-matrix.md).
>
>* När det gäller [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), finns det ett specifikt externt konto för att hantera kommunikationen mellan den lokala databasen i Campaign och molndatabasen i Snowflake. Det här externa kontot har konfigurerats för dig av Adobe och **får inte** ändras.
>



## God praxis och begränsningar

FDA-alternativet begränsas av det tredjepartsdatabassystem som du använder.

Tänk dessutom på följande begränsningar och bästa metoder:

* FDA-alternativet används för att ändra data i externa databaser i batchläge i arbetsflöden. För att undvika prestandaproblem rekommenderar vi inte att du använder FDA-modulen i samband med enhetsåtgärder som: personalisering, interaktion, meddelanden i realtid osv.

* Undvik de åtgärder som behöver använda både Adobe Campaign och den externa databasen så mycket som möjligt. Om du vill göra det kan du:

   * Exportera Adobe Campaign-databasen till den externa databasen och kör åtgärderna endast från den externa databasen innan du importerar resultaten till Adobe Campaign igen.

   * Samla in data från den externa Adobe Campaign-databasen och kör åtgärderna lokalt.
   Om du vill utföra personalisering i leveranser med data från den externa databasen, samlar du in data som ska användas i ett arbetsflöde för att göra dem tillgängliga i en tillfällig tabell. Använd sedan data från den tillfälliga tabellen för att anpassa leveransen. Om du vill utföra detta förbearbetar du meddelandepersonalisering i ett dedikerat arbetsflöde med **[!UICONTROL Prepare the personalization data with a workflow]** alternativ, finns i **[!UICONTROL Analysis]** -fliken för leveransegenskaperna. Under leveransanalysen skapar och kör det här alternativet automatiskt ett arbetsflöde som lagrar alla data som är länkade till målet i en tillfällig tabell, inklusive data från tabeller som är länkade i en extern databas.

   >[!CAUTION]
   >
   >Det här alternativet förbättrar prestanda avsevärt när personaliseringssteget körs.


## Använd externa data i ett arbetsflöde

Campaign innehåller flera arbetsflödesaktiviteter som du kan använda för att interagera med data från dina externa databaser:

* **Filtrera på externa data** - Använd **[!UICONTROL Query]** -aktivitet för att lägga till externa data och använda dem i definierade filterkonfigurationer.

* **Skapa underuppsättningar** - Använd **[!UICONTROL Split]** för att skapa delmängder. Du kan använda externa data för att definiera de filtervillkor som ska användas.

* **Läs in extern databas** - Använd externa data i **[!UICONTROL Data loading (RDBMS)]** aktivitet.

* **Lägga till information och länkar** - Använd **[!UICONTROL Enrichment]** -aktivitet för att lägga till ytterligare data i arbetsflödet och länkar till en extern tabell. I det här sammanhanget kan den använda data från en extern databas.

Du kan också definiera en anslutning till en extern databas direkt från alla arbetsflödesaktiviteter som listas ovan, för tillfällig användning. I det här fallet kommer den att finnas i en lokal extern databas som endast ska användas i det aktuella arbetsflödet.

>[!CAUTION]
>
>Den här typen av konfiguration får endast användas temporärt för att samla in data. Konfiguration av det externa kontot bör föredras för all annan användning.

I **[!UICONTROL Query]** -aktiviteten kan du definiera en tillfällig anslutning till en extern databas enligt följande:

1. Öppna aktiviteten och klicka på **[!UICONTROL Add data...]**
1. Välj **[!UICONTROL External data]** alternativ
1. Välj **[!UICONTROL Locally defining the data source]** option
1. Välj måldatabasmotorn i listrutan. Ange namnet på servern och ange autentiseringsparametrarna. Ange också namnet på den externa databasen.
1. Markera tabellen där data lagras. Du kan ange namnet på tabellen direkt i motsvarande fält eller klicka på redigeringsikonen för att öppna listan med databastabeller.
1. Klicka på **[!UICONTROL Add]** för att definiera ett eller flera avstämningsfält mellan externa databasdata och data i Adobe Campaign-databasen. The **[!UICONTROL Edit expression]** ikoner för **[!UICONTROL Remote field]** och **[!UICONTROL Local field]** ger dig tillgång till listan med fält i varje tabell.
1. Om det behövs anger du ett filtreringsvillkor och datasorteringsläget.
1. Välj de ytterligare data som ska samlas in i den externa databasen. Det gör du genom att dubbelklicka på de fält som du vill lägga till för att visa dem i **[!UICONTROL Output columns]**.
1. Klicka **[!UICONTROL Finish]** för att bekräfta konfigurationen.
