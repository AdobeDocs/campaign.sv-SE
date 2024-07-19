---
product: campaign
title: Publicera kampanjpaketet
description: Publicera kampanjpaketet
feature: Distributed Marketing
role: User
exl-id: 2cd1981d-f192-41dc-b2f2-4fcd60493079
source-git-commit: 09db0cc1a14bffefe8d1b8d0d5a06d5b6517a5bb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 2%

---

# Publicera kampanjpaketet{#publishing-the-campaign-package}

Operatorer för central enhet publicerar kampanjer som de vill erbjuda lokala enheter i **[!UICONTROL list of campaign packages]**.

Kampanjpaketen måste godkännas av den centrala enheten innan de kan publiceras i kampanjpaketlistan. För att göra detta kan du ange en granskare eller grupp av granskare via länken **[!UICONTROL Approval parameters]** i kampanjpaketet.

## Tilldela en granskare {#assigning-a-reviewer}

Om du vill välja granskare klickar du på länken **[!UICONTROL Approval parameters]** i kampanjpaketet och väljer den relevanta granskaren i listrutan.

![](assets/s_advuser_mkg_dist_define_valid.png)

Du kan sedan starta godkännandeprocessen genom att klicka på **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Därefter skickas ett meddelande till granskaren som bekräftar att det här kampanjpaketet är tillgängligt. Meddelandet innehåller en länk för att godkänna eller avvisa godkännandet via webbåtkomst.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>På organisationsnivå kan du även ange granskare som ska godkänna order. Mer information finns i [Organisationsenheter](about-distributed-marketing.md#organizational-entities).

## Lägg till andra granskare {#adding-other-reviewers}

Du kan lägga till andra granskare från länken **[!UICONTROL Edit...]** som finns på fliken **[!UICONTROL Approval parameters...]** i kampanjpaketet.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Tidslinje för godkännande {#approval-periods}

Som standard får granskarna tre dagar på sig att bearbeta godkännandet.

I fönstret Redigera granskare kan du även ange påminnelser för att skicka ett eller flera meddelanden om ett kampanjpaket inte har godkänts. Det gör du genom att klicka på länken **[!UICONTROL Add reminder]** och sedan på knappen **[!UICONTROL Add]**.

Påminnelser kan skickas ut antingen ett visst datum och/eller **x** dagar efter överföringsdatumet. Typen av påminnelse kan konfigureras i den första kolumnen i tabellen med påminnelser. I exemplet nedan får granskarna ett påminnelsemeddelande den 11/01 2023, dvs. två dagar före det datum som valts i kolumnen **[!UICONTROL Date]**, och en andra påminnelse en dag före godkännandeperiodens slut, dvs. två dagar efter det att de skickats in för godkännande.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

När paketet har definierats och skickats för godkännande visas körningsschemat på fliken **[!UICONTROL Audit]**. Den visar bearbetningens tidsgräns som beräknats baserat på tidigare konfiguration samt datum för alla konfigurerade påminnelser.

## Godkänn via klientkonsolen {#approving-via-the-adobe-campaign-console}

Om ingen granskare har angetts, eller om ingen av de anmälda operatorerna har godkänt paketet, kan du med knappen **[!UICONTROL Approve the package]** gå direkt till godkännandet från kampanjpaketet **[!UICONTROL Dashboard]** eller från paketöversikten.

![](assets/s_advuser_mkg_dist_valid_button.png)

Efter godkännande publiceras kampanjen, läggs till i listan och så snart som dess tillgänglighetsdatum har nåtts kan lokala enheter använda den. Om de lokala entiteterna angavs när kampanjen skapades skickas ett meddelande till operatörerna i meddelandegruppen för att meddela dem att kampanjen är tillgänglig. Om ingen entitet har angetts i förväg är kampanjen som standard tillgänglig för alla lokala entiteter. Mer information finns i [Organisationsenheter](about-distributed-marketing.md#organizational-entities).
