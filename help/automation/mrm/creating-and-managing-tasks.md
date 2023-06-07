---
product: campaign
title: Skapa och hantera uppgifter
description: Skapa och hantera uppgifter
exl-id: 730d1712-53a6-4bf7-9aac-523b06bd0d0a
source-git-commit: 290f4e9a0d13ef49caacb7a128ccc266bafd5e69
workflow-type: tm+mt
source-wordcount: '3743'
ht-degree: 0%

---

# Skapa och hantera uppgifter{#creating-and-managing-tasks}

Med Adobe Campaign kan du skapa uppgifter och hantera hela deras livscykel direkt i programmet. Program- och kampanjimplementering kan delas upp i uppgifter som tilldelas Adobe Campaign-operatörer eller externa tjänsteleverantörer. Med det här åtgärdsläget kan du skapa en öppen samarbetsmiljö som innehåller alla programdeltagare och externa deltagare.

Uppgifter kan skapas, visas och övervakas från listan med uppgifter eller kontrollpanelen för kampanjer. De kan också ses och spåras i tidsplanerna för marknadsföringsplanen, programmen och kampanjerna.

Aktiviteter är kopplade till kampanjen och kan ha beroenden, dvs. associerade uppgifter. Varje uppgift har en status, prioritet, uppskattad belastning och relaterade kostnader.

Alla uppgifter grupperas i en lista som är tillgänglig via **Kampanjer** -fliken. Mer information finns i [Åtkomstuppgifter](#accessing-tasks).

De kan visas i schemat för det program de tillhör.

![](assets/campaign-calendar.png)

## Åtkomstuppgifter {#accessing-tasks}

### Visa uppgifter {#displaying-tasks}

Uppgifterna visas i uppgiftslistan som du kommer åt via **[!UICONTROL Campaigns]** -fliken.

![](assets/campaign-task-dashboard.png)

Du kan visa alla uppgifter för den aktuella operatorn.

Mer information finns i [Körningsstatus för en uppgift](#execution-status-of-a-task) och [Status för en uppgift](#progress-status-of-a-task).

### Filtrera uppgifter {#filtering-tasks}

När du visar den här vyn filtreras den automatiskt så att endast **aktuella operatoruppgifter**. Du kan även filtrera uppgifterna med hjälp av fälten i fönstrets övre del.

### Redigera uppgifter {#editing-tasks}

Klicka på en uppgift för att redigera den.

![](assets/edit-a-task.png)

## Skapa en ny uppgift {#creating-a-new-task}

Så här skapar du en uppgift:

1. Bläddra till **[!UICONTROL Tasks]** i **[!UICONTROL Campaigns]** och klicka **[!UICONTROL Create]**.

   ![](assets/create-a-task-from-dashboard.png)

1. Ange namnet på aktiviteten och välj den kampanj som den är länkad till.
1. Ange start- och slutdatum.
1. Klicka **[!UICONTROL Save]** för att skapa uppgiften.

   ![](assets/new-task-edit.png)

Du kan även skapa en uppgift via kontrollpanelen för en kampanj: i det här fallet länkas den automatiskt till kampanjen som den skapades från.

![](assets/add-a-task-in-a-campaign.png)

När en uppgift har skapats läggs den till i kampanjschemat, kampanjinstrumentpanelen och listan med uppgifter. Om du vill redigera en uppgift klickar du på dess namn i listan med uppgifter eller väljer den i schemat eller på kampanjkontrollpanelen och klickar på **[!UICONTROL Open]**.

När du har skapat uppgiften kan du konfigurera den genom att definiera:

* Chefen och deltagarna. [Läs mer](#manager-and-participants)
* Skapandeschemat. [Läs mer](#execution-schedule)
* Utfästa kostnader. [Läs mer](#expenses-and-revenues)

Du kan också lägga till [granskare](#reviewers) och [referensdokument](#documents-referenced).

Aktivitetens livscykel visas i [det här avsnittet](#life-cycle).

### Chef och deltagare {#manager-and-participants}

Som standard tilldelas uppgiften den operator som skapade den. Den här operatorn meddelas när en åtgärd krävs för den uppgiften.

Du kan välja en annan operator i **[!UICONTROL Assigned to]** nedrullningsbar lista.

![](assets/task-assigned-to.png)

>[!NOTE]
>
>Operatörshantering beskrivs i [det här avsnittet](../../v8/start/gs-permissions.md).
>
>Det är bara operatorn som ansvarar för en uppgift som kan stänga den.

Du kan ange fler operatorer som ska utföra uppgiften. Dessa operatorer får inte stänga uppgiften: kan de endast godkänna den uppgift som de tilldelats.

Följ stegen nedan för att lägga till aktivitetsoperatorer:

1. Klicka på **[!UICONTROL Resources]** i verktygsfältet.

   ![](assets/add-task-resources.png)

1. Klicka **[!UICONTROL Add]** och välja ut de berörda aktörerna.
1. Ange användningsfrekvens: detta representerar arbetsbelastningen som tilldelats operatorn för uppgiftskörningens varaktighet. Denna procentsats är endast en indikation och uttrycks som en procentandel.

   ![](assets/define-operator-task-workload.png)

   För en aktivitet vars körningsschema är inställt på 10 dagar, kommer till exempel en operator vars användarfrekvens är 50 % att aktiveras för den här aktiviteten för halva arbetstiden i 10 dagar.

   För varje operator kan du ange en schemalagd arbetsbelastning och en faktisk arbetsbelastning. Dessa varaktigheter är också avsedda endast som information.

1. Du kan konfigurera en påminnelse från **[!UICONTROL Add a reminder...]** länk. Ett e-postmeddelande skickas till alla operatorer som deltar i aktiviteten före slutdatumet.

   ![](assets/task-op-add-a-reminder.png)

1. Du kan också skicka ett meddelande innan uppgiften startar. För att ställa in detta väljer du datumet i **[!UICONTROL Initial notification]** fält.
1. När slutdatumet har nåtts och uppgiften inte har stängts kan ett meddelande skickas till den tilldelande eller den grupp av tilldelningar som har valts i **[!UICONTROL Assignee]** nedrullningsbar lista.


På kontrollpanelen för operatorer kan du kontrollera deras arbetsbelastning (andra pågående uppgifter).

![](assets/operator-dashboard.png)

### Godkännande av uppgift {#reviewers}

Förutom deltagarna kan du definiera operatorer som ska granska uppgiften när den har stängts.

Om du vill göra det klickar du på **[!UICONTROL Enable task approval]** i nedre delen av **[!UICONTROL Resources]** -fönstret. Det kan vara en enskild operator, en grupp operatorer eller en lista med operatorer.

Om du vill ange en lista med operatorer klickar du på **[!UICONTROL Edit...]** länk till höger om den första granskaren och lägg till så många operatorer som behövs, som visas nedan:

![](assets/enable-task-approval.png)

Du kan definiera ett godkännandeschema för uppgiften i det nedre avsnittet av konfigurationsfönstret. Som standard har granskarna tre dagar på sig att godkänna uppgiften från och med överföringsdatumet. Du kan också lägga till en påminnelse som automatiskt skickas till de berörda operatörerna före godkännandedeadline.

Den person som ansvarar för uppgiften kan tilldela sig själv uppgiften att godkänna den, även om andra operatorer redan har tilldelats uppgiften att göra detta. Om ingen granskare har definierats skickas meddelandena till den person som ansvarar för uppgiften. Alla andra Adobe Campaign-operatorer med **[!UICONTROL Administrator]** behörigheter kan också godkänna uppgiften. De får dock inga meddelanden.

### Refererade dokument {#documents-referenced}

Du kan lägga till [dokument och marknadsföringsresurser](managing-marketing-resources.md) till en uppgift.

Så här gör du:

1. Öppna uppgiften och klicka på **[!UICONTROL Documents]** i verktygsfältet.

   ![](assets/add-documents-to-a-task.png)

1. Klicka **[!UICONTROL Add]** och väljer det dokument som ska läggas till i uppgiften. Använd samma process för marknadsföringsresurser.


Refererade dokument läggs till i de meddelanden som skickas till de operatorer som deltar i uppgiften. De läggs också till på kontrollpanelen för uppgifter.

![](assets/s_ncs_user_task_notification_documents.png)

### Körningsschema {#execution-schedule}

Giltighetsperioden för en uppgift anges i **[!UICONTROL Start]** och **[!UICONTROL End]** fält. Den schemalagda belastningen anger den arbetsbelastning som ska utföras under perioden. Den uttrycks i dagar eller timmar.

>[!NOTE]
>
>En uppgifts livscykel visas i [Livscykel](#life-cycle).

The **[!UICONTROL Workload performed]** Med det här fältet kan du även uppdatera aktivitetens förlopp manuellt i förhållande till den schemalagda arbetsbelastningen.

![](assets/s_ncs_user_task_percentage_done_enter.png)

The **[!UICONTROL Progress status]** Uppgiften, uttryckt i procent, uppdateras automatiskt utifrån de uppgifter som utförs av de berörda operatörerna. Den kan anges manuellt.

Den här informationen kan visas på kontrollpanelen för uppgifter.

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

Den visas också på fliken Kampanj.

![](assets/s_ncs_user_task_percentage_done_from_op.png)

Om slutdatumet för schemat för aktivitetskörning har nåtts men aktiviteten inte har slutförts, kommer aktiviteten att **[!UICONTROL Late]**. Ett varningsmeddelande visas även för aviseringsoperatörer.

Mer information finns i [Status för en uppgift](#progress-status-of-a-task).

### Utgifter och intäkter {#expenses-and-revenues}

Du kan definiera relaterade utgifter och prognosintäkter för varje uppgift. Dessa beräknas och konsolideras sedan för den kampanj som aktiviteten är kopplad till.

Om du vill ange den här informationen klickar du på **[!UICONTROL Expenses and revenue]** i verktygsfältet.

![](assets/s_ncs_user_task_edit_costs.png)

Som standard är den debiterade budgeten budgeten för den kampanj som aktiviteten är kopplad till. Den visas i uppgiftsinformationen.

>[!NOTE]
>
>Mer information om utgifter och budgetar finns i [det här avsnittet](../campaigns/providers--stocks-and-budgets.md#cost-commitment--calculation-and-charging).

I det här fönstret kan du också definiera vilka mål som ska uppnås. Målen uttrycks i prognosintäkter för uppgiften.

### Tjänsteleverantörer {#service-providers}

En extern tjänsteleverantör kan vara involverad i hanteringen av en uppgift.

Om du vill göra det redigerar du uppgiftsegenskaperna och väljer tjänsteleverantören. Kostnadskategorierna som är kopplade till tjänsteleverantören listas automatiskt i fönstrets centrala avsnitt.

Välj de kostnadskategorier som är relaterade till utförandet av uppgiften. Välj typ av kostnad och lägg till ett tilläggsbelopp om det behövs.

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>Metoden för att hantera budgetar och kostnader presenteras i [Kontrollkostnader](controlling-costs.md).

När en tjänsteleverantör har valts visas den på kontrollpanelen för uppgifter:

![](assets/s_ncs_user_task_supplier_view.png)

### Sena uppgifter {#late-tasks}

En aktivitet är sen om slutdatumet har nåtts utan att dess status ändras till **[!UICONTROL Finished]**. Som standard varnas ingen operator när en uppgift är sen. Du kan konfigurera leveransen av ett e-postmeddelande: alla operatorer kan meddelas även om de inte deltar i uppgiften.

Gå till **[!UICONTROL Resources]** och lägg till operatorn i **[!UICONTROL Assignation]** fält. Om du vill meddela flera personer väljer du en grupp med operatorer.

![](assets/mrm_task_alert_if_late.png)

### Inledande meddelanden {#initial-notifications}

När du skapar eller ändrar en uppgift med ett startdatum i framtiden erbjuder Adobe Campaign att skicka ett e-postmeddelande till den person som ansvarar för uppgiften så att de får veta när den börjar.

![](assets/mrm_task_first_notif.png)

Om den uppgift du skapar är långt borta kan det dock vara bättre att schemalägga att meddelandet skickas innan aktiviteten startar. Om uppgiften till exempel startar inom en månad kan du meddela den ansvariga personen en vecka innan den börjar.

Om du vill schemalägga ett meddelande går du till **[!UICONTROL Resources]** och använder **[!UICONTROL Initial notification]** fält.

![](assets/mrm_task_alert_before.png)

* För uppgifter inom kampanjer väljer du ett specifikt datum och en viss tid.
* För uppgifter i kampanjmallar uttrycks meddelandetiden som den återstående tiden innan aktiviteten startar (t.ex. om du anger 2d i **[!UICONTROL Initial notification]** skickas e-postmeddelandet 2 dagar före aktivitetens startdatum).

Om du har schemalagt ett meddelande kommer Adobe Campaign att skicka ett meddelande direkt när du sparar uppgiften. Du kan bestämma dig för att skicka det och detta ersätter inte det schemalagda meddelandet.

### Aktivitet länkad till ett program {#task-linked-to-a-program}

Du kan skapa aktiviteter direkt i ett program för att hantera åtgärder som gäller deras övergripande organisation och inte en viss kampanj (till exempel ett möte för att diskutera temat för kommande kampanjer i programmet). Aktiviteten visas i programschemat.

Så här skapar du en uppgift som är länkad direkt till ett program:

1. Öppna programschemat: på startsidan, gå till **[!UICONTROL Campaigns > Browse > Other choices > Programs]**. Det övergripande programschemat öppnas i den högra delen av fönstret.
1. Klicka på önskat program i schemat: ett fönster öppnas.
1. I det här fönstret klickar du på **[!UICONTROL Open]**. Programschemat öppnas.
1. Klicka på **[!UICONTROL Add]** ovanför schemat till höger och klicka sedan på **[!UICONTROL Add a task]**.

![](assets/mrm_task_create_from_prg.png)

### Operatörens tillgänglighet {#operator-availability}

En ikon bredvid operatorns namn på kontrollpanelen för uppgifter anger att de redan arbetar med en annan uppgift eller händelse under den period som aktiviteten omfattar. Uppgiften som operatorn ansvarar för eller deltar i visas i **[!UICONTROL Assigned to]** fält eller i uppgiften **[!UICONTROL Resources]** box.

![](assets/mrm_task_alert_operator_busy.png)

### Uppgift i ett arbetsflöde {#task-in-a-workflow}

Använda en **[!UICONTROL Task]** kan du definiera två scenarier beroende på om aktiviteten har godkänts eller inte.

![](assets/mrm_task_in_workflow.png)

I kampanjarbetsflödena **[!UICONTROL Task]** aktiviteten finns i **[!UICONTROL Flow control]** -fliken.

## Typer av uppgifter {#types-of-task}

När du skapar uppgifter via en kampanj kan du skapa specifika uppgifter. Typen av uppgift definieras i den valda mallen.

![](assets/s_ncs_user_task_select_template.png)

Följande uppgifter kan schemaläggas:

* [Styra uppgifter](#control-tasks),
* [Grupperingsuppgift](#grouping-task),
* [Grupperingsuppgift](#grouping-task),
* [Meddelandeuppgift](#notification-task).

>[!NOTE]
>
>**[!UICONTROL Control task]** och **[!UICONTROL Grouping]** uppgifter kan skapas **endast** via kampanjkontrollpanelen.\
>De visas i aktivitetskartan för den operator som de är tilldelade till. Se [Åtkomstuppgifter](#accessing-tasks).

### Styra uppgifter {#control-tasks}

A **[!UICONTROL Control task]** är länkat till leveransgodkännande: godkännande av målgruppsanpassning, innehåll, extraheringsfil, budget eller korrektur.

![](assets/s_ncs_user_task_new_control.png)

När aktiviteten har skapats läggs den till på kampanjkontrollpanelen.

![](assets/s_ncs_user_task_edit_from_board.png)

Du kan sedan redigera den och ange dess parametrar.

### Skapande av marknadsföringsresurs {#marketing-resource-creation-task}

En uppgift att skapa marknadsföringsresurser kan användas för att hantera skapandet och publiceringen av en marknadsföringsresurs. Om du hanterar en resurs via en aktivitet och inte via själva resursen kan du:

* Styr processen för att skapa resurser via en kampanj.
* Visa resursskapandeprocessen i ett schema.
* Hantera processen för att skapa resurser (påminnelser, meddelanden).
* Beräkna och kontrollera kostnaderna för att skapa resurser.
* Godkänn och publicera resursen via aktiviteten (om det relevanta alternativet är aktiverat).

#### Interaktion mellan aktiviteten och dess länkade resurs {#interaction-between-the-task-and-its-linked-resource}

Aktiviteten för att skapa marknadsföringsresurser interagerar med den resurs som är länkad till den. Detta innebär:

* Schemat för att skapa resurser och de kostnader som är kopplade till det hanteras via aktiviteten.
* Operatorer kan arbeta med resursen som vanligt (hämta eller ladda upp, låsa och låsa upp): detta påverkar inte aktiviteten.
* Godkännande och offentliggörande av resurser kan utföras via uppgiften: om **[!UICONTROL Publish the marketing resource]** om alternativet är aktiverat godkänns och publiceras resursen automatiskt när aktiviteten är klar. Om alternativet inte är aktiverat samverkar aktiviteten och resursen inte: Att agera på en påverkar inte den andra.

   Du kan använda en serie länkade uppgifter för att definiera en fullständig godkännandecykel. Kontrollera **[!UICONTROL Publish the marketing resource]** endast för den senaste uppgiften: alla aktiviteter måste slutföras för att resursen ska kunna publiceras. När du skapar en underordnad marknadsföringsresursuppgift väljs resursen automatiskt i den underordnade aktiviteten.

   * **Via resursen**: om du skickar resursen för godkännande eller godkännande kommer dessa åtgärder inte att påverka aktiviteten.
   * **Via uppgiften**: om **[!UICONTROL Publish the marketing resource]** om alternativet är incheckat i aktiviteten, godkänns resursen och publiceras automatiskt när aktiviteten är klar (se ovan). Om alternativet inte är markerat samverkar aktiviteten och resursen inte: Att agera på en påverkar inte den andra.

#### Konfigurera en uppgift att skapa en marknadsföringsresurs {#configuring-a-marketing-resource-creation-task}

Den person som granskar uppgiften behöver inte samma person som granskar innehållet som definierats i resursen. Om **[!UICONTROL Publish the marketing resource]** alternativet är markerat (se nedan), har uppgiftsgranskaren behörighet att godkänna resursinnehållet, eftersom uppgiften automatiskt godkänner resursen (eller, om ingen granskare är definierad, aktivitetshanteraren).

![](assets/mrm_task_asset_creation.png)

I **[!UICONTROL Marketing resource]** definierar du den resurs som du vill hantera med den här uppgiften. Du kan:

* Välj en befintlig resurs: listrutan innehåller alla resurser med statusen **[!UICONTROL Being edited]**.
* Skapa en resurs: klicka på **[!UICONTROL Select the link]** klickar du på **[!UICONTROL Create]** ikon.

The **[!UICONTROL Publish the marketing resource]** kan du automatisera resurspublicering: när uppgiften är **[!UICONTROL Finished]**, ändras resursens status automatiskt till **[!UICONTROL Published]**, även om det inte har skickats för godkännande eller godkännande, inklusive om granskaren som slutför uppgiften inte är den som har definierats i resursen.

The **[!UICONTROL Publish the resource]** knappen är tillgänglig och resurspubliceringsgranskaren får ett e-postmeddelande om att den är klar att publiceras. I **[!UICONTROL Edit > Tracking]** -fliken, granska och publicera av uppgiftsgranskaren visas. Om ett arbetsflöde för efterbearbetning av resurser har definierats, körs det nu.

![](assets/mrm_resource_audit_tab.png)

### Gruppuppgift {#grouping-task}

The **[!UICONTROL Grouping task]** kan du gruppera flera uppgifter och synkronisera hanteringen av deras förlopp och deras godkännande.

Grupperingsuppgifter har inga länkade utgifter eller resurser.

Alla uppgifter som grupperas efter en grupperingsaktivitet kan visas på en egen kontrollpanel. På så sätt kan du filtrera listan med uppgifter så att endast de som intresserar dig visas.

Grupperingsuppgifter har en länk som gör att du enkelt kan skapa en grupperad uppgift.

Om du vill skapa en grupperad uppgift baserat på en grupperingsaktivitet går du till instrumentpanelen för kampanj och klickar på namnet på grupperingsaktiviteten för att visa dess beskrivning. Klicka sedan på **[!UICONTROL Add a task]**.

![](assets/mrm_task_grouped_create.png)

Om du redan har skapat en uppgift som du vill länka till en grupperingsåtgärd kan du göra det via **[!UICONTROL Linked to]** fält för **[!UICONTROL Properties]** box.

![](assets/s_ncs_user_task_group_with.png)

### Meddelandeuppgift {#notification-task}

Med meddelandeaktiviteter kan du schemalägga e-postleveranser (till en operator, en grupp operatorer, en tjänsteleverantör osv.). På så sätt kan ni schemalägga påminnelser, till exempel för att meddela någon att en kampanj är klar snart, eller för att skicka dokument innan en kampanj startar så att operatörerna kan förbereda den. Det innebär att ni kan hålla koll på er kommunikation inom ramen för kampanjen eller programmet och få ett närmare grepp om de åtgärder som vidtas.

#### Livscykel {#life-cycle}

Meddelandeaktiviteter kräver inte godkännande. Det innebär att deras livscykel är enklare än en standarduppgift:

![](assets/mrm_task_notif_lifecycle.png)

En meddelandeaktivitet kan ha följande status:

* **[!UICONTROL Scheduled]** tills e-postmeddelandet har skickats
* **[!UICONTROL In progress]** när e-postmeddelandet har skickats och till slutdatumet har nåtts
* **[!UICONTROL Finished]** när slutdatumet har nåtts.

#### Konfiguration {#configuration}

![](assets/mrm_task_notif_dashboard.png)

När du skapar en uppgift måste du ange följande element:

* **[!UICONTROL Assigned to]** : den operator eller den grupp av operatorer som ska ta emot e-postmeddelandet. Om du tilldelar om uppgiften när e-postmeddelandet har skickats, skickas inte e-postmeddelandet till den nya operatorn (för att detta ska ske måste du initiera om uppgiften och ändra startdatumet).
* **Startdatum för uppgift**: det datum då e-postmeddelandet skickas. Detta datum måste infalla i framtiden när uppgiften registreras.
* **Slutdatum för uppgift**: det datum då uppgiftsstatusen ändras till **[!UICONTROL Finished]**. Som standard är slutdatumet identiskt med startdatumet. Om du tilldelar en varaktighet till aktiviteten kan du däremot symbolisera hur lång tid operatorn måste utföra i schemat, om det behövs.
* **[!UICONTROL Description]** : den text som anges här kommer att visas i meddelandets brödtext.

   ![](assets/mrm_task_notif_dashboard_msg.png)

Du kan lägga till en bifogad fil till uppgiften och i e-postmeddelandet. Om du vill göra det klickar du på **[!UICONTROL Documents]** i verktygsfältet i det övre högra hörnet.

## Livscykel {#life-cycle-1}

### Länkar mellan uppgifter {#links-between-tasks}

The **[!UICONTROL Properties]** kan du definiera länkarna mellan aktiviteterna i en kampanj med hjälp av knappen för varje uppgift. Du kan dela upp uppgifter i underaktiviteter med hjälp av en grupperingsaktivitet (se [Länkade uppgifter](#linked-tasks)) eller definiera beroenden mellan aktiviteterna (se [Gruppera uppgifter](#grouping-tasks)).

#### Länkade uppgifter {#linked-tasks}

Använd **[!UICONTROL Linked task]** fält för att associera uppgifter med en grupperingsaktivitet. Se [Typer av uppgifter](#types-of-task).

I följande exempel delas godkännandet av målinriktning upp i fyra underaktiviteter.

![](assets/s_ncs_user_task_linked_tasks.png)

Varje underuppgift är en standarduppgift som är länkad till huvuduppgiften.

![](assets/s_ncs_user_task_depends_on.png)

#### Gruppera uppgifter {#grouping-tasks}

Använd **[!UICONTROL Grouped to]** fält för att göra körningen av en uppgift beroende av körningen av en annan uppgift.

![](assets/s_ncs_user_task_group_with.png)

Beroendet mellan aktiviteter representeras av pilar på kontrollpanelen för kampanjer.

![](assets/s_ncs_user_task_dependencies_from_board.png)

När det gäller grupperade uppgifter tilldelar Adobe Campaign automatiskt slutdatumet för den överordnade uppgiften till den underordnade aktiviteten som startdatum. Till exempel om en **Skapa inbjudan** aktiviteten upphör den 15 oktober kl. 3:30, **Skicka e-postinbjudan** underordnad aktivitet börjar 15 oktober klockan 17:30.

Om du skjuter upp slutet på en överordnad uppgift kan vissa av dess underordnade uppgifter påverkas: detta är de underordnade uppgifterna vars status är **[!UICONTROL Scheduled]** och vars startdatum är tidigare än det nya slutdatumet för den överordnade uppgiften. Aktivitetens längd ändras inte. Om startdatumet för en underordnad uppgift är senare än det nya slutdatumet för den överordnade aktiviteten påverkas inte den underordnade aktiviteten.

**Exempel**

En överordnad aktivitet som schemaläggs att avslutas den 9 oktober klockan 17.00 har två underordnade uppgifter, aktivitet A och aktivitet B. Aktivitet A är planerad att påbörjas den 10 oktober kl. 20 och uppgift B är planerad att påbörjas den 12 oktober kl. 8.00.

Låt oss skjuta upp den överordnade uppgiften: upphör nu den 11 oktober klockan 11. Endast uppgift A senareläggs och börjar 11 oktober klockan 16.00.

![](assets/mrm_task_parent_postpones_child.png)

### Körningsstatus för en uppgift {#execution-status-of-a-task}

Uppgiftsstatusvärden kan visas på aktivitetskartan. Körningsstatusen för en aktivitet uppdateras automatiskt enligt operatoråtgärder.

En uppgift kan vara: **[!UICONTROL Scheduled]**, **[!UICONTROL In progress]**, **[!UICONTROL Finished]**, **[!UICONTROL Canceled]**, **[!UICONTROL Pending approval]** eller **[!UICONTROL Rejected]**.

* När en uppgift skapas är den **[!UICONTROL Scheduled]** om startdatumet infaller i framtiden. Den här statusen behålls tills dess startdatum nås.
* När aktiviteten har startats är den **[!UICONTROL In progress]**. När den person som ansvarar för uppgiften stänger den ändras den till **[!UICONTROL Finished]**.
* Om en granskare har definierats blir uppgiften **[!UICONTROL Pending approval]** när den som ansvarar för det har stängt den och tills granskaren har godkänt den. Om granskaren avvisar den blir uppgiften **[!UICONTROL Rejected]**.
* En uppgift kan avbrytas av den som ansvarar för den via kontrollpanelen eller **[!UICONTROL Task map]** genom att klicka på **[!UICONTROL Cancel]** -knappen.
* Om du vill schemalägga en aktivitet anger du ett startdatum i framtiden. Du kan sedan skicka ett första meddelande till de Adobe Campaign-operatorer som utför uppgiften. Se [Slutför aktivitetens livscykel](#complete-task-life-cycle).

>[!NOTE]
>
>* Aktivitetens status uppdateras automatiskt.
>* Även om giltighetsperioden är slut visas uppgifter som inte stängts fortfarande i listan över pågående uppgifter. En varning meddelar operatorer om att aktiviteten är sen.
>


### Status för en uppgift {#progress-status-of-a-task}

Förutom körningsstatus kan en uppgift associeras med en förloppsstatus: **[!UICONTROL Late]**, **[!UICONTROL To approve]**, **[!UICONTROL To do today]** eller **[!UICONTROL To do this week]**. Den här informationen anges automatiskt i enlighet med aktivitetsschemat.

Du kan filtrera listan över uppgifter efter process- eller förloppsstatus.

Mer information finns i [Åtkomst till uppgifter](#accessing-tasks).

### Slutför aktivitetens livscykel {#complete-task-life-cycle}

Nedan visas de steg i en komplett uppgiftslivscykel för vilka den ansvariga personen har definierat deltagare och granskare.

1. Ansvarig skapar uppgiften och anger de olika fälten. Mer information finns i [Skapa en ny uppgift](#creating-a-new-task).

   När du skapar och redigerar en uppgift **schemalagd i framtiden** (så länge som startdatumet för aktiviteten inte nås) kan du skicka ett meddelande till deltagare och chefer för att meddela dem att en ny uppgift har schemalagts.

   ![](assets/s_ncs_user_task_planed_send_message.png)

   Om du vill skicka det här första meddelandet klickar du på **[!UICONTROL Yes]**. Det här meddelandet ger dem information om nästa uppgift och innehåller information om innehållet och antalet dagar som återstår tills tidsgränsen har nåtts.

   När en aktivitet skapas och schemaläggs för framtiden är dess status **[!UICONTROL Scheduled]**.

1. På startdatumet för aktiviteten får den ansvariga och deltagarna ett meddelande om att aktiviteten har startats. Dess status ändras till **[!UICONTROL In progress]**.
1. När du är klar med avsnittet som tilldelats dem kan deltagarna godkänna uppgiften, antingen:

   * via e-postmeddelandet.
   * via klientkonsolen eller webbgränssnittet i kontrollpanelen för uppgifter.

      ![](assets/s_ncs_user_task_start_rea.png)

1. Varje gång en deltagare godkänner ett jobb uppdateras uppgiftens förloppsstatus.

   ![](assets/s_ncs_user_task_percentage_done_op.png)

1. Granskaren får ett e-postmeddelande som talar om för dem att operatorn har slutfört det avsnitt som tilldelats dem.

   De kan följa förloppet på kontrollpanelen för uppgifter.

   ![](assets/s_ncs_user_task_follow_from_dashboard.png)

1. När den person som ansvarar för uppgiften har fastställt att den är slutförd kan han eller hon stänga den med hjälp av länken i e-postmeddelandet som skickades när aktiviteten startades, via klientkonsolen eller gränssnittet.

   ![](assets/s_ncs_user_task_console_ressource_validation.png)

   >[!NOTE]
   >
   >Den person som ansvarar för en uppgift kan när som helst stänga den, även om godkännanden saknas. Förloppsstatusen ändras automatiskt till 100 %.

1. Aktivitetsstatusen ändras till **[!UICONTROL To approve]** och ett meddelande skickas till granskaren.

   De godkänner uppgiften via e-postmeddelandet, klientkonsolen eller webbgränssnittet.

   De kan agera via kampanjkontrollpanelen:

   ![](assets/s_ncs_user_task_console_validation.png)

   De kan också använda knappen för godkännande av uppgifter:

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >Aktivitetens status ändras endast till **[!UICONTROL To approve]** om du har aktiverat **[!UICONTROL Enable task validation]** i **[!UICONTROL Resources]** aktivitetens fönster.\
   >Om granskaren avvisar uppgiften ändras dess status till **[!UICONTROL Rejected]** och uppgiftscykeln startar automatiskt igen.

1. Aktivitetsstatusen ändras till **[!UICONTROL Finished]**. Ett meddelande skickas till alla berörda.

   >[!NOTE]
   >
   >När en uppgift är slutförd kan den ansvariga personen återinitiera dess livscykel. Det gör du genom att öppna uppgiften och klicka på **[!UICONTROL Reset task to execute it again...]** längst ned på kontrollpanelen.
