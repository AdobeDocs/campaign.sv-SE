---
product: campaign
title: Skapa återkommande och periodiska kampanjer
description: Lär dig hur du skapar och kör återkommande och periodiska kampanjer
feature: Campaigns, Cross Channel Orchestration, Programs
role: User
exl-id: 68c5b903-5043-4e74-b3f6-90a7f2fb3b9a
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Återkommande och periodiska kampanjer {#recurring-and-periodic-campaigns}

En **återkommande kampanj** är en kampanj som baseras på en viss mall vars arbetsflöden är konfigurerade att köras enligt ett associerat schema. Målinriktningen dupliceras för varje genomförande och de olika processerna och målpopulationerna spåras.  När de är konfigurerade skapar återkommande kampanjer automatiskt ett nytt arbetsflöde (genom att duplicera arbetsflödesmallen) och kör det. Om du till exempel behöver skicka en påminnelse varje månad till ett målgruppssegment, ska du konfigurera en återkommande kampanj så att den i början av varje år skapar 12 arbetsflöden, en för varje månad. [Läs mer](#create-a-recurring-campaign)

En **periodisk kampanj** är en kampanj som baseras på en viss mall som gör att du kan skapa kampanjinstanser baserat på ett körningsschema. Kampanjinstanser skapas automatiskt baserat på en mall för periodiska kampanjer, beroende på den frekvens som definieras i mallschemat. [Läs mer](#create-a-periodic-campaign)

## Skapa en återkommande kampanj {#create-a-recurring-campaign}

Återkommande kampanjer skapas från en specifik mall som definierar den arbetsflödesmall som ska köras och körningsschemat.

### Skapa en mall för återkommande kampanjer {#create-the-campaign-template}

Följ stegen nedan för att skapa en mall för återkommande kampanjer:

1. Öppna Campaign Explorer och gå till **[!UICONTROL Resources > Templates > Campaign templates]**.
1. Duplicera den inbyggda **[!UICONTROL Recurring campaign]**-mallen.
   ![](assets/recurring-campaign-duplicate.png)
1. Ange namnet på mallen och kampanjens varaktighet.
1. För den här kampanjtypen läggs en **[!UICONTROL Schedule]**-flik till för att skapa mallkörningsschemat. Använd den här fliken för att definiera körningsdatum för kampanjer som baseras på den här mallen.
   ![](assets/recurring-campaign-schedule.png)

   Körningsschemats konfigurationsläge sammanfaller med arbetsflödets **[!UICONTROL Scheduler]**-objekt. [Läs mer](../workflow/scheduler.md).

   >[!CAUTION]
   >
   >Konfigurationen av körningsschemat måste utföras noggrant. Återkommande kampanjer duplicerar arbetsflödet eller arbetsflödena i mallen beroende på angivet schema. Den här åtgärden kan överlagra databasen.

1. Ange ett värde i fältet **[!UICONTROL Create in advance for]** för att skapa motsvarande arbetsflöden för den angivna perioden.
1. Utforma arbetsflödesmallen som ska användas i kampanjer som baseras på den här mallen på fliken **[!UICONTROL Targeting and workflows]**. Det här arbetsflödet innehåller typoskt målparametrar och en eller flera leveranser.

   >[!NOTE]
   >
   >Det här arbetsflödet måste sparas som en mall för återkommande arbetsflöde. Om du vill göra det redigerar du arbetsflödesegenskaperna och väljer alternativet **[!UICONTROL Recurring workflow template]** på fliken **[!UICONTROL Execution]**.

   ![](assets/recurring-campaign-wf-properties.png)

### Skapa den återkommande kampanjen {#create-the-recurring-campaign}

Om du vill skapa den återkommande kampanjen och köra dess arbetsflöden enligt det schema som definierats i mallen måste du:

1. Skapa en ny kampanj baserat på mallen för återkommande kampanjer.
1. Fyll i arbetsflödets körningsschema på fliken **[!UICONTROL Schedule]**. Med kampanjschemat kan du ange ett automatiskt datum för när arbetsflödet skapas eller körs för varje rad.

   För varje rad kan du lägga till följande alternativ:

   * Aktivera alternativet **[!UICONTROL To be approved]** om du vill framtvinga begäranden om leveransgodkännande i arbetsflödet.
   * Aktivera alternativet **[!UICONTROL To be started]** om du vill starta arbetsflödet när startdatumet har uppnåtts.

   I fältet **[!UICONTROL Create in advance for]** kan du skapa alla arbetsflöden som täcker den angivna perioden.

   När arbetsflödet **[!UICONTROL Jobs on campaigns]** körs skapas de dedikerade arbetsflödena baserat på de förekomster som definierats i kampanjschemat. Ett arbetsflöde skapas alltså för varje körningsdatum.

1. Återkommande arbetsflöden skapas automatiskt från arbetsflödesmallen som finns i kampanjen. De visas på fliken **[!UICONTROL Targeting and workflows]** i kampanjen.

   ![](assets/recurring-wf-created.png)

   Etiketten för en återkommande arbetsflödesinstans består av malletiketten och arbetsflödesnumret, med tecknet # däremellan.

   Arbetsflöden som skapas från schemat associeras automatiskt med det i kolumnen **[!UICONTROL Workflow]** på fliken **[!UICONTROL Schedule]**.

   ![](assets/recurring-wf-schedule-executed.png)

   Alla arbetsflöden kan redigeras på den här fliken.

   >[!NOTE]
   >
   >Startdatumet för den schemarad som är associerad med arbetsflödet är tillgängligt från en variabel i arbetsflödet med följande syntax:\
   >`$date(instance/vars/@startPlanningDate)`

## Skapa en periodisk kampanj {#create-a-periodic-campaign}

En periodisk kampanj är en kampanj som baseras på en viss mall som gör att du kan skapa kampanjinstanser baserat på ett körschema. Kampanjinstanser skapas automatiskt baserat på en mall för periodiska kampanjer, beroende på den frekvens som definieras i mallschemat.

### Skapa kampanjmallen {#create-the-campaign-template-1}

1. Öppna Campaign Explorer och gå till **[!UICONTROL Resources > Templates > Campaign templates]**.
1. Duplicera den inbyggda **[!UICONTROL Periodic campaign]**-mallen.
1. Ange mallens egenskaper.

   >[!NOTE]
   >
   >Operatorn som mallen tilldelas måste ha rätt behörighet för att skapa kampanjer i det valda programmet.

1. Skapa arbetsflödet som är associerat med den här mallen. Det här arbetsflödet dupliceras i varje periodisk kampanj som skapas av mallen.

   >[!NOTE]
   >
   >Det här arbetsflödet är en arbetsflödesmall. Den kan inte köras från kampanjmallen.

1. Slutför körningsschemat som för en mall för återkommande kampanjer: klicka på knappen **[!UICONTROL Add]** och definiera start- och slutdatum, eller fyll i körningsschemat via länken.

   >[!CAUTION]
   >
   >Periodiska kampanjmallar skapar nya kampanjer enligt det schema som definieras ovan. Den måste därför fyllas i noggrant för att undvika överbelastning av Adobe Campaign-databasen.

1. När startdatumet för körningen har uppnåtts skapas den matchande kampanjen automatiskt. Den får alla egenskaper som mallarna har.

   Varje kampanj kan redigeras via ett mallschema.

   Varje periodisk kampanj innehåller samma element. När den väl har skapats hanteras den som en standardkampanj.
