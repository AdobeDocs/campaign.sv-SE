---
product: campaign
title: Läsa in data (fil)
description: Läs mer om arbetsflödesaktiviteten Datainläsning (fil)
feature: Workflows, Data Management Activity
role: User
exl-id: 10351620-115c-4bd8-b216-e5ad6f205ef3
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 14%

---

# Läsa in data (fil){#data-loading-file}



## Använd {#use}

The **[!UICONTROL Data loading (File)]** gör att du kan komma åt en extern datakälla och använda den i Adobe Campaign. Alla data som krävs för målinriktade åtgärder finns inte alltid i Adobe Campaign-databasen: de kan göras tillgängliga i externa filer.

Filen som ska läsas in kan anges av övergången eller beräknas under körningen av aktiviteten. Det kan till exempel vara en lista över en kunds 10 favoritprodukter vars inköp hanteras i en extern databas.

I det övre avsnittet av konfigurationsfönstret för den här aktiviteten kan du definiera filformatet. Om du vill göra det använder du en exempelfil med samma format som den som ska importeras. Filen kan lagras lokalt eller på servern.

>[!CAUTION]
>
>Endast &quot;platta&quot; strukturfiler stöds (t.ex. CSV, TXT). Du bör inte använda XML-formatet.

![](assets/s_advuser_wf_etl_file.png)

Du kan definiera en förprocess som ska utföras under filimport, t.ex. för att inte behöva packa upp filen på servern (och därför spara utrymme för den uppzippade filen) utan för att inkludera uppzippning i filbearbetningen. Välj **[!UICONTROL Pre-process the file]** och välj något av tre alternativ: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) eller **[!UICONTROL Decrypt]** (gpg)

![](assets/preprocessing-dataloading.png)

>[!IMPORTANT]
>
>Du kan inte dekomprimera zippade filer som är större än 4 GB.

## Definiera filformatet {#defining-the-file-format}

När du läser in en fil identifieras kolumnformatet automatiskt med standardparametrarna för varje datatyp. Du kan ändra de här standardparametrarna för att ange vilka processer som ska tillämpas på din data särskilt när det finns ett fel eller ett tomt värde.

Gör detta genom att välja **[!UICONTROL Click here to change the file format...]** i huvudfönstret i **[!UICONTROL Data loading (file)]** aktivitet. Fönstret Formatinformation öppnas.

![](assets/file_loading_columns_format.png)

Du kan sedan ändra den allmänna formateringen för filen samt formateringen för varje kolumn.

Med den allmänna filformateringen kan du definiera hur kolumnerna ska identifieras (filkodning, avgränsare, osv.).

Med kolumnformateringen kan du definiera värdebearbetningen för varje kolumn:

* **[!UICONTROL Ignore column]**: bearbetar inte den här kolumnen under datainläsning.
* **[!UICONTROL Data type]**: Anger den typ av data som förväntas för varje kolumn.
* **[!UICONTROL Allow NULLs]**: anger hur tomma värden ska hanteras.

   * **[!UICONTROL Adobe Campaign default]**: genererar ett fel endast för numeriska fält. Annars läggs ett NULL-värde in.
   * **[!UICONTROL Empty value allowed]**: anger tomma värden.  Värdet NULL infogas därför.
   * **[!UICONTROL Always populated]**: genererar ett fel om ett värde är tomt.

* **[!UICONTROL Length]**: anger det maximala antalet tecken för **string** datatyp.
* **[!UICONTROL Format]**: definierar tids- och datumformatet.
* **[!UICONTROL Data transformation]**: definierar om en skiftlägesprocess för tecken måste tillämpas på en **string**.

   * **[!UICONTROL None]**: den importerade strängen ändras inte.
   * **[!UICONTROL First letter in upper case]**: den första bokstaven i varje ord i strängen börjar med ett versal.
   * **[!UICONTROL Upper case]**: alla tecken i strängen skrivs med stora bokstäver.
   * **[!UICONTROL Lower case]**: alla tecken i strängen är i gemener.

* **[!UICONTROL White space management]**: anger om vissa blanksteg måste ignoreras i en sträng. The **[!UICONTROL Ignore spaces]** Värdet tillåter bara att blanksteg i början och i slutet av en sträng ignoreras.
* **[!UICONTROL Error processings]**: definierar beteendet om ett fel påträffas.

   * **[!UICONTROL Ignore the value]**: värdet ignoreras.  En varning genereras i arbetsflödets körningslogg.
   * **[!UICONTROL Reject line]**: hela raden bearbetas inte.
   * **[!UICONTROL Use a default value in case of error]**: ersätter det värde som orsakar felet med ett standardvärde som definieras i fältet **[!UICONTROL Default value]**.
   * **[!UICONTROL Reject the line when there is no remapping value]**: hela raden bearbetas inte såvida inte en mappning har definierats för det felaktiga värdet (se **[!UICONTROL Mapping]** nedan).
   * **[!UICONTROL Use a default value in case the value is not remapped]**: ersätter det värde som orsakar felet med ett standardvärde som definieras i **[!UICONTROL Default value]** om inte en mappning har definierats för det felaktiga värdet (se **[!UICONTROL Mapping]** nedan).

* **[!UICONTROL Default value]**: anger standardvärdet enligt vald felbearbetning.
* **[!UICONTROL Mapping]**: det här fältet är endast tillgängligt i kolumndetaljkonfigurationen (nås via en dubbelklickning eller via alternativen till höger om kolumnlistan). Detta omformar vissa värden när de importeras. Du kan till exempel omvandla &quot;tre&quot; till &quot;3&quot;.

## Exempel: Samla in data och läsa in dem i databasen {#example--collecting-data-and-loading-it-in-the-database}

I följande exempel kan du samla in en fil på servern varje dag, läsa in dess innehåll och uppdatera data i databasen beroende på vilken information den innehåller. Den fil som ska samlas in innehåller information om kunder som kan ha gjort inköp (för mer eller mindre än 3 000 euro), begärt att få pengarna tillbaka på ett köp eller besökt butiken utan att köpa något. Beroende på den här informationen tillämpas olika processer på deras profil i databasen.

![](assets/s_advuser_load_file_sample_0.png)

1. Med filsamlaren kan du återställa filer som lagras i en katalog, beroende på den angivna frekvensen.

   The **[!UICONTROL Directory]** -fliken innehåller information om de filer som ska återställas. I det här exemplet återställs alla filer i textformat vars namn innehåller ordet &quot;kunder&quot; och som lagras i katalogen tmp/Adobe/Data/files på servern.

   Använda **[!UICONTROL File collector]** finns i [Filinsamlare](file-collector.md) -avsnitt.

   ![](assets/s_advuser_load_file_sample_1.png)

   The **[!UICONTROL Schedule]** Med kan du schemalägga körningen av insamlaren, dvs. för att ange med vilken frekvens som förekomsten av dessa filer ska kontrolleras.

   Här vill vi aktivera samlaren varje arbetsdag klockan nio.

   ![](assets/s_advuser_load_file_sample_2.png)

   Klicka på **[!UICONTROL Change...]** i det nedre högra avsnittet av redigeringsverktyget och konfigurera schemat.

   Mer information finns i [Schemaläggare](scheduler.md).

1. Konfigurera sedan aktiviteten för inläsning av data (fil) för att ange hur de insamlade filerna ska läsas. Det gör du genom att markera en exempelfil med samma struktur som de filer som ska läsas in.

   ![](assets/s_advuser_load_file_sample_3.png)

   Här innehåller filen fem kolumner:

   * den första kolumnen innehåller en kod som sammanfaller med evenemanget: köp (mer eller mindre än 3 000 euro), inget köp eller någon återbetalning för ett eller flera inköp.
   * De fyra följande kolumnerna innehåller klientens förnamn, efternamn, e-postadress och kontonummer.

   Formatkonfigurationen för filen som ska läsas in sammanfaller med den som definieras vid dataimport i Adobe Campaign.

1. I den delade aktiviteten anger du de delmängder som ska skapas enligt **Händelse** kolumnvärde.

   Aktiviteten Dela är detaljerad i avsnittet.

   ![](assets/s_advuser_load_file_sample_4.png)

   För varje delmängd anger du ett av värdena i **Händelse** kolumn.

   ![](assets/s_advuser_load_file_sample_5.png)

   The **[!UICONTROL Split]** Verksamheten kommer därför att innehålla följande information:

   ![](assets/s_advuser_load_file_sample_6.png)

1. Ange sedan de processer som ska utföras för varje typ av population. I vårt exempel kommer vi att **[!UICONTROL Update the data]** i databasen. Gör detta genom att placera en **[!UICONTROL Update data]** aktiviteten i slutet av varje utgående övergång från den delade aktiviteten.

   The **[!UICONTROL Update data]** aktiviteten visas i [Uppdatera data](update-data.md) -avsnitt.
