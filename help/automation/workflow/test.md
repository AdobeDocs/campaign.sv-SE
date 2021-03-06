---
product: campaign
title: Test
description: Läs mer om aktiviteten Testa arbetsflöde
feature: Workflows
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Testa{#test}



A **Testa** type-aktivitet aktiverar den första övergång som uppfyller det villkor som är kopplat till den. Om inget villkor är uppfyllt och om **[!UICONTROL Use the default fork]** om du väljer det här alternativet aktiveras standardövergången.

Ett villkor är ett JavaScript-uttryck som måste utvärderas till true eller false. Om du vill ange uttrycket klickar du på ikonen till höger om namnet på villkoret och väljer sedan **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Mer information om alla ytterligare JavaScript-funktioner och SOAP-metoder för programservern som är tillgängliga via JavaScript i arbetsflödet finns i [JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv).

Du kan också infoga variabler direkt från den här redigeraren. Mer information om hur du arbetar med variabler finns i [det här avsnittet](javascript-scripts-and-templates.md#variables).

Villkoren kan läggas till, tas bort eller ordnas i redigeringsfönstret för aktivitetsegenskapen, men kan också ändras från övergången.

Om resultatet av en beräkning ska återanvändas av olika villkor är det möjligt att beräkna det i aktivitetens initieringsskript. Resultatet måste lagras i en variabel av aktiviteten som ska användas av villkorsskripten (task.vars.xxx).
