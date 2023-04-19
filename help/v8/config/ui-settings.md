---
title: Inställningar för kampanjgränssnitt
description: Lär dig hur du anpassar inställningarna för gränssnittet i Campaign
version: v8
feature: Application Settings
role: Admin, Developer
level: Beginner, Intermediate, Experienced
source-git-commit: 0b4483e0f16f14582a1a4bc28b0e1ff719823ef3
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 1%

---

# Inställningar för gränssnittet i kampanjen {#ui-settings}

## Uppräkningar {#enumerations}

En uppräkning (kallas även&quot;lista med specificerade värden&quot;) är en lista med värden som föreslås av systemet för att fylla i fält. Använd uppräkningar för att standardisera värdena för dessa fält, hjälp med inmatning av data eller användning inom frågor.

Värdelistan visas som en nedrullningsbar lista där du kan välja vilket värde som ska anges i fältet. Listrutan möjliggör även prediktiv inmatning: anger de första bokstäverna så fyller programmet i resten.

Värdena för den här typen av fält definieras och den övergripande administrationen av dessa fält (genom att lägga till/ta bort ett värde) utförs via **[!UICONTROL Administration > Platform > Enumerations]** trädnod.

![Åtkomstuppräkningar](assets/enumerations-menu.png)

### Uppräkningstyper {#types-of-enum}

Uppräkningar lagras i **[!UICONTROL Administration > Platform > Enumerations]** Utforskarens mapp.

De kan vara: Öppna, System, Moticon eller Stängd.

* An **Öppna** Med uppräkning kan användare lägga till nya värden direkt i de fält som är baserade på den här uppräkningen.
* A **Stängd** uppräkningen har en fast lista med värden som bara kan ändras från **[!UICONTROL Administration > Platform > Enumerations]** Utforskarens mapp.
* An **Emoticon** uppräkning används för att uppdatera uttryckslistan. Läs mer
* A **System** uppräkningen är kopplad till systemfält och kommer med ett internt namn.

För **Öppna** och **Stängd** uppräkningar, specifika alternativ är tillgängliga:

* **Enkel uppräkning** är standardstandardtypen.
* **Rensa alias** uppräkningen används för att harmonisera uppräkningsvärdena som lagras i databasen. [Läs mer](#alias-cleansing)
* **Reserverad för bindning** är ett alternativ som gör att du kan länka kubvärden till den här uppräkningen. [Läs mer](../reporting/gs-cubes.md)


### Rensa alias {#alias-cleansing}

I uppräkningsfälten kan du välja ett värde eller ange ett anpassat värde som inte är tillgängligt i listrutan. Anpassade värden kan läggas till i de befintliga uppräkningsvärdena som ett nytt - i det här fallet **[!UICONTROL Open]** måste vara markerat. Dessa anpassade värden kan rensas med hjälp av aliasrensningsfunktioner. Om en användare till exempel anger `Adob` i stället för `Adobe`, kan aliasrensningsprocessen automatiskt ersätta den med rätt term.

>[!CAUTION]
>
>Datarensning är en kritisk process som påverkar data i databasen. Adobe Campaign genomför massuppdateringar, vilket kan leda till att vissa värden tas bort. Den här åtgärden är därför reserverad för expertanvändare.

Aktivera **[!UICONTROL Alias cleansing]** om du vill använda datarensningsfunktioner för en uppräkning. När det här alternativet är markerat visas **[!UICONTROL Alias]** -fliken visas längst ned i fönstret.

När en användare anger ett värde som inte finns i en uppräkning för aliasrensning läggs det till i **Värden** lista. Du kan [skapa alias utifrån dessa värden](#convert-to-alias), eller [skapa nya alias från grunden](#create-alias).

#### Skapa ett alias{#create-alias}

Så här skapar du ett alias:

1. Klicka **[!UICONTROL Add]** knappen **[!UICONTROL Alias]** -fliken.
1. Ange det alias som du vill konvertera och välj det värde som ska användas i listrutan.

   ![Skapa ett nytt alias](assets/new-alias.png)

1. Klicka **[!UICONTROL Ok]** och bekräfta.

1. Spara ändringarna. Ersättningen av värden utförs av **Rensa alias** arbetsflöde som körs varje kväll. Se [Kör datarensning](#running-data-cleansing).

För alla fält som baseras på den här uppräkningen, när en användare anger värdet **Adobe** i ett&quot;företag&quot;-fält (i Adobe Campaign-konsolen, i ett webbformulär) ersätts det automatiskt med värdet **Adobe**.

#### Konvertera fel värde till alias{#convert-to-alias}

Du kan också konvertera ett befintligt uppräkningsvärde till ett alias. Så här gör du:

1. Högerklicka och bläddra till listan med värden för en uppräkning **[!UICONTROL Actions... > Convert values into aliases...]**.

   ![Konvertera ett värde till ett alias](assets/convert-into-aliases.png)

1. Markera de värden som ska konverteras i alias och klicka på **[!UICONTROL Next]**.
1. Klicka **[!UICONTROL Start]** för att köra konverteringen.

   När körningen är klar läggs alias till i listan i **Alias** -fliken. Du kan associera ett korrekt värde om du vill ersätta fel poster. Så här gör du:

1. Välj ett värde som ska rensas.
1. Klicka på **Detalj...** -knappen.
1. Välj det nya värdet i listrutan.

   ![Skapa ett nytt alias](assets/define-new-alias.png)


>[!NOTE]
>
>Du kan spåra förekomster av ett alias i dialogrutan **[!UICONTROL Hits]** kolumn i **[!UICONTROL Alias]** underflik. Den kan visa hur många gånger det här värdet har angetts.  [Läs mer](#calculate-entry-occurrences).

#### Kör datarensning {#running-data-cleansing}

Datarensning utförs av **[!UICONTROL Alias cleansing]** tekniskt arbetsflöde. Som standard utförs den dagligen.

Rensning kan också aktiveras via **[!UICONTROL Cleanse values...]** länk.

The **[!UICONTROL Advanced parameters...]** -länken kan du ange det datum från vilket insamlade värden ska tas med i beräkningen.

Klicka på **[!UICONTROL Start]** för att köra datarensning.

##### Övervaka förekomster {#calculate-entry-occurrences}

The **[!UICONTROL Alias]** en uppräknings underflik kan visa antalet förekomster av ett alias bland alla värden som anges. Den här informationen är en uppskattning och kommer att visas i **[!UICONTROL Hits]** kolumn.

>[!CAUTION]
>
>Det kan ta lång tid att beräkna aliaspostförekomster.

Du kan köra träffberäkning manuellt via **[!UICONTROL Cleanse values...]** länk. Om du vill göra det klickar du på **[!UICONTROL Advanced parameters...]** och välj alternativ.

* **[!UICONTROL Update the number of alias hits]**: gör att du kan uppdatera träffar som redan har beräknats, baserat på det angivna datumet.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: gör att du kan köra beräkningar på hela Adobe Campaign-plattformen.

Du kan också skapa ett dedikerat arbetsflöde så att beräkningen körs automatiskt för en viss period, till exempel en gång i veckan.

Om du vill göra det skapar du en kopia av **[!UICONTROL Alias cleansing]** arbetsflöde, ändra schemaläggaren och använd följande inställningar i **[!UICONTROL Enumeration value cleansing]** aktivitet:

* **-updateHits** för att uppdatera antalet aliasträffar,
* **-updateHits:full** om du vill beräkna om alla aliasträffar.
