---
title: Filtrera kampanjscheman
description: Lär dig filtrera kampanjscheman
exl-id: e8ad021c-ce2e-4a74-b9bf-a989d8879fd1
source-git-commit: d2f4e54b0c37cc019061dd3a7b7048cd80876ac0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Filterscheman{#filter-schemas}

## Systemfilter {#system-filters}

Du kan filtrera schemaåtkomst till specifika användare, beroende på deras behörigheter. Med systemfilter kan du hantera läs- och skrivbehörigheter för enheter som anges i scheman med **readAccess** och **writeAccess** parametrar.

>[!NOTE]
>
>Denna begränsning gäller endast icke-tekniska användare: en teknisk användare, med relaterade behörigheter eller med ett arbetsflöde, kan hämta och uppdatera data.

* **readAccess**: ger skrivskyddad åtkomst till schemadata.

   **Varning** - Alla länkade tabeller måste anges med samma begränsning. Den här konfigurationen kan påverka prestanda.

* **writeAccess**: ger skrivåtkomst till schemadata.

De här filtren anges i **element** schemanivå och, som visas i följande exempel, kan formas för att begränsa åtkomsten.

* Begränsa skrivbehörighet

   Här används filtret för att inte tillåta skrivbehörighet för schemat för operatorer utan administratörsbehörighet. Det innebär att bara administratörer har skrivbehörighet för entiteter som beskrivs i det här schemat.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Begränsa läs- och skrivbehörigheter:

   Här används filtret för att inte tillåta både LÄS- och SKRIVbehörigheter för schemat för alla operatorer. Endast **internal** -kontot, som representeras av uttrycket&quot;$(loginId)!=0&quot;, har dessa behörigheter.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Möjlig **expr** Attributvärden som används för att definiera villkoret är TRUE eller FALSE.

>[!NOTE]
>
>Om inget filter anges har alla operatorer läs- och skrivbehörighet till schemat.

## Protect inbyggda scheman

Inbyggda scheman är som standard bara tillgängliga med SKRIV-behörighet för operatorer med ADMINISTRATIONbehörighet:

* ncm:publicera
* nl:övervakning
* nms:kalender
* xtk:builder
* xtk:anslutningar
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:formulär
* xtk:funcList
* xtk:fusion
* xtk:bild
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rättigheter
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strängar
* xtk:xslt

>[!CAUTION]
>
>LÄS- och SKRIVbehörigheter för **xtk:sessionInfo** schema är bara tillgängligt för ett internt konto i en Adobe Campaign-instans.

## Ändra systemfilter för inbyggda scheman

Inbyggda scheman är skyddade för att undvika kompatibilitetsproblem med äldre versioner. Adobe rekommenderar att du inte ändrar standardparametrarna för schemat för att garantera optimal säkerhet.

I vissa sammanhang kan du dock behöva ändra systemfiltren för de inbyggda schemana. Gör så här:

1. Skapa ett tillägg för det inbyggda schemat eller öppna ett befintligt tillägg.
1. Lägga till ett underordnat element **`<sysfilter name="<filter name>" _operation="delete"/>`** i huvudelementet för att ignorera filtret under samma i det inbyggda schemat.
1. Du kan lägga till ett nytt filter, enligt informationen i [Systemfilter](#system-filters) -avsnitt.
