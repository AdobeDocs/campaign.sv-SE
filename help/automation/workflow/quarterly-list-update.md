---
product: campaign
title: Kvartalsvis listuppdatering med en inkrementell fråga
description: I det här fallet används en stegvis fråga för att automatiskt uppdatera en mottagarlista.
feature: Workflows
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 5%

---

# Kvartalsvis listuppdatering med en inkrementell fråga {#quarterly-list-update}



I följande exempel har [inkrementell fråga](incremental-query.md) används för att automatiskt uppdatera en mottagarlista. Dessa mottagare ingår i säsongskampanjer.

Eftersom dessa kampanjer lanseras i början av varje säsong för att erbjuda relevanta sportaktiviteter uppdateras dessa listor varje kvartal. Men en mottagare här får bara anges som mål en gång var 9:e månad för den här kampanjen. Detta gör att du kan fördela mottagarens frekvens för behörighet och erbjuda aktiviteter för olika årstider under åren.

![](assets/incremental_query_example.png)

1. Lägg till en inkrementell fråga samt en listuppdateringsaktivitet i ett nytt arbetsflöde.
1. Konfigurera **[!UICONTROL Incremental query]** aktivitetens flik enligt [Skapa en fråga](query.md#creating-a-query).
1. Välj **[!UICONTROL Scheduling & History]** och sedan ange en 270-dagarshistorik. Målgruppen för en mottagare som redan är målinriktad kommer inte längre att gälla under en period på 270 dagar, eller ungefär 9 månader.

   Klicka sedan på **[!UICONTROL Change...]** -knappen.

1. Om du vill att listan ska uppdateras innan säsongen börjar väljer du **[!UICONTROL Monthly]**.
1. På nästa skärm väljer du mars, juni, september och december. Välj den 20:e i månaden och välj vilken tid du vill starta arbetsflödet.
1. Välj sedan giltighetsperioden för frågan. Om du till exempel vill att den här aktiviteten ska vara permanent aktiv väljer du **[!UICONTROL Permanent validity]**.

1. När du har godkänt den inkrementella frågan konfigurerar du listuppdateringsaktiviteten enligt anvisningarna i [Listuppdatering](list-update.md).

Arbetsflödet kommer därför att startas automatiskt precis innan säsongen börjar. Listan kommer att uppdateras med nya, berättigade mottagare som kan ta emot erbjudandena.