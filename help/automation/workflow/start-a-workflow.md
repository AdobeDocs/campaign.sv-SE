---
product: campaign
title: Starta ett arbetsflöde
description: Lär dig hur du startar ett arbetsflöde och identifierar arbetsflöden, verktygsfältet och högerklicksmenyn
feature: Workflows
exl-id: 6d9789e3-d721-4ffd-b3fb-a0c522ab1c0a
source-git-commit: 6464e1121b907f44db9c0c3add28b54486ecf834
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%

---

# Starta ett arbetsflöde {#starting-a-workflow}

Ett arbetsflöde startas alltid manuellt. När programmet startas kan det dock förbli inaktivt beroende på vilken information som anges via en schemaläggare (se [Schemaläggare](scheduler.md)) eller aktivitetsplanering.

Åtgärder för att målinrikta arbetsflödeskörning (starta, stoppa, pausa osv.) är **asynkron** processer: beställningen registreras och träder i kraft så snart servern är tillgänglig för att använda den.

Med verktygsfältet kan du starta och spåra arbetsflödets körning.

Listan med tillgängliga alternativ i **[!UICONTROL Actions]** och högerklicksmenyn visas nedan.

>[!IMPORTANT]
>
>Tänk på att när en operator utför en åtgärd i ett arbetsflöde (starta, stoppa, pausa osv.) utförs inte åtgärden direkt, utan i stället placeras i en kö för att bearbetas av arbetsflödesmodulen.

## Verktygsfältet Åtgärder {#actions-toolbar}

The **[!UICONTROL Actions]** i verktygsfältet kan du använda ytterligare körningsalternativ för valda arbetsflöden. Du kan också använda **[!UICONTROL File > Actions]** eller högerklicka på ett arbetsflöde och välj **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   Med den här åtgärden kan du starta körningen av ett arbetsflöde: ett arbetsflöde som **Slutförd**, **Redigeras** eller **Pausad** ändrar status till **Startat**. Arbetsflödesmotorn hanterar sedan körningen av det här arbetsflödet. Om arbetsflödet pausades återupptas det, annars startas arbetsflödet från början och de inledande aktiviteterna aktiveras.

   Starten är en asynkron process: Begäran sparas och behandlas så snart som möjligt av en arbetsflödesserver.

* **[!UICONTROL Pause]**

   Den här åtgärden anger arbetsflödets status till **Pausad**. Inga aktiviteter aktiveras förrän arbetsflödet återupptas. pågående åtgärder är dock inte pausade.

* **[!UICONTROL Stop]**

   Den här åtgärden stoppar ett arbetsflöde som körs. Status för instansen är inställd på **Slutförd**. Pågående åtgärder stoppas om det är möjligt. Import och SQL-frågor avbryts omedelbart.

   >[!IMPORTANT]
   >
   >Att stoppa ett arbetsflöde är en asynkron process: Begäran registreras och arbetsflödesservern eller servrarna avbryter pågående åtgärder. Det kan därför ta tid att stoppa en arbetsflödesinstans, särskilt om arbetsflödet körs på flera servrar, där var och en måste ta kontroll för att avbryta de pågående åtgärderna. Du kan undvika problem genom att vänta tills stoppåtgärden har slutförts och inte utföra flera stoppbegäranden i samma arbetsflöde.

* **[!UICONTROL Restart]**

   Den här åtgärden avbryter och startar sedan om arbetsflödet. I de flesta fall går det att starta om snabbare. Det är också användbart att automatisera omstarten när stoppet tar en viss tid: Detta beror på att &quot;Stoppa&quot;-kommandot inte är tillgängligt när arbetsflödet stoppas.

* **[!UICONTROL Purge history]**

   Med den här åtgärden kan du rensa arbetsflödeshistoriken. Mer information finns i [Rensar loggarna](monitor-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   Med det här alternativet kan du starta arbetsflödet i simuleringsläge i stället för i realläge. Det innebär att när du aktiverar det här läget utförs endast aktiviteter som inte påverkar databasen eller filsystemet (t.ex. **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, osv.). Verksamhet som har en effekt (t.ex. **[!UICONTROL Export]**, **[!UICONTROL Import]**, osv.) samt de som kommer efter dem (i samma gren) inte utförs.

* **[!UICONTROL Execute pending tasks now]**

   Med den här åtgärden kan du starta alla väntande uppgifter så snart som möjligt. Om du vill starta en viss uppgift högerklickar du på aktiviteten och väljer **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   Det här alternativet ändrar arbetsflödets status till **[!UICONTROL Finished]**. Denna åtgärd bör endast användas som en sista utväg om den normala stoppprocessen misslyckas efter flera minuter. Använd bara det ovillkorliga stoppet om du är säker på att inga verkliga arbetsflödesjobb pågår.

   >[!CAUTION]
   >
   >Det här alternativet är reserverat för expertanvändare.

* **[!UICONTROL Save as template]**

   Den här åtgärden skapar en ny arbetsflödesmall baserad på det valda arbetsflödet. Du måste ange mappen där den ska sparas (i **[!UICONTROL Folder]** fält).

## Högerklicka på menyn {#right-click-menu}

När du har valt en eller flera arbetsflödesaktiviteter kan du högerklicka för att agera på ditt val.

![](assets/contextual_menu.png)

Följande alternativ är tillgängliga på högerklicksmenyn:

**[!UICONTROL Open]**: Med det här alternativet kan du komma åt aktivitetsegenskaperna.

**[!UICONTROL Display logs:]** Med det här alternativet kan du visa loggen för uppgiftskörning för den valda aktiviteten. Se [Visa loggar](monitor-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** Med den här åtgärden kan du starta väntande uppgifter så snart som möjligt.

**[!UICONTROL Workflow restart from a task:]** Med det här alternativet kan du starta om arbetsflödet med de resultat som tidigare lagrats för den här aktiviteten.

**[!UICONTROL Cut/Copy/Paste/Delete:]** Med dessa alternativ kan du klippa ut, kopiera, klistra in och ta bort aktiviteter.

**[!UICONTROL Copy as bitmap:]** Med det här alternativet kan du ta en skärmbild av alla aktiviteter.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** de här alternativen är också tillgängliga i **[!UICONTROL Advanced]** aktivitetsegenskaperna. De beskrivs i [Körning](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** Med kan du spara eller avbryta ändringar som gjorts i ett arbetsflöde.

>[!NOTE]
>
>Du kan markera en grupp aktiviteter och använda något av dessa kommandon på dem.

