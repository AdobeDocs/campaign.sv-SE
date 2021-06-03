---
product: Adobe Campaign
title: Kampanjinteraktion - Erbjudandehantering
description: Kom igång med erbjudandehantering
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: b11b42220dae7d0a878ba102523ee2825d6fb2e2
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 1%

---

# Interaktion och erbjudandehantering{#interaction-and-offer-management}

Campaign innehåller en **interaktionsmodul** som gör att du kan svara i realtid under en interaktion med en viss kontakt (en kund eller ett visst mål) genom att göra dem till ett eller flera anpassade erbjudanden. Det kan till exempel vara enkla kommunikationsmeddelanden, specialerbjudanden för en eller flera produkter eller en tjänst.

Du kan skapa en erbjudandekatalog som kommer att interagera med dina utgående kanaler (e-post, direktreklam, SMS) för att välja det bästa erbjudandet att skicka till en kontakt i ett visst sammanhang. Det bästa erbjudandevalet för en mottagare baseras på **berättiganderegler**. Urvalet av ett erbjudande från en uppsättning relevanta erbjudanden bestäms med hjälp av prioritetsregler. Regler för presentation av erbjudanden tar hänsyn till kontaktens historik och hjälper dig att undvika att få samma erbjudande flera gånger.

Med Interaction kan du skapa och hantera en katalog med erbjudanden och konfigurera regler och programteman som är länkade till dem. Beroende på vilken kanal du väljer kan innehållet anpassas tack vare olika återgivningsfunktioner. Slutligen kan du använda simuleringsmodulen för att beräkna effekten av en erbjudandepresentation.

## Kom igång med erbjudanden

Viktiga steg att starta visas nedan.

### Konfigurera plattformen

Innan du startar som Campaign **administratör** bör du kontrollera att du har utfört följande uppgifter i designmiljöer:

1. Skapa användarprofiler. [Läs mer](interaction-operators.md)
1. (valfritt) Skapa en erbjudandemiljö för varje målgruppsdimension. [Läs mer](interaction-env.md)
1. Skapa typologiregler för varje miljö. [Läs mer](interaction-offer.md#offer-presentation)
1. Skapa utrymme för varje miljö och konfigurera återgivningsfunktioner. [Läs ](interaction-offer-spaces.md)
merOm utrymmet definieras av en enhetskanal i identifierat läge måste du ange de avancerade parametrarna för det här utrymmet.

### Skapa och publicera erbjudandekatalogen {#managing-the-offer-catalog-}

Som **erbjudandehanterare** måste du utföra följande uppgifter:

1. Skapa erbjudandekategorier i designmiljöer. [Läs mer](interaction-offer-catalog.md#creating-offer-categories)
1. Skapa erbjudanden i designmiljöer. [Läs mer](interaction-offer.md)
1. Godkänn och publicera erbjudanden på ett eller flera platser för att göra dem tillgängliga för leveranshanteraren. [Läs mer](interaction-offer.md#approve-offers)

### Utnyttja erbjudandekatalogen {#using-the-offer-catalog-}

Som **leveranshanterare** måste du utföra följande uppgifter:

1. Skapa en kampanj.
1. Referera ett erbjudande i kampanjen eller leveransen. [Läs mer](interaction-send-offers.md).


## Begrepp och terminologi

Upptäck erbjudandespecifika villkor och tillhörande vägledning innan du börjar.

* **I** miljöer ingår en erbjudandekatalog och platser (krokar). Ni måste skapa en miljö genom att inrikta er på olika aspekter.
Det finns två typer av miljöer:

   * **Designmiljö**: erbjudanden skapas i designmiljön, liksom i typologiregler. Typologiregler avgör vilka erbjudanden som ska visas (eller inte) för en målperson. Tabellen över de individer som erbjudandena avser och tabellen för lagring av alla erbjudandeförslag definieras också i den här miljön. Noden **[!UICONTROL Design environment]** innehåller undermappar, fördefinierade filter och erbjudandekategorier. För varje **[!UICONTROL Design environment]** finns en motsvarande skrivskyddad **[!UICONTROL Live environment]** som genereras från samma **[!UICONTROL Design environment]**.
   * **Live-miljö**: miljö länkad till en  **[!UICONTROL Design environment]** som innehåller skrivskyddade erbjudanden vars innehåll och behörighet har godkänts via  **[!UICONTROL Design environment]**. De ska väljas för att läggas in i ett meddelande.

* **Erbjudandeutrymme** är en plats (mapp) som anger platsen där erbjudandet visas. När du skapar ett erbjudande kan du ange kanalen, bygga innehållet i erbjudandet med hjälp av återgivningsfunktioner, ange ordningen för erbjudandena och dess läge: enhetsläge och/eller gruppläge (standard). Erbjudandeutrymmet är gränssnittet mellan kanalen och erbjudandemotorn.
* **Erbjudandekatalogen** är en uppsättning erbjudanden som definieras i Adobe Campaign och som kan väljas under en interaktion. Katalogen ordnas hierarkiskt med varje nod som motsvarar en kategori.
* En **kategori** är en mapp som är länkad till erbjudandekatalogen i en miljö, som organiserar erbjudanden baserat på typ, berättigandedatum och programtema. En kategori kan innehålla underkategorier, som ärver alla egenskaper i den överordnade kategorin. Kvalifikationsregler kan definieras för en kategori så att de kan delas för flera erbjudanden.
* **Programteman** är nyckelord som definieras i kategorin, vilket gör att du kan filtrera erbjudanden när de presenteras genom att begränsa urvalet av erbjudanden till en eller två kategorier.
* **Behörighetsregler** är begränsningar som gäller för en miljö, kategori eller erbjudande, som avser giltighetsperiod, mål och vikt. Med dem kan ni se till att ett erbjudande är i linje med den avsedda kontakten.

   I miljöerna omfattar reglerna för rätt till uppgradering presentationsregler som tillämpas på erbjudandena och vilka personer som ska målgruppsanpassas.

   I kategorierna kan du begränsa kategoriens giltighet i tid, definiera programteman och avgöra vilka personer som ska väljas. De kan också få en multiplikatvikt för en viss tidsperiod. På så sätt kan du dela reglerna för erbjudanden i andra kategorier och på så sätt förenkla hanteringen av dem.

   I erbjudandena kan ni begränsa giltigheten för erbjudanden i tid och avgöra vilka personer som ska målgruppsanpassas.

* **Godtycke** är åtgärden att välja erbjudanden som ska visas i en miljö (giltiga erbjudanden). Skiljedomarna rangordnar erbjudanden efter prioritet enligt kriterierna som definieras i kategorierna, erbjudandena och sammanhangserbjudandena.
* En **utgående interaktion** anropar interaktionsmotorn från en kontaktlista (används för att leverera e-post, direktreklam osv.). Samma regler och processer tillämpas för varje kontakt. Den här typen av interaktion bearbetas vanligtvis i gruppläge.
* Med **batchläget** kan du välja det bästa erbjudandet för en uppsättning kontakter. Regler för behörighet/prioritering tillämpas på alla kontakter i uppsättningen. Det här läget används vanligtvis för utgående interaktioner.
* Med **enhetsläget** kan du bearbeta en enskild kontakt i taget. Det här läget används vanligtvis för transaktionsmeddelanden.
* **Berättigade** erbjudanden som uppfyller de definierade villkoren uppströms och som konsekvent kan erbjudas ett mål.
* **Presentationsregler är** typologiregler som refereras i erbjudandemiljön, som gör att du kan utesluta vissa erbjudanden genom att ta hänsyn till förslagshistoriken.
* **Med** viktningsformler kan du exakt beräkna hur relevant ett erbjudande är för att välja det mest relevanta erbjudandet. Vikten definieras i erbjudandena. Berättigade erbjudanden beaktas i minskande viktordning.
* **Återgivningsfunktionen** definieras i erbjudandeutrymmet för att skapa sin offertrepresentation baserat på de attribut som anges i erbjudandet. Det finns tre olika återgivningsfunktionslägen: HTML, XML och text.
* **Erbjudandet** är resultatet av en åtgärd som består av att presentera ett eller flera erbjudanden för en kontakt i ett givet utrymme (banner på en webbplats, ett e-postmeddelande eller ett SMS-meddelande till exempel). Det här resultatet lagras i tabellen för erbjudandeförslag. Det är dock inte obligatoriskt att spara förslagen.
* **Simulering** är en modul som gör att du kan testa erbjudandepresentationen för målmottagarna innan du skickar erbjudandena.
* **Förhandsgranskningen** av erbjudandet visar erbjudandet så som det visas i sin mapp. Den är tillgänglig från inställningsfönstret för erbjudandet eller kontaktprofilen.
* **Fördefinierade** filterfiltreringsregler kan ta hänsyn till erbjudandeparametrar (till exempel en erbjudandekod). De kan återanvändas efter att erbjudandena har skapats.
* En **Erbjudanderepresentation** är en information som används av kanalen för att visa erbjudandet. Erbjudanderepresentationen kan skapas med hjälp av återgivningsfunktionen i det utrymme där erbjudandet finns representerat eller anges direkt i gränssnittet (t.ex. i HTML-blocket). Ett erbjudande kan representeras av space.

