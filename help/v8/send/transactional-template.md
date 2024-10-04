---
title: Skapa och publicera din mall för transaktionsmeddelanden
description: Lär dig hur du skapar och publicerar din mall för transaktionsmeddelanden
feature: Transactional Messaging
role: User
level: Beginner, Intermediate
exl-id: 858c9216-c5a0-4bf9-b4b0-91e403293f73
source-git-commit: 253f3be945cbfa304fa7342c68f0c73b079e2870
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 1%

---

# Skapa och publicera din mall för transaktionsmeddelanden{#template-transactional-messages}

Varje händelse kan utlösa ett personligt meddelande. För att detta ska ske måste du skapa en meddelandemall som matchar varje händelsetyp. Mallar innehåller den information som behövs för att anpassa transaktionsmeddelandet. Du kan också använda mallar för att testa förhandsvisningen av meddelanden och skicka korrektur med dirigerade adresser innan du levererar till det slutliga målet.

## Skapa mallen{#create-message-template}

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

## Skapa innehållet{#create-message-content}

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

### Skicka en korrektur {#send-proof}

Du kan testa meddelandeleveransen genom att skicka ett korrektur till en startadress som skapats tidigare.

När du skickar ett korrektur utförs samma process som för alla leveranser.

Läs mer om korrektur i [det här avsnittet](../send/preview-and-proof.md#proofs-send).

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

#### Övergång från [!DNL Campaign Classic] v7 {#transition-from-v7}

Om du [övergår från Campaign Classic v7](../start/v7-to-v8.md) går alla leveranser via servern för mellanlagring.

När du skapar en transaktionsmall för e-postmeddelanden behöver du dock **intern e-postleverans** för att mallen ska kunna användas. Denna routning förhindrar att du skickar korrektur.

Om du vill skicka ett korrektur för din transaktionsmeddelandemall måste du därför ändra routningen från intern e-postleverans till **mellanleverantörens routningskonto**.

![](assets/messagecenter_send_proof_004.png)

När korrekturen har skickats måste du ändra routningen tillbaka till intern e-postleverans innan du publicerar transaktionsmeddelandemallen.

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
