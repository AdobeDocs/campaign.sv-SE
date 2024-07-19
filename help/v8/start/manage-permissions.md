---
title: Bevilja behörigheter för Campaign v8
description: Lär dig hur du tilldelar behörigheter till Campaign v8-användare
feature: Permissions
role: User, Admin
level: Beginner
exl-id: 90154f84-b6a7-407c-93b7-9731dc94d9de
source-git-commit: 09db0cc1a14bffefe8d1b8d0d5a06d5b6517a5bb
workflow-type: tm+mt
source-wordcount: '1618'
ht-degree: 0%

---

# Hantera användarbehörigheter{#manage-permissions}

## Lägg till användare {#add-users}

Som produktadministratör kan du lägga till användare och bevilja åtkomst till Campaign.

Följ stegen nedan för att lägga till en användare:

1. På hemsidan [Admin Console](https://adminconsole.adobe.com/enterprise){target="_blank"} väljer du **Lägg till användare**.

   ![](assets/add-a-user.png)

1. Ange användarens e-postadress.
1. Använd plustecknet (+) för att välja de produktprofiler eller användargrupper som ska tilldelas användaren.

   ![](assets/add-a-product-profile.png)

   De inbyggda produktprofilerna för kampanjen listas i [det här avsnittet](#ootb-productprofiles).

   Lär dig skapa användargrupper i [det här avsnittet](#user-groups)

1. Klicka på **Spara**. Användaren läggs till och visas i listan Användare. Om du tilldelar användare en administratörsroll eller en produktprofil får de ett e-postmeddelande. Användarna måste följa länken för att slutföra sin profil.

Läs mer om hur du skapar användare i Admin Console på [den här sidan](https://helpx.adobe.com/ie/enterprise/using/manage-users-individually.html){target="_blank"}.

När nya användare [loggar in på Campaign](connect.md) med sina Adobe ID läggs de till i listan över kampanjoperatorer i klientkonsolen. Kampanjoperatorer lagras i mappen **[!UICONTROL Administration > Access management > Operators]** i Campaign Explorer.

## Arbeta med produktprofiler{#product-profiles}

Använd produktprofiler för att ge användarna rätt till de funktioner som ingår i produkten.

* För varje produkt på Admin Console kan du skapa en eller flera produktprofiler.
* I varje produktprofil tilldelar du användare och användargrupper (i din organisation).
* När en användare loggar in med sina inloggningsuppgifter enligt specifikationen i produktprofilen, får de tillgång till programmen och tjänsterna i den produkt som produktprofilen baseras på.

Dessa produktprofiler matchar operatörsgrupper som lagras i mappen **[!UICONTROL Administration > Access management > Operator groups]** i Campaign Explorer.

I Admin Console används följande syntax för produktprofiler:

kampanj - `<your instance>` - operatorgruppens interna namn

För gruppen **Delivery operator** i instansen test är produktprofilen i Admin Console:

kampanj - test - leverans

Du kan använda standardproduktprofiler eller skapa nya.

### Skapa en produktprofil{#create-product-profile}

Om du vill lägga till en ny produktprofil i Adobe måste du först skapa den i Campaign-klientkonsolen och sedan lägga till den i Admin Console.

Om du till exempel vill skapa en produktprofil för &#39;granskare&#39; följer du stegen nedan.

#### Skapa operatorgruppen i Campaign{#create-op-group}

1. Anslut till Campaign, öppna Utforskaren och gå till **[!UICONTROL Administration > Access management > Operator groups]**.
1. Klicka på **[!UICONTROL New]** och definiera namnet på operatörsgruppen och ange dess interna namn (&#39;reviewers&#39;).
   ![](assets/new-op-group.png)
1. Definiera de associerade behörigheterna genom att välja namngivna rättigheter. Namngivna rättigheter beskrivs i [det här avsnittet](#use-named-rights)
1. Spara den nya operatörsgruppen.

#### Skapa produktprofilen i Admin Console{#create-profile-in-admin-console}

1. Anslut till [Admin Console](https://adminconsole.adobe.com/enterprise){target="_blank"}.
1. Öppna Campaign-produkten från avsnittet **Produkt och tjänster** på startsidan.
1. Klicka på **Ny profil** och ange namnet på produktprofilen som ska skapas, med exakt rätt syntax enligt beskrivningen [här](#product-profiles). Vi skriver till exempel: kampanj - `<your-instance-name>` - granskare

   ![](assets/new-product-profile-ui.png)

1. Spara ändringarna.

Nu kan du lägga till användare i den nya produktprofilen, vilket förklaras i [det här avsnittet](#add-users).

Det bästa sättet är att tilldela produktprofiler till användargrupper. Att hantera behörigheter efter användare är inte en hållbar modell.


### Standardproduktprofiler och operatörsgrupper {#ootb-productprofiles}

Adobe Campaign levereras med inbyggda **produktprofiler** som definieras när Adobe aktiverar din miljö.

![](assets/ootb-product-profiles.png)

De här produktprofilerna överensstämmer med Campaign **operatorgrupper**. Standardoperatorgrupperna och deras [namngivna rättigheter](#use-named-rights) visas nedan:

1. **[!UICONTROL Administrator]** (admin)

   Operatorerna i den här gruppen har fullständig åtkomst till instansen. Administratörer är användare som har tillgång till de flesta tekniska delarna av användargränssnittet.

   Den här gruppen innehåller följande namngivna rättigheter:

   * **[!UICONTROL ADMINISTRATION]**: behörighet att köra/skapa/redigera/ta bort objekt som arbetsflöde, leverans, skript osv.

1. **[!UICONTROL Delivery operators]** (leverans)

   Operatörerna i den här gruppen ansvarar för att hantera leveranser: de ger åtkomst till de viktigaste resurser som krävs för att skapa och förbereda leveranser (kampanjtyper, leveransmappningar, standardmallar, personaliseringsblock osv.).

   Den här gruppen innehåller följande namngivna rättigheter:

   * **[!UICONTROL PREPARE DELIVERIES]**: behörighet att skapa, redigera och starta leveransanalysen,
   * **[!UICONTROL START DELIVERIES]**: behörighet att godkänna tidigare analyserade leveranser.

1. **[!UICONTROL Campaign managers]** (åtgärd)

   Operatörerna i den här gruppen kan hantera marknadsföringskampanjer: ni får tillgång till objekt som är kopplade till kampanjer (planer, program, arbetsflöden, budgetar osv.) inom ramverket för **[!UICONTROL Campaign]** (valfri Adobe Campaign-modul).

   Den här gruppen innehåller följande namngivna rättigheter:

   * **[!UICONTROL INSERT FOLDERS]**: behörighet att infoga mappar i Adobe Campaign-trädet (förutsatt att du har redigeringsbehörighet för de berörda grenarna),
   * **[!UICONTROL WORKFLOW]**: rätt att använda arbetsflöden.

   >[!NOTE]
   >
   >Den här gruppen tillåter inte att operatorer påbörjar leveranser.

1. **[!UICONTROL Content contributors]** (innehåll)

   Användare i den här gruppen kan komma åt innehållsmapparna i samband med tillägget **[!UICONTROL Content management]**. Den här gruppen ger inte några ytterligare behörigheter.

1. **[!UICONTROL Access to reports]** (rapport)

   Den här gruppen är reserverad för externa operatorer för att få åtkomst till leveransrapporter via [webbåtkomst](../start/campaign-ui.md#web-browser).

1. **[!UICONTROL Workflow execution]** (arbetsflöde)

   Med gruppen **[!UICONTROL Workflow execution]** kan du styra körning och godkännande av arbetsflöden för målinriktning: det namngivna högra arbetsflödet mappas till den här gruppens operatorer. Det krävs för alla åtgärder i arbetsflöden, förutom åtkomsträttigheter till datafilerna. Som standard har gruppen **[!UICONTROL Workflow execution]** skrivskyddad åtkomst till arbetsflödesfiler och arbetsflödesmallar för målinriktning. Operatörer i den här gruppen har även läs- och skrivåtkomst till filen för väntande godkännanden.

1. **[!UICONTROL Workflow supervisors]** (workflowSupervisor)

   Användare i den här gruppen hanterar godkännanden av arbetsflöden och får ett e-postmeddelande om det uppstår varningar om kampanjarbetsflöden.

1. **Lokal/Central hantering** (central/lokal)

   Användare i den här gruppen kan använda tillägget **[!UICONTROL Distributed marketing]**.

1. **[!UICONTROL Offer managers]** (erbjudande)

   Operatorerna i den här gruppen kan skapa och underhålla erbjudanden när interaktionstillägget används. [Läs mer](../interaction/interaction-operators.md).

   Den här gruppen innehåller följande namngivna rättigheter:

   * **[!UICONTROL INSERT FOLDERS]**: Rätt att infoga mappar i Adobe Campaign-trädet (förutsatt att du har redigeringsbehörighet för de berörda grenarna),
   * **[!UICONTROL EDIT FOLDERS]**: Rätt att ändra mappegenskaper som internt namn, etikett, associerad bild, undermappsordning osv.

   Behörigheter som tilldelats till erbjudandehanterare gör det möjligt för dem att utföra följande uppgifter:

   * Ändra **[!UICONTROL Design]**-miljöer.
   * Visa **[!UICONTROL Live]**-miljöer.
   * Konfigurera administrationsfunktioner (fördefinierade blanksteg och filter).
   * Skapa och uppdatera kategorier.
   * Skapa erbjudanden.
   * Konfigurera berättigande för erbjudanden.
   * Godkänn erbjudanden.

   >[!NOTE]
   >
   >**Erbjudandehanterare** kan bara godkänna ett erbjudande om ingen granskare har angetts, eller om de har angetts som granskare i erbjudandemallen.

   Behörighetsmatris för erbjudandehanteraren per miljö finns på [den här sidan](../interaction/interaction-operators.md#recap-of-rights-according-to-operator).

## Arbeta med användargrupper{#user-groups}

Du kan använda Admin Console för att skapa användargrupper och tilldela användare till dem.

En användargrupp är en samling olika användare som måste få en delad uppsättning behörigheter. Lär dig hur du skapar användargrupper i [det här avsnittet](https://helpx.adobe.com/ie/enterprise/using/user-groups.html){target="_blank"}.

Du kan tilldela produktprofiler till användargrupper. Alla användare i gruppen får alltså samma produktbehörigheter.

## Namngivna rättigheter{#use-named-rights}

Adobe Campaign har en uppsättning namngivna rättigheter som gör att du kan definiera behörigheter som tilldelats användare och grupper av användare. Dessa rättigheter kan redigeras från mappen **[!UICONTROL Administration > Access management > Named rights]** i Campaign Explorer.

Namngivna rättigheter ger behörigheter till:

* Utföra åtgärder
Knappen **Analysera** i leveransredigeraren aktiveras till exempel för medlemmar i gruppen **Leveransoperatör** som har namnet **Förbered leverans** till höger

* Åtkomst till mappar
Medlemskap i operatörsgrupper kan ge eller begränsa åtkomsträttigheter till mappar genom att ändra säkerhetsinställningarna för mappar. [Läs mer](folder-permissions.md#restrict-access-to-a-folder).

  Det kan till exempel påverka: **Skrivåtkomst** för att skapa nya entiteter (som leveranser, profiler osv.), **Läsåtkomst** för att använda entiteter, **Ta bort åtkomst** för att ta bort entiteter.

Namngivna standardrättigheter i Adobe Campaign är:

* **[!UICONTROL ADMINISTRATION]**: Operatorer med rättigheten **[!UICONTROL ADMINISTRATION]** har fullständig åtkomst till instansen. Administratörsanvändare kan köra/skapa/redigera/ta bort objekt som arbetsflöde, leverans, skript osv.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: Du kan ange flera godkännandesteg i arbetsflöden och leveranser för att säkerställa att det aktuella tillståndet har godkänts av en tilldelad operator eller grupp. Användare med rättigheten **[!UICONTROL APPROVAL ADMINISTRATION]** kan ange godkännandesteg och även tilldela en operator eller operatorgrupp som ska godkänna dessa steg.

* **[!UICONTROL CENTRAL]**: Rätt till central hantering (distribuerad marknadsföring).

* **[!UICONTROL DELETE FOLDER]**: Rätt att ta bort mappar. Med den här rättigheten kan användare ta bort mappar från utforskarvyn.

* **[!UICONTROL EDIT FOLDERS]**: Rätt att ändra mappegenskaper som internt namn, etikett, associerad bild, undermappsordning osv.

* **[!UICONTROL EXPORT]**: Användare kan exportera data från sina Adobe Campaign-instanser till en fil på servern eller den lokala datorn med hjälp av arbetsflödesaktiviteten i **[!UICONTROL EXPORT]**.

* **[!UICONTROL FILES ACCESS]**: Rätt att läsa och skriva åtkomst för filer via ett skript som kan skrivas i arbetsflödesaktiviteten i **[!UICONTROL JavaScript]** för att läsa/skriva filer på en server.

* **[!UICONTROL IMPORT]**: Rätt för allmän dataimport. **[!UICONTROL IMPORT]** tillåter att du importerar data till andra tabeller, medan rättigheten **[!UICONTROL RECIPIENT IMPORT]** bara tillåter import till mottagartabellen.

* **[!UICONTROL INSERT FOLDERS]**: Rätt att infoga mappar. Användare med rättigheten **[!UICONTROL INSERT FOLDERS]** kan skapa nya mappar i mappträdet i utforskarvyn.

* **[!UICONTROL LOCAL]**: Rätt till lokal hantering (distribuerad marknadsföring).

* **[!UICONTROL MERGE]**: Höger att sammanfoga de markerade posterna till en. Om mottagarna finns som dubbletter tillåter rättigheten **[!UICONTROL MERGE]** användaren att välja dubbletter och sammanfoga dem till en primär mottagare.

* **[!UICONTROL PREPARE DELIVERIES]**: Rätt att skapa, redigera och spara en leverans. Användare med rättigheten **[!UICONTROL PREPARE DELIVERIES]** kan också starta leveransanalysprocessen.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Rätt att samla in och ta bort sekretessdata. [Läs mer](privacy.md).

* **[!UICONTROL PROGRAM EXECUTION]**: Rätt att köra kommandon på olika programmeringsspråk.

* **[!UICONTROL RECIPIENT IMPORT]**: Rätt att importera mottagare. Användare med rättigheten **[!UICONTROL RECIPIENT IMPORT]** kan importera en lokal fil till mottagartabellen.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Rätt att köra ett SQL-kommando direkt i databasen.

* **[!UICONTROL START DELIVERIES]**: Rätt att godkänna tidigare analyserade leveranser. Efter leveransanalysen pausas leveransen vid olika godkännandesteg och måste godkännas för att kunna återupptas. Användare med rättigheten **[!UICONTROL START DELIVERIES]** kan godkänna leveranser.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Rätt att skriva egna SQL-skript med SQL Data Management-aktiviteten för att skapa och fylla i arbetstabeller. [Läs mer](../../automation/workflow/sql-data-management.md).

* **[!UICONTROL WORKFLOW]**: Den här namngivna rättigheten är specifik för arbetsflöden: du kan skapa, starta och stoppa arbetsflöden. Läsbehörighet för arbetsflödesfilen krävs för att den namngivna rättigheten ska kunna användas. För målarbetsflöden krävs läsbehörighet för mappen **[!UICONTROL Profiles and Targets]**.


* **[!UICONTROL WEBAPP]**: Rätt att använda webbprogram.

>[!NOTE]
>
>Listan kan variera beroende på vilka tillägg som är installerade i din miljö.



## Ytterligare resurser{#additional-res}

* [Hantera behörigheter för arbetsflöden](../../automation/workflow/managing-rights.md)
* [Hantera behörigheter för distribuerad marknadsföring](../../automation/distributed-marketing/about-distributed-marketing.md#operators)
* [Hantera behörigheter för interaktionsmodulen](../interaction/interaction-operators.md)
* [Filtrera åtkomst till scheman](../dev/filter-schema.md)
* [Begränsa PI-vy](../dev/restrict-pi-view.md)
