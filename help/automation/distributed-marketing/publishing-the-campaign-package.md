---
product: campaign
title: Publicera kampanjpaketet
description: Publicera kampanjpaketet
feature: Distributed Marketing
exl-id: 2cd1981d-f192-41dc-b2f2-4fcd60493079
source-git-commit: 290f4e9a0d13ef49caacb7a128ccc266bafd5e69
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 2%

---

# Publicera kampanjpaketet{#publishing-the-campaign-package}

Operatörer av centralenheter publicerar kampanjer som de vill erbjuda lokala enheter i **[!UICONTROL list of campaign packages]**.

Kampanjpaketen måste godkännas av den centrala enheten innan de kan publiceras i kampanjpaketlistan. För att göra detta kan du ange en granskare eller grupp av granskare via **[!UICONTROL Approval parameters]** i kampanjpaketet.

## Tilldela en granskare {#assigning-a-reviewer}

Klicka på knappen **[!UICONTROL Approval parameters]** i kampanjpaketet och välj granskare i listrutan.

![](assets/s_advuser_mkg_dist_define_valid.png)

Du kan sedan starta godkännandeprocessen genom att klicka på **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Därefter skickas ett meddelande till granskaren som bekräftar att det här kampanjpaketet är tillgängligt. Meddelandet innehåller en länk för att godkänna eller avvisa godkännandet via webbåtkomst.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>På organisationsnivå kan du även ange granskare som ska godkänna order. Mer information finns i [Organisationsenheter](about-distributed-marketing.md#organizational-entities).

## Lägg till andra granskare {#adding-other-reviewers}

Du kan lägga till andra granskare från **[!UICONTROL Edit...]** länk, finns i kampanjpaketets **[!UICONTROL Approval parameters...]** -fliken.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Tidslinje för godkännande {#approval-periods}

Som standard får granskarna tre dagar på sig att bearbeta godkännandet.

I fönstret Redigera granskare kan du även ange påminnelser för att skicka ett eller flera meddelanden om ett kampanjpaket inte har godkänts. Om du vill göra det klickar du på **[!UICONTROL Add reminder]** länk, sedan **[!UICONTROL Add]** -knappen.

Påminnelser kan skickas ut antingen på ett visst datum och/eller **x** dagar efter inlämningsdatumet. Typen av påminnelse kan konfigureras i den första kolumnen i tabellen med påminnelser. I exemplet nedan får granskarna ett påminnelsemeddelande på den 01/11/2023, dvs. två dagar före det datum som valts i **[!UICONTROL Date]** och en andra påminnelse en dag före godkännandeperiodens slut, dvs. två dagar efter inlämningsdatumet för godkännandet.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

När paketet har definierats och skickats för godkännande visas körningsschemat i **[!UICONTROL Audit]** -fliken. Den visar bearbetningens tidsgräns som beräknats baserat på tidigare konfiguration samt datum för alla konfigurerade påminnelser.

## Godkänn via klientkonsolen {#approving-via-the-adobe-campaign-console}

Om ingen granskare har specificerats eller om ingen av de anmälda operatörerna har godkänt paketet, **[!UICONTROL Approve the package]** kan du gå direkt till godkännandet från kampanjpaketet **[!UICONTROL Dashboard]** eller via paketöversikten.

![](assets/s_advuser_mkg_dist_valid_button.png)

Efter godkännande publiceras kampanjen, läggs till i listan och så snart som dess tillgänglighetsdatum har nåtts kan lokala enheter använda den. Om de lokala entiteterna angavs när kampanjen skapades skickas ett meddelande till operatörerna i meddelandegruppen för att meddela dem att kampanjen är tillgänglig. Om ingen entitet har angetts i förväg är kampanjen som standard tillgänglig för alla lokala entiteter. Mer information finns i [Organisationsenheter](about-distributed-marketing.md#organizational-entities).
