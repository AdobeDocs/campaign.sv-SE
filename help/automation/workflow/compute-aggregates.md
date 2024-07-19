---
product: campaign
title: Utför sammanställd beräkning
description: Lär dig hur du utför sammanställd datoranvändning i frågor
feature: Workflows
role: User, Developer
exl-id: 00e564b5-3c8e-45d4-b240-c872a8b8ccb6
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Utför sammanställd beräkning {#performing-aggregate-computing}

I det här exemplet vill vi räkna antalet mottagare som bor i London enligt kön.

* Vilken tabell måste markeras?

  Mottagartabellen (**nms:mottagare**)

* Vilka fält ska markeras i utdatakolumnen?

  Primärnyckel (med antal) och kön

* Vilka villkor baseras informationen på?

  Baserat på de mottagare som bor i London

Så här skapar du det här exemplet:

1. I **[!UICONTROL Data to extract]** definierar du ett antal för primärnyckeln (som i föregående exempel). Lägg till fältet **[!UICONTROL Gender]** i utdatakolumnen. Markera alternativet **[!UICONTROL Group]** i kolumnen **[!UICONTROL Gender]**. På så sätt grupperas mottagarna efter kön.

   ![](assets/query_editor_nveau_27.png)

1. Klicka på **[!UICONTROL Next]** i fönstret **[!UICONTROL Sorting]**: ingen sortering behövs här.
1. Konfigurera datafiltrering. Här vill du begränsa urvalet till kontakter som bor i London.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Värdena är skiftlägeskänsliga. Om värdet London anges i villkoret utan versal och om listan över mottagare innehåller ordet London med stor bokstav, misslyckas frågan.

1. Klicka på **[!UICONTROL Next]** i fönstret **[!UICONTROL Data formatting]**: ingen formatering krävs för det här exemplet.
1. Klicka på **[!UICONTROL Launch data preview]** i förhandsgranskningsfönstret.

   Det finns tre separata värden för varje sortering efter kön: **2** för hona, **1** för hane och **0** när kön är okänd. I det här exemplet innehåller listan 10 kvinnor, 16 män och 2 personer vars kön inte är känd.

   ![](assets/query_editor_agregat_04.png)
