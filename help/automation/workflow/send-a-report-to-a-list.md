---
product: campaign
title: Skicka en rapport till en lista
description: Lär dig hur du skickar en rapport till en lista med ett arbetsflöde
feature: Workflows
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 1%

---

# Skicka en rapport till en lista{#sending-a-report-to-a-list}



Här finns information om hur du skapar en månadsklar **[!UICONTROL Tracking indicators]** rapportera i PDF-format och skicka det till en lista med mottagare.

![](assets/use_case_report_intro.png)

De viktigaste implementeringsstegen för det här användningsexemplet är:

* Skapa en lista över mottagare som ska ta emot leveransen (se: [Steg 1: Skapa mottagarlistan](#step-1--creating-the-recipient-list)).
* Skapa en leveransmall som gör att du kan generera en ny leverans varje gång arbetsflödet körs (se: [Steg 2: Skapa leveransmallen](#step-2--creating-the-delivery-template)).
* Skapa ett arbetsflöde som gör att du kan generera rapporten i PDF-format och skicka den till mottagarlistan (se: [Steg 3: Skapa arbetsflödet](#step-3--creating-the-workflow)).

## Steg 1: Skapa mottagarlistan {#step-1--creating-the-recipient-list}

Gå till **[!UICONTROL Profiles and targets]** klickar du på **[!UICONTROL Lists]** länk, sedan **[!UICONTROL Create]** -knappen. Välj **[!UICONTROL New list]** och skapa en ny mottagarlista för rapporten som ska skickas till.

![](assets/use_case_report_1.png)

Mer information om hur du skapar listor finns i den här .

## Steg 2: Skapa leveransmallen {#step-2--creating-the-delivery-template}

1. Gå till **[!UICONTROL Resources > Templates > Delivery templates]** noden i Adobe Campaign Explorer och duplicera **[!UICONTROL Email delivery]** färdiga mallar.

   ![](assets/use_case_report_2.png)

   Mer information om hur du skapar en leveransmall finns i den här .

1. Ange de olika mallparametrarna: label, target (the list of earlier eived), subject and content.

   ![](assets/use_case_report_3.png)

1. Varje gång arbetsflödet körs **[!UICONTROL Tracking indicators]** rapporten uppdateras (se [Steg 3: Skapa arbetsflödet](#step-3--creating-the-workflow)). Om du vill inkludera den senaste versionen av rapporten i leveransen måste du lägga till en **[!UICONTROL Calculated attachment]**:

   Mer information om hur du skapar en beräknad bilaga finns i det här .

   * Klicka på **[!UICONTROL Attachments]** länk och klicka **[!UICONTROL Add]** väljer **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * Gå till **[!UICONTROL Type]** och välj det fjärde alternativet: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      Värdet som anges i **[!UICONTROL Label]** fältet visas inte i den slutliga leveransen.

   * Gå till redigeringszonen och ange filens åtkomstsökväg och namn.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >Filen måste finnas på servern. Sökvägen och namnet måste vara identiska med de som anges i **[!UICONTROL JavaScript code]** typ av aktivitet i arbetsflödet (se: [Steg 3: Skapa arbetsflödet](#step-3--creating-the-workflow)).

   * Välj **[!UICONTROL Advanced]** tabb och kontrollera **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Gå till redigeringszonen och ange det namn du vill ge den bifogade filen i den slutliga leveransen.

      ![](assets/use_case_report_6bis.png)

## Steg 3: Skapa arbetsflödet {#step-3--creating-the-workflow}

Följande arbetsflöde skapades för det här användningsfallet. Den har tre verksamheter:

* Ett **[!UICONTROL Scheduler]** typaktivitet som gör att du kan köra arbetsflödet en gång i månaden,
* Ett **[!UICONTROL JavaScript code]** typaktivitet som gör att du kan generera rapporten i PDF-format,
* en **[!UICONTROL Delivery]** typaktivitet som använder den leveransmall som skapades tidigare.

![](assets/use_case_report_8.png)

1. Gå till **[!UICONTROL Administration > Production > Technical workflows]** och skapa ett nytt arbetsflöde.

   ![](assets/use_case_report_7.png)

1. Börja med att lägga till en **[!UICONTROL Scheduler]** typaktivitet och konfigurera den så att arbetsflödet körs den första måndagen i månaden.

   ![](assets/use_case_report_9.png)

   Mer information om hur du konfigurerar schemaläggaren finns i [Schemaläggare](scheduler.md).

1. Lägg sedan till en **[!UICONTROL JavaScript code]** typaktivitet.

   ![](assets/use_case_report_10.png)

   Ange följande kod i redigeringszonen:

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   Följande variabler används:

   * **var reportName**: Ange rapportens interna namn med citattecken. I det här fallet är det interna namnet på **Spårningsindikator** rapporten är&quot;deliveryFeedback&quot;.
   * **var path**: Ange filens sparningssökväg (&quot;tmp/files/&quot;), det namn du vill ge filen (&quot;deliveryFeedback&quot;) och filnamnstillägget (&quot;.pdf&quot;). I det här fallet har vi använt det interna namnet som filnamn. Värdena måste vara mellan dubbla citattecken och avgränsade med plustecknet (+).

      >[!CAUTION]
      >
      >Filen måste sparas på servern. Du måste ange samma sökväg och samma namn i **[!UICONTROL General]** fliken i redigeringsfönstret för den beräknade bilagan (se: [Steg 2: Skapa leveransmallen](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: Ange exportformatet för filen (&quot;PDF&quot;).
   * **var _ctx** (kontext): i det här fallet använder vi **[!UICONTROL Tracking indicators]** rapportera i sitt globala sammanhang.

1. Slutför genom att lägga till en **[!UICONTROL Delivery]** typaktivitet med följande alternativ:

   * **[!UICONTROL Delivery]**: välj **[!UICONTROL New, created from a template]** och välj den leveransmall som skapades tidigare.
   * För **[!UICONTROL Recipients]** och **[!UICONTROL Content]** fält, markera **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**: välj **[!UICONTROL Prepare and start]**.
   * Avmarkera **[!UICONTROL Generate an outbound transition]** och **[!UICONTROL Process errors]**.
   ![](assets/use_case_report_11.png)
