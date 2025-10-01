---
title: Hantera uppräkningar
description: Lär dig arbeta med uppräkningar
feature: Configuration, Application Settings
role: Developer
version: Campaign v8, Campaign Classic v7
level: Intermediate, Experienced
source-git-commit: 428de72e0459b95a6db0b06ec8541d0475b72fdd
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%

---

# Hantera uppräkningar {#manage-enumerations}

En uppräkning (kallas även för en specificerad lista) är en fördefinierad lista med värden som du kan använda för att fylla i vissa fält. Uppräkningar hjälper till att standardisera fältvärden, vilket gör datainmatningen mer konsekvent och förenklar frågor.

Värdena visas i en nedrullningsbar lista när de är tillgängliga. Du kan antingen välja ett värde direkt eller börja skriva - prediktiv inmatning föreslår matchning av värden och slutför dem automatiskt.

![](assets/enum_values.png)

Vissa konsolfält har konfigurerats med uppräkningar. Om en uppräkning är **öppen** kan du även lägga till nya värden direkt i fältet.

## Åtkomstuppräkningar

Värdena som används i dessa fält hanteras centralt. Du kan lägga till, redigera, uppdatera eller ta bort dem från Utforskarträdet, under **Administration** `>` **Plattform** `>` **Uppräkningar**.

* I det övre avsnittet finns en lista med fält för vilka en uppräkning har definierats.
* I det nedre avsnittet visas tillgängliga värden.

När en uppräkning är **[!UICONTROL Open]** kan användare ange ett nytt värde direkt i motsvarande fält i användargränssnittet.

När en uppräkning är **[!UICONTROL Closed]** kan nya värden bara läggas till från menyn **Uppräkning**.

## Lägg till ett nytt värde

Om du vill skapa ett nytt uppräkningsvärde klickar du på knappen **[!UICONTROL Add]**.

![](assets/enumeration_screen.png)

Ange värdets etikett.


## Rensa alias {#alias-cleansing}

I uppräkningsfälten kan du ange andra värden än uppräkningsvärden. Dessa kan antingen lagras som de är eller rensas.

>[!CAUTION]
>
>Datarensning är en kritisk process som påverkar data i databasen. Adobe Campaign genomför massuppdateringar, vilket kan leda till att vissa värden tas bort. Den här åtgärden är därför reserverad för expertanvändare.

Det angivna värdet är då antingen:

* Tillagd i de specificerade listvärdena: i det här fallet måste alternativet **[!UICONTROL Open]** väljas,
* eller ersätts automatiskt av motsvarande alias: i det här fallet måste det definieras på fliken **[!UICONTROL Alias]** i den specificerade listan.
* eller lagras i listan med alias: ett alias kan tilldelas senare.

### Skapa ett alias {#creating-an-alias}

Alternativet **[!UICONTROL Alias cleansing]** gör det möjligt att använda alias för den valda specificerade listan. När det här alternativet är markerat visas fliken **[!UICONTROL Alias]** längst ned i fönstret.

Så här skapar du ett alias:

1. Bläddra till uppräkningen för att uppdatera klickningen **[!UICONTROL Add]**.

   ![](assets/enumeration_alias_create.png)

1. Ange det alias som du vill konvertera och det värde som ska användas och klicka på **[!UICONTROL Ok]**.

1. Kontrollera parametrarna innan du bekräftar den här åtgärden.

>[!CAUTION]
>
>När det här steget har bekräftats kan de tidigare värdena inte återställas: de ersätts.

När en användare anger värdet **NEILSEN** i ett&quot;företag&quot;-fält (i Adobe Campaign-konsolen eller i ett formulär) ersätts det alltså automatiskt av värdet **NIELSEN Ltd**. Värderingsersättningen utförs av **aliasrensningsarbetsflödet**. Se [Kör datarensning](#running-data-cleansing).

![](assets/enumeration_alias_use.png)

### Konvertera värden till alias {#values-into-aliases}

Du kan konvertera befintliga värden till alias. Gör så här:

1. Högerklicka i listan med värden och välj **[!UICONTROL Convert values into aliases...]**.

1. Välj de värden som ska konverteras och klicka på **[!UICONTROL Next]**.

1. Klicka på **[!UICONTROL Start]** för att köra konverteringen.

När körningen är klar läggs aliaset till i listan över alias.

### Hämta aliasträffar {#alias-hits}

När användare anger värden som inte ingår i uppräkningen lagras de på fliken **[!UICONTROL Alias]**.

Det tekniska arbetsflödet **Aliasrensning** återställer dessa värden varje kväll för att uppdatera uppräkningen. Se [Kör datarensning](#running-data-cleansing)

Om det behövs kan kolumnen **[!UICONTROL Hits]** visa hur många gånger det här värdet har angetts. Det kan dock vara både tids- och minneskrävande att beräkna det här värdet. Mer information finns i [Beräkna inmatningsförekomster](#calculating-entry-occurrences).

### Kör datarensning {#run-data-cleansing}

Datarensning utförs av det tekniska arbetsflödet **[!UICONTROL Alias cleansing]**. De konfigurationer som definieras för uppräkningar tillämpas under körningen. Se [Aliasrensningsarbetsflöde](#alias-cleansing-workflow).

Rensningen kan utlösas via länken **[!UICONTROL Cleanse values...]**.

Med länken **[!UICONTROL Advanced parameters...]** kan du ange från vilket datum insamlade värden ska tas med i beräkningen.

Klicka på knappen **[!UICONTROL Start]** om du vill köra datarensning.

### Beräkna anmälningsförekomster {#entry-occurrences}

Underfliken **[!UICONTROL Alias]** i en specificerad lista kan visa antalet förekomster av ett alias bland alla angivna värden. Den här informationen är en uppskattning och visas i kolumnen **[!UICONTROL Hits]**.

>[!CAUTION]
>
>Det kan ta lång tid att beräkna aliaspostförekomster. Därför bör försiktighet iakttas när den här funktionen används.

Du kan köra träffberäkning manuellt via länken **[!UICONTROL Cleanse values...]**. Om du vill göra det klickar du på länken **[!UICONTROL Advanced parameters...]** och väljer önskade alternativ.

* **[!UICONTROL Update the number of alias hits]**: Detta gör att du kan uppdatera träffar som redan har beräknats baserat på det angivna datumet.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: gör att du kan köra beräkning på hela Adobe Campaign-plattformen.

Du kan också skapa ett dedikerat arbetsflöde så att beräkningen körs automatiskt för en viss period, till exempel en gång i veckan.

Det gör du genom att skapa en kopia av arbetsflödet **[!UICONTROL Alias cleansing]**, ändra schemaläggaren och använda följande inställningar i aktiviteten **[!UICONTROL Enumeration value cleansing]**:

* **-updateHits** om du vill uppdatera antalet aliasträffar,
* **-updateHits:full** om du vill beräkna om alla aliasträffar.

### Rensningsarbetsflöde för alias {#alias-cleansing-workflow}

Arbetsflödet **Aliasrensning** kör uppräkningsvärderensning. Som standard utförs den dagligen.

Den nås via noden **[!UICONTROL Administration > Production > Technical workflows]**.


