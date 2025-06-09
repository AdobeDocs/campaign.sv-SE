---
title: Filtrera kampanjscheman
description: Lär dig filtrera kampanjscheman
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: e8ad021c-ce2e-4a74-b9bf-a989d8879fd1
source-git-commit: 2ce1ef1e935080a66452c31442f745891b9ab9b3
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Filterscheman{#filter-schemas}

## Systemfilter {#system-filters}

Du kan filtrera schemaåtkomst till specifika användare, beroende på deras behörigheter. Med systemfilter kan du hantera läs- och skrivbehörigheter för entiteter som är detaljerade i scheman med hjälp av parametrarna **readAccess** och **writeAccess**.

>[!NOTE]
>
>Begränsningen gäller endast icke-tekniska användare: en teknisk användare med tillhörande behörigheter eller ett arbetsflöde kan hämta och uppdatera data.

* **readAccess**: ger skrivskyddad åtkomst till schemadata.

  **Varning** - Alla länkade tabeller måste anges med samma begränsning. Den här konfigurationen kan påverka prestanda.

* **writeAccess**: ger skrivåtkomst till schemadata.

Dessa filter anges på huvudnivån **element** för scheman och kan, som visas i följande exempel, utformas för att begränsa åtkomsten.

* Begränsa skrivbehörighet

  Här används filtret för att inte tillåta skrivbehörighet för schemat för operatorer utan administratörsbehörighet. Det innebär att bara administratörer har skrivbehörighet för entiteter som beskrivs i det här schemat.

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* Begränsa läs- och skrivbehörigheter:

  Här används filtret för att inte tillåta både LÄS- och SKRIVbehörigheter för schemat för alla operatorer. Endast det **interna**-kontot, som representeras av uttrycket&quot;$(loginId)!=0&quot;, har dessa behörigheter.

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  Möjliga **expr**-attributvärden som används för att definiera villkoret är TRUE eller FALSE.

>[!NOTE]
>
>Om inget filter anges har alla operatorer läs- och skrivbehörighet till schemat.

## Skydda inbyggda scheman

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
>LÄS- och SKRIVbehörigheter för schemat **xtk:sessionInfo** är bara tillgängliga för det interna kontot för en Adobe Campaign-instans.

## Ändra systemfilter för inbyggda scheman

Inbyggda scheman är skyddade för att undvika kompatibilitetsproblem med äldre versioner. Adobe rekommenderar att du inte ändrar standardparametrarna för schemat för att garantera optimal säkerhet.

I vissa sammanhang kan du dock behöva ändra systemfiltren för de inbyggda schemana. Gör så här:

1. Skapa ett tillägg för det inbyggda schemat eller öppna ett befintligt tillägg.
1. Lägg till ett underordnat element **`<sysfilter name="<filter name>" _operation="delete"/>`** i huvudelementet för att ignorera filtret under samma element i det inbyggda schemat.
1. Du kan lägga till ett nytt filter, enligt informationen i avsnittet [Systemfilter](#system-filters).
