---
title: Arbeta med Campaign och Adobe Analytics
description: Lär dig integrera Campaign och Analytics
feature: Analytics Integration, Reporting
role: Admin, User
level: Beginner
exl-id: 11370fb6-e192-4626-944e-b80a7496e50d
source-git-commit: e465b846b3144a2138bb912b4baa09238f8c5b4c
workflow-type: tm+mt
source-wordcount: '1333'
ht-degree: 65%

---

# Arbeta med Campaign och Adobe Analytics {#ac-aa}

Ni kan konfigurera Adobe Analytics för att integrera Campaign och Analytics.

Tack vare den här integreringen kan Adobe Campaign och Adobe Analytics interagera via tillägget **Web Analytics-anslutningar**. Denna integrering skickar indikatorer och attribut för e-postkampanjer som levereras av Adobe Campaign till Adobe Analytics.

>[!NOTE]
>
>Som användare av hanterade Cloud Service [kontaktar du Adobe](../start/campaign-faq.md#support) för att ansluta Campaign med Adobe Experience Cloud tjänster och lösningar. Tillägget för Web Analytics-anslutningen måste installeras i din miljö via det dedikerade paketet.

Med Adobe Analytics Connector kan Adobe Campaign mäta internetpublik (Web Analytics). Med webbanalysverktygen kan Adobe Campaign vidarebefordra indikatorer och kampanjattribut till Analytics.

Åtgärdsgränserna för varje verktyg är följande:

* **Adobe Analytics** markerar de e-postkampanjer som har startats med Adobe Campaign

* **Adobe Campaign** skickar indikatorerna och kampanjattributen till kopplingen, som i sin tur vidarebefordrar dem till webbanalysverktyget


>[!CAUTION]
>
>Adobe Analytics Connector är inte kompatibel med transaktionsmeddelanden (meddelandecentret).

Om du vill konfigurera en anslutning för Campaign-Analytics måste du utföra följande åtgärder:

1. [Skapa en rapportsvit i Adobe Analytics](#report-suite-analytics)
1. [Konfigurera konverteringsvariabler och lyckade händelser](#configure-conversion-success)
1. [Konfigurera ditt externa konto i Adobe Campaign](#external-account-ac)

## Skapa en analysrapportsserie {#report-suite-analytics}

Följ stegen nedan för att skapa din **[!UICONTROL Report suite]** i [!DNL Adobe Analytics]:

1. I [!DNL Adobe Analytics] väljer du **[!UICONTROL Admin tab]** och klickar sedan på **[!UICONTROL All admin]**.

   ![](assets/analytics_connnector_1.png)

1. Klicka på **[!UICONTROL Report suites]**.

   ![](assets/analytics_connnector_2.png)

1. På sidan **[!UICONTROL Report suite manager]** klickar du på **[!UICONTROL Create new]** och sedan på **[!UICONTROL Report suite]**.

   Detaljerade anvisningar om hur du skapar **[!UICONTROL Report suite]** finns i [Adobe Analytics-dokumentation](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=sv-SE#prerequisites){target="_blank"}.

   ![](assets/analytics_connnector_3.png)

1. Välj en mall.

1. Konfigurera din nya rapportsvit med följande information:

   * **[!UICONTROL Report Suite ID]**
   * **[!UICONTROL Site Title]**
   * **[!UICONTROL Time Zone]**
   * **[!UICONTROL Go Live Date]**
   * **[!UICONTROL Estimated Page Views Per Day]**

   ![](assets/analytics_connnector_4.png)

1. När konfigurationen är klar klickar du på **[!UICONTROL Create report suite]**.

## Konfigurera konverteringsvariabler och lyckade händelser {#configure-conversion-success}

När du har skapat din **[!UICONTROL Report suite]** måste du konfigurera **[!UICONTROL Conversion variables]** och **[!UICONTROL Success events]** enligt följande:

1. Välj din tidigare konfigurerade **[!UICONTROL Report suite]**.

1. Från **[!UICONTROL Edit settings]** knappen, välj **[!UICONTROL Conversion]** >  **[!UICONTROL Conversion variables]**.

   ![](assets/analytics_connnector_5.png)

1. Klicka på **[!UICONTROL Add new]** för att skapa de identifierare som krävs för att mäta effekten av e-postkampanjen, dvs. det interna kampanjnamnet (cid) och ID:t för registret iNmsBroadlog (bid).

   Mer information om hur du redigerar **[!UICONTROL Conversion variables]** finns i den här [Adobe Analytics-dokumentationen](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/t-conversion-variables-admin.html?lang=sv-SE#admin-tools){target="_blank"}.

   ![](assets/analytics_connnector_6.png)

1. Klicka på **[!UICONTROL Save]** när du är klar.

1. Skapa sedan **[!UICONTROL Success events]** genom att välja **[!UICONTROL Conversion]** > **[!UICONTROL Success events]** från knappen **[!UICONTROL Edit settings]**.

   ![](assets/analytics_connnector_7.png)

1. Klicka på **[!UICONTROL Add new]** för att konfigurera följande **[!UICONTROL Success events]**:

   * **[!UICONTROL Clicked]**
   * **[!UICONTROL Opened]**
   * **[!UICONTROL Person clicks]**
   * **[!UICONTROL Processed]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL Sent]**
   * **[!UICONTROL Total bounces]**
   * **[!UICONTROL Unique Clicks]**
   * **[!UICONTROL Unique Opens]**
   * **[!UICONTROL Unsubscribed]**

   Mer information om hur du konfigurerar **[!UICONTROL Success events]** finns i [Adobe Analytics-dokumentationen](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/success-event.html?lang=sv-SE)

   ![](assets/analytics_connnector_8.png)

1. Klicka på **[!UICONTROL Save]** när du är klar.

När rapportsviten har konfigurerats måste du konfigurera **[!UICONTROL External accounts]** i Adobe Campaign.

## Konfigurera ett externt kampanjkonto {#external-account-ac}

Nu måste du konfigurera ditt externa **[!UICONTROL Web Analytics]**-konto i Adobe Campaign för att aktivera synkroniseringen mellan de två lösningarna.

Observera att om en av dina **[!UICONTROL Report suite]**, **[!UICONTROL Conversion variables]** eller **[!UICONTROL Success events]** inte visas när du konfigurerar ditt externa konto, innebär det att du saknar behörighet för den nya komponenten i **[!UICONTROL Product profile]** som är associerad med användaren.

Mer information finns på sidan [Produktprofiler för Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/permissions/product-profile.html?lang=sv-SE#product-profile-admins){target="_blank"}.

1. Bläddra till mappen **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Adobe Campaign Explorer-trädet och klicka på **[!UICONTROL New]**.

   ![](assets/analytics_connnector_9.png)

1. Använd listrutan för att välja typen **[!UICONTROL Web Analytics]** och **[!UICONTROL Adobe Analytics]** i listrutan **[!UICONTROL Integration]**.

   ![](assets/analytics_connnector_10.png)

1. Klicka på **[!UICONTROL Configure]** bredvid listrutan **[!UICONTROL Integration]**.

1. Mappa det externa kontot från **[!UICONTROL Configure Analytics integration]**-fönstret med den rapportsvit du skapat tidigare och ge följande information:

   * **[!UICONTROL E-Mail]**
   * **[!UICONTROL IMS Org]**
   * **[!UICONTROL Analytics Company]**
   * **[!UICONTROL Report Suite]**


1. Mappa de två **[!UICONTROL Conversion variables]** som konfigurerats i [!DNL Adobe Analytics] från kategorin **[!UICONTROL eVars]**.

   >[!NOTE]
   >
   >Fälten för kampanj-ID och Broadload ID samlas in via JavaScript på landningssidan eller via bearbetningsregler. [Läs mer om hur du bearbetar regler](https://experienceleague.adobe.com/sv/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules)

   ![](assets/analytics_connnector_11.png)

1. Mappa de tio **[!UICONTROL Success events]** som konfigurerats i [!DNL Adobe Analytics] från kategorin **[!UICONTROL Events]**.

1. Klicka på **[!UICONTROL Submit]** när du är klar. Adobe Campaign skapar en **[!UICONTROL Data source]**, **[!UICONTROL Calculated metrics]**, **[!UICONTROL Remarketing segments]** och **[!UICONTROL Classifications]** i den mappade analysen **[!UICONTROL Report Suite]**.

   När synkroniseringen mellan [!DNL Adobe Analytics] och Adobe Campaign är klar kan du stänga fönstret.

1. Inställningarna kan visas från fliken **[!UICONTROL Data Settings]** i fönstret **[!UICONTROL Configure Analytics integration]**.

   Med knappen **[!UICONTROL Sync]** kommer [!DNL Adobe Campaign] att synkronisera namnändringarna i [!DNL Adobe Analytics]. Om komponenten tas bort i [!DNL Adobe Analytics] kommer komponenten att genomstrykas i [!DNL Adobe Campaign] eller visas med ett meddelande som säger **ej hittad**.

   ![](assets/analytics_connnector_12.png)

   >[!NOTE]
   >
   > Du kan inte lägga till eller ta bort segment i den här versionen av Campaign v8.

1. Från **[!UICONTROL External account]**, klicka på **[!UICONTROL Enrich the formula...]**-länken för att ändra URL-beräkningsformeln och ange integreringsinformation för webbanalysverktyget (kampanj-ID) och domänerna för de webbplatser vars aktivitet måste spåras.

   ![](assets/analytics_connnector_13.png)

1. Ange domännamn för webbplatserna.

   ![](assets/analytics_connnector_14.png)

1. Klicka på **[!UICONTROL Next]** och kontrollera att domännamnen har sparats.

   ![](assets/analytics_connnector_15.png)

1. Om det behövs kan du överlagra beräkningsformeln. Markera rutan och redigera formeln direkt i fönstret.

   >[!IMPORTANT]
   >
   >Det här konfigurationsläget är reserverat för expertanvändare: eventuella fel i den här formeln kan leda till avbrutna e-postleveranser.

1. På fliken **[!UICONTROL Advanced]** kan du konfigurera eller ändra fler tekniska inställningar.

   * **[!UICONTROL Lifespan]**: gör att du kan ange efter vilken fördröjning (i dagar) som webbhändelser återställs i Adobe Campaign med tekniska arbetsflöden. Standard: 180 dagar.
   * Med **[!UICONTROL Persistence]**: kan du ange den period under vilken alla webbhändelser (till exempel ett köp) kan tillskrivas en återmarknadsföringskampanj, standard: 7 dagar.

>[!NOTE]
>
>Om du använder flera målgruppsmätningsverktyg kan du välja **[!UICONTROL Other]** i listrutan **[!UICONTROL Partners]** när du skapar det externa kontot. Du får endast referera till ett externt konto i leveransegenskaperna: du måste därför anpassa formeln för spårade URL-adresser genom att lägga till de parametrar som förväntas av Adobe och alla andra mätverktyg som används.

## Tekniskt arbetsflöde för webbanalysprocesser {#technical-workflows-of-web-analytics-processes}

Datautbyte mellan Adobe Campaign och Adobe Analytics hanteras av ett tekniskt arbetsflöde som körs som en bakgrundsuppgift.

Det här arbetsflödet är tillgängligt från Campaign Explorer-trädet, under mappen **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Web analytics process]**.

![](assets/webanalytics_workflows.png)

Med arbetsflödet **[!UICONTROL Sending of indicators and campaign attributes]** kan du skicka kampanjindikatorer via Adobe Campaign till Adobe Experience Cloud med Adobe Analytics Connector. Arbetsflödet utlöses kl. 4.00 varje dag och det kan ta 24 timmar innan data skickas till Analytics.

Observera att det här arbetsflödet inte ska startas om, annars skickas alla tidigare data på nytt, vilket kan förvränga analysresultaten.

Följande indikatorer ingår:

* **[!UICONTROL Messages to deliver]** (@toDeliver)
* **[!UICONTROL Processed]** (@processed)
* **[!UICONTROL Success]** (@success)
* **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
* **[!UICONTROL Recipients who have opened]** (@recipientOpen)
* **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
* **[!UICONTROL People who clicked]** (@personClick)
* **[!UICONTROL Number of distinct clicks]** (@recipientClick)
* **[!UICONTROL Opt-Out]** (@optOut)
* **[!UICONTROL Errors]** (@error)

>[!NOTE]
>
>Skickade data är deltavärdet baserat på den senaste ögonblicksbilden vilket kan leda till ett negativt värde i mätdata.

Följande attribut skickas:

* **[!UICONTROL Internal name]** (@internalName)
* **[!UICONTROL Label]** (@label)
* **[!UICONTROL Label]** (operation/@label): bara om **Campaign**-paketet är installerat
* **[!UICONTROL Nature]** (operation/@natur): bara om **Campaign**-paketet är installerat
* **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
* **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
* **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
* **[!UICONTROL Contact date]** (scheduling/@contactDate)

## Spåra leveranser {#tracking-deliveries-in-adobe-campaign}

För att Adobe Experience Cloud ska kunna spåra aktiviteter på webbplatserna när leveransen har skickats av Adobe Campaign måste du referera till matchande koppling i leveransegenskaperna. Gör så här:

1. Öppna leveransen av kampanjen som ska spåras.

   ![](assets/webanalytics_delivery_properties_003.png)

1. Öppna leveransegenskaperna.
1. Gå till fliken **[!UICONTROL Web Analytics]** och välj det tidigare skapade externa kontot. Se [Konfigurera ditt externa konto i Adobe Campaign](#external-account-ac).

   ![](assets/webanalytics_delivery_properties_002.png)

1. Nu kan du skicka leveransen och öppna rapporten i Adobe Analytics.


## Skapa en ny marknadsföringskampanj {#create-a-re-marketing-campaign}

För att förbereda din återmarknadsföringskampanj skapar du helt enkelt leveransmallar som kan användas för återmarknadsföringskampanjer. Konfigurera sedan din återmarknadsföringskampanj och länka den till ett segment. Varje segment måste ha olika återmarknadsföringskampanjer.

Återmarknadsföringskampanjer startas automatiskt när Adobe Campaign har återställt segmenten och analyserat beteendet hos de personer som den inledande kampanjen riktar sig till. Om kunden överger en varukorg eller visar en produkt utan att köpa den skickas en leverans till de berörda mottagarna för att de ska kunna slutföra köpet.

Adobe Campaign tillhandahåller skräddarsydda leveransmallar som ni kan använda eller registrera er själva i för att förbereda kampanjer.

1. Från **[!UICONTROL Explorer]**, gå till mappen **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** i Adobe Campaign-trädet.
1. Duplicera **[!UICONTROL Email delivery (re-marketing)]**-mallen eller mallexemplen för återmarknadsföring som Adobe Campaign erbjuder.
1. Anpassa mallen efter dina behov och spara den.
1. Skapa en ny kampanj och välj mallen **[!UICONTROL Re-marketing campaign]** i listrutan.
1. Klicka på länken **[!UICONTROL Configure...]** för att ange segmentet och leveransmallen som är länkad till kampanjen.
1. Välj e[externt konto](#external-account-ac) för Analytics och det berörda segmentet.
1. Välj leveransmallen som ska användas för den här återmarknadsföringskampanjen och klicka sedan på **[!UICONTROL Finish]** för att stänga fönstret.
1. Klicka på **[!UICONTROL OK]** för att stänga kampanjfönstret.

**[!UICONTROL Re-marketing efficiency]**-rapporten nås via den globala rapportsidan. Här kan du se antalet konverterade kontakter (dvs. de har köpt något) i relation till antalet övergivna varukorgar efter Adobe Campaign marknadsföringskampanj. Konverteringsgraden beräknas per vecka, månad eller sedan synkroniseringen mellan Adobe Campaign och Adobe Analytics inleddes.

**Relaterade ämnen**

* [Campaign - integrering av Experience Cloud-utlösare](ac-triggers.md)
