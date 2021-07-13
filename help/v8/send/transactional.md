---
product: Adobe Campaign
title: Kampanjtransaktionsmeddelanden
description: Kom igång med Transactional Messaging
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: c61d8aa8e0a68ccc81a6141782f860daf061bc61
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 1%

---

# Kom igång med Transactional Messaging{#send-transactional-messages}

Transactional Messaging (Message Center) är en Campaign-modul som är utformad för att hantera utlösarmeddelanden. Dessa meddelanden genereras från händelser som utlöses från informationssystem och kan vara: Faktura, orderbekräftelse, leveransbekräftelse, lösenordsändring, meddelande om att produkten inte är tillgänglig, kontoutdrag eller skapande av webbkonto till exempel.

? Som användare av hanterade Cloud Services ska du [kontakta Adobe](../start/campaign-faq.md#support) för att installera och konfigurera Campaign Transactional Messaging i din miljö.

Transaktionsmeddelanden används för att skicka:

* meddelanden, till exempel orderbekräftelser eller lösenordsåterställningar
* ett individuellt svar i realtid på en kunds handling
* icke-marknadsföringsmaterial

? Inställningar för transaktionsmeddelanden beskrivs i [det här avsnittet](../config/transactional-msg-settings.md).

? Förstå arkitekturen för transaktionsmeddelanden i [den här sidan](../dev/architecture.md).

>[!CAUTION]
>
>Transactional messaging kräver en specifik licens. Kontrollera licensavtalet.

## Definiera mallar för transaktionsmeddelanden

Varje händelse kan utlösa ett personligt meddelande. För att detta ska ske måste du skapa en meddelandemall som matchar varje händelsetyp. Mallar innehåller den information som behövs för att anpassa transaktionsmeddelandet. Du kan också använda mallar för att testa förhandsvisningen av meddelanden och skicka korrektur med dirigerade adresser innan du levererar till det slutliga målet.

### Skapa mallen

Följ stegen nedan för att skapa en meddelandemall:

1. Gå till mappen **[!UICONTROL Message Center >Transactional message templates]** i Adobe Campaign-trädet.
1. Högerklicka och välj **[!UICONTROL New]** i listrutan i listan över transaktionsmeddelandemallar eller klicka på knappen **[!UICONTROL New]** ovanför listan med transaktionsmeddelandemallar.

   ![](assets/messagecenter_create_model_001.png)

1. I leveransfönstret väljer du den leveransmall som passar den kanal du vill använda.

   ![](assets/messagecenter_create_model_002.png)

1. Ändra vid behov etiketten.
1. Välj den typ av händelse som matchar meddelandet som du vill skicka.

   ![](assets/messagecenter_create_model_003.png)

   Händelsetyper som ska bearbetas av Adobe Campaign måste skapas på kontrollinstansen av Adobe.

   >[!NOTE]
   >
   >En händelsetyp får aldrig länkas till mer än en mall.

1. Ange en typ och en beskrivning och klicka sedan på **[!UICONTROL Continue]** för att skapa meddelandetexten. Se [Skapa meddelandeinnehållet](#create-message-content).

### Skapa innehållet{#create-message-content}

Definitionen av transaktionens meddelandeinnehåll är densamma som för alla leveranser i Adobe Campaign. För e-postleveranser kan du till exempel skapa innehåll i HTML- eller textformat, lägga till bilagor eller anpassa leveransobjektet. Mer information om detta finns i [det här avsnittet](../start/create-message.md).

>[!CAUTION]
>
>Bilderna i meddelandet måste vara tillgängliga för alla. Adobe Campaign har ingen mekanism för överföring av bilder för transaktionsmeddelanden.\
>Till skillnad från i JSSP och webApp har `<%=` ingen standardflytning.
>
>Du måste undvika alla data som kommer från händelsen på rätt sätt. Detta beror på hur det här fältet används. Använd till exempel encodeURIComponent i en URL. Om du vill visas i HTML-koden kan du använda escapeXMLString.

När du har definierat meddelandeinnehållet kan du integrera händelseinformation i meddelandetexten och anpassa den. Händelseinformation infogas i texten tack vare personaliseringstaggar.

![](assets/messagecenter_create_content.png)

* Alla anpassningsfält kommer från nyttolasten.
* Det går att referera till ett eller flera personaliseringsblock i ett transaktionsmeddelande. Blockinnehållet läggs till i leveransinnehållet under publiceringen i körningsinstansen.

Gör så här om du vill infoga personaliseringstaggar i brödtexten i ett e-postmeddelande:

1. Klicka på fliken som matchar e-postformatet (HTML eller text) i meddelandemallen.
1. Ange meddelandets brödtext.
1. Infoga taggen med hjälp av menyerna **[!UICONTROL Real time events>Event XML]** i texten.

   ![](assets/messagecenter_create_custo_1.png)

1. Fyll i taggen med följande syntax: **elementnamn**.@**attributnamn** enligt nedan.

   ![](assets/messagecenter_create_custo_2.png)

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

### Lägg till personaliseringsdata{#personalization-data}

Du kan lägga till data i meddelandemallen för att testa anpassning av transaktionsmeddelanden. Då kan du generera en förhandsgranskning eller skicka ett korrektur. Om du installerar modulen **Deliverability** kan du med den här informationen visa en återgivning av meddelandena för olika dator-, webb- eller mobilklienter.

Syftet med dessa data är att testa dina meddelanden innan de levereras. Dessa meddelanden sammanfaller inte med faktiska data som ska bearbetas av meddelandecentret. XML-strukturen måste dock vara identisk med den för händelsen som lagras i körningsinstansen, vilket visas nedan.

![](assets/messagecenter_create_custo_4.png)

Med den här informationen kan du anpassa meddelandeinnehåll med personaliseringstaggar.

1. Klicka på fliken **[!UICONTROL Seed addresses]** i meddelandemallen.
1. I händelseinnehållet anger du testinformationen i XML-format.

   ![](assets/messagecenter_create_custo_3.png)

### Förhandsgranska ditt transaktionsmeddelande{#transactional-message-preview}

När du har skapat en eller flera dirigerade adresser och meddelandetexten kan du förhandsgranska meddelandet och kontrollera dess personalisering.

1. Klicka på fliken **[!UICONTROL Preview]** i meddelandemallen och välj **[!UICONTROL A seed address]** i listrutan.

   ![](assets/messagecenter_preview_1.png)

1. Välj den startadress som skapades tidigare för att visa det anpassade meddelandet.

   ![](assets/messagecenter_create_seed_7.png)

### Skicka ett bevis

Du kan testa meddelandeleveransen genom att skicka ett korrektur till en startadress som skapats tidigare.

När du skickar ett korrektur utförs samma process som för alla leveranser.

↗️ Läs mer om korrektur i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-validating-the-delivery.html){target=&quot;_blank&quot;}

Om du vill skicka ett bevis på ett transaktionsmeddelande måste du utföra följande åtgärder:

* Skapa en eller flera [dirigeringsadresser](#add-seeds) med testdata för personalisering
* Skapa meddelandeinnehållet

Så här skickar du korrekturet:

1. Klicka på knappen **[!UICONTROL Send a proof]** i leveransfönstret.
1. Analysera leveransen.
1. Åtgärda eventuella fel och bekräfta leveransen.

   ![](assets/messagecenter_send_proof_001.png)

1. Kontrollera att meddelandet levererades till startadressen och att innehållet överensstämmer med din konfiguration.

   ![](assets/messagecenter_send_proof_002.png)

Du kan komma åt korrektur i varje mall via fliken **[!UICONTROL Audit]**.

![](assets/messagecenter_send_proof_003.png)

### Publicera mallen

När meddelandemallen som skapats för kontrollinstansen är klar kan du publicera den. Den här processen kommer även att publicera den på alla körningsinstanser.

>[!NOTE]
>
>När du publicerar transaktionsmeddelandemallar publiceras också typologiregler automatiskt på körningsinstanserna.

Med Publication kan du automatiskt skapa två meddelandemallar för körningsinstanserna, som gör att du kan skicka meddelanden som är länkade till realtids- och grupphändelser.

>[!CAUTION]
>
>När du gör några ändringar i en mall måste du publicera den igen för att ändringarna ska gälla vid leverans av transaktionsmeddelanden.

1. Gå till mappen **[!UICONTROL Message Center > Transactional message templates]** i trädet i kontrollinstansen.
1. Välj den mall som du vill publicera i dina körningsinstanser.
1. Klicka på **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_template.png)

När publiceringen är klar skapas båda meddelandemallarna som ska användas för batch- och realtidshändelser i trädet för produktionsinstansen i mappen **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model.png)

När en mall har publicerats, om motsvarande händelse aktiveras, kommer körningsinstansen att ta emot händelsen, länka den till transaktionsmallen och skicka motsvarande transaktionsmeddelande till varje mottagare.

>[!NOTE]
>
>Om du ersätter ett befintligt fält i transaktionsmeddelandemallen, t.ex. avsändaradressen, med ett tomt värde, kommer motsvarande fält i körningsinstansen/instanserna inte att uppdateras när transaktionsmeddelandet publiceras igen. Det innehåller fortfarande det föregående värdet.
>
>Om du lägger till ett värde som inte är tomt uppdateras motsvarande fält som vanligt efter nästa publicering.


### Avpublicera en mall

När en meddelandemall har publicerats på körningsinstanserna kan den avpubliceras.

* En publicerad mall kan fortfarande anropas om motsvarande händelse aktiveras: Om du inte längre använder en meddelandemall bör du avpublicera den. Detta för att undvika att skicka ett oönskat transaktionsmeddelande av misstag.

   Du publicerade till exempel en meddelandemall som du bara använder för julkampanjer. Du kanske vill avpublicera den när julperioden är slut och publicera den igen nästa år.

* Du kan inte heller ta bort en transaktionsmeddelandemall som har statusen **[!UICONTROL Published]**. Du måste avpublicera det först.

Följ stegen nedan om du vill avpublicera en transaktionsmeddelandemall.

1. I kontrollinstansen bläddrar du till mappen **[!UICONTROL Message Center > Transactional message templates]**.
1. Välj den mall som ska avpubliceras.
1. Klicka på **[!UICONTROL Unpublish]**.
1. Klicka på **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

Status för transaktionsmeddelandemallen ändras tillbaka från **[!UICONTROL Published]** till **[!UICONTROL Being edited]**.

När borttagningen är klar:

* Båda meddelandemallarna (som används för batch- och realtidshändelser) tas bort från varje körningsinstans.

   De visas inte längre i mappen **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]**.

* När en mall har avpublicerats kan du ta bort den från kontrollinstansen.

   Det gör du genom att markera den i listan och klicka på knappen **[!UICONTROL Delete]** längst upp till höger på skärmen.
