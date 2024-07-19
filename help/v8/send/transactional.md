---
title: Kampanjtransaktionsmeddelanden
description: Kom igång med Transactional Messaging
feature: Transactional Messaging
role: User
level: Beginner, Intermediate
exl-id: 06fdb279-3776-433f-8d27-33d016473dee
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 1%

---

# Kom igång med Transactional Messaging{#send-transactional-messages}

Transactional Messaging (Message Center) är en Campaign-modul som är utformad för att hantera utlösarmeddelanden. Dessa meddelanden genereras från händelser som utlöses från informationssystem och kan vara: faktura, orderbekräftelse, leveransbekräftelse, lösenordsändring, meddelande om otillgänglighet för produkt, kontobesked, skapande av webbkonto osv.

>[!NOTE]
>
>Som användare av hanterade Cloud Service [kontaktar du Adobe](../start/campaign-faq.md#support){target="_blank"} för att konfigurera kampanjtransaktionsmeddelanden i din miljö.

Transaktionsmeddelanden används för att skicka:

* meddelanden, till exempel orderbekräftelser eller lösenordsåterställningar
* ett individuellt svar i realtid på en kunds handling
* icke-marknadsföringsmaterial

Inställningar för transaktionsmeddelanden beskrivs i [det här avsnittet](../config/transactional-msg-settings.md).

Förstå arkitekturen för transaktionsmeddelanden på [den här sidan](../architecture/architecture.md#transac-msg-archi).

## Transactional messaging operating policy policy {#transactional-messaging-operating-principle}

Adobe Campaign Transactional Messaging-modulen integreras i ett informationssystem som returnerar händelser som ska ändras till personaliserade transaktionsmeddelanden. Dessa meddelanden kan skickas individuellt eller gruppvis via e-post, SMS eller push-meddelanden.

Tänk dig att du är ett företag med en webbplats där kunderna kan köpa produkter.

Med Adobe Campaign kan du skicka ett e-postmeddelande till kunder som har lagt till produkter i kundvagnen. När någon av dem lämnar er webbplats utan att gå igenom sina inköp (en extern händelse som utlöser en Campaign-händelse) skickas ett e-postmeddelande om att kunden överger en kundvagn automatiskt till dem (leverans av transaktionsmeddelanden).

De viktigaste stegen för att införa detta är följande:

1. [Skapa en händelsetyp](#create-event-types).
1. [Skapa och utforma meddelandemallen](#create-message-template). Du måste länka en händelse till ditt meddelande under det här steget.
1. [Testa meddelandet](#test-message-template).
1. [Publish meddelandemallen](#publish-message-template).

När du har utformat och publicerat transaktionsmeddelandemallen skickas relevanta data till Campaign via metoderna PushEvent och PushEvents [SOAP ](../send/event-description.md) om en motsvarande händelse aktiveras, och leveransen skickas till målmottagarna.

## Skapa händelsetyper {#create-event-types}

För att vara säker på att varje händelse kan ändras till ett anpassat meddelande måste du först skapa **händelsetyper**.

När [skapar en meddelandemall](#create-message-template) väljer du den typ av händelse som matchar meddelandet som du vill skicka.

>[!CAUTION]
>
>Du måste skapa händelsetyper innan du kan använda dem i meddelandemallar.

Följ stegen nedan för att skapa händelsetyper som ska bearbetas av Adobe Campaign:

1. Bläddra till mappen **[!UICONTROL Administration > Platform > Enumerations]** i Campaign Explorer.
1. Välj uppräkningen **[!UICONTROL Event type]** i listan.
1. Klicka på **[!UICONTROL Add]** om du vill skapa ett uppräkningsvärde. Detta kan vara en orderbekräftelse, lösenordsändring, orderleveransändring osv.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!CAUTION]
   >
   >Varje händelsetyp måste matcha ett värde i uppräkningen **[!UICONTROL Event type]**.

1. När de specificerade listvärdena har skapats loggar du ut och tillbaka till instansen för att det ska gå att skapa.

>[!NOTE]
>
>Läs mer om uppräkningar på [den här sidan](../../v8/config/ui-settings.md#enumerations).


## Definiera en mall för transaktionsmeddelanden {#create-message-template}

Varje händelse kan utlösa ett personligt meddelande. För att detta ska ske måste du skapa en meddelandemall som matchar varje händelsetyp. Mallar innehåller den information som behövs för att anpassa transaktionsmeddelandet. Du kan också använda mallar för att testa förhandsvisningen av meddelanden och skicka korrektur med dirigerade adresser innan du levererar till det slutliga målet.

### Skapa mallen

Följ stegen nedan för att skapa en meddelandemall:

1. Gå till mappen **[!UICONTROL Message Center >Transactional message templates]** i Adobe Campaign-trädet.
1. Högerklicka och välj **[!UICONTROL New]** i listrutan i listan över transaktionsmeddelandemallar eller klicka på knappen **[!UICONTROL New]** ovanför listan med transaktionsmeddelandemallar.

   ![](assets/messagecenter_create_model_001.png)

1. I leveransfönstret väljer du den leveransmall som passar den kanal du vill använda.

   ![](assets/messagecenter_create_model_002.png)

1. Ändra vid behov etiketten.
1. Välj den typ av händelse som matchar meddelandet som du vill skicka. Händelsetyper som ska bearbetas av Adobe Campaign måste skapas i förväg. [Läs mer](#create-event-types)

   ![](assets/messagecenter_create_model_003.png)

   >[!CAUTION]
   >
   >En händelsetyp får aldrig länkas till mer än en mall.

1. Ange en natur och en beskrivning och klicka sedan på **[!UICONTROL Continue]** för att skapa meddelandetexten.

### Skapa innehållet{#create-message-content}

Definitionen av transaktionens meddelandeinnehåll är densamma som för alla leveranser i Adobe Campaign. För e-postleveranser kan du till exempel skapa innehåll i HTML eller textformat, lägga till bilagor eller anpassa leveransobjektet. [Läs mer](../start/create-message.md).

>[!CAUTION]
>
>Bilderna i meddelandet måste vara tillgängliga för alla. Adobe Campaign har ingen mekanism för överföring av bilder för transaktionsmeddelanden.\
>Till skillnad från i JSSP och webApp har `<%=` ingen standardflytning.
>
>Du måste undvika alla data som kommer från händelsen på rätt sätt. Den här inställningen beror på hur det här fältet används. Använd till exempel encodeURIComponent i en URL. Om du vill visas i HTML kan du använda escapeXMLString.

När du har definierat meddelandeinnehållet kan du integrera händelseinformation i meddelandetexten och anpassa den. Händelseinformation infogas i texten tack vare personaliseringstaggar.

![](assets/messagecenter_create_content.png)

* Alla anpassningsfält kommer från nyttolasten.
* Det går att referera till ett eller flera personaliseringsblock i ett transaktionsmeddelande. <!--The block content will be added to the delivery content during the publication to the execution instance.-->

Gör så här om du vill infoga personaliseringstaggar i brödtexten i ett e-postmeddelande:

1. Klicka på fliken som matchar e-postformatet (HTML eller text) i meddelandemallen.
1. Ange meddelandets brödtext.
1. Infoga taggen med **[!UICONTROL Real time events>Event XML]**-menyerna i texten.

   ![](assets/messagecenter_create_custo_1.png)

1. Fyll i taggen med följande syntax: **elementnamn**.@**attributnamn** enligt nedan.

   ![](assets/messagecenter_create_custo_2.png)

## Testa mallen för transaktionsmeddelanden {#test-message-template}

### Lägg till dirigerade adresser{#add-seeds}

Med en dirigerad adress kan du visa en förhandsgranskning av meddelandet, skicka ett korrektur och testa meddelandets personalisering innan du skickar meddelandet. Seed-adresserna är kopplade till leveransen och kan inte användas för andra leveranser.

1. Klicka på fliken **[!UICONTROL Seed addresses]** i mallen för transaktionsmeddelanden och klicka sedan på knappen **[!UICONTROL Add]**.

   ![](assets/messagecenter_create_seed_1.png)

1. Tilldela den en etikett som du enkelt kan välja senare och ange startadressen (e-post eller mobiltelefon beroende på kommunikationskanalen).

1. Ange den externa identifieraren: I det här valfria fältet kan du ange en affärsnyckel (unikt ID, namn + e-post osv.) som är gemensamma för alla program på webbplatsen och som används för att identifiera dina profiler. Om det här fältet också finns i Adobe Campaign marknadsföringsdatabas kan du sedan koppla en händelse till en profil i databasen.

   ![](assets/messagecenter_create_seed_2.png)

1. Infoga testdata. Se [det här avsnittet](#personalization-data).

   ![](assets/messagecenter_create_custo_3.png)

1. Klicka på **[!UICONTROL Ok]** för att bekräfta att startadressen har skapats.

1. Upprepa processen för att skapa så många adresser du behöver.

   ![](assets/messagecenter_create_seed_6.png)

När adresserna har skapats har du tillgång till deras förhandsgranskning och personalisering.

<!--

### Add personalization data{#personalization-data}

You can add data in the message template to test transactional message personalization. This will allow you to generate a preview or send a proof. If you install the **Deliverability** module, this data allows you to display a rendering of the messages for various desktop, web or mobile clients.

The purpose of this data is to test your messages before their final delivery. These messages do not coincide with actual data to be processed by Message Center.

However, the XML structure must be identical to that of the event stored in the execution instance, as shown below. 

![](assets/messagecenter_create_custo_4.png)

This information enables you to personalize message content using personalization tags.

1. In the message template, click the **[!UICONTROL Seed addresses]** tab.
1. In the event content, enter the test information in XML format.

   ![](assets/messagecenter_create_custo_3.png)
-->

### Förhandsgranska ditt transaktionsmeddelande{#transactional-message-preview}

När du har skapat en eller flera dirigerade adresser och meddelandetexten kan du förhandsgranska meddelandet och kontrollera dess personalisering.

1. Klicka på fliken **[!UICONTROL Preview]** i meddelandemallen och välj sedan **[!UICONTROL A seed address]** i listrutan.

   ![](assets/messagecenter_preview_1.png)

1. Välj den startadress som skapades tidigare för att visa det anpassade meddelandet.

   ![](assets/messagecenter_create_seed_7.png)

### Skicka en korrektur

Du kan testa meddelandeleveransen genom att skicka ett korrektur till en startadress som skapats tidigare.

När du skickar ett korrektur utförs samma process som för alla leveranser. Läs mer om korrektur i [det här avsnittet](../send/preview-and-proof.md).

Om du vill skicka ett bevis på ett transaktionsmeddelande måste du utföra följande åtgärder:

* Skapa en eller flera [dirigerade adresser](#add-seeds) med personaliseringstestdata
* Skapa meddelandeinnehållet

Skicka korrekturet:

1. Klicka på knappen **[!UICONTROL Send a proof]** i leveransfönstret.
1. Analysera leveransen.
1. Åtgärda eventuella fel och bekräfta leveransen.

   ![](assets/messagecenter_send_proof_001.png)

1. Kontrollera att meddelandet levererades till startadressen och att innehållet överensstämmer med din konfiguration.

   ![](assets/messagecenter_send_proof_002.png)

Du kan komma åt korrektur i varje mall via fliken **[!UICONTROL Audit]**.

![](assets/messagecenter_send_proof_003.png)

## Publish the template {#publish-message-template}

När meddelandemallen <!-- on the control instance--> har skapats kan du publicera den, så att du kan skicka meddelanden som är länkade till realtids- och grupphändelser.

<!--This process will also publish it on all execution instances.

NOTE: When publishing transactional message templates, typology rules are also automatically published on the execution instances.

Publication lets you automatically create two message templates on the execution instances, which will allow you to send messages linked to real-time and batch events.-->

>[!CAUTION]
>
>När du gör några ändringar i en mall måste du publicera den igen för att ändringarna ska gälla vid leverans av transaktionsmeddelanden.

1. Gå till mappen **[!UICONTROL Message Center > Transactional message templates]** i trädet.
1. Välj den mall som du vill publicera <!--on your execution instances-->.
1. Klicka på **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_template.png)

När publikationen är klar skapas båda meddelandemallarna som ska användas för batch- och realtidshändelser i mappen **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model.png)

När en mall har publicerats, om motsvarande händelse aktiveras, kommer Adobe Campaign<!--execution instance--> att ta emot händelsen, länka den till transaktionsmallen och skicka motsvarande transaktionsmeddelande till varje mottagare.

<!--
>[!NOTE]
>
>If you replace an existing field of the transactional message template, such as the sender address, with an empty value, the corresponding field on the execution instance(s) will not be updated once the transactional message is published again. It will still contain the previous value.
>
>However, if you add a non-empty value, the corresponding field will be updated as usual after the next publication.
-->

## Avpublicera en mall

När en meddelandemall har publicerats <!--on the execution instances--> kan den avpubliceras.

* En publicerad mall kan fortfarande anropas om motsvarande händelse aktiveras: om du inte längre använder en meddelandemall bör du avpublicera den. Detta för att undvika att skicka ett oönskat transaktionsmeddelande av misstag.

  Du publicerade till exempel en meddelandemall som du bara använder för julkampanjer. Du kanske vill avpublicera den när julperioden är slut och publicera den igen nästa år.

* Du kan inte heller ta bort en transaktionsmeddelandemall som har statusen **[!UICONTROL Published]**. Du måste avpublicera det först.

Följ stegen nedan om du vill avpublicera en transaktionsmeddelandemall.

1. Gå till mappen **[!UICONTROL Message Center > Transactional message templates]**.
1. Välj den mall som ska avpubliceras.
1. Klicka på **[!UICONTROL Unpublish]**.
1. Klicka på **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

Mallstatusen för transaktionsmeddelandet ändras tillbaka från **[!UICONTROL Published]** till **[!UICONTROL Being edited]**.

När borttagningen är klar:

* Båda meddelandemallarna (används för batch- och realtidshändelser) tas bort <!-- from each execution instance-->.

  De visas inte längre i mappen **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]**.

* När en mall har avpublicerats kan du ta bort den <!-- from the control instance-->.

  Det gör du genom att markera den i listan och klicka på knappen **[!UICONTROL Delete]** överst till höger på skärmen.
