---
product: campaign
title: Skicka personaliserade aviseringar till operatörer
description: Lär dig hur du skickar personaliserade aviseringar till operatorer
feature: Workflows
version: Campaign v8, Campaign Classic v7
exl-id: 41a009f6-d1e9-40c9-8494-3bbb4bd3d134
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# Skicka personaliserade aviseringar till operatörer{#sending-personalized-alerts-to-operators}



I det här exemplet vill vi skicka en varning till en operator som ska innehålla namnet på profiler som öppnade ett nyhetsbrev men som inte klickade på länken som det innehåller.

Profilernas för- och efternamnsfält är länkade till måldimensionen **[!UICONTROL Recipients]**, medan aktiviteten **[!UICONTROL Alert]** är länkad till måldimensionen **[!UICONTROL Operator]**. Därför finns det inget tillgängligt fält mellan de två måldimensionerna för att utföra en avstämning och hämta för- och efternamnsfälten, och visa dem i aviseringsaktiviteten.

Processen är att skapa ett arbetsflöde enligt nedan:

1. Använd en **[!UICONTROL Query]**-aktivitet för måldata.
1. Lägg till en **[!UICONTROL JavaScript code]**-aktivitet i arbetsflödet för att spara ifyllningen från frågan till instansvariabeln.
1. Använd en **[!UICONTROL Test]**-aktivitet för att kontrollera antalet populationer.
1. Använd en **[!UICONTROL Alert]**-aktivitet för att skicka en avisering till en operator, beroende på aktivitetsresultatet för **[!UICONTROL Test]**.

![](assets/uc_operator_1.png)

## Spara populationen i instansvariabeln {#saving-the-population-to-the-instance-variable}

Lägg till koden nedan i aktiviteten **[!UICONTROL JavaScript code]**.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Kontrollera att JavaScript-koden motsvarar arbetsflödesinformationen:

* Taggen **[!UICONTROL queryDef schema]** ska motsvara namnet på måldimensionen som används i frågeaktiviteten.
* Taggen **[!UICONTROL node expr]** ska motsvara namnet på de fält som du vill hämta.

![](assets/uc_operator_3.png)

Följ stegen nedan för att hämta informationen:

1. Högerklicka på den utgående övergången från aktiviteten **[!UICONTROL Query]** och välj sedan **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Högerklicka på listan och välj sedan **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. Frågemålets dimension- och fältnamn visas i listan.

   ![](assets/uc_operator_6.png)

## Testning av populationsantal {#testing-the-population-count}

Lägg till koden nedan i aktiviteten **[!UICONTROL Test]** för att kontrollera om målpopulationen innehåller minst en profil.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Ställa in aviseringen {#setting-up-the-alert}

Nu när populationen har lagts till i instansvariabeln med de önskade fälten kan du lägga till informationen i aktiviteten **[!UICONTROL Alert]**.

Om du vill göra det lägger du till koden nedan på fliken **[!UICONTROL Source]**:

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>Med kommandot **[!UICONTROL <%= item.target.recipient.@fieldName %>]** kan du lägga till ett av fälten som har sparats i instansvariabeln via aktiviteten **[!UICONTROL JavaScript code]**.\
>Du kan lägga till så många fält som du vill så länge de har infogats i JavaScript-koden.

![](assets/uc_operator_8.png)
