---
product: campaign
title: Skapa marknadsföringskampanjer
description: Lär dig skapa och genomföra marknadsföringskampanjer
feature: Campaigns, Cross Channel Orchestration, Programs
role: User
exl-id: 90dd2dad-1380-490e-b958-4a28a7d930ed
source-git-commit: c3f4ad0b56dd45d19eebaa4d2f06551c8fecac1d
workflow-type: tm+mt
source-wordcount: '1327'
ht-degree: 2%

---

# Skapa program och kampanjer{#create-programs-and-campaigns}

Kampanjkoordinatkomponenter finns i **[!UICONTROL Campaigns]** här kan du se en översikt över marknadsföringsprogram och -kampanjer och deras associerade element.

Ett marknadsföringsprogram består av kampanjer, som består av leveranser, resurser osv. All information om leveranser, budgetar, granskare och länkade dokument grupperas i kampanjen.

![](assets/campaigns-create-from-home.png)

![](assets/do-not-localize/how-to-video.png) [Upptäck program och kampanjer i video](#video)

## Arbeta med program och planer{#work-with-plan-and-program}

### Skapa planerings- och programhierarkin {#create-plan-and-program}

Varje kampanj tillhör ett program som tillhör en plan. Alla planer, program och kampanjer är tillgängliga via **[!UICONTROL Campaign calendar]** i **Kampanjer** -fliken.

Konfigurera mapphierarkin för marknadsföringsplaner och program innan du börjar bygga kampanjer och leveranser.

1. Klicka på **Explorer** på startsidan.
1. Högerklicka på den mapp där du vill skapa din plan.
1. Välj **Lägg till ny mapp > Campaign Management > Plan**.

   ![](assets/create-new-plan-folder.png)

1. Byt namn på planen.
1. Högerklicka på den nya planen och välj **Egenskaper...**.
1. I **Allmänt** -fliken, ändra **Internt namn** för att undvika dubbletter vid paketexport.

   ![](assets/plan-properties.png)

1. Klicka **Spara**.
1. Högerklicka på den nya planen och välj **Skapa en ny programmapp**.

   ![](assets/program-folder.png)

1. Upprepa stegen ovan för att byta namn på den nya programmappen och dess interna namn.


### Konfigurera ett program {#edit-a-program}

När du redigerar ett program använder du flikarna nedan för att bläddra och konfigurera det.

* The **Schema** -fliken visar kalendern för program för en månad, vecka eller dag beroende på vilken flik du klickar på i kalenderrubriken. Du kan skapa en kampanj, ett program eller en uppgift från den här sidan. [Läs mer](#campaign-calendar)

* The **Redigera** kan du anpassa programmet: namn, start- och slutdatum, budget, länkade dokument osv.

  ![](assets/new-program-edit-tab.png)

## Arbeta med kampanjer{#work-with-campaigns}

### Skapa en kampanj {#create-a-campaign}

Du kan skapa en kampanj via listan med kampanjer. Om du vill visa den här vyn väljer du **[!UICONTROL Campaigns]** i **[!UICONTROL Campaigns]** kontrollpanelen och klicka på **[!UICONTROL Create]**.

The **[!UICONTROL Program]** kan du välja det program som kampanjen ska kopplas till. Denna information är obligatorisk.

![](assets/new-campaign-settings.png)

Kampanjer kan också skapas via kampanj- eller programkalendern. [Läs mer](#campaign-calendar)

Välj kampanjmallen och lägg till ett namn och en beskrivning av kampanjen i fönstret där kampanjen skapades. Du kan också ange kampanjens start- och slutdatum.

Klicka **[!UICONTROL OK]** för att skapa kampanjen. Det läggs till i programschemat och i listan över kampanjer.

Sedan kan du redigera kampanjen som du just har skapat och definiera dess parametrar. Om du vill öppna och konfigurera kampanjen kan du:

1. Bläddra i kampanjkalendern och välj den kampanj som du vill visa. Klicka sedan på **[!UICONTROL Open]** länk.
1. Sök i **[!UICONTROL Schedule]** väljer du kampanjen och öppnar den.
1. Bläddra i listan över kampanjer och klicka på namnet på kampanjen som ska redigeras.

Alla dessa åtgärder tar dig till kontrollpanelen för kampanjer.

![](assets/campaigns-dashboard-approve.png)

Gå till följande avsnitt för att lära dig hur du konfigurerar kampanjen:

* [Lägg till leveranser](marketing-campaign-deliveries.md)
* [Hantera resurser och dokument](marketing-campaign-assets.md)
* [Bygg målgruppen](marketing-campaign-target.md)
* [Ställ in godkännandeprocessen](marketing-campaign-approval.md)
* [Hantera lager och budgetar](providers-stocks-and-budgets.md)


### Redigera kampanjinställningar {#campaign-settings}

Kampanjer skapas via kampanjmallar. Du kan konfigurera återanvändbara mallar för vilka vissa alternativ har valts och andra inställningar redan har sparats.

För varje kampanj finns följande funktioner:

* Referensdokument och resurser: du kan associera dokument med kampanjen (i korthet, rapport, bilder osv.). Alla dokumentformat stöds. [Läs mer](marketing-campaign-deliveries.md#manage-associated-documents).
* Definiera kostnader: För varje kampanj kan Adobe Campaign definiera kostnadsposter och kostnadsberäkningsstrukturer som kan användas när marknadsföringskampanjen skapas. Exempel: tryckkostnader, användning av en extern byrå, rumshyrning osv. [Läs mer](providers-stocks-and-budgets.md#defining-cost-categories).
* Definiera mål: du kan definiera kvantifierbara mål för en kampanj, t.ex. antal prenumeranter, affärsvolym osv. Den här informationen används senare i kampanjrapporter.
* Hantera dirigerade adresser och kontrollgrupper. [Läs mer](marketing-campaign-deliveries.md#defining-a-control-group).
* Hantera godkännanden: du kan välja de behandlingar som ska godkännas och, om det behövs, välja granskningsoperatorer eller grupper av operatorer. [Läs mer](marketing-campaign-approval.md#checking-and-approving-deliveries).

>[!NOTE]
>
>Bläddra till **[!UICONTROL Advanced campaign parameters...]** i **[!UICONTROL Edit]** -fliken.

### Övervaka en kampanj {#monitor-a-campaign}

För varje kampanj finns jobb, resurser och leveranser centralt på kontrollpanelen. Med det här gränssnittet kan ni hantera och samordna marknadsföringsåtgärder.

Med Adobe Campaign kan ni skapa samarbetsprocesser för att skapa och godkänna de olika stegen i era kampanjer: godkännande av budget, mål, innehåll osv. Den här orkestrationen beskrivs i [det här avsnittet](marketing-campaign-approval.md).

![](assets/campaigns-dashboard-approval-tab.png)

>[!NOTE]
>
>Vilka komponenter som är tillgängliga i en kampanj beror på dess mall. Kampanjmallskonfigurationen presenteras i [det här avsnittet](marketing-campaign-templates.md#campaign-templates).

När kampanjen är klar använder du **[!UICONTROL Reports]** länk för att komma åt kampanjrapporterna.

![](assets/campaigns-reports-dashboard.png)

## Kampanjkalender {#campaign-calendar}

Kampanjkalendern innehåller alla program, planer, kampanjer och leveranser.

Om du vill redigera en plan, ett program, en kampanj eller en leverans bläddrar du till namnet i kalendern och använder sedan kommandot **[!UICONTROL Open]** länk. Den visas sedan på en ny flik, enligt nedan:

![](assets/campaign-calendar.png)

Du kan filtrera den information som visas i kampanjkalendern. Klicka på **[!UICONTROL Filter]** och välj filtreringsvillkor.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>När du filtrerar på ett datum visas alla kampanjer med ett startdatum som är senare än det angivna datumet och/eller med ett slutdatum som är tidigare än det angivna datumet. Datum markeras med hjälp av kalendrarna till höger om varje fält.

Du kan också använda **[!UICONTROL Search]** för att filtrera de visade objekten.

Med ikonerna som är länkade till varje objekt kan du visa objektets status: färdig, pågående, redigerad osv.

Om du vill filtrera kampanjer som ska visas klickar du på **[!UICONTROL Filter]** och välj status för de kampanjer som ska visas.

![](assets/calendar-filter-options.png)

När du bläddrar i kalendern kan du även skapa ett program eller en kampanj.

![](assets/campaign-create-from-calendar.png)

När du skapar en kampanj via **[!UICONTROL Schedule]** under ett program kopplas kampanjen automatiskt till det berörda programmet. The **[!UICONTROL Program]** fältet är dolt i det här fallet.


## Öppna Campaign med en webbläsare {#use-the-web-interface}


>[!AVAILABILITY]
>
>Från och med Campaign v8.6 är Campaign tillgängligt i ett webbanvändargränssnitt. De flesta marknadsföringsåtgärder kan utföras från det nya gränssnittet. [Läs mer](../../v8/start/campaign-ui.md#discover-the-user-interface).

Du kan komma åt vissa av Adobe Campaign klientkonsolskärmar via en webbläsare för att visa alla kampanjer och leveranser samt rapporter och information om profilerna i din databas. Du kan inte skapa komponenter från den här webbåtkomsten, men beroende på åtkomstbehörighet kan du visa och/eller agera utifrån data i databasen. Normalt kan ni godkänna kampanjinnehåll och målinriktning, starta om eller stoppa en leverans osv.

1. Logga in som vanligt via https://`<your instance>:<port>/view/home`.
1. Använd menyerna för att komma åt översikterna.

   ![](assets/web-access-campaigns.png)

Förutom att navigera mellan kampanjer och visa dem kan du utföra följande typer av uppgifter:

* Övervaka aktivitet i en instans
* Delta i valideringsprocesser, till exempel godkänna eller avvisa ett leveransinnehåll
* Utför andra snabbåtgärder, till exempel pausa ett arbetsflöde
* Få tillgång till alla rapportfunktioner
* Delta i forumdiskussioner

I tabellen sammanfattas de åtgärder du kan vidta i kampanjer från en webbläsare:

| Sida  | Åtgärd |
| --- | --- |
| Lista över kampanjer, leveranser, erbjudanden osv. | Ta bort ett listobjekt |
| Campaign | Avbryta en kampanj |
| Leverans | Godkänn leveransinnehållet och målet<br/>Skicka leveransinnehållet<br/>Bekräfta leverans<br/>Pausa och stoppa leverans |
| Webbprogram | Skapa ett webbprogram<br/>Redigera programinnehåll och -egenskaper<br/>Spara programinnehållet som en mall<br/>Publicera programmet |
| Erbjudande | Godkänn erbjudandets innehåll och behörighet<br/>Inaktivera ett onlineerbjudande |
| Uppgift | Avsluta en uppgift<br/>Avbryt en uppgift |
| Marknadsföringsresurser | Godkänn en resurs<br/>Låsa och låsa upp en resurs |
| Kampanjpaket | Skicka ett paket för godkännande<br/>Godkänn eller avvisa ett paket<br/>Avbryt ett paket |
| Kampanjorder | Skapa en order<br/>Acceptera eller avvisa en order |
| Stock | Ta bort en aktierad |
| Simulering av erbjudanden | Starta och stoppa en simulering |
| Målarbetsflöde | Starta, pausa och stoppa ett arbetsflöde |
| Rapport | Spara aktuella data i rapporthistoriken |
| Forum | Lägg till en diskussion<br/>Svara på ett meddelande i en diskussion<br/>Följ en diskussion och avsluta prenumerationen på den |

### Hantera godkännanden

Godkännanden av ett mål eller ett leveransinnehåll kan göras via webbåtkomst.

![](assets/web-access-approval.png)

Du kan också använda länken i meddelandena. Mer information om detta finns i [det här avsnittet](marketing-campaign-approval.md#checking-and-approving-deliveries).


## Självstudievideo {#video}

Den här videon visar hur du skapar en marknadsföringsplan, ett program och en kampanj.

>[!VIDEO](https://video.tv.adobe.com/v/333810?quality=12)
