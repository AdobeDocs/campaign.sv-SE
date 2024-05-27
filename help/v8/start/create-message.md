---
title: Kom igång med meddelanden
description: Kom igång med meddelanden
feature: Email, Push, SMS, Direct Mail, Cross Channel Orchestration
role: User
level: Beginner
exl-id: 6cf8a929-637e-4e51-9160-5980ca727efb
source-git-commit: d6160d927601f66f450553a6dd6f91d74b0b1104
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 5%

---

# Kom igång med meddelanden{#gs-ac-audiences}

Med Adobe Campaign kan ni skicka flerkanalskampanjer, inklusive e-post, SMS, push-meddelanden och direktreklam, och mäta hur effektiva de är med hjälp av olika dedikerade rapporter. Dessa meddelanden är utformade och skickas genom leveranser och kan anpassas för varje mottagare.

De viktigaste funktionerna är målinriktning, definition och personalisering av meddelanden, genomförande av kommunikation och tillhörande verksamhetsrapporter. Den huvudsakliga funktionella åtkomstpunkten är leveransassistenten. Den här åtkomstpunkten leder till flera funktioner som täcks av Adobe Campaign.

Adobe Campaign v8 har följande leveranskanaler:

* **E-postkanal**: Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen. [Läs mer](#gs-channel-email)

* **Mobila kanaler**: leveranser i mobilkanaler gör att ni kan skicka personaliserade meddelanden på mobila enheter till målgruppen. [Läs mer](#gs-channel-sms)

* **Mobil programkanal**: vid leverans av mobilappar kan du skicka meddelanden till iOS- och Android-enheter. [Läs mer](#gs-channel-push)

* **Direktpostkanal**: Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen. [Läs mer](#gs-channel-direct)


  Andra kanaler beskrivs på [det här avsnittet](#other-channels).

  >[!NOTE]
  >
  >Antalet tillgängliga kanaler beror på ditt kontrakt. Kontrollera licensavtalet.

## Välj kanal{#gs-channel}

### E-postkanal {#gs-channel-email}

The [E-postkanal](../send/direct-mail.md) är en av huvudkanalerna i Adobe Campaign, som gör att ni kan schemalägga och skicka personaliserade e-postmeddelanden till specifika mål.

Du kan skicka olika typer av e-postmeddelanden:

* Skicka e-post en gång: e-postmeddelanden som du kan skicka en gång till ett definierat mål. De används vanligtvis för att marknadsföra ett visst innehåll som bara ska förberedas och skickas en gång (nyhetsbrev, e-postreklam osv.).
* Återkommande e-postmeddelanden: skicka samma e-postmeddelande regelbundet i en kampanj och samla varje sändning och dess rapporter regelbundet. Samma e-post skickas, men vanligtvis till ett annat mål, baserat på det giltiga målet för den dag då meddelandet skickas. Ett vanligt exempel är ett födelsedagsmeddelande. Mer information finns i [Återkommande leveranser](../../automation/workflow/recurring-delivery.md).
* Transaktionsbaserade e-postmeddelanden: enhetliga e-postmeddelanden som utlöses utifrån kundernas beteende. Se [Transaktionsmeddelanden](../send/transactional.md).

Läs Adobe Campaign Classic om leveransanvändning och rekommendationer [Bästa praxis för leverans](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/delivery-best-practices.html#sending-messages){target="_blank"}

Mer information om olika typer av leveranser finns i [det här avsnittet](#types-of-deliveries).

### Mobilkanal {#gs-channel-sms}

Med Adobe Campaign kan ni leverera [SMS](../send/sms.md) och [LINJE](../send/line.md) meddelanden på mobiler.

För SMS-meddelanden kan du skapa, ändra och anpassa meddelanden endast i textformat. Du kan även förhandsgranska dina SMS-meddelanden innan de skickas.

För LINE-meddelanden kan du skicka text, bilder och länkar.

För att kunna leverera SMS- eller LINE-meddelanden till en mobiltelefon behöver du:

* Ett externt konto har konfigurerats på **[!UICONTROL Mobile (SMS)]** eller på **[!UICONTROL LINE]** kanal.
* En SMS- eller LINE-leveransmall som är korrekt länkad till det här externa kontot.


### Push-meddelandekanal {#gs-channel-push}

Du kan använda Adobe Campaign för att skicka personaliserade och segmenterade [push-meddelanden](../send/push.md) på iOS och Android-mobilenheter, via dedikerade appar. När konfigurations- och integrationsstegen är klara kan iOS- och Android-leveranser skapas och skickas med Adobe Campaign. Du kan också utforma och skicka avancerade meddelanden med bilder eller videoklipp till Android-enheter.

### Direktpostkanal {#gs-channel-direct}

[Direktreklam](../send/direct-mail.md) är en offlinekanal som gör att du kan skapa, anpassa och generera en extern fil som du kan dela med direktreklamleverantörer. Använd den här kanalen för att samordna online- och offlinekanaler i era kundresor.

När du förbereder ett direktutskick genererar Adobe Campaign en fil som innehåller samtliga målprofiler och den valda kontaktinformationen (exempelvis postadress).  Du kan sedan skicka den här filen till din e-postleverantör som tar hand om själva sändningen.


### Andra kanaler {#other-channels}

Adobe Campaign har också en mall för telefonöverföring som används för att skapa externa leveranser. Om du använder den här kanalen måste du implementera dedikerade metoder för att bearbeta utdatafiler. Konfigurationsstegen är desamma som för [Direktpostkanal](../send/direct-mail.md).

>[!NOTE]
>
>Telefonkanalen är inte en inbyggd kanal. För att genomföra detta krävs att Adobe Consulting eller en Adobe Partner deltar. Kontakta din Adobe-representant om du vill ha mer information.

Leveranser av typen Annan använder en specifik teknisk mall som inte utför någon process: På så sätt kan de hantera marknadsföringsåtgärder som utförs utanför Adobe Campaign-plattformen.

Den här kanalen har ingen specifik mekanism. Det är en allmän kanal som har ett eget alternativ för extern kontodirigering, leveransmalltyp och kampanjarbetsflödesaktivitet, precis som alla andra kommunikationskanaler som finns i Adobe Campaign. Den här kanalen är avsedd endast för beskrivande syften, till exempel för att definiera leveranser för vilka du vill hålla reda på målet för en kampanj som har utförts i ett annat verktyg än Adobe Campaign.

## Välj typ av leverans {#types-of-deliveries}

Det finns tre typer av leveransobjekt i Campaign:

### Enskild leverans {#single-delivery}

A **leverans** är ett fristående leveransobjekt som körs en gång. Den kan dupliceras, förberedas på nytt, men så länge den är i det slutliga tillståndet (avbryts, stoppas, slutförd) kan den inte återanvändas.

Leveranser kan skapas antingen i listan över leveranser eller i ett arbetsflöde via en [Leverans](../../automation/workflow/delivery.md) aktivitet.

Arbetsflödena innehåller också specifika leveransaktiviteter beroende på vilken typ av kanal du vill använda. Mer information om dessa aktiviteter finns i [det här avsnittet](../../automation/workflow/cross-channel-deliveries.md).

### Återkommande leverans {#recurring-delivery}

A **återkommande leverans** är tillgängligt i samband med ett arbetsflöde. Du kan skapa en ny leverans varje gång aktiviteten körs. På så sätt slipper du skapa en ny leverans för återkommande uppgifter. Om du till exempel kör den här typen av aktivitet en gång i månaden får du 12 leveranser efter ett år.

Återkommande leveranser skapas i arbetsflöden via [Återkommande leveransaktivitet](../../automation/workflow/recurring-delivery.md). Ett exempel på den här aktiviteten visas i det här avsnittet: [Skapa en återkommande leverans i ett målarbetsflöde](../../automation/workflow/send-a-birthday-email.md).

### Kontinuerlig leverans {#continuous-delivery}

A **kontinuerlig leverans** är tillgängligt i samband med ett arbetsflöde. Det gör att du kan lägga till nya mottagare i en befintlig leverans, vilket innebär att du slipper skapa en ny leverans varje gång den körs.

Om en information i leveransen ändras (innehåll, namn osv.) skapas ett nytt leveransobjekt vid leveranskörningen. Om ingen information har ändrats återanvänds samma leveransobjekt och leverans- och spårningsloggarna läggs till i samma objekt.

Om du till exempel kör den här typen av aktivitet en gång i månaden får du en leverans efter ett år (förutsatt att du inte har ändrat leveransen).

Kontinuerliga leveranser skapas i arbetsflöden via [Kontinuerlig leveransaktivitet](../../automation/workflow/contin).


## Välj hur du vill skicka meddelanden{#gs-send-msg}

När meddelandet har skapats och dess innehåll har utformats och testats kan du välja hur du vill skicka det. Campaign erbjuder en uppsättning funktioner för att:

* Skicka meddelanden manuellt till huvudmålet

  ![](assets/send-email.png)

  Lär dig hur du skickar meddelanden i [det här avsnittet](../send/send.md)

* Skicka meddelanden som är kopplade till en [marknadsföringskampanj](campaigns.md)

  ![](assets/deliveries-in-a-campaign.png)

  Lär dig hur du skickar meddelanden i samband med en kampanj i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html){target="_blank"}

* Skicka meddelanden via en [arbetsflöde](../config/workflows.md)

  ![](assets/send-in-a-wf.png)

  Lär dig automatisera e-postleveranser i [den här sidan](../../automation/workflow/delivery.md)

* [Utlösarmeddelanden](../send/transactional.md) från en händelse

  Transactional messaging (Message Center) är den Campaign-modul som är avsedd för hantering av utlösarmeddelanden.

  Läs mer om funktioner för transaktionsmeddelanden i [det här avsnittet](../architecture/architecture.md#transac-msg-archi)

  Steg för att konfigurera och skicka transaktionsmeddelanden beskrivs i [den här sidan](../send/transactional.md)

* Schemalägg meddelanden

  ![](assets/schedule-send.png)

  Lär dig schemalägga sändning av leveranser i [den här sidan](../send/configure-and-send.md)

  Se även detta [Använd fall: läs om schemat och skicka ett födelsedagskalender via e-post](../../automation/workflow/send-a-birthday-email.md)


## Lägg till personalisering{#personalization}

Meddelanden från Adobe Campaign kan personaliseras på olika sätt. [Läs mer om personaliseringsfunktioner](../send/personalize.md)

Du kan:

* Infoga dynamiska personaliseringsfält. [Läs mer](../send/personalization-fields.md)
* Infoga fördefinierade personaliseringsblock. [Läs mer](../send/personalization-blocks.md)
* Skapa villkorsstyrt innehåll. [Läs mer](../send/conditions.md)


## Loggar för leverans och spårning{#gs-tracking-logs}

Att övervaka era leveranser efter att de har skickats är ett viktigt steg för att se till att era marknadsföringskampanjer är effektiva och når ut till era kunder. Du kan övervaka efter att du har skickat en leverans samt förstå hur leveransfel och karantäner hanteras.

Lär dig hur du övervakar leveranser i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html#sending-messages){target="_blank"}

