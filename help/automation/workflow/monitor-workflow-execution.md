---
product: campaign
title: Övervaka arbetsflödeskörning
description: Övervaka arbetsflödeskörning
feature: Workflows
role: Admin
exl-id: bc13d706-7888-42eb-9116-5538e68cd515
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '1935'
ht-degree: 0%

---

# Övervaka arbetsflödeskörning {#monitoring-workflow-execution}

I det här avsnittet finns information om hur du övervakar arbetsflödenas körning.

Ett användningsexempel om hur du skapar ett arbetsflöde där du kan övervaka statusen för en uppsättning arbetsflöden som är&quot;pausade&quot;,&quot;stoppade&quot; eller&quot;med fel&quot; finns också i [det här avsnittet](workflow-supervision.md#supervising-workflows).

Administratörer för instansen kan dessutom använda **Granskningsspår** för att kontrollera aktiviteter och senaste ändringar av arbetsflöden, arbetsflödenas status. Läs mer om granskningsspår i  [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/monitoring-campaign-classic/production-procedures/audit-trail.html#accessing-audit-trail){target="_blank"}.

## Visa förlopp {#displaying-progress}

Du kan övervaka körningen genom att visa förloppet med lämplig ikon i verktygsfältet.

The **[!UICONTROL Display progress information]** Med -ikonen kan du visa status och aktivitetsresultatet i körningsfönstret.

![](assets/s_user_segmentation_toolbar_progr.png)

När det här alternativet är markerat visas utförda aktiviteter i blått, väntande aktiviteter blinka, varningar visas i orange och fel i rött. Det här alternativet visar också resultatet av aktiviteter vid den utgående övergången, följt av resultatetiketten som definieras i aktivitetsegenskaperna och jobbens varaktighet om den överstiger en sekund

![](assets/s_user_segmentation_results.png)

## Visa loggar {#displaying-logs}

Loggen innehåller historiken eller granskningsspåret för arbetsflödet. Den registrerar alla användaråtgärder, alla åtgärder som utförts och fel som påträffats. Du kan:

* Välj **[!UICONTROL Tracking]** -fliken i detaljerna. Den här listan innehåller alla arbetsflödesmeddelanden.

  ![](assets/new-workflow-display-log-tab.png)

* Filtrera loggmeddelanden efter aktivitet. Det gör du genom att klicka **[!UICONTROL Display the tasks and the log]** i verktygsfältet ovanför diagrammet för att visa **[!UICONTROL Log]** och **[!UICONTROL Tasks]** under diagrammet. Välj en aktivitet om du vill visa alla relaterade meddelanden. Den här listan innehåller alla meddelanden när ingen aktivitet har valts.

  ![](assets/new-workflow-display-log-activity.png)

  >[!NOTE]
  >
  >Klicka på bakgrunden i diagrammet för att avmarkera alla element.

* Visa endast meddelanden som är länkade till en viss uppgift. Om du vill göra det väljer du **[!UICONTROL Tasks]** och sedan välja en aktivitet i diagrammet för att begränsa listan. Dubbelklicka på en uppgift för att visa informationen. Loggen finns på den sista fliken i fönstret.

  ![](assets/new-workflow-display-tasks-activity.png)

  The **[!UICONTROL Details...]** kan du visa all ytterligare information om aktivitetskörning. Du kan till exempel visa valideringsoperatorn och, i tillämpliga fall, den kommentar som de angav vid godkännandet.

>[!NOTE]
>
>Loggen rensas inte när ett arbetsflöde startas om. Alla meddelanden sparas. Om du vill ignorera meddelanden från en tidigare körning måste du rensa historiken.

I loggen visas den kronologiska listan med körningsmeddelanden som rör arbetsflödesaktiviteter för målinriktning.

* Logg över en målinriktningskampanj

  När en målinriktningskampanj har körts klickar du på **[!UICONTROL Tracking]** för att visa körningsspårningen.

  ![](assets/s_user_segmentation_journal.png)

  Alla kampanjmeddelanden visas: genomförda kampanjer samt varningar och fel.

* Logg över en aktivitet

  Du kan också visa körningsloggen och information om varje aktivitet. Det finns två sätt att göra detta:

   1. Välj målaktiviteten och klicka på **[!UICONTROL Display the tasks and the log]** -ikon.

      ![](assets/s_user_segmentation_show_logs.png)

      I det nedre avsnittet av diagrammet visas två flikar: Logg och Uppgifter.

      Aktiviteter som väljs i diagrammet fungerar som filter i loggen och uppgiftslistan.

      ![](assets/s_user_segmentation_logs.png)

   1. Högerklicka på målaktiviteten och välj **[!UICONTROL Display logs]**.

      ![](assets/s_user_segmentation_logs_menu.png)

      Loggen visas i ett separat fönster.

## Rensar loggarna {#purging-the-logs}

Arbetsflödeshistorik rensas inte automatiskt: alla meddelanden behålls som standard. Historiken kan rensas via **[!UICONTROL File > Actions]** eller genom att klicka på **[!UICONTROL Actions]** i verktygsfältet ovanför listan. Välj **[!UICONTROL Purge history]**.  De alternativ som är tillgängliga i **[!UICONTROL Actions]** menyn finns i [Verktygsfältet Åtgärder](start-a-workflow.md) -avsnitt.

![](assets/purge_historique.png)

## Arbetstabeller och arbetsflödesschema {#worktables-and-workflow-schema}

Arbetsflödet konverterar arbetstabeller som kan ändras via vissa aktiviteter. Med Adobe Campaign kan ni via datahanteringsaktiviteter ändra, byta namn på och berika kolumnerna i arbetsflödestabellerna, t.ex. för att anpassa dem till nomenklaturen beroende på kundens behov, för att samla in ytterligare information om medmottagaren av ett kontrakt osv.

Det går också att skapa länkar mellan olika arbetsdimensioner och definiera dimensionsändringar. För varje kontrakt som registreras i databasen anger du t.ex. huvudinnehavaren och använder uppgifter om medägare i den ytterligare informationen.

Arbetstabellerna i arbetsflödet tas bort automatiskt när arbetsflödet försätts i viloläge. Om du vill behålla en arbetstabell sparar du den i en lista via **[!UICONTROL List update]** aktivitet (se [Listuppdatering](list-update.md)).

## Hantera fel {#managing-errors}

När ett fel inträffar pausas arbetsflödet och aktiviteten körs när felet blinkar. I arbetsflödesöversikten, under **[!UICONTROL Monitoring]** tab -  **[!UICONTROL Workflows]** kan du bara visa arbetsflöden med fel, vilket visas nedan.

![](assets/wf-global-view_filter_only_errors.png)

I Utforskaren i Adobe Campaign visas en **[!UICONTROL Failed]** kolumn som standard.

![](assets/wf-explorer_errors_col.png)

När ett arbetsflöde är felaktigt meddelas de operatorer som tillhör arbetsflödesövervakningsgruppen via e-post, förutsatt att deras e-postadress anges i deras profil. Den här gruppen är markerad i **[!UICONTROL Supervisor(s)]** i arbetsflödesegenskaperna.

![](assets/wf-properties_select-supervisors.png)

Meddelandeinnehållet är konfigurerat i **[!UICONTROL Workflow manager notification]** standardmall: Den här mallen är markerad i **[!UICONTROL Execution]** -fliken i arbetsflödesegenskaperna. Meddelandet visar namnet på felarbetsflödet och den berörda uppgiften.

Exempel på meddelande:

![](assets/wf-notification_error-msg.png)

Med länken kan du komma åt Adobe Campaign Client Console i webbläge och arbeta med felarbetsflödet när du har loggat in.

![](assets/wf-notification_error-console.png)

Du kan konfigurera arbetsflödet så att det inte pausar och fortsätter att köras om fel uppstår. Om du vill göra det redigerar du arbetsflödet **[!UICONTROL Properties]** och **[!UICONTROL Error management]** väljer du **[!UICONTROL Ignore]** i **[!UICONTROL In case of error]** fält. Du kan sedan ange antalet på varandra följande fel som kan ignoreras innan processen pausas.

I det här fallet avbryts felaktiviteten. Det här läget passar särskilt bra för arbetsflöden som är utformade för att försöka göra om kampanjen senare (periodiska åtgärder).

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>Du kan använda den här konfigurationen separat för varje aktivitet. Om du vill göra det redigerar du aktivitetsegenskaperna och väljer felhanteringsläget i dialogrutan **[!UICONTROL Advanced]** -fliken.

## Bearbetningsfel {#processing-errors}

När det gäller verksamheter, **[!UICONTROL Process errors]** I visas en viss övergång som aktiveras om ett fel genereras. I det här fallet försätts arbetsflödet inte i felläge och körningen fortsätter.

Fel som beaktas är filsystemfel (filen kunde inte flyttas, katalogen kunde inte nås osv.).

Det här alternativet bearbetar inte fel relaterade till aktivitetskonfigurationen, dvs. ogiltiga värden. Fel relaterade till felaktig konfiguration aktiverar inte den här övergången (katalogen finns inte, osv.).

Om ett arbetsflöde pausas (manuellt eller automatiskt efter ett fel) visas **[!UICONTROL Start]** startar om arbetsflödeskörningen där den stoppades. Den felaktiga aktiviteten (eller den pausade aktiviteten) kommer att köras igen. De föregående aktiviteterna har inte körts om.

Om du vill köra alla arbetsflödesaktiviteter igen använder du **[!UICONTROL Restart]** -knappen.

Om du ändrar aktiviteter som redan har körts beaktas inte ändringarna när arbetsflödeskörningen startas om.

Om du ändrar aktiviteter som inte har utförts beaktas de när arbetsflödeskörningen startas om.

Om du ändrar pausade aktiviteter kan ändringarna inte beaktas korrekt när arbetsflödet startas om.

Om det är möjligt rekommenderar vi att du startar om arbetsflödet när du har gjort ändringar.

## Instansövervakning {#instance-supervision}

The **[!UICONTROL Instance supervision]** kan du visa Adobe Campaign serveraktivitet och visa en lista över arbetsflöden och leveranser med fel.

Gå till **[!UICONTROL Monitoring]** och klicka på **[!UICONTROL General view]** länk.

![](assets/wf-monitoring_from-homepage.png)

Om du vill visa alla arbetsflöden klickar du på **[!UICONTROL Workflows]** länk. Använd listrutan för att visa arbetsflödena på plattformen baserat på deras tillstånd.

![](assets/wf-monitoring_edit-wf.png)

Klicka på länken i ett arbetsflöde med fel för att öppna det och visa loggen.

![](assets/wf-monitoring_edit-task-wf.png)

## Förhindra samtidig körning av flera program {#preventing-simultaneous-multiple-executions}

Ett arbetsflöde kan ha flera körningar samtidigt. I vissa fall bör du förhindra att detta händer.

Du kan till exempel ha en schemaläggare som utlöser arbetsflödeskörningen varje timme, men ibland tar körningen av hela arbetsflödet mer än en timme. Du kanske vill hoppa över körningen om arbetsflödet redan körs.

Om du har en signalaktivitet i början av arbetsflödet kanske du vill hoppa över signalen om arbetsflödet körs.

Den allmänna principen är följande:

![](assets/workflow-reentrancy-protection-principle.png)

Lösningen är att använda en förekomstvariabel. Förekomstvariabler delas av alla parallella körningar i arbetsflödena.

Här är ett enkelt testarbetsflöde:

![](assets/wkf_simultaneous_execution1.png)

The **[!UICONTROL Scheduler]** utlöser en händelse varje minut. Följande **[!UICONTROL Test]** aktiviteten kommer att testa **isRunning** instansvariabel som avgör om körningen ska fortsätta eller inte:

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning** är ett variabelnamn som valts för det här exemplet. Det här är inte en inbyggd variabel.

Aktiviteten omedelbart efter **[!UICONTROL Test]** i **ja** förgreningen måste ange instansvariabeln i sin **Initieringsskript**:

```
instance.vars.isRunning = true
```

Den allra sista aktiviteten i **ja** grenen måste återställa variabeln till false i sin **Initieringsskript**:

```
instance.vars.isRunning = false
```

Observera att:

* Du kan kontrollera det aktuella värdet för instansvariabeln via **Variabel** i arbetsflödet **Egenskaper**.
* Förekomstvariabler återställs när du startar om ett arbetsflöde.
* I JavaScript är ett odefinierat värde false i ett test, vilket gör att instansvariabeln kan testas även innan den har initierats.
* Du kan övervaka aktiviteter som inte bearbetas på grund av den här mekanismen genom att lägga till en loggningsinstruktion i initieringsskriptet för &quot;nej&quot;-slutet.

  ```
  logInfo("Workflow already running, parallel execution not allowed.");
  ```

Ett användningsexempel presenteras i detta avsnitt: [Samordna datauppdateringar](coordinate-data-updates.md).

## Databasunderhåll {#database-maintenance}

I arbetsflöden används många arbetstabeller som förbrukar utrymme och gör att hela plattformen blir långsammare om den inte underhålls.

The **Databasrensning** arbetsflöde tillgängligt via **Administration > Produktion > Tekniska arbetsflöden** -nod, kan du ta bort föråldrade data för att undvika exponentiell tillväxt i databasen. Arbetsflödet utlöses automatiskt utan användaråtgärder.

Du kan också skapa specifika tekniska arbetsflöden för att rensa bort onödiga datamängder. Läs mer i [section](#purging-the-logs).

## Hantering av pausade arbetsflöden {#handling-of-paused-workflows}

Om ett arbetsflöde pausas rensas aldrig arbetsflödets arbetsregister som standard. Från och med bygge 880 stoppas automatiskt arbetsflöden som har pausats för länge och arbetsflödena töms. Detta beteende aktiveras enligt följande:

* Arbetsflöden som har pausats sedan mer än 7 dagar visas som en varning på kontrollpanelen (och övervaknings-API:t) och ett meddelande skickas till den övervakande gruppen.
* Samma sak händer varje vecka, när **[!UICONTROL cleanupPausedWorkflows]** det tekniska arbetsflödet utlöses. Mer information om arbetsflödet finns i [det här avsnittet](delivery.md).
* Efter fyra meddelanden (en månad i pausat läge som standard) stoppas arbetsflödet ovillkorligt. En logg visas i arbetsflödet när det har stoppats. Tabellerna rensas vid nästa körning **[!UICONTROL cleanup]** arbetsflöde

Dessa punkter kan konfigureras via alternativet NmsServer_PausedWorkflowPeriod.

Arbetsflödesansvariga meddelas. Den som skapade arbetsflödet och den sista användaren som ändrade det meddelas också. Administratörer får inte meddelanden.

## Filtrera arbetsflöden utifrån deras status {#filtering-workflows-status}

Med hjälp av gränssnittet Campaign Classic kan du övervaka körningsstatusen för alla arbetsflöden i instansen med hjälp av fördefinierade **vyer**. Öppna **[!UICONTROL Administration]** / **[!UICONTROL Audit]** / **[!UICONTROL Workflows Status]** nod.

Följande vyer är tillgängliga:

* **[!UICONTROL Running]**: visar alla arbetsflöden som körs.
* **[!UICONTROL Paused]**: visar alla pausade arbetsflöden.
* **[!UICONTROL Failed]**: visar alla misslyckade arbetsflöden.
* ** ).

![](assets/workflow-monitoring-views.png)

Som standard är dessa vyer tillgängliga i **[!UICONTROL Audit]** mapp. Du kan dock återskapa dem på valfri plats i mappträdet. På så sätt blir de tillgängliga för standardanvändare utan administrationsbehörighet.

Så här gör du:

1. Högerklicka på den mapp där du vill lägga till vyn.
1. I **[!UICONTROL Add new folder]** / **[!UICONTROL Administration]** markerar du den vy som du vill lägga till.
1. När mappen har lagts till i trädet måste du konfigurera den som en vy, så att alla arbetsflöden visas oavsett deras ursprungliga mapp. Mer information om hur du konfigurerar vyer finns i [den här sidan](../../v8/audiences/folders-and-views.md#turn-a-folder-to-a-view).

Utöver dessa vyer kan du skapa filtermappar så att du kan filtrera listan med arbetsflöden utifrån deras körningsstatus. Så här gör du:

1. Öppna en mapp av arbetsflödestyp och välj sedan **[!UICONTROL Filters]** / **[!UICONTROL Advanced filter]** -menyn.
1. Konfigurera filtret så att arbetsflödets **[!UICONTROL @status]** fältet är lika med det läge du väljer.
1. Spara och namnge filtret. Den blir sedan direkt tillgänglig i filterlistan.

![](assets/workflow-monitoring-filter.png)

Mer information finns i följande avsnitt:
