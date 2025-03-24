---
product: campaign
title: Egenskaper för arbetsflöde
description: Läs mer om egenskaper för kampanjarbetsflöde
feature: Workflows
exl-id: 7fef434e-f6bd-46a4-9ec2-0182f081c928
source-git-commit: c6b4f4cee6f033218c77a495c39885e231c06126
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---

# Egenskaper för arbetsflöde{#workflow-properties}

## Fliken Körning {#execution-tab}

Fliken **[!UICONTROL Execution]** i fönstret **[!UICONTROL Properties]** i ett arbetsflöde är uppdelad i tre avsnitt:

![](assets/wf_execution_tab.png)

### Schemaläggare {#scheduler}

Det här avsnittet visas bara i kampanjarbetsflöden.

* **[!UICONTROL Priority]**

  Arbetsflödesmotorn bearbetar de arbetsflöden som ska köras baserat på det prioritetskriterium som definieras i det här fältet. Alla arbetsflöden med prioriteten **[!UICONTROL Average]** körs till exempel före arbetsflöden med prioriteten **[!UICONTROL Low]**.

* **[!UICONTROL Schedule execution for a time of low activity]**

  Det här alternativet skjuter upp arbetsflödet från början till en period med mindre upptagen. Vissa arbetsflöden kan vara dyra när det gäller resurser för databasmotorn. Vi rekommenderar att du schemalägger körning under en tid med låg aktivitet (exempelvis på natten). Låga aktivitetsperioder definieras i det tekniska arbetsflödet för **[!UICONTROL Processes on campaigns]**.

### Körning {#execution}

* **[!UICONTROL Default affinity]**

  Om installationen innehåller flera arbetsflödesservrar använder du det här fältet för att välja vilken dator arbetsflödet ska köras på. Om värdet som definieras i det här fältet inte finns på någon server, kommer arbetsflödet att förbli väntande.

* **[!UICONTROL History in days]**

  I arbetstabellerna i databasen finns en historik över körningar (uppgifter, händelser, loggar). Här kan du definiera antalet dagar som ska arkiveras för det här arbetsflödet: rensningsprocessen tar bort de äldsta arkiven en gång om dagen. Om värdet i det här fältet är noll tas arkivet aldrig bort.

* **[!UICONTROL Log SQL queries in the journal]**

  Den här funktionen är reserverad för avancerade användare. Det gäller arbetsflöden som innehåller riktade aktiviteter (fråga, union, skärning osv.). När det här alternativet är markerat visas de SQL-frågor som skickas till databasen under arbetsflödeskörningen i Adobe Campaign, vilket innebär att du kan analysera dem för att optimera frågor eller diagnostisera problem.

  Frågor visas på en **[!UICONTROL SQL logs]**-flik som läggs till i arbetsflödet (förutom kampanjarbetsflöden) och i **[!UICONTROL Properties]**-aktiviteten när alternativet är aktiverat. Fliken **[!UICONTROL Audit]** innehåller även SQL-frågor.

  ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

  Det här alternativet får endast användas för felsökning och aldrig i produktion. När det är aktiverat prioriteras arbetsflödet och alla andra arbetsflöden stoppas tills det är klart.

* **[!UICONTROL Enable watchdog supervisor to keep workflow running permanently]**

  Det här alternativet tvingar arbetsflöden att starta om automatiskt när ett fel inträffar. När det här alternativet är aktiverat kontrolleras arbetsflödets status var 30:e sekund av omstarten och den startas om vid behov. Om du vill justera 30-sekundersintervallet kan du skapa det tekniska alternativet `XtkWorkflow_WatchdogRestartTimerTimeout` och använda en heltalsdatatyp för att ange önskad fördröjning.

  >[!NOTE]
  >
  >Det här alternativet är avsett för avancerade användare och bör endast aktiveras för **tekniska arbetsflöden**.
  >
  >Den är aktiverad som standard för centraliserade replikeringsarbetsflöden som är tillgängliga med paketet `fullFdaMkt`.

### Felhantering {#error-management}

* **[!UICONTROL Troubleshooting]**

  I det här fältet kan du definiera de åtgärder som ska vidtas om en arbetsflödesuppgift innehåller fel. Det finns två möjliga alternativ:

   * **[!UICONTROL Stop the process]**: arbetsflödet pausas automatiskt. arbetsflödets status ändras till **[!UICONTROL Failed]**. När problemet är löst startar du om arbetsflödet med knapparna **[!UICONTROL Start]** eller **[!UICONTROL Restart]**.
   * **[!UICONTROL Ignore]**: statusen för den uppgift som utlöste felet ändras till **[!UICONTROL Failed]**, men arbetsflödet behåller statusen **[!UICONTROL Started]**. Den här konfigurationen är relevant för återkommande aktiviteter: Om grenen innehåller en schemaläggare startas den normalt nästa gång arbetsflödet körs.

* **[!UICONTROL Consecutive errors]**

  Det här fältet blir tillgängligt när värdet **[!UICONTROL Ignore]** väljs i fältet **[!UICONTROL In case of errors]**. Du kan ange antalet fel som kan ignoreras innan processen stoppas. När det här numret har nåtts ändras arbetsflödets status till **[!UICONTROL Failed]**. Om värdet för det här fältet är 0 stoppas aldrig arbetsflödet oavsett antalet fel.

* **[!UICONTROL Template]**

  I det här fältet kan du välja den meddelandemall som ska skickas till arbetsflödets ansvariga när dess status ändras till **[!UICONTROL Failed]**.

  De berörda operatörerna meddelas via e-post, om det finns en e-postadress i deras profil. Om du vill definiera arbetsflödesansvariga går du till fältet **[!UICONTROL Supervisor(s)]** för egenskaperna (**[!UICONTROL General]**-fliken).

  ![](assets/wf-properties_select-supervisors.png)

  Standardmallen **[!UICONTROL Notification to a workflow supervisor]** innehåller en länk för att komma åt Adobe Campaign klientkonsol via webben, så att mottagaren kan arbeta med problemet när han eller hon är inloggad.

  Om du vill skapa en personlig mall går du till **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**.
