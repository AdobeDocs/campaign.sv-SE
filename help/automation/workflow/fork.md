---
product: campaign
title: Förgrening
description: Läs mer om arbetsflödesaktiviteten för gafflar
feature: Workflows
role: User
exl-id: 7b94776c-2478-4e12-82a6-c94be12e7e22
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 1%

---

# Förgrening{#fork}



Du kan använda aktiviteten **[!UICONTROL Fork]** för att skapa flera utgående övergångar och köra flera aktiviteter oberoende av varandra i samma arbetsflöde.

>[!IMPORTANT]
>
>De utgående övergångar som du lägger till efter en **[!UICONTROL Fork]**-aktivitet körs inte samtidigt. Det här beteendet kan påverka arbetsflödets prestanda. Använd aktiviteten **[!UICONTROL Fork]** om du behöver köra flera aktiviteter separat. Du kan även ansluta till de utgående aktiviteterna före den efterföljande delen av arbetsflödet.

Så här konfigurerar du en **[!UICONTROL Fork]**-aktivitet och dess relaterade aktiviteter:

1. Öppna aktiviteten **[!UICONTROL Fork]** och definiera namn och etikett för utgående övergångar.

   ![](assets/s_user_segmentation_fork.png)

1. Öppna varje utgående övergång och konfigurera den.
1. Om du vill ansluta till utgående övergångar lägger du till en AND-join-aktivitet. [Läs mer](and-join.md).

   Den efterföljande delen av arbetsflödet körs endast när de kopplade utgående övergångarna har slutförts.

## Exempel: segmentering

I det här exemplet skickas olika e-postmeddelanden till olika populationsgrupper. En **[!UICONTROL Fork]**-aktivitet används efter en fråga för att utföra två parallella åtgärder:

* Spara frågeresultatet
* Segmentera resultatet för att skicka flera leveranser

  ![Aktiviteten för gaffeln följer skärningspunkten för två frågor och föregår en aktivitet för listuppdatering och en delad aktivitet.](assets/wkf_fork_example.png)

Arbetsflödet omfattar följande:

1. **[!UICONTROL Query]** aktivitet

   Två populationsgrupper väljs ut: kvinnor och pariser.

1. **[!UICONTROL Intersection]** aktivitet

   Korsningen mellan frågeresultaten, dvs. Parisiska kvinnor, markeras.

1. **[!UICONTROL Fork]** aktivitet

   Den beräknade populationen sparas och segmenteras parallellt i två grupper:

   1. Parisiska kvinnor mellan 18 och 40 år
   1. Parisiska kvinnor över 40

1. **[!UICONTROL Delivery]** aktivitet

   Ett annat e-postmeddelande skickas till varje populationsgrupp.

## Användningsexempel: skicka ett födelsedagskalender via e-post

Ett återkommande e-postmeddelande skickas till en lista över mottagare på deras födelsedag. En **[!UICONTROL Fork]**-aktivitet används för att inkludera mottagare som är födda den 29 februari ett skottår. [Läs mer](send-a-birthday-email.md) om det här användningsexemplet.

![Tryckaktiviteten följer en testaktivitet och föregår två frågeaktiviteter.](assets/birthday-workflow_usecase_1.png)

## Exempel: automatisera innehåll med ett arbetsflöde


Du kan sedan konfigurera alla utgående övergångar och sedan förena dem med en [AND-join](and-join.md) -aktivitet, om det behövs. På så sätt kommer resten av arbetsflödet endast att köras när **[!UICONTROL Fork]**-aktivitetens utgående övergångar har slutförts.

## Relaterade ämnen

* [AND-join activity](and-join.md)
* [Användningsfall: födelsedagseftergift-e-post](send-a-birthday-email.md)
