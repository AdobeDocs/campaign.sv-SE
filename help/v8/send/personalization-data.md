---
title: Datakällor för personalisering
description: Lär dig vilka källor som kan användas för personalisering
feature: Personalization
role: User
level: Beginner
exl-id: 711256e2-ab77-404a-b052-6793a85da193
source-git-commit: c248dd899ea704e43873652545c6b945c2915b57
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 2%

---

# Datakällor för personalisering{#personalization-data}

Personaliseringsdata kan hämtas från olika typer av källor: Kampanjdatabasdatakälla, extern fildatakälla eller extern databasdatakälla.

## Kampanjdatabasdatakälla

I det vanligaste fallet lagras personaliseringsdata i databasen. Till exempel är &quot;fält för mottagaranpassning&quot; alla fält som definieras i mottagartabellen, standardfält (vanligtvis: efternamn, förnamn, adress, ort, födelsedatum osv.) eller anpassade fält.

![Kampanjanpassningsfält i ett e-postmeddelande](assets/perso-campaign-datasource.png)


## Extern fildatakälla

Du kan använda en extern fil som innehåller alla fält som är definierade i kolumner. Den här filen används som indata under en meddelandeleveransdefinition. Du kan välja att infoga dessa profiler i databasen eller inte.

Om du vill välja vilken fil som ska användas som datakälla bläddrar du till länken Till i meddelandefönstret och väljer **Definieras i en extern fil** alternativ. När filen har lästs in kan du få åtkomst till mottagardata i anpassningsalternativen på menyn **Fält från filen** post.

![Personaliseringsdata från en fil](assets/perso-from-file.png)


## FDA-datakälla

Personaliseringsdata kan hämtas ut från ett externt register via [Åtkomst till federerade data](../connect/fda.md).  Om du vill utföra personalisering i leveranser med data från den externa databasen, samlar du in data som ska användas i ett arbetsflöde för att göra dem tillgängliga i en tillfällig tabell.

Lägg till en **Fråga** -aktivitet i målarbetsflödet och använd **Lägg till data...** för att välja den externa databasen. Den detaljerade processen finns i [det här avsnittet](../../automation/workflow/query.md#adding-data).

Använd sedan data från den tillfälliga tabellen för att anpassa leveransen. När frågeaktiviteten är konfigurerad kan du komma åt externa data i personaliseringsalternativen från **Måltillägg** post.

![Personaliseringsdata från en extern databas](assets/perso-external-db.png)

När du använder externa data som används i FDA bör du förbearbeta meddelandepersonalisering i ett dedikerat arbetsflöde med hjälp av **Förbered personaliseringsdata med ett arbetsflöde** enligt nedan.

### Optimera personalisering {#optimize-personalization}

Ni kan optimera personaliseringen med ett dedikerat alternativ: **[!UICONTROL Prepare the personalization data with a workflow]**, finns i **[!UICONTROL Analysis]** -fliken för leveransegenskaperna.

Under leveransanalysen skapar och kör det här alternativet automatiskt ett arbetsflöde som lagrar alla data som är länkade till målet i en tillfällig tabell, inklusive data från tabeller som är länkade i FDA.

Om du markerar det här alternativet kan leveransanalysens prestanda förbättras avsevärt när mycket data bearbetas, särskilt om personaliseringsdata kommer från en extern tabell via FDA. [Läs mer](../connect/fda.md).

Följ stegen nedan om du vill använda det här alternativet:

1. Skapa en kampanj.
1. I **[!UICONTROL Targeting and workflows]** fliken med kampanjen, lägg till en **Fråga** till arbetsflödet.
1. Lägg till en **[!UICONTROL Email delivery]** till arbetsflödet och öppna det.
1. Gå till **[!UICONTROL Analysis]** -fliken i **[!UICONTROL Delivery properties]** och väljer **[!UICONTROL Prepare the personalization data with a workflow]** alternativ.
1. Konfigurera leveransen och starta arbetsflödet för att starta analysen.

När analysen är klar lagras personaliseringsdata i ett temporärt register via ett tillfälligt tekniskt arbetsflöde som skapas direkt under analysen.

Det här arbetsflödet visas inte i Adobe Campaign gränssnitt. Det är bara tänkt att vara ett tekniskt sätt att snabbt lagra och hantera personaliseringsdata.

När analysen är klar går du till arbetsflödet **[!UICONTROL Properties]** och väljer **[!UICONTROL Variables]** -fliken. Där ser du namnet på den temporära tabellen som du kan använda för att göra ett SQL-anrop för att visa de ID som den innehåller.

## Personaliseringsdata i ett arbetsflöde

När en leverans skapas i ett arbetsflödes sammanhang kan du använda data från den tillfälliga arbetsflödestabellen. De data som lagras i arbetsflödets temporära arbetsregister är tillgängliga för personaliseringsåtgärder. Data kan användas i personaliseringsfälten.

Dessa data grupperas i **[!UICONTROL Target extension]** -menyn. Mer information om detta finns i [det här avsnittet](../../automation/workflow/use-workflow-data.md#target-data).
