---
product: campaign
title: Diskussionsforum
description: Lär dig använda diskussionsforum för Campaign
exl-id: c2336507-beea-4ddb-aa8c-1ec591eb5683
source-git-commit: 72fc29c49fca5767133be4a9927b57b3cfb51a14
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Diskussionsforum{#discussion-forums}

Operatörer i Adobe Campaign kan använda diskussionsforum för att dela information. Följande element har ett eget forum: planer, program, kampanjer, marknadsföringsresurser, simuleringar, aktier. Varje operator har också ett personligt forum. Alla diskussioner är offentliga, även på personliga forum.

Operatörer kan prenumerera på ett forum och få ett e-postmeddelande varje gång ett meddelande skickas.

## Gå till ett forum {#accessing-a-forum}

Om du vill komma åt ett forum går du till en instrumentpanel och klickar på **[!UICONTROL Forum]** i det övre högra hörnet.

![](assets/mrm-forum-icon.png)

Meddelanden och deras svar visas från senaste till äldsta.

Om du vill starta en ny tråd klickar du på **[!UICONTROL Add a discussion]** i det övre högra hörnet. The **[!UICONTROL Discussion forum]** öppnas (se nedan).

![](assets/mrm-forum-new-thread.png)


Ange texten i dialogrutan **[!UICONTROL Message]** -fält och en diskussionsrubrik i **[!UICONTROL Subject]** fält.

Operatörer som redan har publicerat ett meddelande i det här forumet meddelas som standard. Du kan välja ytterligare en operator att meddela. Om du vill meddela flera operatorer väljer du en grupp med operatorer.

Du kan lägga till en bifogad fil i meddelandet med  **[!UICONTROL Browse...]** -knappen. Den bifogade filen kommer också att inkluderas i e-postmeddelandet. Bifogade filer får endast skickas individuellt: om du vill skicka flera filer måste du komprimera dem i en ZIP-fil.

>[!CAUTION]
>
>När ett meddelande har skickats till forumet kan det inte längre ändras eller tas bort.

## Publicera på en operatörs personliga forum {#posting-to-the-personal-forum-of-an-operator}

Du kan skicka ett meddelande till en operatörs forum. Personliga forum är offentliga och alla operatorer kan se ditt meddelande. Operatören får ett e-postmeddelande varje gång någon publicerar på sitt personliga forum.

Om du vill komma åt en operatörs forum kan du:

* Bläddra till **[!UICONTROL Administration > Access management > Operators]** mapp för Campaign Explorer, välj den operator som ska öppna kontrollpanelen och klicka sedan på **[!UICONTROL Forum]** i det övre högra hörnet.
* Leta reda på namnet på operatorn i Adobe Campaign-användargränssnittet (via ett meddelande som skickats till forumet av den här operatorn, en uppgift som tilldelats dem) och klicka på den för att komma åt kontrollpanelen för operatorer.

## Prenumerera på ett forum {#subscribing-to-a-forum}

Genom att prenumerera på ett forum kan du följa alla diskussioner. När du prenumererar får du ett e-postmeddelande varje gång ett meddelande skickas till forumet.

Om du vill svara på ett meddelande klickar du i e-postmeddelandet och loggar sedan in på Adobe Campaign webbgränssnitt.

* Om du vill prenumerera på ett forum klickar du på **[!UICONTROL Follow discussions]** i det övre högra avsnittet ovanför listan med meddelanden.

   Avsnittet blir blått och visar att du prenumererar på forumet.

* Om du vill avbryta prenumerationen klickar du på **[!UICONTROL Unsubscribe]** -knappen.

* På din personliga instrumentpanel visas de forum som du prenumererar på. Klicka på **[!UICONTROL Subscription to discussion forums]** för att visa listan och sedan klicka på det objekt som intresserar dig för att komma åt dess forum.

   ![](assets/forum-subscribed.png)


## Felsöka meddelandeleverans {#checking-notification-delivery}

Om operatorer som prenumererar på ett forum inte får meddelanden som förväntat:

* Kontrollera att e-postadresser anges i operatörens profiler.
* Bläddra till **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** mappen Campaign Explorer och kontrollera **[!UICONTROL Jobs in discussion forums]** arbetsflödet startas utan fel.
* Kontrollera leveransloggarna:

   * På Adobe Campaign hemsida går du till **[!UICONTROL Campaigns > Navigation > Deliveries]**&#x200B;öppnar du **[!UICONTROL Discussion forum notification]** leverans.
   * I Campaign Explorer går du till **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** och sedan klicka **[!UICONTROL Discussion forum notifications]**.
   I **[!UICONTROL Discussion forum notifications]** finns leveransloggarna i **[!UICONTROL Edit > Delivery]** -fliken. Du kan även visa **[!UICONTROL Tracking > Log]** och **[!UICONTROL Exclusion causes]** -tabbar.
