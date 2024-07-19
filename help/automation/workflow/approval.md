---
product: campaign
title: Godkännande
description: Godkännande
feature: Workflows, Approvals
role: User
exl-id: 9e57d21c-ce16-448d-97f1-8c6844acb37b
source-git-commit: 09db0cc1a14bffefe8d1b8d0d5a06d5b6517a5bb
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# Godkännande{#approval}



En **Approval**-aktivitet kräver att en operator deltar. Operatorn tilldelas en uppgift och kan svara via e-post, via den webbsida som är länkad i e-postmeddelandet eller via konsolen.

## Uppgiftstilldelning {#task-assignment}

Som standard tilldelas godkännande till en grupp operatorer. Den här gruppen representerar en roll, t.ex.&quot;Innehållsgrupp för nyhetsbrev&quot; eller&quot;Målgrupp för nyhetsbrev&quot;. Varje operator i gruppen kan svara, men endast det första svaret beaktas (utom vid flera godkännanden).

Om det behövs kan du tilldela godkännandeuppgiften till en enda operator eller en uppsättning operatorer som definieras av ett filter.

* Om du vill välja en enskild operator markerar du värdet **[!UICONTROL Operator]** i fältet **[!UICONTROL Assignment type]** och väljer den relevanta operatorn i listrutan i fältet **[!UICONTROL Assignee]**.

  ![](assets/s_advuser_validation_box_assign.png)

  >[!CAUTION]
  >
  >Endast den valda operatorn kommer att få behörighet att godkänna uppgiften.

* Du kan definiera en fråga för filtrering av godkännandeoperatorer. Det gör du genom att markera värdet **[!UICONTROL Filter]** i fältet **[!UICONTROL Assignment type]** och klicka på länken **[!UICONTROL Advanced parameters...]** för att definiera filtreringsvillkoren, vilket visas i följande exempel:

  ![](assets/s_advuser_validation_box_filter.png)

Vid ett enda godkännande aktiveras övergången som motsvarar valet av operator och uppgiften är klar: övriga operatorer kan inte svara.

Vid flera godkännanden aktiveras övergångar som motsvarar valet av operatorer. Uppgiften är slutförd när alla operatorer i gruppen har svarat eller när uppgiften har upphört att gälla.

Den här aktiviteten blockerar inte bearbetning och arbetsflödet kan utföra andra åtgärder medan det väntar på ett svar.

En operator kan godkänna de uppgifter som tilldelats den operatorn från klientkonsolen. En operator med administratörsbehörighet kan visa och ta bort uppgifter som tilldelats en operator, men kan inte svara på dem.

Om du ändrar aktivitetens titel eller meddelandetext påverkas inte de aktuella uppgifterna, men om du å andra sidan ändrar de möjliga alternativen påverkas de aktuella uppgifterna direkt, vilket automatiskt ärver den nya listan med alternativ.

Typåtgärder av typen **Godkännande** är tillgängliga från noden **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]**: operatorer kan komma åt godkännandeformuläret direkt via den här vyn.

![](assets/s_advuser_validation_from_console.png)

## Egenskaper {#properties}

Anpassningsvariabler kan användas i meddelanden som skickas till granskarna. De kan infogas i meddelandets rubrik eller brödtext.

![](assets/edit_validation.png)

Det här **[!UICONTROL Title]**-fältet innehåller meddelandets titel: Det här är ämnet för det skickade e-postmeddelandet. Titeln och meddelandetexten är JavaScript-mallar och kan därför innehålla värden som beräknas utifrån arbetsflödets sammanhang.

I den nedre delen av redigeraren kan du definiera en lista med möjliga svar. Det finns en övergång som motsvarar varje svar. Namnet är den interna identifieraren och etiketten är den text som visas i listan med alternativ.

Klicka på länken **[!UICONTROL Advanced parameters...]** för att välja den leveransmall som ska användas för att meddela operatorer. Standardmallen (det interna namnet notifyAssigner) tar titeln och meddelandet och lägger till en länk till den webbsida som används för att svara.

Den här mallen kan ändras för att anpassa meddelandelayouten, men du bör skapa en kopia. Målinriktningsmekanismen (extern fil, målmappning) får inte ändras eftersom den krävs för att meddelanden ska fungera korrekt.

Ett godkännandeexempel visas i [Definiera godkännanden](define-approvals.md).

## Utdataparametrar {#output-parameters}

* **[!UICONTROL response]**

  Kommentar relaterade till svaret

* **[!UICONTROL responseOperator]**

  Identifierare för den operator som svarade. Det här fältet är ett numeriskt värde, men ett **[!UICONTROL String]**-fält.
