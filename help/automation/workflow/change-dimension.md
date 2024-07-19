---
product: campaign
title: Ändra dimension i ett arbetsflöde
description: Lär dig hur du använder aktiviteten Ändra dimension
feature: Workflows, Targeting Activity
role: User
exl-id: 71f36413-377a-4be6-921c-9e794fe882fd
source-git-commit: b77c37ab9ba9556fdefc563deac6b55ab0d91dc8
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Ändra dimension{#change-dimension}

Använd aktiviteten **[!UICONTROL Change dimension]** om du vill ändra målinriktningsdimensionen när du skapar en målgrupp. Den här aktiviteten flyttar axeln beroende på datamallen och indatatypen. Du kan till exempel växla från dimensionen &quot;kontrakt&quot; till dimensionen &quot;kunder&quot;.

Du kan också använda den här aktiviteten för att definiera ytterligare kolumner för det nya målet och definiera villkor för datadeduplicering.

>[!IMPORTANT]
>
>Observera att aktiviteterna **[!UICONTROL Change Dimension]** och **[!UICONTROL Change Data source]** inte ska läggas till på en rad. Om du behöver använda båda aktiviteterna i följd måste du ta med en **[!UICONTROL Enrichement]**-aktivitet mellan dem. Detta garanterar att programmet körs på rätt sätt och förhindrar eventuella konflikter och fel.

Så här konfigurerar du aktiviteten **[!UICONTROL Change dimension]**:

1. Välj den nya måldimensionen via fältet **[!UICONTROL Change dimension]**.

   ![](assets/s_user_change_dimension_param1.png)

1. Vid dimensionsändring kan du behålla alla element eller välja de som ska bevaras i utdata. I följande exempel är max. antalet dubbletter anges till 2.

   ![](assets/s_user_change_dimension_limit.png)

   När du väljer att bara behålla en post visas en samling i arbetsschemat: Den här samlingen representerar alla poster som inte kommer att ingå i slutresultatet (eftersom endast en post behålls). I likhet med alla andra samlingar kan du med den här metoden beräkna aggregeringar eller återställa information i kolumner.

   Om du till exempel ändrar dimensionen **[!UICONTROL Customers]** till dimensionen **[!UICONTROL Recipients]** kan du rikta in dig på kunder i en viss butik samtidigt som du lägger till antalet köp.

1. Om du väljer att inte behålla all den här informationen kan du konfigurera det duplicerade hanteringsläget.

   ![](assets/s_user_change_dimension_param2.png)

   Med de blå pilarna kan du definiera den duplicerade bearbetningsprioriteten.

   I exemplet ovan dedupliceras mottagarna först till sin e-postadress och sedan till sitt kontonummer om det behövs.

1. På fliken **[!UICONTROL Result]** kan du lägga till ytterligare information.

   Du kan till exempel återskapa regionen baserat på postnumret med hjälp av en **Substring**-typfunktion. Så här gör du:

   * Klicka på länken **[!UICONTROL Add data...]** och välj **[!UICONTROL Data linked to the filtering dimension]**.

     ![](assets/wf_change-dimension_sample_01.png)

     >[!NOTE]
     >
     >Mer information om hur du skapar och hanterar ytterligare kolumner finns i [Lägg till data](query.md#add-data).

   * Markera föregående måldimension (före axelväxling) och markera **[!UICONTROL Zip Code]** i mottagarens **[!UICONTROL Location]**-underträd och klicka sedan på **[!UICONTROL Edit expression]**.

     ![](assets/wf_change-dimension_sample_02.png)

   * Klicka på **[!UICONTROL Advanced selection]** och välj **[!UICONTROL Edit the formula using an expression]**.

     ![](assets/wf_change-dimension_sample_03.png)

   * Använd funktionerna i listan och ange vilken beräkning som ska utföras.

     ![](assets/wf_change-dimension_sample_04.png)

   * Ange slutligen etiketten för den kolumn som du just har skapat.

     ![](assets/wf_change-dimension_sample_05.png)

1. Kör arbetsflödet för att visa resultatet av den här konfigurationen. Jämför data i tabellerna före och efter ändringsdimensionsaktiviteten och jämför arbetsflödestabellernas struktur, vilket visas i följande exempel:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
