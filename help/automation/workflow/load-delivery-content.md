---
product: campaign
title: Läs in leveransinnehåll
description: Läser in leveransinnehåll
feature: Workflows
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 08febcbc-1703-4d36-89e1-32c903618084
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 2%

---

# Läs in leveransinnehåll{#loading-delivery-content}

Om ditt leveransinnehåll finns i en HTML-fil som finns på Amazon S3-, FTP- eller SFTP-servrar kan du enkelt läsa in det i Adobe Campaign.

Så här gör du:

1. Om du inte redan har definierat en anslutning mellan Adobe Campaign och den (S)FTP-server som är värd för innehållsfilerna skapar du ett nytt externt S3-, FTP- eller SFTP-konto i **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. I det här externa kontot anger du den adress och de autentiseringsuppgifter som används för att upprätta anslutningen till S3- eller (S)FTP-servern.

   Här är ett exempel på ett externt S3-konto:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Skapa ett nytt arbetsflöde, till exempel från **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Lägg till en **[!UICONTROL File transfer]**-aktivitet i arbetsflödet och konfigurera den genom att ange

   * Det externa konto som ska användas för att ansluta till S3- eller (S)FTP-servern.
   * Sökvägen till filen på S3- eller (S)FTP-servern.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Lägg till en **[!UICONTROL Delivery]**-aktivitet och anslut den till den utgående övergången för aktiviteten **[!UICONTROL File transfer]**. Konfigurera den på följande sätt:

   * Leverans: Beroende på dina behov kan det vara en specifik leverans som redan har skapats i systemet eller en ny leverans som baseras på en befintlig mall.
   * Mottagare: I det här exemplet anses målet vara angivet i själva leveransen.
   * Innehåll: Välj **[!UICONTROL Specified in the delivery]** även om innehållet importeras i den tidigare aktiviteten. Eftersom innehållet importeras direkt från en fil som finns på en fjärrserver har det ingen identifierare när det bearbetas av arbetsflödet och kan inte identifieras som om det kommer från den inkommande händelsen.
   * Åtgärd som ska utföras: Välj **[!UICONTROL Save]** om du vill spara leveransen och kunna komma åt den från **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** när arbetsflödet har körts.

   ![](assets/delivery_loadcontent_activityexample.png)

1. Lägg till följande kommando på fliken **[!UICONTROL Script]** i aktiviteten **[!UICONTROL Delivery]** för att läsa in innehållet i den importerade filen i leveransen:

   ```
   delivery.content.html.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Spara och kör arbetsflödet. En ny leverans med det inlästa innehållet skapas under **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

