---
product: campaign
title: Adobe Campaign Interaction best practices
description: Metodtips för att hantera interaktionsmodulen i Adobe Campaign
feature: Interaction, Offers
role: User, Admin
exl-id: 28f3a5bc-67f5-413e-b2ba-35c341f9ec5f
source-git-commit: 1a0b473b005449be7c846225e75a227f6d877c88
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 0%

---

# Bästa praxis för interaktion {#interaction-best-practices}

## Allmänna rekommendationer {#general-recommendations}

Hantering av erbjudanden i Adobe Campaign kräver noggrann hantering för att fungera effektivt. För att undvika problem måste du hitta en balans mellan antalet kontakter och antalet erbjudandekategorier och erbjudanden.

I det här avsnittet beskrivs de bästa sätten att hantera **Interaktion** i Adobe Campaign, inklusive regler för behörighet, fördefinierade filter, arbetsflödesaktiviteter och databasalternativ.

* När **implementera och konfigurera interaktioner** måste du vara medveten om följande rekommendationer:

   * För batchmotor (som vanligtvis används i utgående kommunikation som e-post) är dataflöde huvudproblemet, eftersom flera kontakter kan hanteras samtidigt. Den typiska flaskhalsen är databasprestanda.
   * Den huvudsakliga begränsningen för en enastående motor (används vanligtvis i inkommande kommunikation som en banderoll på en webbplats) är fördröjning, eftersom någon förväntar sig ett svar. Den typiska flaskhalsen är processorprestanda.
   * Katalogdesignen har stor inverkan på Adobe Campaign prestanda.
   * När du arbetar med många erbjudanden är det bäst att dela upp dem i flera olika erbjudandekataloger.

* Nedan visas några metodtips när du arbetar med **regler för behörighet**:

   * Förenkla reglerna. Reglernas komplexitet påverkar prestanda när det utökar sökningen. En komplex regel är en regel som har fler än fem villkor.
   * För att öka prestandan kan reglerna delas upp i distinkta fördefinierade filter som delas över flera erbjudanden.
   * Placera de mest restriktiva erbjudandekategorireglerna på den högsta möjliga positionen i trädet. På så sätt filtreras de flesta kontakter först, vilket minskar målnumret och förhindrar att de bearbetas av fler regler.
   * Lägg de dyraste reglerna vad gäller tid och bearbetning längst ned i trädet. På så sätt körs dessa regler bara på den återstående målgruppen.
   * Börja i en viss kategori för att undvika att skanna hela trädet.
   * För att spara bearbetningstid kan du beräkna aggregat i stället för att skapa komplexa regler med kopplingar. Det gör du genom att försöka lagra kunddata i en referenstabell som kan slås upp i reglerna för behörighet.
   * Använd ett minsta antal vikter för att begränsa antalet frågor.
   * Vi rekommenderar ett begränsat antal erbjudanden per erbjudandeplats. Detta gör att erbjudandena kan hämtas snabbare på alla typer av platser.
   * Använd index, särskilt för ofta använda uppslagskolumner.

* Nedan visas några metodtips för **förslagstabell**:

   * Använd ett minsta antal regler för att göra bearbetningen så snabb som möjligt.
   * Begränsa antalet poster i förslagstabellen: spara bara de poster som behövs för att spåra dess statusuppdatering och vad som behövs för reglerna och arkivera dem sedan i ett annat system.
   * Utför omfattande databasunderhåll i förslagstabellen, till exempel återskapa index eller återskapa tabell.
   * Begränsa antalet förslag som efterfrågas per mål. Ställ inte in mer än vad du faktiskt kommer att använda.
   * Undvik kopplingar så mycket som möjligt i regelkriterierna.

## Tips när erbjudanden hanteras {#tips-managing-offers}

I det här avsnittet finns mer detaljerad information om hur du hanterar erbjudanden och använder interaktionsmodulen i Adobe Campaign.

### Flera erbjudanden i ett e-postmeddelande {#multiple-offer-spaces}

När erbjudanden inkluderas i leveranser väljs de vanligtvis upp i kampanjen via ett **Berikning** arbetsflödesaktivitet (eller annan liknande aktivitet).

När du väljer erbjudanden i en **Berikning** väljer du vilket utrymme som ska användas. Oberoende av vilket utrymme som har valts beror menyn för leveransanpassning på hur mycket utrymme som finns i leveransformuläret.

I exemplet nedan är erbjudandeutrymmet som valts i leveransen **[!UICONTROL Email (Environment - Recipient)]**:

![](assets/Interaction-best-practices-offer-space-selected.png)

Om det lediga utrymme som du har valt i leveransen inte har någon HTML-återgivningsfunktion kommer du inte att se det på leveransmenyn och det kommer inte att gå att välja det. Detta är oberoende av vilket erbjudandeutrymme som valts i **Berikning** aktivitet.

I exemplet nedan är återgivningsfunktionen HTML tillgänglig i listrutan eftersom det erbjudandeutrymme som valts i leveransen har en återgivningsfunktion:

![](assets/Interaction-best-practices-HTML-rendering.png)

Den här funktionen infogar kod som: `<%@ include proposition="targetData.proposition" view="rendering/html" %>`.

När du markerar förslaget, är värdet för **[!UICONTROL view]** är följande:
* &quot;rendering/html&quot;: html-rendering. Det använder återgivningsfunktionen HTML.
* &quot;offer/view/html&quot;: html-innehåll. Återgivningsfunktionen HTML används inte. Det innehåller bara fältet HTML.

När du inkluderar flera erbjudandeplatser i en och samma e-postleverans och om vissa av dem har återgivningsfunktioner och andra inte har det, måste du komma ihåg vilka erbjudanden som innehåller blanksteg och vilka som erbjuder återgivningsfunktioner.

För att undvika eventuella problem rekommenderar vi att alla erbjudandeutrymmen har en HTML-återgivningsfunktion definierad, även om ditt erbjudandeutrymme endast kräver HTML.

### Ange rangordningen i förslagsloggtabellen {#rank-proposition-log-table}

Erbjudandeutrymmen kan lagra data i förslagstabellen när förslag genereras eller godkänns:

![](assets/Interaction-best-practices-offer-space-storage.png)

Detta gäller dock endast inkommande interaktioner.

Det går också att lagra ytterligare data i förslagstabellen när utgående interaktioner används, och även när utgående erbjudanden används utan interaktionsmodulen.

Alla fält i arbetsflödets temporära tabell vars namn matchar ett fältnamn i förslagstabellen kopieras till samma fält i förslagstabellen.

t.ex. när du väljer ett erbjudande manuellt (utan interaktion) i en **Berikning** arbetsflödesaktivitet, standardfälten definieras så här:

![](assets/Interaction-best-practices-manual-offer-std-fields.png)

Ytterligare fält kan läggas till, till exempel en `@rank` fält:

![](assets/Interaction-best-practices-manual-offer-add-fields.png)

Eftersom det finns ett fält i förslagstabellen med namnet `@rank`, kopieras värdet i arbetsflödets temporära tabell.

Mer information om hur du lagrar ytterligare fält i förslagstabellen finns i [det här avsnittet](interaction-send-offers.md#storing-offer-rankings-and-weights).

För utgående erbjudanden med interaktion är detta användbart när flera erbjudanden är markerade och du vill registrera i vilken ordning de ska visas i ett e-postmeddelande.

Du kan också lagra ytterligare metadata direkt i förslagstabellen, t.ex. aktuell utgiftsnivå, för att hålla historik över utgifter när erbjudandena genereras.

Vid användning av utgående interaktion `@rank` -fältet kan läggas till, som i exemplet ovan, men dess värde ställs in automatiskt baserat på den ordning som returneras av Interaction. Om du t.ex. använder Interaction för att välja tre erbjudanden `@rank` fältet får värdena 1, 2 och 3.

När du använder Interaction och väljer erbjudanden manuellt kan användaren kombinera båda metoderna. Användaren kan till exempel ställa in `@rank` ska vara 1 för det manuellt valda erbjudandet och använda ett uttryck som `"1 + @rank"` för erbjudanden som returneras av Interaction. Om Interaction väljer tre erbjudanden rangordnas de som returneras av båda metoderna 1-4:

![](assets/Interaction-best-practices-manual-offer-combined.png)

### Utöka schemat nms:offer {#extending-nms-offer-schema}

När du utökar schemat nms:offer måste du följa den färdiga strukturen som redan är konfigurerad:
* Definiera nya fält för innehållslagring under `<element name="view">`.
* Varje nytt fält måste definieras två gånger. En gång som ett vanligt XML-fält och en gång som ett CDATA XML-fält med &quot;_jst&quot; som tillägg till namnet. Exempel:

  ```
  <element label="Price" name="price" type="long" xml="true"/>
  <element advanced="true" label="Script price" name="price_jst" type="CDATA" xml="true"/>
  ```

* Alla fält som innehåller URL:er som ska spåras måste placeras under `<element name="trackedUrls">` som finns under `<element name="view" >`.
