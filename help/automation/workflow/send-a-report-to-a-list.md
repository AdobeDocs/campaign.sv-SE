---
product: campaign
title: Skicka en rapport till en lista
description: Lär dig hur du skickar en rapport till en lista med ett arbetsflöde
feature: Workflows
source-git-commit: 4c3caa8e31c2076d32a03a8778a28edce50cde63
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 3%

---


# Skicka en rapport till en lista{#send-a-report-to-a-list}

Här finns information om hur du skapar en månadsklar **[!UICONTROL Tracking indicators]** rapportera i PDF-format och skicka det till en lista med mottagare.

![](assets/use_case_report_intro.png)

De viktigaste implementeringsstegen för det här användningsexemplet är:

* Skapa en lista med mottagare för den här rapporten. [Läs mer](#step-1--create-the-recipient-list).
* Skapa en leveransmall som skapar en ny leverans varje gång arbetsflödet körs. [Läs mer](#step-2--create-the-delivery-template).
* Skapa ett arbetsflöde som genererar rapporten i PDF-format och skickar den till mottagarlistan. [Läs mer](#step-3--create-the-workflow)).

## Steg 1: Skapa mottagarlistan {#step-1--create-the-recipient-list}

Följ stegen nedan om du vill skapa en lista med mottagare som mål:

1. Bläddra till **[!UICONTROL Profiles and targets]** klickar du på **[!UICONTROL Lists]** länk.
1. Klicka på knappen **[!UICONTROL Create]**.
1. Välj **[!UICONTROL New list]** och skapa en ny mottagarlista för rapporten som ska skickas till.

Mer information om hur du skapar listor finns i [det här avsnittet](../../v8/audiences/create-audiences.md).

## Steg 2: Skapa leveransmallen {#step-2--create-the-delivery-template}

Följ stegen nedan för att skapa leveransmallen:

1. Bläddra till **[!UICONTROL Resources > Templates > Delivery templates]** noden i Adobe Campaign Explorer och duplicera **[!UICONTROL Email delivery]** inbyggd mall.

   Mer information om hur du skapar en leveransmall finns i [det här avsnittet](../../v8/send/create-templates.md).

1. Ange mallparametrar: label, target (the list of earlier eived), subject and content.

   Varje gång arbetsflödet körs **[!UICONTROL Tracking indicators]** rapporten uppdateras enligt anvisningarna i [Steg 3: Skapa arbetsflödet](#step-3--creating-the-workflow)).

1. Om du vill inkludera den senaste versionen av rapporten i leveransen måste du lägga till en **[!UICONTROL Calculated attachment]**:

   * Klicka på **[!UICONTROL Attachments]** och klicka på pilen bredvid **[!UICONTROL Add]** -knappen. Välj **[!UICONTROL Calculated attachment...]**.

      ![](assets/use_case_report_4.png)

   * I **[!UICONTROL Type]** väljer du det senaste alternativet: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      Värdet som anges i **[!UICONTROL Label]** fältet visas inte i den slutliga leveransen.

   * Ange filens åtkomstsökväg och namn i textzonen.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >Sökvägen och namnet måste vara identiska med de som anges i **[!UICONTROL JavaScript code]** typ av aktivitet i arbetsflödet, vilket förklaras i [Steg 3: Skapa arbetsflödet](#step-3--creating-the-workflow).

   * Välj **[!UICONTROL Advanced]** tabb och kontrollera **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Ange namnet på den bifogade filen i den slutliga leveransen i textzonen.

      ![](assets/use_case_report_6b.png)

## Steg 3: Skapa arbetsflödet {#step-3--creating-the-workflow}

Skapa följande arbetsflöde för det här användningsfallet.

![](assets/use_case_report_8.png)

Den använder tre verksamheter:

* A **[!UICONTROL Scheduler]** aktivitet som utför arbetsflödet en gång i månaden,
* A **[!UICONTROL JavaScript code]** verksamhet som genererar rapporten i PDF-format,
* A **[!UICONTROL Delivery]** aktivitet som refererar till den tidigare skapade leveransmallen.

Följ stegen nedan för att skapa arbetsflödet:

1. Bläddra till **[!UICONTROL Administration > Production > Technical workflows]** noden Campaign utforskar och skapar en ny mapp för att lagra dina arbetsflöden.
1. Skapa ett nytt arbetsflöde.

   ![](assets/use_case_report_7.png)

1. Börja med att lägga till en **[!UICONTROL Scheduler]** typaktivitet och konfigurera den så att arbetsflödet körs den första måndagen i månaden.

   ![](assets/use_case_report_9.png)

   Mer information om hur du konfigurerar schemaläggaren finns i [Schemaläggare](scheduler.md).

1. Lägg sedan till en **[!UICONTROL JavaScript code]** typaktivitet.

   ![](assets/use_case_report_10.png)

   Ange följande kod i redigeringszonen:

   ```sql
   var reportName = "indicators";
   var path = "/tmp/indicators.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```


   med följande variabler:

   * **var reportName**: Ange rapportens interna namn med citattecken. I det här fallet är det interna namnet på **Spårningsindikator** rapporten är&quot;deliveryFeedback&quot;.
   * **var path**: Ange filens sparningssökväg (&quot;tmp&quot;), namnet som du vill ge filen (&quot;deliveryFeedback&quot;) och filnamnstillägget (&quot;.pdf&quot;). I det här fallet har vi använt det interna namnet som filnamn. Värdena måste vara mellan dubbla citattecken och avgränsade med plustecknet (+).

      >[!CAUTION]
      >
      >Filen måste sparas på servern. Du måste ange samma sökväg och samma namn som i **[!UICONTROL General]** -fliken i redigeringsfönstret för den beräknade bilagan, som [här](#step-2--create-the-delivery-template)).

   * **var exportFormat**: Ange exportformatet för filen (&quot;PDF&quot;).
   * **var _ctx** (kontext): i det här fallet använder vi **[!UICONTROL Tracking indicators]** rapportera i sitt globala sammanhang.

1. Slutför genom att lägga till en **[!UICONTROL Delivery]** aktivitet med följande alternativ:

   ![](assets/use_case_report_11.png)

   * **[!UICONTROL Delivery]**: välj **[!UICONTROL New, created from a template]** och välj den leveransmall som skapades tidigare.
   * För **[!UICONTROL Recipients]** och **[!UICONTROL Content]** fält, markera **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to perform]**: välj **[!UICONTROL Prepare and start]**.
   * Avmarkera **[!UICONTROL Generate an outbound transition]** och **[!UICONTROL Process errors]** alternativ.

1. Spara ändringarna och starta arbetsflödet. Meddelandet skickas till listan över mottagare varje månad med den bifogade rapporten.