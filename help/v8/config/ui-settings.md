---
title: Inställningar för kampanjgränssnitt
description: Lär dig hur du anpassar inställningarna för gränssnittet i Campaign
feature: Application Settings
role: Admin, Developer
level: Beginner
exl-id: 9fa6fc42-45be-41db-9b4a-19b3b0c40dcd
source-git-commit: 2898fe400e9bf53fc2fe8fde26ccc61ec43bc69e
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 0%

---

# Inställningar för gränssnittet i kampanjen {#ui-settings}

## Standardenheter {#default-units}

I Adobe Campaign kan värden uttryckas i följande **enheter** för fält som uttrycker en varaktighet (t.ex. resursernas giltighetsperiod, sista datum för godkännande av en uppgift):

* **[!UICONTROL s]** i sekunder
* **[!UICONTROL mn]** i minuter
* **[!UICONTROL h]** i timmar
* **[!UICONTROL d]** i dagar

## Anpassa Campaign Explorer{#customize-explorer}

Du kan lägga till mappar i Campaign Explorer, skapa vyer och tilldela behörigheter.

Lär dig hantera mappar och vyer på [den här sidan](../audiences/folders-and-views.md)

## Hantera och anpassa listor {#customize-lists}

I Campaign Client Console visas data i listor. Du kan anpassa listorna efter dina behov. Du kan till exempel lägga till kolumner, filtrera data, räkna poster, spara och dela inställningarna.

Dessutom kan du skapa och spara filter.  Läs mer om filter på [den här sidan](../audiences/create-filters.md).

### Antal poster {#number-of-records}

Som standard läser Adobe Campaign in de första 200 posterna i en lista. Det innebär att visningen inte nödvändigtvis visar alla poster i tabellen som du visar. Du kan räkna antalet poster i listan och läsa in fler poster.

I den nedre högra delen av listskärmen visar en **räknare** hur många poster som har lästs in och det totala antalet poster i databasen (efter att eventuella filter har använts):

![Visa totalt antal poster i en lista](assets/number-of-records.png)

Om ett frågetecken visas i stället för numret till höger, till exempel `240/?`, klickar du på räknaren för att starta beräkningen.

Klicka **[!UICONTROL Continue loading]** om du vill läsa in och visa fler poster. Som standard läses 200 poster in. Om du vill ändra standardantalet poster som ska läsas in använder du ikonen **[!UICONTROL Configure list]** längst ned till höger i listan. Klicka på **[!UICONTROL Advanced parameters]** (längst ned till vänster) i fönstret för listkonfigurationen och ändra antalet rader som ska hämtas.

Om du vill läsa in alla poster högerklickar du på listan och väljer **[!UICONTROL Load all]**.

>[!CAUTION]
>
>När en lista innehåller många poster kan det ta en stund att läsa in hela filen.
>

### Lägga till och ta bort kolumner {#add-columns}

För varje lista kan den inbyggda kolumnkonfigurationen anpassas för att visa mer information eller dölja oanvända kolumner.

När data visas i detaljerna för en post högerklickar du på fältet och väljer **[!UICONTROL Add in the list]**.

![Lägg till ett fält i listan](assets/add-in-the-list.png)

Kolumnen läggs till till höger om de befintliga kolumnerna.

![Lägg till en fältkolumn](assets/add-a-column.png)

Du kan också använda skärmen för listkonfiguration för att lägga till och ta bort kolumner:

1. Klicka på ikonen **[!UICONTROL Configure list]** längst ned till höger i en lista med poster.
1. Dubbelklicka på fälten som ska läggas till i listan **[!UICONTROL Available fields]**: de läggs till i listan **[!UICONTROL Output columns]**.

   ![Visa konfigurationsskärmen](assets/list-config-screen.png)


   >[!NOTE]
   >
   >Som standard visas inte avancerade fält. Om du vill visa dem klickar du på ikonen **Visa avancerade fält** längst ned till höger i listan med tillgängliga fält.
   >
   >Fält identifieras av specifika ikoner: SQL-fält, länkade tabeller, beräkningsfält osv. För varje markerat fält visas beskrivningen under listan med tillgängliga fält.
   >

1. Använd upp-/nedpilarna för att ändra **visningsordningen**.

1. Klicka på **[!UICONTROL OK]** för att bekräfta konfigurationen och visa resultatet.

Om du behöver ta bort en kolumn markerar du den och klickar på ikonen **Papperskorgen** .

Du kan använda ikonen **[!UICONTROL Distribution of values]** för att visa ompartitionen av värden för det valda fältet i den aktuella mappen.

![](assets/value-distribution.png)


### Skapa en ny kolumn {#create-a-new-column}

Du kan skapa nya kolumner för att visa ytterligare fält i listan.

Så här skapar du en kolumn:

1. Klicka på ikonen **[!UICONTROL Configure list]** längst ned till höger i en lista med poster.
1. Klicka på ikonen **[!UICONTROL Add]** om du vill visa ett nytt fält i listan.
1. Konfigurera fältet som ska läggas till i kolumnen.


### Visa data i undermappar {#display-sub-folders-records}

Listor kan visa:

* Alla poster i den valda mappen (standard)
* Alla poster i den markerade mappen och dess undermappar

Om du vill växla från ett visningsläge till ett annat klickar du på **[!UICONTROL Display sub-levels]** i verktygsfältet Kampanj.

### Spara en listkonfiguration {#saving-a-list-configuration}

Listkonfigurationerna definieras lokalt för varje användare. När den lokala cachen rensas inaktiveras lokala konfigurationer.

Som standard gäller inställningsparametrar för alla listor med motsvarande mapptyp. När du ändrar hur listan med mottagare visas från en mapp, tillämpas den här konfigurationen på alla andra mottagarmappar.

Du kan spara mer än en konfiguration som ska användas för olika mappar av samma typ. Konfigurationen sparas med egenskaperna för den mapp som innehåller data och kan tillämpas på nytt.

Så här sparar du en listkonfiguration så att den kan återanvändas:

1. I Utforskaren högerklickar du på mappen som innehåller de data som visas.
1. Välj **[!UICONTROL Properties]**.
1. Klicka på **[!UICONTROL Advanced settings]** och ange sedan ett namn i fältet **[!UICONTROL Configuration]**.
1. Klicka på **[!UICONTROL OK]** och sedan på **[!UICONTROL Save]**.

Du kan sedan använda den här konfigurationen i en annan mapp av samma typ. Läs mer om mappar på [den här sidan](../audiences/folders-and-views.md).

### Exportera en lista {#exporting-a-list}

Om du vill exportera data från en lista måste du använda en exportguide. Om du vill komma åt den markerar du de element som ska exporteras från listan, högerklickar och väljer **[!UICONTROL Export...]**.

<!--The use of the import and export functions is explained in [Generic imports and exports](../../platform/using/about-generic-imports-exports.md).-->

>[!CAUTION]
>
>Element från en lista får inte exporteras med funktionen Kopiera/Klistra in.

### Sortera en lista {#sorting-a-list}

Listor kan innehålla en stor mängd data. Du kan sortera dessa data eller använda enkla eller avancerade filter. Med sortering kan du visa data i stigande eller fallande ordning. Med filter kan du definiera och kombinera villkor så att endast markerade data visas.

Klicka på kolumnrubriken om du vill använda en stigande eller fallande sortering eller om du vill avbryta sorteringen. Aktiv sorteringsstatus och sorteringsordning anges med en blå pil före kolumnetiketten. Ett rött streck före kolumnetiketten betyder att sorteringen tillämpas på data som indexeras från databasen. Den här sorteringsmetoden används för att optimera sorteringsjobb.

Du kan också konfigurera sortering eller kombinera sorteringsvillkor. Gör så här:

1. **[!UICONTROL Configure list]** nedanför och till höger om listan.
1. Klicka på fliken **[!UICONTROL Sorting]** i listkonfigurationsfönstret.
1. Markera de fält som ska sorteras och sorteringsriktningen (stigande eller fallande).
1. Sorteringsprioriteten definieras av sorteringskolumnernas ordning. Om du vill ändra prioriteten använder du lämpliga ikoner för att ändra ordningen på kolumnerna.

   Sorteringsprioriteten påverkar inte visningen av kolumnerna i listan.

1. Klicka på **[!UICONTROL Ok]** för att bekräfta konfigurationen och visa resultatet i listan.


## Ytterligare resurser

* **[Börja med användargränssnittet för Campaign](../start/campaign-ui.md)** - Upptäck hur du kommer åt och bläddrar i Adobe Campaign-gränssnittet.
* **[Arbeta med uppräkningar](../config/enumerations.md)** - Standardisera fältvärden med fördefinierade listrutor för snabbare och enhetligare datainmatning.
