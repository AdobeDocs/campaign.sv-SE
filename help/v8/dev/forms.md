---
title: Formulär för kampanjindata
description: Lär dig hur du anpassar indataformulär
exl-id: 62908bba-9cfa-42b6-b463-b601496d535b
source-git-commit: 391eac2f5e4d4c8c5d4dadd3394798361640e1d8
workflow-type: tm+mt
source-wordcount: '2552'
ht-degree: 0%

---

# Kom igång med indataformulär{#gs-ac-forms}

När du skapar eller utökar ett schema måste du skapa eller ändra de associerade indataformulären för att göra ändringarna synliga för slutanvändarna.

Med ett inmatningsformulär kan du redigera en instans som är associerad med ett dataschema från Adobe Campaign klientkonsol. Formuläret identifieras av dess namn och namnutrymme.

Identifieringsnyckeln för ett formulär är en sträng som består av namnutrymmet och namnet avgränsat med ett kolon, till exempel: &quot;cus:contact&quot;.

## Redigera inmatningsformulär

Skapa och konfigurera indataformulär från mappen **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** i klientkonsolen:

![](assets/form_arbo.png)

I redigeringszonen kan du ange XML-innehållet i indataformuläret:

![](assets/form_edit.png)

Förhandsgranskningen genererar en visning av indataformuläret:

![](assets/form_preview.png)

## Formulärstruktur

Beskrivningen av ett formulär är ett strukturerat XML-dokument som observerar formulärschemats grammatik **xtk:form**.

XML-dokumentet i indataformuläret måste innehålla rotelementet `<form>` med attributen **name** och **namespace** för att fylla i formulärnamnet och namnutrymmet.

```
<form name="form_name" namespace="name_space">
...
</form>
```

Som standard är ett formulär kopplat till dataschemat med samma namn och namnutrymme. Om du vill associera ett formulär med ett annat namn anger du **entity-schema**-attributet för `<form>`-elementet till schemanyckelns namn. Om du vill visa strukturen för ett inmatningsformulär kan du beskriva ett gränssnitt med exempelschemat &quot;cus:mottagare&quot;:

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="Male" value="1"/>   
    <value name="female" label="Female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
    <attribute name="birthDate" type="datetime" label="Date"/>
    <attribute name="gender" type="byte" label="Gender" enum="gender"/>
  </element>
</srcSchema>
```

Indataformuläret baserat på exempelschemat:

![](assets/do-not-localize/form_exemple1.png)

```
<form name="recipient" namespace="cus">
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email"/>
</form>
```

Beskrivningen av redigeringskontrollerna startar från rotelementet `<form>`. En redigeringskontroll anges i ett **`<input>`**-element med attributet **xpath** som innehåller sökvägen för fältet i dess schema.

Redigeringskontrollen anpassas automatiskt till motsvarande datatyp och använder den etikett som definierats i schemat.

>[!NOTE]
>
>Du kan skriva över etiketten som definierats i dess dataschema genom att lägga till attributet **label** till elementet `<input>`:\
>`<input label="E-mail address" xpath="@name" />`

Som standard visas varje fält på en rad och tar upp allt tillgängligt utrymme beroende på datatypen.

![](../assets/do-not-localize/book.png) Alla formulärattribut visas i dokumentationen [ för ](https://experienceleague.adobe.com/developer/campaign-api/api/control-Button.html)Campaign Classic v7.

## Formatering {#formatting}

Layouten på kontrollerna ser ut som den layout som används i tabeller i HTML, med möjlighet att dela upp en kontroll i flera kolumner, sammanflätade element eller ange hur mycket utrymme som finns tillgängligt. Tänk dock på att du bara kan dela upp området efter proportioner med formateringen. Du kan inte ange fasta dimensioner för ett objekt.

Så här visar du kontrollerna i exemplet ovan i två kolumner:

![](assets/do-not-localize/form_exemple2.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email"/>
  </container>
</form>
```

Med elementet **`<container>`** med attributet **colcount** kan du tvinga visningen av underordnade kontroller till två kolumner.

**colspan**-attributet på en kontroll utökar kontrollen med det antal kolumner som har angetts i värdet:

![](assets/do-not-localize/form_exemple3.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form> 
```

Genom att fylla i attributet **type=&quot;frame&quot;** lägger behållaren till en ram runt de underordnade kontrollerna med etiketten som finns i attributet **label**:

![](assets/do-not-localize/form_exemple4.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2" type="frame" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form>
```

Ett **`<static>`**-element kan användas för att formatera indataformuläret:

![](assets/do-not-localize/form_exemple5.png)

```
<form name="recipient" namespace="cus">
  <static type="separator" colspan="2" label="General"/>
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email" colspan="2"/>
  <static type="help" label="General information about recipient with date of birth, gender, and e-mail address." colspan="2"/>
</form>
```

Med taggen **`<static>`** med typen **avgränsare** kan du lägga till en avgränsare med en etikett i attributet **label**.

En hjälptext lades till med taggen `<static>` med hjälptypen. Innehållet i texten anges i attributet **label**.

## Använd behållare {#containers}

Använd **behållare** för att gruppera en uppsättning kontroller. De representeras av elementet **`<container>`**. De användes ovan för att formatera kontroller över flera kolumner.

Med attributet **xpath** på en `<container>` kan du förenkla referenserna för underordnade kontroller. Referensen för kontroller är sedan relativ till den överordnade `<container>`.

Exempel på en behållare utan &quot;xpath&quot;:

```
<container colcount="2">
  <input xpath="location/@zipCode"/>
  <input xpath="location/@city"/>
</container>
```

Exempel med tillägget &quot;xpath&quot; i elementet &quot;location&quot;:

```
<container colcount="2" xpath="location">
  <input xpath="@zipCode"/>
  <input xpath="@city"/>
</container>
```

Behållare används för att skapa komplexa kontroller med hjälp av en uppsättning fält som är formaterade på sidor.

### Lägg till flikar (anteckningsbok) {#tab-container}

Använd en **anteckningsbok**-behållare för att formatera data på sidor som är tillgängliga från flikar.

![](assets/do-not-localize/form_exemple6.png)

```
<container type="notebook">
  <container colcount="2" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location">
    ...
  </container>
</container>
```

Huvudbehållaren definieras av attributet **type=&quot;anteckningsbok&quot;**. Tabbar deklareras i de underordnade behållarna och etiketten för flikarna fylls i från attributet **label**.

Lägg till attributet **style=&quot;down&quot;** för att tvinga fram den lodräta placeringen av tabbetiketter under kontrollen. Det här attributet är valfritt. Standardvärdet är **&quot;upp&quot;**.

![](assets/do-not-localize/form_exemple7.png)

`<container style="down" type="notebook">  ... </container>`

### Lägg till ikoner (ikonruta) {#icon-list}

Använd den här behållaren för att visa ett lodrätt ikonfält där du kan välja vilka sidor som ska visas.

![](assets/do-not-localize/form_exemple8.png)

```
<container type="iconbox">
  <container colcount="2" label="General" img="xtk:properties.png">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location" img="nms:msgfolder.png">
    ...
  </container>
</container>
```

Huvudbehållaren definieras av attributet **type=&quot;iconbox&quot;**. De sidor som är associerade med ikonerna deklareras i de underordnade behållarna. Etiketten för ikonerna fylls i från attributet **label**.

Ikonen för en sida fylls i från attributet `img="<image>"`, där `<image>` är namnet på bilden som motsvarar dess nyckel som består av namnet och namnutrymmet (t.ex. &quot;xtk:properties.png&quot;).

Bilderna är tillgängliga från noden **[!UICONTROL Administration > Configuration > Images]**.

### Dölj behållare (visibleGroup) {#visibility-container}

Du kan dölja en uppsättning kontroller via ett dynamiskt villkor.

I det här exemplet visas synligheten för kontroller av värdet i fältet &quot;Kön&quot;:

```
<container type="visibleGroup" visibleIf="@gender=1">
  ...
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  ...
</container>
```

En synlighetsbehållare definieras av attributet **type=&quot;visibleGroup&quot;**. Attributet **visibleIf** innehåller synlighetsvillkoret.

Exempel på villkorssyntax:

* **visibleIf=&quot;@email=&#39;peter.martinezATneolane.net&#39;&quot;**: testar likhet för strängtypsdata. Jämförelsevärdet måste anges inom citattecken.
* **visibleIf=&quot;@kön >= 1 och @kön != 2&quot;**: villkor för ett numeriskt värde.
* **visibleIf=&quot;@boolean1=true eller @boolean2=false&quot;**: test on Boolean fields.

### Villkorlig visning (enabledGroup) {#enabling-container}

Med den här behållaren kan du aktivera eller inaktivera en uppsättning data från ett dynamiskt villkor. Om du inaktiverar en kontroll kan du inte redigera den. I följande exempel visas aktiveringen av kontroller från värdet i fältet Genus:

```
<container type="enabledGroup" enabledIf="@gender=1">
  ...
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  ...
</container>
```

En aktiveringsbehållare definieras av attributet **type=&quot;enabledGroup&quot;**. Attributet **enabledIf** innehåller aktiveringsvillkoret.

## Redigera en länk {#editing-a-link}

Kom ihåg att en länk deklareras i dataschemat enligt följande:

```
<element label="Company" name="company" target="cus:company" type="link"/>
```

Redigeringskontrollen för länken i indataformuläret är följande:

![](assets/do-not-localize/form_exemple9.png)

```
<input xpath="company"/>
```

Målmarkeringen är tillgänglig via redigeringsfältet. Posten assisteras av typen ahead så att ett målelement enkelt kan hittas från de första tecknen som anges. Sökningen baseras sedan på **beräkningssträngen** som definierats i målschemat. Om schemat inte finns efter valideringen i kontrollen visas ett bekräftelsemeddelande om att målet har skapats direkt. Bekräftelsen skapar en ny post i måltabellen och kopplar den till länken.

En nedrullningsbar lista används för att välja ett målelement från listan med poster som redan har skapats.

Ikonen **[!UICONTROL Modify the link]** (mapp) startar ett urvalsformulär med listan över målelement och en filterzon.

Ikonen **[!UICONTROL Edit link]** (förstorare) startar redigeringsformen för det länkade elementet. Formuläret som används dras som standard av nyckeln för målschemat. Med attributet **form** kan du tvinga fram namnet på redigeringsformuläret (t.ex. &quot;cus:company2&quot;).

Du kan begränsa valet av målelement genom att lägga till elementet **`<sysfilter>`** från länkdefinitionen i indataformuläret:

```
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

Du kan även sortera listan med elementet **`<orderby>`**:

```
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

## Kontrollegenskaper {#control-properties}

* **noAutoComplete**: inaktiverar type-ahead (med värdet &quot;true&quot;)
* **createMode**: skapar länken i farten om den inte finns. Möjliga värden är:

   * **ingen**: inaktiverar skapande. Ett felmeddelande visas om länken inte finns
   * **textbunden**: skapar länken med innehållet i redigeringsfältet
   * **utgåva**: visar redigeringsformuläret på länken. När formuläret valideras sparas data (standardläge)

* **noZoom**: inget redigeringsformulär på länken (med värdet &quot;true&quot;)
* **formulär**: överför målelementets redigeringsform

## Lägg till en lista med länkar (obunden) {#list-of-links}

En länk som anges i dataschemat som ett samlingselement (unbound=&quot;true&quot;) måste gå igenom en lista för att alla element som är associerade med den ska kunna visas.

Principen består i att visa listan med länkade element med optimerad datainläsning (nedladdning per datauppsättning, körning av listan endast om den är synlig).

Exempel på en samlingslänk i ett schema:

```
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
...
</element>
```

Listan i indataformuläret:

```
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Listkontrollen definieras av attributet **type=&quot;linklist&quot;**. Listsökvägen måste referera till samlingslänken.

Kolumnerna deklareras via **`<input>`**-elementen i listan. Attributet **xpath** refererar till sökvägen för fältet i målschemat.

Ett verktygsfält med en etikett (som definieras på länken i schemat) placeras automatiskt ovanför listan.

Listan kan filtreras med knappen **[!UICONTROL Filters]** och konfigureras för att lägga till och sortera kolumnerna.

Med knapparna **[!UICONTROL Add]** och **[!UICONTROL Delete]** kan du lägga till och ta bort samlingselement på länken. Om du lägger till ett element startas målschemats redigeringsformulär som standard.

Knappen **[!UICONTROL Detail]** läggs till automatiskt när attributet **zoom=&quot;true&quot;** har slutförts i taggen **`<input>`** i listan: kan du starta redigeringsformuläret för den markerade raden.

Filtrering och sortering kan användas när listan läses in:

```
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
  <orderBy>
    <node expr="@date" sortDesc="true"/>
  </orderBy>
</input>
```

## Definiera en relationstabell {#relationship-table}

Med en relationstabell kan du länka två tabeller med N-N-kardinalitet. Relationstabellen innehåller bara länkarna till de två tabellerna.

Om du lägger till ett element i listan bör du därför kunna fylla i en lista från en av de två länkarna i relationstabellen.

Exempel på en relationstabell i ett schema:

```
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

Vi börjar t.ex. med indataformen för &quot;cus:mottagare&quot;-schemat. Listan måste visa associationer med abonnemang på tjänster och du måste kunna lägga till en prenumeration genom att välja en befintlig tjänst.

![](assets/do-not-localize/form_exemple12.png)

```
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

Med attributet **xpathChoiceTarget** kan du starta ett urvalsformulär från den angivna länken. Om du skapar relationstabellposten uppdateras länken till den aktuella mottagaren och den valda tjänsten automatiskt.

>[!NOTE]
>
>Med attributet **xpathEditTarget** kan du tvinga fram redigering av den markerade raden på den angivna länken.

### Listegenskaper {#list-properties}

* **noToolbar**: döljer verktygsfältet (med värdet &quot;true&quot;)
* **toolbarBildtext**: överför verktygsfältsetiketten
* **toolbarAlign**: ändrar verktygsfältets lodräta eller vågräta geometri (möjliga värden: &quot;vertical&quot;|&quot;horizontal&quot;)
* **img**: visar bilden som är associerad med listan
* **formulär**: överför målelementets redigeringsform
* **zooma**: lägger till  **[!UICONTROL Zoom]** knappen för att redigera målelementet
* **xpathEditTarget**: anger redigering för den angivna länken
* **xpathChoiceTarget**: dessutom startar urvalsformuläret på den angivna länken

## Lägga till minneslistkontroller {#memory-list-controls}

Med minneslistor kan du redigera samlingselementen med förinläsning av listdata. Listan kan inte filtreras eller konfigureras.

De här listorna används för XML-mappade samlingselement eller på länkar med låg volym.

## Lägga till en kolumnlista {#column-list}

Den här kontrollen visar en redigerbar kolumnlista med ett verktygsfält som innehåller knapparna Lägg till och Ta bort.

```
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Listkontrollen måste fyllas i med attributet **type=&quot;list&quot;**, och sökvägen till listan måste referera till mängdelementet.

Kolumnerna deklareras i de underordnade **`<input>`**-taggarna för listan. Kolumnetikett och kolumnstorlek kan tvingas med attributen **label** och **colSize**.

>[!NOTE]
>
>Pilar för sorteringsordning läggs till automatiskt när attributet **ordered=&quot;true&quot;** läggs till i samlingselementet i dataschemat.

Verktygsfältsknapparna kan justeras vågrätt:

```
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

**toolbarCaption**-attributet tvingar verktygsfältets vågräta justering och anger titeln ovanför listan.

### Aktivera zoomning i en lista {#zoom-in-a-list}

Du kan infoga och redigera data i en lista i ett separat redigeringsformulär.

```
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true" zoomOnAdd="true">
  <input xpath="@label"/>
  <input xpath="@date"/>

  <form colcount="2" label="Event">
    <input xpath="@label"/>
    <input xpath="@date"/>
  </form>
</input>
```

Redigeringsformuläret har fyllts i från `<form>`-elementet under listdefinitionen. Dess struktur är identisk med strukturen för ett indataformulär. Knappen **[!UICONTROL Detail]** läggs till automatiskt när attributet **zoom=&quot;true&quot;** har slutförts i taggen **`<input>`** i listan. Med det här attributet kan du starta redigeringsformuläret för den markerade raden.

>[!NOTE]
>
>Om du lägger till attributet **zoomOnAdd=&quot;true&quot;** anropas redigeringsformuläret när ett listelement infogas.

### Listegenskaper {#list-properties-1}

* **noToolbar**: döljer verktygsfältet (med värdet &quot;true&quot;)
* **toolbarBildtext**: överför verktygsfältsetiketten
* **toolbarAlign**: ändrar verktygsfältets placering (möjliga värden: &quot;vertical&quot;|&quot;horizontal&quot;)
* **img**: visar bilden som är associerad med listan
* **formulär**: överför målelementets redigeringsform
* **zooma**: lägger till  **[!UICONTROL Zoom]** knappen för att redigera målelementet
* **zoomOnAdd**: öppnar redigeringsformuläret samtidigt
* **xpathChoiceTarget**: dessutom startar urvalsformuläret på den angivna länken

## Lägg till icke-redigerbara fält {#non-editable-fields}

Om du vill visa ett fält och förhindra att det redigeras använder du taggen **`<value>`** eller slutför attributet **readOnly=&quot;true&quot;** för taggen **`<input>`**.

Exempel på fältet&quot;Kön&quot;:

![](assets/do-not-localize/form_exemple16.png)

```
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## Lägg till alternativknapp {#radio-button}

Med en alternativknapp kan du välja mellan flera alternativ. **`<input>`**-taggarna används för att lista möjliga alternativ, och **checkedValue**-attributet anger det värde som är associerat med valet.

Exempel på fältet&quot;Kön&quot;:

```
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/do-not-localize/form_exemple17.png)

## Lägg till en kryssruta {#checkbox}

En kryssruta återspeglar ett booleskt läge (markerat eller inte). Som standard används den här kontrollen av fälten &quot;Boolean&quot; (true/false). En variabel med standardvärdet 0 eller 1 kan kopplas till den här knappen. Det här värdet kan överladdas via attributen **checkValue**.

```
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/do-not-localize/form_exemple20.png)

## Redigera navigeringshierarki {#navigation-hierarchy-edit}

Den här kontrollen skapar ett träd i en uppsättning fält som ska redigeras.

Kontrollerna som ska redigeras grupperas i en **`<container>`** som anges under taggen **`<input>`** för trädkontrollen:

```
<input nolabel="true" type="treeEdit">
  <container label="Text fields">
    <input xpath="@text1"/>
    <input xpath="@text2"/>
  </container>
  <container label="Boolean fields">
    <input xpath="@boolean1"/>
    <input xpath="@boolean2"/>
  </container>
</input>
```

![](assets/do-not-localize/form_exemple18.png)

## Lägga till ett uttrycksfält {#expression-field}

Ett uttrycksfält uppdaterar ett fält dynamiskt från ett uttryck; taggen **`<input>`** används med attributet **xpath** för att ange sökvägen till fältet som ska uppdateras och ett **expr**-attribut som innehåller uppdateringsuttrycket.

```
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## Formulärsammanhang {#context-of-forms}

Körningen av ett inmatningsformulär initierar ett XML-dokument som innehåller data för enheten som redigeras. Det här dokumentet representerar formulärets kontext och kan användas som en arbetsyta.

### Uppdatera kontexten {#updating-the-context}

Om du vill ändra formulärets kontext använder du taggen `<set expr="<value>" xpath="<field>"/>`, där `<field>` är målfältet och `<value>` är uppdateringsuttrycket eller uppdateringsvärdet.

Exempel på användning av taggen `<set>`:

* **`<set expr="'Test'" xpath="/tmp/@test" />`**: placerar värdet för Test på den temporära platsen /tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**: uppdaterar entiteten för attributet lastName med värdet Test
* **`<set expr="true" xpath="@boolean1" />`**: ställer in värdet för fältet &quot;boolean1&quot; till &quot;true&quot;
* **`<set expr="@lastName" xpath="/tmp/@test" />`**: uppdateras med innehållet i attributet&quot;lastName&quot;

Formulärets kontext kan uppdateras när formuläret initieras och stängs via taggarna **`<enter>`** och **`<leave>`**.

```
<form name="recipient" namespace="cus">
  <enter>
    <set...
  </enter>
  ...
  <leave>
    <set...
  </leave>
</form>
```

>[!NOTE]
>
>`<enter>` och `<leave>`   -taggar kan användas på `<container>` sidor (&quot;anteckningsbok&quot; och&quot;ikon&quot;).

### Uttrycksspråk {#expression-language-}

Ett makrospråk kan användas i formulärdefinitionen för att utföra villkorstester.

Taggen **`<if expr="<expression>" />`** kör instruktionerna som anges under taggen om uttrycket verifieras:

```
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

Taggen **`<check expr="<condition>" />`** i kombination med taggen **`<error>`** förhindrar validering av formuläret och visar ett felmeddelande om villkoret inte uppfylls:

```
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

## Assistent (guide) {#wizards}

En assistent guidar dig genom en uppsättning datainmatningssteg i form av sidor. De data som anges sparas när du validerar formuläret.

Om du vill lägga till en assistent använder du följande typ av struktur:

```
<form type="wizard" name="example" namespace="cus" img="nms:rcpgroup32.png" label="Wizard example" entity-schema="nms:recipient">
  <container title="Title of page 1" desc="Long description of page 1">
    <input xpath="@lastName"/>
    <input xpath="comment"/>
  </container>
  <container title="Title of page 2" desc="Long description of page 2">
    ...
  </container>
  ...
</form>
```

Om **type=&quot;wizard&quot;**-attributet finns i `<form>`-elementet kan du definiera guideläget när du skapar formuläret. Sidorna fylls i från `<container>`-element, som är underordnade `<form>`-elementet. `<container>`-elementet för en sida fylls i med rubrikattributen för rubriken och desc för att visa beskrivningen under sidrubriken. Knapparna **[!UICONTROL Previous]** och **[!UICONTROL Next]** läggs till automatiskt för att tillåta bläddring mellan sidor.

Knappen **[!UICONTROL Finish]** sparar de data som anges och stänger formuläret.

### SOAP-metoder {#soap-methods}

Körning av SOAP-metoder kan startas från en ifylld **`<leave>`**-tagg i slutet av en sida.

Taggen **`<soapcall>`** innehåller anropet till metoden med följande indataparametrar:

```
<soapCall name="<name>" service="<schema>">
  <param type="<type>" exprIn="<xpath>"/>  
  ...
</soapCall>
```

Namnet på tjänsten och dess implementeringsschema anges via attributen **name** och **service** för taggen **`<soapcall>`**.

Indataparametrarna beskrivs i **`<param>`**-elementen under taggen **`<soapcall>`**.

Parametertypen måste anges via attributet **type**. Möjliga typer är:

* **sträng**: teckensträng
* **boolesk**: Boolean
* **byte**: 8-bitars heltal
* **kort**: 16-bitars heltal
* **long**: 32-bitars heltal
* **kort**: 16-bitars heltal
* **dubbel**: flyttal med dubbel precision
* **DOMElement**: elementtypsnod

Attributet **exprIn** innehåller platsen för de data som ska skickas som en parameter.

**Exempel**:

```
<leave>
  <soapCall name="RegisterGroup" service="nms:recipient">         
    <param type="DOMElement" exprIn="/tmp/entityList"/>         
    <param type="DOMElement" exprIn="/tmp/choiceList"/>         
    <param type="boolean"    exprIn="true"/>       
  </soapCall>
</leave>
```
