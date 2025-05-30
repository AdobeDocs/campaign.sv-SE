---
product: campaign
title: Använd typologiregler
description: Lär dig hur du använder typologiregler
feature: Typology Rules
exl-id: 4ec3bbe1-fc4c-4b1e-989c-f4dcf8ee8d5e
source-git-commit: a8568e0c1e9af11b533b7d435691dc12cc0a2485
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 7%

---

# Använd typologiregler{#applying-rules}

## Använd typologi på en leverans {#apply-a-typology-to-a-delivery}

Om du vill tillämpa de typologiregler du har skapat kopplar du den till en typologi och refererar sedan till den här typologin i leveransen.

Gör så här:

1. Skapa en kampanjtypologi.

   Typologier nås via mappen **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** i Campaign Explorer.

1. Gå till fliken **[!UICONTROL Rules]**, klicka på knappen **[!UICONTROL Add]** och välj reglerna som ska användas med den här typologin.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Spara typologin: läggs den till i listan över befintliga typologier.
1. Öppna den leverans som du vill tillämpa reglerna på.
1. Bläddra till leveransegenskaperna och öppna fliken **[!UICONTROL Typology]**.
1. Välj typologi i listrutan.

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >Typologin kan definieras i leveransmallen som automatiskt ska tillämpas på alla leveranser som skapas med den här mallen.

## Definiera programvillkor {#define-application-conditions}

Du kan begränsa programfältet för en regel efter behov (förutom kontrollregler).

Det är möjligt att konfigurera typologiregler så att de endast gäller vissa leveranser som de är kopplade till, eller vissa mottagare bland målet för en leverans.

Om du vill definiera programvillkoren för en regel klickar du på länken **[!UICONTROL Edit the rule application conditions...]** på fliken **[!UICONTROL General]**.

Använd sedan frågeredigeraren för att definiera filtreringsvillkor. I följande exempel gäller kapacitetsregeln endast leveranser med ordet&quot;offer&quot; på etiketten eller leveranser som skapats före 1 april 2013.

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>För filtreringsregler kan du välja programvillkor för filtreringsvillkor: de kan vara beroende av leveransen eller leveransdispositionen. [Läs mer](filtering-rules.md#condition-a-filtering-rule).

## Justera beräkningsfrekvens {#adjust-calculation-frequency}

Godkännanden verkställs automatiskt varje kväll via databasrensningsarbetsflödet. Värden kan dock sparas efter den här perioden.

I vissa beräkningar används värden som inte ändras dagligen. Det skulle därför vara irrelevant att omberäkna data varje dag och överlagra databasen helt utan någonting. Om en process till exempel förbättrar marknadsföringsdatabasen med kundbenägenhetspoäng och inköpsinformation varje vecka, behöver data som baseras på dessa värden inte beräknas om varje dag.

För att göra detta kan du i fältet **[!UICONTROL Frequency]** på fliken **[!UICONTROL General]** definiera en maximal period under vilken mål sparas. Som standard anger värdet **&#x200B;**&#x200B;att beräkningen är giltig tills nästa gång den dagliga omskiljningen utförs.

Om du vill spara resultaten efter den här perioden anger du ett värde som är större än 12 i fältet **[!UICONTROL Frequency]**: när den här perioden har gått ut tillämpas alla regler igen.

Med alternativet **[!UICONTROL Re-apply the rule at the start of personalization]** kan du tillämpa regeln automatiskt under personaliseringsfasen, även om den period som anges i fältet **[!UICONTROL Frequency]** fortfarande är giltig.

## Välja regelprogramfas {#selecting-the-rule-application-phase}

Typologiregler tillämpas i en viss sekvens under målgrupps-, analys- och personaliseringsfaserna för de leveranser de avser.

### Körningsordning {#execution-order}

I standarddriftsläget används reglerna i följande sekvens:

1. Kontrollregler, om de tillämpas i början av målinriktningen.
1. Filtreringsregler:

   * Interna ansökningsregler för adresskvalifikation: definierad adress/ej verifierad adress/adress på blockeringslista/i karantän adress/adresskvalitet.
   * Filtreringsregler som definieras av användaren.
   * Dedupliceringsregel för adressen eller identifieraren (används om det behövs).

1. Tryckregler
1. Kapacitetsregler.
1. Kontrollregler, om de tillämpas när målinriktningen är slut.
1. Styr regler, om de tillämpas i början av personaliseringen. Om användarregler (filtrering/tryck/aktivering) har upphört att gälla och behöver beräknas om, tillämpas de under det här steget.
1. Styr reglerna, om de gäller när personaliseringen är klar.

>[!NOTE]
>
>Om du arbetar med Campaign Interaction Module tillämpas regler för kvalificering av erbjudanden samtidigt som filtreringsregler (för erbjudanden som finns i leveransdispositionerna) eller under personaliseringsfasen, under anropet till erbjudandemotorn.

Du kan anpassa körningssekvensen för regler som har samma typ med hjälp av lämpligt fält på fliken **[!UICONTROL General]** för regeln. När flera regler körs under samma meddelandebearbetningsfas kan du konfigurera deras körningssekvens i fältet **[!UICONTROL Execution sequence]**.

En tryckregel med körningsordningen 20 körs till exempel före en tryckregel med körningsordningen 30.

### Kontrollregler {#control-rules}

För **[!UICONTROL Control]**-regler kan du bestämma vid vilken tidpunkt i leveranscykeln regeln ska tillämpas: före eller efter målanpassning, i början av personaliseringen, i slutet av analysen. Välj det värde som ska användas i listrutan för fältet **[!UICONTROL Phase]** på fliken **[!UICONTROL General]** i typologiregeln.

![](assets/campaign_opt_define_control_phase.png)

Möjliga värden är:

* **[!UICONTROL At the start of targeting]**

  Om du vill förhindra att personaliseringssteget körs om det uppstår fel kan du använda kontrollregeln här.

* **[!UICONTROL After targeting]**

  Om du behöver känna till målvolymen för att kunna använda kontrollregeln väljer du den här fasen.

  Kontrollregeln **[!UICONTROL Check proof size]** gäller till exempel efter varje målfas: den här regeln förhindrar meddelandeanpassning om det finns för många korrekturmottagare.

* **[!UICONTROL At the start of personalization]**

  Denna fas måste väljas om kontrollen avser godkännande av meddelandepersonalisering. Anpassning av meddelanden utförs under analysfasen.

* **[!UICONTROL At the end of the analysis]**

  Välj den här fasen när en kontroll kräver att meddelandepersonalisering är slutförd.

## Ytterligare konfigurationer {#additional-configurations}

### Kontrollera utgående SMTP-trafik {#control-outgoing-smtp-traffic}

Du kan använda fältet **[!UICONTROL Managing affinities with IP addresses]** för att länka leveranser till leveransservern (MTA) med den här tillhörigheten. På så sätt kan du begränsa antalet e-postmeddelanden för specifika leveranser till maskiner eller utdatameddelanden.

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>Tillhörighetshantering gäller inte för **[!UICONTROL Filtering]**-typologier.

<!--
>Affinities are defined in the instance configuration file, on the Adobe Campaign server. For more on this, refer to [this section](../../installation/using/about-initial-configuration.md).-->

### Kampanjoptimering och distribuerad marknadsföring {#campaign-optimization-and-distributed-marketing}

På fliken **[!UICONTROL Distributed Marketing]** kan du definiera ommappning av typologier och/eller regler som gäller när en delad kampanj beställs och/eller reserveras. Typologier/regler som definieras för en lokal enhet (länkade till dem som definierats för den centrala enheten) ersätter regler/typer som är kopplade till den centrala enheten. Med ommappning kan ni anpassa reglerna för centrala enheter till de lokala enheter som beställer kampanjen.

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>I typologier och typologiregler läggs fliken **[!UICONTROL Distributed Marketing]** till om din licens innehåller det här alternativet: kontrollera ditt licensavtal.\
>Mer information om distribuerad marknadsföring finns i [det här avsnittet](../distributed-marketing/about-distributed-marketing.md).
