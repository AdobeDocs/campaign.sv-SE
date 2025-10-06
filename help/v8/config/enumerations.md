---
title: Hantera uppräkningar
description: Lär dig arbeta med uppräkningar
feature: Configuration, Application Settings
role: Developer
version: Campaign v8, Campaign Classic v7
level: Intermediate, Experienced
source-git-commit: 2898fe400e9bf53fc2fe8fde26ccc61ec43bc69e
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 0%

---

# Arbeta med uppräkningar {#enumerations}

En uppräkning (kallas även för en specificerad lista) är en fördefinierad lista med värden som du kan använda för att fylla i vissa fält. Uppräkningar hjälper till att standardisera fältvärden, vilket gör datainmatningen mer konsekvent och förenklar frågor.

Värdena visas i en nedrullningsbar lista när de är tillgängliga. Du kan antingen välja ett värde direkt eller börja skriva - prediktiv inmatning föreslår matchning av värden och slutför dem automatiskt.

![](assets/enum_values.png)

Vissa konsolfält har konfigurerats med uppräkningar. Om en uppräkning är **öppen** kan du även lägga till nya värden direkt i fältet.

![Åtkomstuppräkningar](../config/assets/enumerations-menu.png)

## Uppräkningstyper {#types-of-enum}

Uppräkningar lagras i mappen **[!UICONTROL Administration > Platform > Enumerations]** i Utforskaren.

De kan vara: Open, System, Emoticon eller Closed.

* Med en **Open**-uppräkning kan användare lägga till nya värden direkt i fälten baserat på den här uppräkningen.
* En **stängd**-uppräkning har en fast lista med värden som bara kan ändras från mappen **[!UICONTROL Administration > Platform > Enumerations]** i Utforskaren.
* En **uttryckssymbol**-uppräkning används för att uppdatera uttryckslistan. Läs mer
* En **System**-uppräkning är kopplad till systemfält och kommer med ett internt namn.

Det finns specifika alternativ för uppräkningarna **Öppna** och **Stängda**:

* **Enkel uppräkning** är standardtypen.
* Uppräkning för **Aliasrensning** används för att harmonisera uppräkningsvärdena som lagras i databasen. [Läs mer](#alias-cleansing)
* **Reserverad för bindning** är ett alternativ som gör att du kan länka kubvärden till den här uppräkningen. [Läs mer](../reporting/gs-cubes.md)


## Rensa alias {#alias-cleansing}

I uppräkningsfälten kan du välja ett värde eller ange ett anpassat värde som inte är tillgängligt i listrutan. Anpassade värden kan läggas till i de befintliga uppräkningsvärdena, som ett nytt - i det här fallet måste alternativet **[!UICONTROL Open]** väljas. Dessa anpassade värden kan rensas med hjälp av funktioner för aliasrensning. Om en användare till exempel anger `Adob` i stället för `Adobe` kan aliasrensningsprocessen automatiskt ersätta den med rätt term.

>[!CAUTION]
>
>Datarensning är en kritisk process som påverkar data i databasen. Adobe Campaign genomför massuppdateringar, vilket kan leda till att vissa värden tas bort. Den här åtgärden är därför reserverad för expertanvändare.

Aktivera alternativet **[!UICONTROL Alias cleansing]** om du vill använda datarensningsfunktioner för en uppräkning. När det här alternativet är markerat visas fliken **[!UICONTROL Alias]** längst ned i fönstret.

När en användare anger ett värde som inte finns i en uppräkning för aliasrensning läggs det till i listan **Värden**. Du kan [skapa alias från dessa värden](#convert-to-alias) eller [skapa nya alias från grunden](#create-alias).

### Skapa ett alias{#create-alias}

Så här skapar du ett alias:

1. Klicka på knappen **[!UICONTROL Add]** på fliken **[!UICONTROL Alias]**.
1. Ange det alias som du vill konvertera och välj det värde som ska användas i listrutan.

   ![Skapa ett nytt alias](assets/new-alias.png)

1. Klicka på **[!UICONTROL Ok]** och bekräfta.

1. Spara ändringarna. Värdena ersätts av **aliasrensningsarbetsflödet** som körs varje natt. Se [Kör datarensning](#running-data-cleansing).

När en användare anger värdet **Adobe** i ett&quot;företag&quot;-fält (i Adobe Campaign Client Console i ett webbformulär) ersätts det automatiskt av värdet **Adobe** för alla fält som baseras på den här uppräkningen.

### Konvertera fel värde till alias{#convert-to-alias}

Du kan också konvertera ett befintligt uppräkningsvärde till ett alias. Så här gör du:

1. Högerklicka och bläddra till **[!UICONTROL Actions... > Convert values into aliases...]** i listan med värden för en uppräkning.

   ![Konvertera ett värde till ett alias](assets/convert-into-aliases.png)

1. Markera de värden som ska konverteras i alias och klicka på **[!UICONTROL Next]**.
1. Klicka på **[!UICONTROL Start]** för att köra konverteringen.

   När körningen är klar läggs alias till i listan på fliken **Alias**. Du kan associera ett korrekt värde om du vill ersätta fel poster. Så här gör du:

1. Välj ett värde som ska rensas.
1. Klicka på knappen **Detalj..**.
1. Välj det nya värdet i listrutan.

   ![Skapa ett nytt alias](assets/define-new-alias.png)


>[!NOTE]
>
>Du kan spåra förekomster av ett alias i kolumnen **[!UICONTROL Hits]** på underfliken **[!UICONTROL Alias]**. Den kan visa hur många gånger det här värdet har angetts.  [Läs mer](#calculate-entry-occurrences).

### Kör datarensning {#running-data-cleansing}

Datarensning utförs av det tekniska arbetsflödet **[!UICONTROL Alias cleansing]**. Som standard utförs den dagligen.

Rensningen kan också utlösas via länken **[!UICONTROL Cleanse values...]**.

Med länken **[!UICONTROL Advanced parameters...]** kan du ange från vilket datum insamlade värden ska tas med i beräkningen.

Klicka på knappen **[!UICONTROL Start]** om du vill köra datarensning.

### Övervaka förekomster {#calculate-entry-occurrences}

Underfliken **[!UICONTROL Alias]** i en uppräkning kan visa antalet förekomster av ett alias bland alla angivna värden. Den här informationen är en uppskattning och visas i kolumnen **[!UICONTROL Hits]**.

>[!CAUTION]
>
>Det kan ta lång tid att beräkna aliaspostförekomster.
>

Du kan köra träffberäkning manuellt via länken **[!UICONTROL Cleanse values...]**. Det gör du genom att klicka på länken **[!UICONTROL Advanced parameters...]** och välja alternativ.

* **[!UICONTROL Update the number of alias hits]**: Detta gör att du kan uppdatera träffar som redan har beräknats baserat på det angivna datumet.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: gör att du kan köra beräkning på hela Adobe Campaign-plattformen.

Du kan också skapa ett dedikerat arbetsflöde så att beräkningen körs automatiskt för en viss period, till exempel en gång i veckan.

Det gör du genom att skapa en kopia av arbetsflödet **[!UICONTROL Alias cleansing]**, ändra schemaläggaren och använda följande inställningar i aktiviteten **[!UICONTROL Enumeration value cleansing]**:

* **-updateHits** om du vill uppdatera antalet aliasträffar,
* **-updateHits:full** om du vill beräkna om alla aliasträffar.
