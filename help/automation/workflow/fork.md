---
product: campaign
title: Förgrening
description: Läs mer om arbetsflödesaktiviteten för gafflar
feature: Workflows
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 1%

---

# Förgrening{#fork}



Du kan använda **[!UICONTROL Fork]** aktivitet för att skapa flera utgående övergångar och för att köra flera aktiviteter oberoende av varandra i samma arbetsflöde.

>[!IMPORTANT]
>
>De utgående övergångar som du lägger till efter en **[!UICONTROL Fork]** aktiviteten inte körs samtidigt. Det här beteendet kan påverka arbetsflödets prestanda. Använd **[!UICONTROL Fork]** om du behöver köra flera aktiviteter oberoende av varandra. Du kan även ansluta till de utgående aktiviteterna före den efterföljande delen av arbetsflödet.

Så här konfigurerar du en **[!UICONTROL Fork]** följer dessa steg när det gäller verksamhet och tillhörande verksamheter:

1. Öppna **[!UICONTROL Fork]** och definiera namn och etikett för utgående övergångar.

   ![](assets/s_user_segmentation_fork.png)

1. Öppna varje utgående övergång och konfigurera den.
1. Om du vill ansluta till utgående övergångar lägger du till en AND-join-aktivitet. [Läs mer](and-join.md).

   Den efterföljande delen av arbetsflödet körs endast när de kopplade utgående övergångarna har slutförts.

## Exempel: segmentering

I det här exemplet skickas olika e-postmeddelanden till olika populationsgrupper. A **[!UICONTROL Fork]** -aktiviteten används efter en fråga för att utföra två parallella åtgärder:

* Spara frågeresultatet
* Segmentera resultatet för att skicka flera leveranser

   ![Aktiviteten för gaffeln följer skärningspunkten mellan två frågor och föregår en listuppdateringsaktivitet och en delad aktivitet.](assets/wkf_fork_example.png)

Arbetsflödet omfattar följande:

1. **[!UICONTROL Query]** aktivitet

   Två populationsgrupper har valts: kvinnor och pariser.

1. **[!UICONTROL Intersection]** aktivitet

   Korsningen mellan frågeresultaten, dvs. Parisiska kvinnor, markeras.

1. **[!UICONTROL Fork]** aktivitet

   Den beräknade populationen sparas och segmenteras parallellt i två grupper:

   1. Parisiska kvinnor mellan 18 och 40 år
   1. Parisiska kvinnor över 40

1. **[!UICONTROL Delivery]** aktivitet

   Ett annat e-postmeddelande skickas till varje populationsgrupp.

## Användningsfall: skicka ett födelsedagsmeddelande

Ett återkommande e-postmeddelande skickas till en lista över mottagare på deras födelsedag. A **[!UICONTROL Fork]** aktiviteten används för att inkludera mottagare som är födda den 29 februari ett skottår. [Läs mer](send-a-birthday-email.md) om det här användningsexemplet.

![Aktiviteten för förgreningar följer en testaktivitet och föregår två frågeaktiviteter.](assets/birthday-workflow_usecase_1.png)

## Användningsfall: automatisera innehåll med ett arbetsflöde


Du kan sedan konfigurera varje utgående övergång och sedan förena dem med en [AND-join](and-join.md) aktivitet, om det behövs. På så sätt körs resten av arbetsflödet bara en gång **[!UICONTROL Fork]** utgående övergångar för aktiviteten är färdiga.

## Relaterade ämnen

* [AND-join activity](and-join.md)
* [Användningsfall: födelsedagsmeddelande](send-a-birthday-email.md)