---
title: Skapa profilmålgrupper i Campaign
description: Lär dig hur du skapar listor och skapar en målgrupp
feature: Audiences, Profiles
role: User
level: Beginner
exl-id: 6fbe5616-7b8b-4504-988b-2bbbfd062548
source-git-commit: 70af3bceee67082d6a1bb098e60fd2899dc74600
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 1%

---

# Skapa en målgrupp i en lista {#create-segments}

Använd Campaign-listor för att skapa och ordna era målgrupper.

En lista är en statisk uppsättning kontakter som kan användas för leveransåtgärder eller uppdateras under en import- eller en annan arbetsflödesåtgärd. En population som har extraherats från databasen via en fråga kan till exempel lagras som en lista.

Listor skapas och hanteras via länken **[!UICONTROL Lists]** på fliken **[!UICONTROL Profiles and targets]**. Listan baseras på Adobe Campaign standardprofiltabell (nms:mottagare). [Läs mer](../dev/datamodel.md#ootb-profiles.md)

![](assets/list-dashboard.png)

Du kan skapa en lista med aktiviteten **Uppdatera lista** i ett arbetsflöde. Den här aktiviteten lagrar den resulterande populationen i en lista. Använd den för att skapa en ny lista eller uppdatera en befintlig lista. Om du vill skapa listor som innehåller andra typer av data än den inbyggda profiltabellen måste du köra ett arbetsflöde. Om du till exempel använder en fråga i besökstabellen och sedan uppdaterar listan, kan du skapa en besökslista. [Läs mer](#create-a-list-wf).

I den här videon får du lära dig mer om Lists hantering i Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/3426465?quality=12&captions=swe)


## Skapa en lista med kontakter {#create-a-list-of-contacts}

Följ stegen nedan för att skapa en lista över kontakter:

1. Klicka på knappen **[!UICONTROL Create]** och välj **[!UICONTROL New list]**.

   ![](assets/new-list.png)

1. Ange informationen på fliken **[!UICONTROL Edit]** i fönstret där listan skapas.

   ![](assets/list-details.png)

   * Ange listnamnet i fältet **[!UICONTROL Label]** och ändra det interna namnet om det behövs.
   * Lägg till en beskrivning av den här listan.
   * Du kan ange ett förfallodatum: när det här datumet nås rensas listan och tas automatiskt bort.


1. Klicka på **[!UICONTROL Add]** på fliken **[!UICONTROL Content]** för att välja de profiler som tillhör listan.

   ![](assets/add-profiles-to-a-list.png)

   Du kan skapa en ny profil och lägga till den i listan direkt från det här fönstret med hjälp av ikonen **[!UICONTROL Create]**. Profilen läggs till i databasen.

1. Klicka på **[!UICONTROL Save]** om du vill spara listan. Sedan läggs den till i översikten över listor.


## Konvertera filtrerade kontakter till en lista {#convert-data-to-a-list}

Du kan välja profiler och lägga till dem i en lista. Gör så här:

1. I Campaign Explorer väljer du profiler och högerklickar.

   Dessa profiler kan filtreras så att de uppfyller vissa villkor.

1. Välj **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/add-selection-to-a-list.png)

1. Välj en befintlig lista eller skapa en ny lista och klicka på **[!UICONTROL Next]**.

   ![](assets/select-the-list.png)

1. Klicka på knappen **[!UICONTROL Start]**.

   ![](assets/record-a-list.png)

Välj alternativet **[!UICONTROL Recreate the list]** om du vill ta bort det befintliga innehållet från listan och optimera skapandet av listan (ingen fråga behövs för att verifiera om profilerna redan är länkade till listan).

Om du avmarkerar alternativet **[!UICONTROL No trace of this job is saved in the database]** kan du välja (eller skapa) körningsmappen där den information som är länkad till den här processen lagras.

I fönstrets övre del kan du övervaka körningen. Med knappen **[!UICONTROL Stop]** kan du stoppa processen. Kontakter som redan har bearbetats länkas till listan.

När körningen är klar går du till menyn **[!UICONTROL Profiles and Targets > Lists]** och väljer listan: på fliken **[!UICONTROL Content]** visas de profiler som är länkade till den här listan.


## Skapa en lista med ett arbetsflöde  {#create-a-list-wf}

Du kan använda aktiviteten **[!UICONTROL List update]** för att skapa en lista eller lägga till en fyllning i en lista med mottagare.

I exemplet nedan skapar du en lista med alla mottagare mellan 25 och 40.

1. Välj **[!UICONTROL Profiles and targets]** och **[!UICONTROL Targeting workflows]** och skapa sedan ett nytt arbetsflöde från knappen **[!UICONTROL Create]**.
1. Ange en etikett för det här arbetsflödet, till exempel&quot;25-40 kontakter&quot;, lägg till en beskrivning och klicka på **[!UICONTROL Next]**.

   ![](assets/targeting-wf-sample.png)

1. Infoga en **[!UICONTROL Query]**-aktivitet för att definiera målpopulationen och redigera frågan.

   ![](assets/targeting-wf-edit-query.png)

1. Definiera filtervillkoren enligt nedan:

   ![](assets/targeting-wf-age-filter.png)

   Lär dig hur du skapar en fråga i ett arbetsflöde i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=sv-SE){target="_blank"}.

1. Lägg till en etikett för den här frågan och spara ändringarna.
1. Lägg till en **[!UICONTROL List update]**-aktivitet och redigera den.

   ![](assets/list-update-activity.png)

1. Ange en etikett för aktiviteten.
1. Välj alternativet **[!UICONTROL Create the list if necessary (Computed name)]** om du vill visa att listan skapas när det första arbetsflödet har körts och sedan uppdateras med följande körningar.
1. Markera en mapp och ange en etikett för listan.
1. Markera **[!UICONTROL Database of the targeting dimension]** för att lagra tabellen.
1. Låt alternativet **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** vara markerat om du vill ta bort mottagare som inte matchar målinriktningsvillkoren och infoga de nya i listan.
1. Låt även alternativet **[!UICONTROL Create or use a list with its own table]** vara markerat.
1. Låt alternativet **[!UICONTROL Generate an outbound transition]** vara avmarkerat.
1. Klicka på **[!UICONTROL Ok]** och spara arbetsflödet.
1. Starta arbetsflödet.

   Listan med matchande mottagare skapas sedan. Du kan komma åt den här listan från posten **[!UICONTROL Lists]** på startsidan.

   ![](assets/access-new-list.png)

   Du kan göra det här arbetsflödet återkommande genom att lägga till en schemaläggare i arbetsflödet. [Läs mer](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/scheduler.html?lang=sv-SE){target="_blank"}.

## Ta bort en profil från en lista {#remove-a-profile-from-a-list}

Om du vill ta bort en profil från en lista redigerar du listan, markerar profilen på fliken **[!UICONTROL Content]** och klickar sedan på ikonen **[!UICONTROL Delete]** .

## Ta bort en lista med profiler {#delete-a-list-of-profiles}

Om du vill ta bort en lista går du till den i Campaign Explorer, markerar den och högerklickar. Välj **[!UICONTROL Delete]**. Ett varningsmeddelande ber dig bekräfta borttagningen.

>[!NOTE]
>
>När du tar bort en lista påverkas inte profilerna i listan, men data i deras profil uppdateras.
