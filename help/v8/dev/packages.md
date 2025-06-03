---
title: Arbeta med datapaket
description: Arbeta med datapaket
feature: Data Management, Package Export/Import
role: Developer
level: Intermediate, Experienced
exl-id: bf1ae889-9c07-4acf-8fd0-55b57151bc47
version: Campaign v8, Campaign Classic v7
source-git-commit: a2efad26232cd380eea850a589b22b23928253e8
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 0%

---

# Arbeta med datapaket{#data-packages}

## Kom igång med paket {#gs-data-packages}

Du kan använda datapaket för att exportera och importera anpassade plattformsinställningar och data. Ett paket kan innehålla olika typer av konfigurationer och komponenter, filtrerade eller inte.

I Campaign-datapaket kan enheter i Adobe Campaign-databasen visas i XML-filer. I ett paket representeras varje entitet med alla dess data.

Principen för **datapaket** är att exportera en datakonfiguration och integrera den i en annan Adobe Campaign-miljö. Lär dig hur du upprätthåller en konsekvent uppsättning datapaket i det här [avsnittet](#data-package-best-practices).

### Typ av paket {#types-of-packages}

Du kan arbeta med tre typer av paket i Adobe Campaign: användarpaket, plattformspaket och administratörspaket.

* Med ett **användarpaket** kan du välja en lista över entiteter som ska exporteras. Den här typen av paket hanterar beroenden och kontrollerar fel.
* Ett **plattformspaket** innehåller alla tillagda tekniska resurser (ej standard): scheman, JavaScript-kod osv.
* Ett **administratörspaket** innehåller alla tillagda mallar och affärsobjekt (ej standard): mallar, bibliotek osv.

>[!CAUTION]
>
>Paketen **platform** och **admin** innehåller en fördefinierad lista med entiteter som ska exporteras. Varje entitet är länkad till filtervillkor som gör att du kan ta bort de färdiga resurserna i det skapade paketet.

## Datastruktur {#data-structure}

Beskrivningen av ett datapaket är ett strukturerat XML-dokument som är kompatibelt med grammatiken för dataramodellen **xrk:navtree**, som i exemplet nedan:

```xml
<package>
  <entities schema="nms:recipient">
    <recipient email="john.smith@adobe.com" lastName="Smith" firstName="John">      
      <folder _operation="none" name="nmsRootFolder"/>      
      <company _operation="none" name="Adobe"/>
    </recipient>
  </entities>
  <entities schema="sfa:company">
    <company name="Adobe">
      <location city="London" zipCode="W11 2BQ"/>
    </company>
  </entities>
</package>
```

XML-dokumentet måste börja och sluta med elementet `<package>`. Alla `<entities>`-element som följer distribuerar data efter dokumenttyp. Ett `<entities>`-element innehåller data från paketet i det format som datarammet som anges i attributet **schema** har. Data i ett paket får inte innehålla interna nycklar som inte är kompatibla mellan baser, till exempel autogenererade nycklar (**autopk** -alternativ).

I det här exemplet har kopplingarna på länkarna `folder` och `company` ersatts med så kallade &quot;high level&quot;-nycklar i måltabellerna:

```xml
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

Attributet `operation` med värdet `none` definierar en avstämningslänk.

Ett datapaket kan skapas manuellt från valfri textredigerare. Du måste se till att XML-dokumentets struktur överensstämmer med `xtk:navtree`-dataschemat. Klientkonsolen har en export- och importmodul för datapaket.

## Exportera paket {#export-packages}

Paket kan exporteras på tre olika sätt:

* Använd assistenten **[!UICONTROL Package Export]** för att exportera en uppsättning objekt i ett enskilt paket. [Läs mer](#export-a-set-of-objects-in-a-package)
* Om du vill exportera ett **enskilt objekt** högerklickar du på det och väljer **[!UICONTROL Actions > Export in a package]**.
* Använd **paketdefinitionerna** för att skapa en paketstruktur där du lägger till objekt som ska exporteras senare i ett paket. [Läs mer](#manage-package-definitions)

När ett paket har exporterats kan du importera det och alla tillagda enheter till en annan Campaign-instans.

### Exportera en uppsättning objekt i ett paket {#export-a-set-of-objects-in-a-package}

Så här exporterar du en uppsättning objekt i ett datapaket:

1. Bläddra till paketexportassistenten via **[!UICONTROL Tools > Advanced > Export package...]**-menyn i Utforskaren.
1. Välj [typer av paket](#types-of-packages).

   ![](assets/package_type.png)

1. Klicka på knappen **Lägg till** för att välja de enheter som ska exporteras som ett paket.

   >[!CAUTION]
   >
   >Om du exporterar en **[!UICONTROL Offer category]**-, **[!UICONTROL Offer environment]**-, **[!UICONTROL Program]**- eller **[!UICONTROL Plan]**-typmapp ska du aldrig markera **xtk:folder** eftersom du kan förlora vissa data. Välj den entitet som motsvarar mappen: **nms:offerCategory** för erbjudandekategorier, **nms:offerEnv** för erbjudandemiljöer, **nms:program** för program och **nms:plan** för planer.

   Beroendemekanismen styr entitetens exportsekvens. Mer information finns i [Hantera beroenden](#manage-dependencies).

1. Klicka på **[!UICONTROL Next]** och definiera filterfrågan för den typ av dokument som ska extraheras. Du måste konfigurera filtersatsen för dataextrahering.

   >[!NOTE]
   >
   >Frågeredigeraren visas i [det här avsnittet](../../automation/workflow/query.md).

1. Klicka på **[!UICONTROL Next]** och välj sorteringsordning för exporterade data.

1. Förhandsgranska de data som ska extraheras för att kontrollera konfigurationen.

1. På den sista sidan i paketets exportassistent kan du starta exporten. Data lagras i den fil som anges i fältet **[!UICONTROL File]**.

### Hantera beroenden {#manage-dependencies}

I exportprocessen spåras länkarna mellan de olika exporterade elementen. Den här mekanismen definieras av två regler:

* objekt som är länkade till en länk med en `own`- eller `owncopy`-typintegritet exporteras i samma paket som det exporterade objektet.
* objekt som är länkade till en länk med en `neutral`- eller `define`-typintegritet (definierad länk) måste exporteras separat.

>[!NOTE]
>
>Integritetstyper som är länkade till schemaelement definieras på [den här sidan](database-links.md).

#### Exportera en kampanj {#export-a-campaign}

Nedan visas ett exempel på hur du exporterar en kampanj. Marknadsföringskampanjen som ska exporteras innehåller:
* en `MyTask`aktivitet
* ett `campaignWorkflow`-arbetsflöde i följande mapp: **[!UICONTROL Administration > Production > Technical workflows > Campaign processes > MyWorkflow]**.

Aktiviteten och arbetsflödet exporteras i samma paket som kampanjen eftersom matchande scheman är kopplade av länkar med en `own`-typintegritet.

Paketinnehållet är:

```xml
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="7.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="2013-01-09 10:30:18.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="2013-01-14" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="2013-01-09">
   <controlGroup>
    <where filteringSchema=""/>
   </controlGroup>
   <seedList>
    <where filteringSchema="nms:seedMember"></where>
    <seedMember internalName="SDM1"></seedMember>
   </seedList>
   <parameter useAsset="1" useBudget="1" useControlGroup="1" useDeliveryOutline="1"
   useDocument="1" useFCPValidation="0" useSeedMember="1" useTask="1"
   useValidation="1" useWorkflow="1"></parameter>
   <fcpSeed>
    <where filteringSchema="nms:seedMember"></where>
   </fcpSeed>
   <owner _operation="none" name="admin" type="0"/>
   <program _operation="none" name="nmsOperations"/>
   <task end="2013-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2013-01-16 10:07:51.000Z"
   status="1">
    <owner _operation="none" name="admin" type="0"/>
    <operation _operation="none" internalName="OP1"/>
    <folder _operation="none" name="nmsTask"/>
   </task>
   <workflow internalName="WKF12" label="CampaignWorkflow" modelName="newOpEmpty"
   order="8982" scenario-cs="Notification of the workflow supervisor (notifySupervisor)"
   schema="nms:recipient">
    <scenario internalName="notifySupervisor"/>
    <desc></desc>
    <folder _operation="none" name="Folder4"/>
    <operation _operation="none" internalName="OP1"/>
   </workflow>
  </operation>
 </entities>
</package>   
```

Anslutning till en typ av paket har definierats i ett schema med attributet `@pkgAdmin and @pkgPlatform`. Båda dessa attribut får ett XTK-uttryck som definierar villkoren för anslutning till paketet.

```xml
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

Slutligen kan du med attributet `@pkgStatus` definiera exportreglerna för dessa element eller attribut. Beroende på attributets värde finns elementet eller attributet i det exporterade paketet. De tre möjliga värdena för det här attributet är:

* `never`: exporterar inte fältet/länken
* `always`: tvingar fram export för det här fältet
* `preCreate`: auktoriserar skapande av den länkade entiteten

>[!NOTE]
>
>Värdet `preCreate` tillåts bara för länktypshändelser. Det gör att du kan skapa eller peka på en enhet som ännu inte har lästs in i det exporterade paketet.

## Hantera paketdefinitioner {#manage-package-definitions}

Med paketdefinitioner kan du skapa en paketstruktur där du lägger till entiteter som ska exporteras senare i ett paket. Du kan sedan importera det här paketet och alla tillagda enheter till en annan Campaign-instans.

### Skapa en paketdefinition {#create-a-package-definition}

Du kommer åt paketdefinitioner på menyn **[!UICONTROL Administration > Configuration > Package management > Package definitions]**.

Om du vill skapa en paketdefinition klickar du på knappen **[!UICONTROL New]** och fyller sedan i den allmänna paketdefinitionsinformationen.

![](assets/packagedefinition_create.png)

Du kan sedan lägga till enheter i paketdefinitionen och exportera den till ett XML-filpaket.

**Relaterade ämnen:**

* [Lägga till entiteter i en paketdefinition](#add-entities-to-a-package-definition)
* [Konfigurera generering av paketdefinitioner](#configure-package-definitions-generation)
* [Exportera paket från en paketdefinition](#export-packages-from-a-package-definition)

### Lägga till entiteter i en paketdefinition {#add-entities-to-a-package-definition}

På fliken **[!UICONTROL Content]** klickar du på knappen **[!UICONTROL Add]** för att markera de enheter som ska exporteras med paketet. De bästa sätten att välja enheter visas i [det här avsnittet](#export-a-set-of-objects-in-a-package).

![](assets/packagedefinition_addentities.png)

Enheter kan läggas till i en paketdefinition direkt från sin plats i instansen. Gör så här:

1. Högerklicka på önskad entitet och välj sedan **[!UICONTROL Actions > Export in a package]**.

1. Välj **[!UICONTROL Add to a package definition]** och välj sedan den paketdefinition som du vill lägga till entiteten i.

1. Entiteten läggs till i paketdefinitionen och exporteras med paketet (se [det här avsnittet](#export-packages-from-a-package-definition)).

### Konfigurera generering av paketdefinitioner {#configure-package-definitions-generation}

Paketgenerering kan konfigureras från fliken för paketdefinitionen **[!UICONTROL Content]**. Klicka på länken **[!UICONTROL Generation parameters]** om du vill göra det.

![](assets/packagedefinition_generationparameters.png)

* Använd alternativet **[!UICONTROL Include the definition]** för att inkludera den definition som för närvarande används i paketdefinitionen.
* Använd alternativet **[!UICONTROL Include an installation script]** för att lägga till ett javascript-skript som ska köras vid paketimporten. När du väljer det här alternativet läggs en **[!UICONTROL Script]**-flik till på paketdefinitionsskärmen.
* Använd alternativet **[!UICONTROL Include default values]** för att lägga till värdena för alla entiteters attribut i paketet.

  Det här alternativet är inte markerat som standard för att undvika långa exporter. Det innebär att entiteter-attribut med standardvärden (tom sträng, 0 och false om de inte definieras på annat sätt i schemat) inte läggs till i paketet och därför inte exporteras.

  >[!CAUTION]
  >
  >Om instansen som paketet importeras till innehåller entiteter som är identiska med de i paketet (till exempel med samma externa ID) uppdateras inte deras attribut. Detta kan inträffa om attributen från den tidigare instansen har standardvärden eftersom de inte ingår i paketet. Om du i så fall väljer alternativet **[!UICONTROL Include default values]** förhindras versionssammanslagning, eftersom alla attribut från den tidigare instansen exporteras med paketet.

### Exportera paket från en paketdefinition {#export-packages-from-a-package-definition}

Om du vill exportera ett paket från en paketdefinition följer du stegen nedan:

1. Markera den paketdefinition som ska exporteras, klicka på knappen **[!UICONTROL Actions]** och välj **[!UICONTROL Export the package]**.
1. Kontrollera den exporterade filens namn och plats.
1. Klicka på knappen **[!UICONTROL Start]** för att starta exporten.

## Importera paket {#import-packages}

Paketimportassistenten är tillgänglig via huvudmenyn **[!UICONTROL Tools > Advanced > Import package]** i klientkonsolen.

### Installera ett paket från en fil {#install-a-package-from-a-file}

Så här importerar du ett befintligt datapaket:

1. Få åtkomst till importassistenten via huvudmenyn **[!UICONTROL Tools > Advanced > Import package]** i klientkonsolen.
1. Markera XML-filen och klicka på **[!UICONTROL Open]**.

Innehållet i det paket som ska importeras visas sedan i mitten av redigeraren.

Klicka på **[!UICONTROL Next]** och **[!UICONTROL Start]** för att starta importen.

### Installera ett inbyggt paket {#install-a-standard-package}

Inbyggda paket standardpaket) installeras när Adobe Campaign konfigureras. Beroende på dina behörigheter, din distributionsmodell och ditt produkterbjudande kan du importera nya standardpaket.

Se licensavtalet för att se vilka paket du kan installera.

## Bästa praxis för datapaket {#data-package-best-practices}

I det här avsnittet beskrivs hur du organiserar datapaket på ett konsekvent sätt under projektets hela livslängd.


### Versioner

Du måste alltid importera i samma version av plattformen. Du måste kontrollera att du distribuerar dina paket mellan två instanser som har samma programversion. Tvinga aldrig importen och uppdatera alltid plattformen först (om bygget är annorlunda).

>[!IMPORTANT]
>
>Import mellan olika versioner stöds inte av Adobe.

Var uppmärksam på schema- och databasstrukturen. Importera ett paket med schema måste följas av schemagenerering.

### Pakettyper {#package-types}

Börja med att definiera olika typer av paket. Endast fyra typer används:

**Entiteter**

* Alla xtk- och nms-specifika element i Adobe Campaign som scheman, formulär, mappar, leveransmallar osv.
* Du kan betrakta en entitet som både ett admin- och plattformselement.
* Du bör inte inkludera mer än en enhet i ett paket när du överför det till en Campaign-instans.

Om du behöver distribuera konfigurationen på en ny instans kan du importera alla enhetspaket.

**Funktioner**

Den här typen av paket:
* Besvarar ett klientbehov/en kundspecifikation.
* Innehåller en eller flera funktioner.
* Bör innehålla alla beroenden för att kunna köra funktionen utan något annat paket.

**Kampanjer**

Detta paket är inte obligatoriskt. Ibland kan det vara användbart att skapa en specifik typ för alla kampanjer, även om en kampanj kan ses som en funktion.

**Uppdateringar**

När en funktion har konfigurerats kan den exporteras till en annan miljö. Paketet kan till exempel exporteras från en utvecklingsmiljö till en testmiljö. I det här testet avslöjas en defekt. Först måste den korrigeras i utvecklingsmiljön. Sedan ska plåstret appliceras på testplattformen.

Den första lösningen skulle vara att exportera hela funktionen igen. Men för att undvika risker (uppdatera oönskade element) är det säkrare att ha ett paket som bara innehåller korrigeringen.

Därför rekommenderar vi att du skapar ett uppdateringspaket som bara innehåller en enhetstyp av funktionen.

En uppdatering kan inte bara vara en korrigering, utan även ett nytt element i ditt enhets-/funktions-/kampanjpaket. Du kan undvika att distribuera hela paketet genom att exportera ett uppdateringspaket.

### Namnkonventioner {#data-package-naming}

Nu när typerna är definierade bör vi ange en namnkonvention. Adobe Campaign tillåter inte att du skapar undermappar för paketspecifikationer, vilket innebär att tal är den bästa lösningen för att hålla ordning. Numreringsprefixpaketnamn.

Du kan till exempel använda följande konvention:

* Enhet: från 1 till 99
* Funktion: från 100 till 199
* Kampanj: från 200 till 299
* Uppdatering: från 5 000 till 5 999

#### Ordning för enhetspaket {#entity-packages-order}

För att underlätta importen bör enhetspaket sorteras efter importerad information.

Exempel:

* 001 - Schema
* 002 - Formulär
* 003 - Bilder
* osv.

>[!NOTE]
>
>Forms ska bara importeras **efter** schemauppdateringar.


#### Paketdokumentation {#package-documentation}

När du uppdaterar ett paket bör du alltid placera en kommentar i beskrivningsfältet för att beskriva eventuella ändringar och orsaker (till exempel&quot;lägg till ett nytt schema&quot; eller&quot;åtgärda ett fel&quot;).

Det bästa sättet är också att ange uppdateringsdatumet.

>[!IMPORTANT]
>
>Beskrivningsfältet får innehålla högst 2 000 tecken.
