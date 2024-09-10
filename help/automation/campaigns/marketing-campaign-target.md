---
product: campaign
title: Målgrupper för marknadsföringskampanjer
description: Lär dig definiera målgruppen för era marknadsföringskampanjer
feature: Campaigns, Audiences
role: User
exl-id: 70a63632-f66d-40f2-806d-bde89303936a
source-git-commit: d292c20e520b2466f782ccf86eb9d61e01915563
workflow-type: tm+mt
source-wordcount: '1470'
ht-degree: 0%

---

# Välj målgruppen för dina kampanjer {#marketing-campaign-deliveries}

I en marknadsföringskampanj kan ni för varje leverans definiera:

* Målgruppen. Du kan skicka meddelanden till en [lista över mottagare](#send-to-a-group) eller skapa en [målgrupp i ett arbetsflöde](#build-the-main-target-in-a-workflow)
* En kontrollgrupp. Du kan [lägga till en kontrollgrupp](#add-a-control-group) för att övervaka mottagarnas beteende efter meddelandeleveransen
* dirigerade adresser - Läs mer i [det här avsnittet](../../v8/audiences/test-profiles.md).—>

En del av den här informationen kan ärvas från [kampanjmallen](marketing-campaign-templates.md#campaign-templates).

<!--
To build the delivery target, you can define filtering criteria for the recipients in the database. This recipient selection mode is presented in [this section](../../delivery/using/steps-defining-the-target-population.md).
-->

## Skicka till en grupp{#send-to-a-group}

Du kan importera en population till en lista och sedan ange den här listan som mål i leveranser. Gör så här:

1. Redigera leveransen och klicka på länken **[!UICONTROL To]** för att ändra målpopulationen.
1. Välj alternativet **[!UICONTROL Defined via the database]** på fliken **[!UICONTROL Main target]** och klicka på **[!UICONTROL Add]** för att välja mottagare.

   ![](assets/select-main-target.png)

1. Välj **[!UICONTROL A list of recipients]**.

   ![](assets/target-a-list.png)


1. Klicka på **[!UICONTROL Next]** för att markera listan.

   ![](assets/select-the-list.png)

   Du kan förfina målet genom att lägga till nya filtervillkor.

1. Klicka på **[!UICONTROL Finish]** när alla villkor har definierats och spara huvudmålet.

## Bygg målgruppen i ett kampanjarbetsflöde {#build-the-main-target-in-a-workflow}

Huvudmålet för en leverans kan också definieras i kampanjarbetsflödet: i den grafiska miljön kan du skapa ett mål med hjälp av frågor, tester och operatorer: union, borttagning av dubbletter, delning osv.

>[!IMPORTANT]
>
>Du får inte lägga till fler än 28 arbetsflöden i en kampanj. Tidigare är ytterligare arbetsflöden inte synliga i gränssnittet och kan generera fel.

### Skapa arbetsflödet {#create-a-targeting-workflow}

Målinriktning kan skapas med en kombination av filtreringsvillkor i en grafisk sekvens i ett arbetsflöde. Ni kan skapa populationer och underpopulationer som ska anpassas efter era behov. Om du vill visa arbetsflödesredigeraren klickar du på fliken **[!UICONTROL Targeting and workflows]** på kontrollpanelen för kampanjer.

![](assets/targeting-and-wf-tab.png)

Målpopulationen extraheras från Adobe Campaign-databasen via en eller flera frågor i ett arbetsflöde. Lär dig hur du skapar en fråga i [det här avsnittet](../workflow/query.md).

Du kan starta frågor och dela populationer via rutor som Union, Intersection, Sharing, Exclusion osv.

Markera objekten i listorna till vänster om arbetsytan och länka dem för att skapa målet.

![](assets/campaign-wf.png)

I diagrammet länkar du upp de mål- och planeringsfrågor som krävs för målkonstruktion i diagrammet. Du kan utföra målinriktningen medan konstruktionen pågår för att kontrollera populationen som extraherats från databasen.

>[!NOTE]
>
>Exempel och procedurer för att definiera frågor finns i [det här avsnittet](../workflow/query.md).

I den vänstra delen av redigeraren finns ett bibliotek med grafiska objekt som representerar aktiviteter. Den första fliken innehåller målinriktningsaktiviteterna och den andra fliken innehåller flödeskontrollaktiviteterna, som används ibland för att samordna målinriktningsaktiviteter.

Körnings- och formateringsfunktionerna för målarbetsflödet är tillgängliga via verktygsfältet för diagramredigering.

![](assets/wf-diagram.png)

>[!NOTE]
>
>Vilka aktiviteter som är tillgängliga för att skapa diagrammet och alla visnings- och layoutfunktioner finns i [det här avsnittet](../workflow/about-workflows.md).

Ni kan skapa flera arbetsflöden för målinriktning för en enskild kampanj. Lägga till ett arbetsflöde:

1. Gå till den övre vänstra delen av arbetsflödets område, högerklicka och välj **[!UICONTROL Add]**. Du kan också använda knappen **[!UICONTROL New]** som finns ovanför den här zonen.

   ![](assets/add-a-wf.png)

1. Välj mallen **[!UICONTROL New workflow]** och ge arbetsflödet ett namn.
1. Klicka på **[!UICONTROL OK]** för att bekräfta att arbetsflödet har skapats och skapa sedan diagrammet för arbetsflödet.

### Kör arbetsflödet {#execute-a-workflow}

Målarbetsflöden kan startas manuellt med knappen **[!UICONTROL Start]** i verktygsfältet, förutsatt att du har rätt behörighet.

Målsättningen kan programmeras för automatisk körning enligt ett schema (schemaläggare) eller en händelse (extern signal, filimport osv.).

Åtgärder som rör körning av målarbetsflödet (starta, stoppa, pausa, osv.) är **asynkrona** processer: kommandot sparas och börjar gälla så fort servern är tillgänglig för att använda det.

Med verktygsfältsikonerna kan du utföra åtgärder för arbetsflödet för målanpassning.

* Starta eller starta om

   * Med ikonen **[!UICONTROL Start]** kan du starta målarbetsflödet. När du klickar på den här ikonen aktiveras alla aktiviteter utan en indataövergång (förutom slutpunktshopp).

     ![](assets/start.png)

     Servern tar hänsyn till begäran, vilket visas av dess status: **[!UICONTROL Start as soon as possible]**.

   * Du kan starta om arbetsflödet för målanpassning via motsvarande verktygsfältsikon. Det här kommandot kan vara användbart om ikonen **[!UICONTROL Start]** inte är tillgänglig, till exempel när du har stoppat målarbetsflödet. I det här fallet klickar du på ikonen **[!UICONTROL Restart]** för att förutse omstarten. Servern tar hänsyn till begäran enligt dess status: **[!UICONTROL Restart requested]**.

* Stoppa eller pausa

   * Med verktygsfältsikonerna kan du stoppa eller pausa ett pågående målarbetsflöde.

     När du klickar på **[!UICONTROL Pause]** pausas åtgärder som pågår **[!UICONTROL are not]**, men ingen annan aktivitet startas förrän nästa omstart.

     ![](assets/pause.png)

     Servern tar hänsyn till kommandot, vilket visas i dess status: **[!UICONTROL Pause requested]**.

     Du kan också pausa ett arbetsflöde för målinriktning automatiskt när körningen når en viss aktivitet. Om du vill göra det högerklickar du på aktiviteten som målarbetsflödet ska pausas från och väljer **[!UICONTROL Enable but do not execute]**.

     ![](assets/donotexecute.png)

     Den här konfigurationen visas med en särskild ikon.

     ![](assets/pause_activity.png)

     >[!NOTE]
     >
     >Det här alternativet är användbart under design- och testfaser av avancerade riktade kampanjer.

     Klicka på **[!UICONTROL Start]** om du vill återuppta körningen.

   * Klicka på ikonen **[!UICONTROL Stop]** för att stoppa den pågående körningen.

     ![](assets/stop.png)

     Servern tar hänsyn till kommandot, vilket visas i dess status: **[!UICONTROL Stop requested]**.

  Du kan också stoppa ett målarbetsflöde automatiskt när körningen når en aktivitet. Det gör du genom att högerklicka på aktiviteten som målarbetsflödet stoppas från och välja **[!UICONTROL Do not activate]**.

  ![](assets/donotactivate.png)

  Den här konfigurationen visas med en särskild ikon.

  ![](assets/unactivation.png)


  >[!NOTE]
  >
  >Det här alternativet är användbart under design- och testfaser av avancerade riktade kampanjer.

* Ovillkorligt stopp

  I Utforskaren väljer du **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** för att få åtkomst till och agera på alla kampanjarbetsflöden.

  Du kan avbryta ditt arbetsflöde genom att klicka på ikonen **[!UICONTROL Actions]** och välja **[!UICONTROL Unconditional]** stop. Den här åtgärden avbryter kampanjarbetsflödet.

  ![](assets/stop_unconditional.png)

  >[!CAUTION]
  >
  >Ovillkorligt stopp är begränsat till Admin-användare.

## Lägga till en kontrollgrupp {#add-a-control-group}

En kontrollgrupp är en population som inte kommer att få leveransen. Den används för att spåra beteenden efter leverans och kampanjpåverkan genom att göra en jämförelse med beteendet hos målpopulationen, som har fått leveransen.

Kontrollgruppen kan extraheras från huvudmålet och/eller komma från en viss grupp eller fråga.

### Aktivera kontrollgruppen för en kampanj {#activate-the-control-group-for-a-campaign}

Du kan definiera en kontrollgrupp på kampanjnivå, och i så fall tillämpas kontrollgruppen på varje leverans av den aktuella kampanjen.

1. Redigera den aktuella kampanjen och klicka på fliken **[!UICONTROL Edit]**.
1. Klicka på **[!UICONTROL Advanced campaign parameters...]**.

   ![](assets/enable-control-group.png)

1. Välj alternativet **[!UICONTROL Enable and edit control group configuration]**.
1. Klicka på **[!UICONTROL Edit...]** om du vill konfigurera kontrollgruppen.

   ![](assets/edit-control-group.png)

Den fullständiga proceduren beskrivs i [det här avsnittet](#extract-the-control-group-from-the-main-target). Läs mer om kontrollgrupper i [det här avsnittet](#add-a-population).

### Aktivera kontrollgruppen för en leverans {#activate-the-control-group-for-a-delivery}

Du kan definiera en kontrollgrupp på leveransnivå. I så fall tillämpas kontrollgruppen på varje leverans av den aktuella kampanjen.

Som standard gäller den kontrollgruppskonfiguration som definieras på kampanjnivå för varje leverans av kampanjen. Du kan dock anpassa kontrollgruppen för en enskild leverans.

>[!NOTE]
>
>Om du har definierat en kontrollgrupp för en kampanj, och du även konfigurerar den för en leverans som är länkad till den här kampanjen, tillämpas bara den kontrollgrupp som har definierats för leveransen.

1. Redigera den aktuella leveransen och klicka sedan på länken **[!UICONTROL To]**.
1. Klicka på fliken **[!UICONTROL Control group]** och välj sedan **[!UICONTROL Enable and edit control group configuration]**.

   ![](assets/enable-control-group-for-a-delivery.png)

1. Klicka på **[!UICONTROL Edit...]** om du vill konfigurera kontrollgruppen.

Den fullständiga proceduren beskrivs i [det här avsnittet](#extract-the-control-group-from-the-main-target).

### Använda en ny population som kontrollgrupp {#add-a-population}

Du kan använda en specifik population för kontrollgruppen. I så fall väljer du den lista som ska användas som kontrollgrupp i det relaterade fältet.

Den här populationen kan komma från en lista med mottagare eller så kan du definiera den via en specifik fråga.

![](assets/new-population-as-control-group.png)

>[!NOTE]
>
>Adobe Campaign frågeredigerare visas i [det här avsnittet](../workflow/query.md).

### Extrahera kontrollgruppen från huvudmålet {#extract-the-control-group-from-the-main-target}

Du kan även extrahera mottagare från leveransens huvudmål. I det här fallet hämtas mottagarna från målet för leveransåtgärder som påverkas av den här konfigurationen. Extraheringen kan vara slumpmässig eller bero på att mottagarna har sorterats.

![](assets/extract-control-group-from-target.png)

Om du vill extrahera en kontrollgrupp aktiverar du kontrollgruppen för kampanjen eller leveransen och väljer något av följande alternativ: **[!UICONTROL Activate random sampling]** eller **[!UICONTROL Keep only the first records after sorting]**.

* Använd alternativet **[!UICONTROL Activate random sampling]** för att tillämpa slumpmässig sampling på mottagarna i huvudpopulationen. Om du sedan anger tröskelvärdet till 100 kommer kontrollgruppen att bestå av 100 mottagare som väljs slumpmässigt från målpopulationen. Det slumpmässiga urvalet beror på databasmotorn.
* Använd alternativet **[!UICONTROL Keep only the first records after sorting]** för att definiera en begränsning baserat på en eller flera sorteringsordningar. Om du väljer fältet **[!UICONTROL Age]** som sorteringsvillkor och sedan definierar 100 som ett tröskelvärde, kommer kontrollgruppen att bestå av de 100 yngsta mottagarna. Det kan till exempel vara intressant att definiera en kontrollgrupp som innehåller mottagare som gör få inköp, eller mottagare som gör vanliga inköp, och att jämföra deras beteende med de kontaktade mottagarna.

Klicka på **[!UICONTROL Next]** för att definiera sorteringsordningen (om det behövs) och välj mottagarbegränsningsläget.

![](assets/limit-control-group.png)

Den här konfigurationen motsvarar en **[!UICONTROL Split]**-aktivitet i arbetsflödet, vilket gör att du kan dela upp målet i delmängder. Kontrollgruppen är en av dessa deluppsättningar.


### Självstudievideo {#create-email-video}

I den här videon förklaras hur du lägger till en kontrollgrupp i en kampanj.

>[!VIDEO](https://video.tv.adobe.com/v/335606?quality=12)

Det finns ytterligare utbildningsvideor för Campaign [här](https://experienceleague.adobe.com/docs/campaign-learn/tutorials/getting-started/introduction-to-adobe-campaign.html){target="_blank"}.
