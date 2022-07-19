---
product: campaign
title: God praxis för arbetsflöden
description: Lär dig mer om arbetsflöden för kampanjer
feature: Workflows
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 5%

---

# God praxis för arbetsflöden{#workflow-best-practices}

Nedan visas allmänna riktlinjer för att optimera prestanda för Campaign-arbetsflöden, förbättra arbetsflödesdesignen och välja rätt inställningar.

## Arbetsflödesmappar {#workflow-folders}

Adobe rekommenderar att du skapar arbetsflöden i en dedikerad mapp.

Om arbetsflödet påverkar hela plattformen (till exempel rensningsprocesser) kan du lägga till en undermapp i den inbyggda **[!UICONTROL Technical Workflows]** mapp.

## Namnge arbetsflöde {#workflow-naming}

Eftersom det gör det enklare att hitta och felsöka dem om de inte fungerar på rätt sätt rekommenderar Adobe att du ger arbetsflödena egna namn och etiketter: fyll i arbetsflödets beskrivningsfält för att sammanfatta den process som ska utföras så att operatören kan förstå den utan problem.

Om arbetsflödet är en del av en process som innefattar flera arbetsflöden kan du vara tydlig när du anger en etikett; Att använda siffror är ett bra sätt att ordna arbetsflödena (med Label).

Exempel:

* 001 - Importera - Importera mottagare
* 002 - Import - Importförsäljning
* 003 - Importera - Importera försäljningsinformation
* 010 - Exportera - Exportera leveransloggar
* 011 - Export - loggar för exportspårning

## Arbetsflödets allvarlighetsgrad {#workflow-severity}

Du kan konfigurera ett arbetsflödes svårighetsgrad i arbetsflödesegenskaperna i **[!UICONTROL Execution]** tab:

* Normal
* Produktion
* Kritisk

Om du anger den här informationen när du skapar ett arbetsflöde blir det lättare att förstå hur allvarlig den konfigurerade processen är.

Det här alternativet har ingen funktionell inverkan på andra arbetsflöden än kampanjarbetsflöden.

Kampanjarbetsflöden (arbetsflöden som skapas som en del av en kampanj/åtgärd) med högre allvarlighetsgrad körs i första hand om kampanjen har många processer som ska köras samtidigt. Som standard kan bara 10 processer köras samtidigt i en kampanj, enligt alternativet NmsOperation_LimitConcurrency. Om en kampanj till exempel innehåller 25 arbetsflöden kommer arbetsflöden med högre allvarlighetsgrad att köras i den första poolen med 10 processer.

## Arbetsflödesövervakning {#workflow-monitoring}

Alla schemalagda arbetsflöden som körs i produktionsmiljöer bör övervakas för att varnas om ett fel uppstår.

I arbetsflödesegenskaperna väljer du en Supervisor-grupp, antingen standardgruppen **[!UICONTROL Workflow supervisors]** eller en anpassad grupp. Se till att minst en operator tillhör den här gruppen, med en e-postkonfiguration.

Innan du börjar skapa ett arbetsflöde måste du definiera arbetsflödesansvariga. De meddelas via e-post om fel uppstår. Mer information finns i [Hantera fel](monitor-workflow-execution.md#managing-errors).

Kontrollera regelbundet **[!UICONTROL Monitoring]** om du vill visa den övergripande statusen för de aktiva arbetsflödena. Mer information finns i [Instansövervakning](monitor-workflow-execution.md#instance-supervision).

Med Workflow HeatMap kan Adobe Campaign plattformsadministratörer övervaka inläsningen av instansen och planera arbetsflödena utifrån detta. Mer information finns i [Arbetsflödesövervakning](heatmap.md).

## Aktiviteter {#using-activities}

>[!CAUTION]
>
>Du kan kopiera och klistra in aktiviteter i samma arbetsflöde. Vi rekommenderar dock inte att du kopierar inklistringsaktiviteter i olika arbetsflöden. Vissa inställningar som är kopplade till aktiviteter som Leveranser och Schemaläggare kan leda till konflikter och fel när målarbetsflödet körs. I stället rekommenderar vi att du  **Duplicera** arbetsflöden. Mer information finns i [Duplicera arbetsflöden](build-a-workflow.md#duplicate-workflows).

### Namn på aktiviteten {#name-of-the-activity}

När du utvecklar ditt arbetsflöde får alla aktiviteter ett namn, liksom alla Adobe Campaign-objekt. När namnet genereras av verktyget rekommenderar vi att du byter namn på det med ett explicit namn när du konfigurerar det. Risken med att göra det senare är att det kan avbryta arbetsflödet med aktiviteter med hjälp av namnet på en annan tidigare aktivitet. Det skulle därför vara svårt att uppdatera namnen efteråt.

Aktivitetsnamnet finns i **[!UICONTROL Advanced]** -fliken. Låt dem inte namnges **[!UICONTROL query]**, **[!UICONTROL query1]**, **[!UICONTROL query11]**, men ge dem explicita namn som **[!UICONTROL querySubscribedRecipients]**. Det här namnet visas i journalen, och om tillämpligt i SQL-loggarna, och det hjälper till att felsöka arbetsflödet när det konfigureras.

### Första och sista aktiviteten {#first-and-last-activities}

* Starta alltid arbetsflödet med en **[!UICONTROL Start]** aktivitet eller **[!UICONTROL Scheduler]** aktivitet. När det är relevant kan du även använda en **[!UICONTROL External signal]** aktivitet.
* När du skapar arbetsflödet ska du bara använda ett **[!UICONTROL Scheduler]** aktivitet per gren. Om samma gren i ett arbetsflöde har flera schemaläggare (länkade till varandra) så multipliceras antalet uppgifter som ska utföras exponentiellt vilket skulle innebära att databasen överbelastas avsevärt. Den här regeln gäller även alla aktiviteter med en **[!UICONTROL Scheduling & History]** -fliken. Läs mer på [Schemaläggning](scheduler.md).

   ![](assets/wf-scheduler.png)

* Använd **[!UICONTROL End]** aktiviteter för varje arbetsflöde. På så sätt kan Adobe Campaign frigöra temporärt utrymme som används för beräkningar i arbetsflöden. Mer information finns i: [Start och slut](start-and-end.md).

### Javascript inom en aktivitet {#javascript-within-an-activity}

Du kanske vill lägga till JavaScript när du initierar en arbetsflödesaktivitet. Detta kan göras i en aktivitets **[!UICONTROL Advanced]** aktivitetens flik.

Om du vill göra det enklare att spåra arbetsflödet rekommenderar vi att du använder dubbla streck i början och slutet av aktivitetsetiketten enligt följande: — Min etikett —.

### Signal {#signal}

Oftast vet du inte varifrån signalen anropas. För att undvika det här problemet använder du **[!UICONTROL Comment]** fält i **[!UICONTROL Advanced]** signalaktivitetens flik för att dokumentera det förväntade ursprunget för en signal för denna aktivitet.

## Uppdateringar om arbetsflöden {#workflow-update}

Ett produktionsarbetsflöde får inte uppdateras direkt. Om inte processen består av att skapa en kampanj med mallarbetsflöden, bör processerna först testas i en utvecklingsmiljö. Efter den här valideringen kan arbetsflödet distribueras och startas i produktionen.

Utför alla tester i utvecklings- eller testmiljöer, inte i produktionsmiljöer. Prestanda kan inte säkerställas i sådana fall.

Arkiverade arbetsflöden kan finnas på utvecklings- eller testplattformar i en arkiverad mapp, men produktionsmiljön bör vara så ren som möjligt. Gamla arbetsflöden bör tas bort från produktionsmiljön om de är inaktiva.

## Körning och prestanda {#execution-and-performance}

### Loggar {#logs}

JavaScript-metoden **[!UICONTROL logInfo()]** är en lösning för att felsöka ett arbetsflöde. Den måste dock användas med försiktighet, särskilt för aktiviteter som ofta utförs: loggarna kan överbelastas och storleken på loggtabellen kan öka avsevärt.

### Behåll tillfälliga populationer

The **Behåll resultatet från mellanliggande populationer mellan två avrättningar** Alternativet håller temporära tabeller mellan två körningar av ett arbetsflöde.

Den är tillgänglig i arbetsflödesegenskapernas **[!UICONTROL General]** och kan användas för utveckling och testning för att övervaka data och kontrollera resultat. Du kan använda det här alternativet i utvecklingsmiljöer, men aldrig använda det i produktionsmiljöer. Om du behåller tillfälliga tabeller kan databasens storlek öka avsevärt och så småningom kan storleksgränsen nås. Dessutom kommer säkerhetskopieringen att bli långsammare.

Endast arbetsregister för den senaste körningen av arbetsflödet behålls. Arbetsregister från tidigare körningar rensas av **[!UICONTROL cleanup]** arbetsflöde, som körs dagligen.

>[!CAUTION]
>
>Det här alternativet måste **aldrig** checkas in i **produktion** arbetsflöde. Det här alternativet används för att analysera resultaten och är utformat endast för teständamål och ska därför endast användas i utvecklings- eller stagingmiljöer.


### Logga SQL-frågor

The **Logga SQL-frågor i journalen** finns i **[!UICONTROL Execution]** fliken med arbetsflödesegenskaper. Med det här alternativet loggas alla SQL-frågor från de olika aktiviteterna, och det är ett sätt att se vad som faktiskt utförs av plattformen. Det här alternativet bör dock endast användas **temporärt** under utveckling och **inte aktiverat vid produktion**.

Det bästa är att rensa loggarna när de inte behövs längre. Arbetsflödeshistorik rensas inte automatiskt: alla meddelanden behålls som standard. Historiken kan rensas via **[!UICONTROL File > Actions]** eller genom att klicka på knappen Åtgärder i verktygsfältet ovanför listan. Välj Rensa historik.
Mer information om hur du tömmer dina loggar finns i [dokumentation](start-a-workflow.md).

### Arbetsflödesplanering {#workflow-planning}

Ytterligare metodtips bör tillämpas på din körningsplanering för arbetsflöden för att undvika problem:

* Behåll en stabil aktivitetsnivå under dagen och undvik toppar för att förhindra att instansen överbelastas. Det gör du genom att fördela arbetsflödets starttider jämnt över hela dagen.
* Schemalägg datainläsning över en natt för att minska resurskonflikter.
* Långa arbetsflöden kan eventuellt påverka server- och databasresurserna. Dela de längsta arbetsflödena för att minska bearbetningstiden.
* Om du vill minska den totala körtiden ersätter du tidskrävande aktiviteter med förenklade och snabbare aktiviteter.
* Undvik att köra fler än 20 arbetsflöden samtidigt. När alltför många arbetsflöden körs samtidigt kan plattformen överbelastas och bli instabil.

### Arbetsflödeskörning {#workflow-execution}

Förbättra instansstabiliteten genom att implementera följande metodtips:

* **Schemalägg inte ett arbetsflöde så att det körs mer än var 15:e minut** eftersom det kan påverka systemets prestanda negativt och skapa block i databasen.

* **Undvik att lämna arbetsflödena i pausat läge**. Om du skapar ett tillfälligt arbetsflöde måste du se till att det kan slutföras korrekt och inte stanna i en **[!UICONTROL paused]** tillstånd. Om den pausas innebär det att du måste behålla de temporära tabellerna och på så sätt öka storleken på databasen. Tilldela arbetsflödesgranskare under Arbetsflödesegenskaper för att skicka en avisering när ett arbetsflöde misslyckas eller pausas av systemet.

   Så här undviker du att arbetsflöden är i pausat läge:

   * Kontrollera dina arbetsflöden regelbundet för att se om det inte finns några oväntade fel.
   * Håll arbetsflödena så enkla som möjligt, t.ex. genom att dela upp stora arbetsflöden i flera olika arbetsflöden. Du kan använda **[!UICONTROL External signal]** aktiviteter utlöser sin körning baserat på andra arbetsflödenas körning.
   * Undvik inaktiverade aktiviteter med arbetsflöden som lämnar trådar öppna och leder till många tillfälliga tabeller som kan ta mycket plats. Behåll inte aktiviteter i **[!UICONTROL Do not enable]** eller **[!UICONTROL Enable but do not execute]** lägen i dina arbetsflöden.

* **Stoppa oanvända arbetsflöden**. Arbetsflöden som fortsätter att köras behåller anslutningar till databasen.

* **Använd endast ovillkorlig stop i de sällsynta fallen**. Använd inte den här åtgärden regelbundet. Utan att utföra en ren stängning av anslutningar som genereras av arbetsflöden till databasen påverkar prestanda.

* **Utför inte flera stoppbegäranden i samma arbetsflöde**. Att stoppa ett arbetsflöde är en asynkron process: Begäran registreras och arbetsflödesservern eller servrarna avbryter pågående åtgärder. Det kan därför ta tid att stoppa en arbetsflödesinstans, särskilt om arbetsflödet körs på flera servrar, där var och en måste ta kontroll för att avbryta de pågående åtgärderna. Om du vill undvika problem väntar du tills stoppåtgärden har slutförts och undviker att stoppa ett arbetsflöde flera gånger.

### Kör i motoralternativet {#execute-in-the-engine-option}

Undvik att köra arbetsflöden i motorn i en produktionsmiljö. När **[!UICONTROL Execute in the engine]** alternativet är markerat i **[!UICONTROL Workflow properties]**, får arbetsflödet prioritet och alla andra arbetsflöden stoppas av arbetsflödesmotorn tills det är klart.

![](assets/wf-execute-in-engine.png)