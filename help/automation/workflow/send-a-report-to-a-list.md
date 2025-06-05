---
product: campaign
title: Skicka en rapport till en lista
description: Lär dig skicka en rapport till en lista med ett arbetsflöde
feature: Workflows
version: Campaign v8, Campaign Classic v7
exl-id: 5bc576d0-cab7-4d26-a3a5-91982a00e356
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 3%

---

# Skicka en rapport till en lista{#send-a-report-to-a-list}

I det här användningsexemplet finns information om hur du skapar en **[!UICONTROL Tracking indicators]**-rapport som är färdig varje månad i PDF-format och hur du skickar den till en lista med mottagare.

![](assets/use_case_report_intro.png)

De viktigaste implementeringsstegen för det här användningsexemplet är:

* Skapa en lista med mottagare för den här rapporten. [Läs mer](#step-1--create-the-recipient-list).
* Skapa en leveransmall som skapar en ny leverans varje gång arbetsflödet körs. [Läs mer](#step-2--create-the-delivery-template).
* Skapa ett arbetsflöde som genererar rapporten i PDF-format och skickar den till mottagarlistan. [Läs mer](#step-3--create-the-workflow)).

## Steg 1: Skapa mottagarlistan {#step-1--create-the-recipient-list}

Följ stegen nedan om du vill skapa en lista med mottagare som mål:

1. Bläddra till fliken **[!UICONTROL Profiles and targets]** och klicka på länken **[!UICONTROL Lists]**.
1. Klicka på knappen **[!UICONTROL Create]**.
1. Välj **[!UICONTROL New list]** och skapa en ny mottagarlista för rapporten som ska skickas till.

Mer information om hur du skapar listor finns i [det här avsnittet](../../v8/audiences/create-audiences.md).

## Steg 2: Skapa leveransmallen {#step-2--create-the-delivery-template}

Följ stegen nedan för att skapa leveransmallen:

1. Bläddra till noden **[!UICONTROL Resources > Templates > Delivery templates]** i Adobe Campaign Explorer och duplicera den inbyggda mallen **[!UICONTROL Email delivery]**.

   Mer information om hur du skapar en leveransmall finns i [det här avsnittet](../../v8/send/create-templates.md).

1. Ange mallparametrarna: label, target (listan med tidigare skapade mottagare), subject och content.

   Varje gång arbetsflödet körs uppdateras rapporten **[!UICONTROL Tracking indicators]** enligt beskrivningen i [Steg 3: Skapa arbetsflödet](#step-3--creating-the-workflow)).

1. Om du vill inkludera den senaste versionen av rapporten i leveransen måste du lägga till en **[!UICONTROL Calculated attachment]**:

   * Klicka på länken **[!UICONTROL Attachments]** och klicka på pilen bredvid knappen **[!UICONTROL Add]**. Välj **[!UICONTROL Calculated attachment...]**.

     ![](assets/use_case_report_4.png)

   * I listrutan **[!UICONTROL Type]** väljer du det senaste alternativet: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

     ![](assets/use_case_report_5.png)

     Värdet som anges i fältet **[!UICONTROL Label]** visas inte i den slutliga leveransen.

   * Ange filens åtkomstsökväg och namn i textzonen.

     ![](assets/use_case_report_6.png)

     >[!CAUTION]
     >
     >Sökvägen och namnet måste vara identiska med de som anges i arbetsflödets **[!UICONTROL JavaScript code]**-typaktivitet, enligt beskrivningen i [Steg 3: Skapa arbetsflödet](#step-3--creating-the-workflow).

   * Markera fliken **[!UICONTROL Advanced]** och markera **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Ange namnet på den bifogade filen i den slutliga leveransen i textzonen.

     ![](assets/use_case_report_6b.png)

## Steg 3: Skapa arbetsflödet {#step-3--creating-the-workflow}

Skapa följande arbetsflöde för det här användningsfallet.

![](assets/use_case_report_8.png)

Den använder tre verksamheter:

* En **[!UICONTROL Scheduler]**-aktivitet som kör arbetsflödet en gång i månaden,
* En **[!UICONTROL JavaScript code]**-aktivitet som genererar rapporten i PDF-format,
* En **[!UICONTROL Delivery]**-aktivitet som refererar till den leveransmall som skapats tidigare.

Följ stegen nedan för att skapa arbetsflödet:

1. Bläddra till noden **[!UICONTROL Administration > Production > Technical workflows]** i Campaign och skapa en ny mapp där du kan lagra dina arbetsflöden.
1. Skapa ett nytt arbetsflöde.

   ![](assets/use_case_report_7.png)

1. Börja med att lägga till en **[!UICONTROL Scheduler]**-typaktivitet och konfigurera den så att arbetsflödet körs den första måndagen i månaden.

   ![](assets/use_case_report_9.png)

   Mer information om hur du konfigurerar schemaläggaren finns i [Schemaläggaren](scheduler.md).

1. Lägg sedan till en aktivitet av typen **[!UICONTROL JavaScript code]**.

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

   * **var reportName**: ange rapportens interna namn med citattecken. I det här fallet är det interna namnet på **spårningsindikatorn**&quot;deliveryFeedback&quot;.
   * **var path**: ange filens sparningssökväg (&quot;tmp&quot;), namnet som du vill ge filen (&quot;deliveryFeedback&quot;) och filnamnstillägget (&quot;.pdf&quot;). I det här fallet har vi använt det interna namnet som filnamn. Värdena måste vara mellan dubbla citattecken och avgränsade med plustecknet (+).

     >[!CAUTION]
     >
     >Filen måste sparas på servern. Du måste ange samma sökväg och samma namn som på fliken **[!UICONTROL General]** i redigeringsfönstret för den beräknade bifogade filen, vilket beskrivs i [här](#step-2--create-the-delivery-template)).

   * **var exportFormat**: ange filens exportformat (&quot;PDF&quot;).
   * **var _ctx** (kontext): i det här fallet använder vi rapporten **[!UICONTROL Tracking indicators]** i dess globala kontext.

1. Slutför genom att lägga till en **[!UICONTROL Delivery]**-aktivitet med följande alternativ:

   ![](assets/use_case_report_11.png)

   * **[!UICONTROL Delivery]**: välj **[!UICONTROL New, created from a template]** och välj den leveransmall som skapades tidigare.
   * För fälten **[!UICONTROL Recipients]** och **[!UICONTROL Content]** väljer du **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to perform]**: välj **[!UICONTROL Prepare and start]**.
   * Avmarkera alternativen **[!UICONTROL Generate an outbound transition]** och **[!UICONTROL Process errors]**.

1. Spara ändringarna och starta arbetsflödet. Meddelandet skickas till listan över mottagare varje månad med den bifogade rapporten.
