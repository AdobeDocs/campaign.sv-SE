---
product: campaign
title: Webbhämtning
description: Läs mer om arbetsflödet för nedladdning av webbsidor
feature: Workflows
exl-id: 73bacf61-ac03-4a5c-b03b-6dfbe3fb9538
source-git-commit: 76a5737e2326e9691113957d1c7bf390ea969695
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 1%

---

# Webbhämtning{#web-download}



Aktiviteten **Webbhämtning** startar nedladdningen av en fil på en explicit URL, ett externt konto eller en Adobe Campaign-instans. HTTP-protokollet används. Det kan vara en nedladdning av GET eller POST.

## Egenskaper {#properties}

1. **Markera webbfilen**

   Om du vill ange vilken fil som ska laddas ned kan du ange fil-URL:en, använda det externa HTTP-kontot där filen lagras eller läsa in filen via en Adobe Campaign-instans. Tillgängliga parametrar beskrivs nedan:

   * Om du vill ange URL:en för filen som ska laddas ned direkt markerar du alternativet **[!UICONTROL Explicit URL]** och anger URL:en i lämpligt fält. Den här URL:en kan konstrueras med variabeldata.

     ![](assets/download_web_edit.png)

   * Om du vill använda en **[!UICONTROL External account]** väljer du kontot i listrutan och anger vilken fil som ska hämtas.

     Externa konton konfigureras från noden **[!UICONTROL Administration > Platform > External accounts]** i Adobe Campaign-trädet. Kontoparametrarna kan redigeras via ikonen **[!UICONTROL Edit link]**.

     ![](assets/download_web_edit_external.png)

   * Om du vill hämta filen från Adobe Campaign-instansen väljer du alternativet **[!UICONTROL Adobe Campaign Instance]**.

     ![](assets/download_web_edit_instance.png)

1. **Filhistorik**

   Med länken **[!UICONTROL File historization settings...]** kan du ange lagringskatalogen för filen och tömningsfrekvensen för den här katalogen.

   ![](assets/download_web_edit_hist.png)

   Följande alternativ är tillgängliga:

   * **[!UICONTROL Use a default storage directory]**: filen flyttas alltid innan den bearbetas. Om det här alternativet är markerat flyttas filen till standardlagringskatalogen (katalogen **vars** i Adobe Campaign installationsmapp). Om du vill ange en lagringskatalog avmarkerar du kryssrutan och anger sökvägen i fältet **[!UICONTROL Storage directory]**
   * **[!UICONTROL Number of files]**: Ange det maximala antalet filer som ska sparas i lagringskatalogen.
   * **[!UICONTROL Maximum size (in Mb)]**: Ange maximal kapacitet för lagringskatalogen (i MB).

   Varje fil sparas i 24 timmar innan den omfattas av de definierade reningsreglerna. Rensa sker precis innan aktiviteten startas och tar därför inte hänsyn till den aktuella arbetsflödesfilen.

   Filerna tas bort som en funktion av deras ålder (äldsta till nyaste). De äldsta filerna rensas tills båda tömningsreglerna verifieras. Om du definierar en gräns på 100 filer innebär det därför att lagringskatalogen alltid innehåller de 100 senaste filerna innan arbetsflödet påbörjas, samt de som bearbetas i arbetsflödet som pågår.

   Om du inte längre vill ange en gräns för alternativen **[!UICONTROL Number of files]** och **[!UICONTROL Maximum size (in Mb)]** anger du 0 som ett värde.

1. **Avancerade parametrar**

   Med länken **[!UICONTROL Advanced parameters...]** kan du ange ytterligare alternativ som visas nedan:

   * **[!UICONTROL Follow redirections]**: Med filomdirigering kan du använda åsidosättningar för att dirigera dataindata eller utdata till en enhet av en annan typ.
   * **[!UICONTROL Add the HTTP headers to the file]**: I vissa fall kanske du vill lägga till ytterligare HTTP-huvuden i en fil. Vanligtvis används dessa rubriker för att tillhandahålla ytterligare information i felsökningssyfte, för [Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/docs/Web/HTTP/CORS) eller för att ange specifika cachelagringsdirektiv.
   * **[!UICONTROL Ignore the HTTP return code]**: HTTP-returkoder, som också kallas HTTP-statuskoder, anger resultatet av en HTTP-begäran.

   ![](assets/download_web_edit_advanced.png)

   Alternativet **[!UICONTROL Process errors]** finns detaljerat i [Bearbetningsfel](monitor-workflow-execution.md#processing-errors).

## Utdataparametrar {#output-parameters}

* filnamn: Den hämtade filens fullständiga namn.
