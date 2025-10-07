---
title: Kom igång med meddelanden
description: Kom igång med meddelanden
feature: Email, Push, SMS, Direct Mail, Cross Channel Orchestration
role: User
level: Beginner
version: Campaign v8, Campaign Classic v7
exl-id: a523e76d-776c-47d3-9c15-34241cee1092
source-git-commit: 110a2cac920ca3087f6fcb3cab8474729f6075be
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 6%

---

# Kom igång med meddelanden {#gs-ac-msg}

Med Adobe Campaign kan ni skicka flerkanalskampanjer, inklusive e-post, SMS, push-meddelanden och direktreklam, och mäta hur effektiva de är med hjälp av olika dedikerade rapporter. Dessa meddelanden är utformade och skickas genom leveranser och kan anpassas för varje mottagare.

De viktigaste funktionerna är målinriktning, definition och personalisering av meddelanden, genomförande av kommunikation och tillhörande verksamhetsrapporter.

## Användningsfall {#gs-ac-delivery}

Om du vill skicka meddelanden måste du skapa en leverans. Leveransläget beror på hur du använder det.

>[!NOTE]
>
>När du skapar en leverans måste du välja en mall. Standardmallar är tillgängliga för varje kanal. Läs mer om leveransmallar på [den här sidan](../send/create-templates.md).

1. **Enbildsmeddelanden** - Du kan skicka enbildsmeddelanden till en publik. Lär dig hur du skickar ditt första meddelande i [det här avsnittet](create-message.md).

   ![](assets/send-email.png)

1. **Meddelanden i en marknadsföringskampanj** - Du kan skicka meddelanden i samband med en [marknadsföringskampanj](campaigns.md), definiera en godkännandeprocess, skicka och spåra dem i en konsoliderad instrumentpanel. Lär dig hur i [det här avsnittet](../../automation/campaigns/marketing-campaign-deliveries.md).

   ![](assets/deliveries-in-a-campaign.png)

1. **Meddelanden i ett arbetsflöde** - Du kan skicka meddelanden via ett [arbetsflöde](../config/workflows.md) och automatisera leveranserna. Lär dig hur i [den här sidan](../../automation/workflow/delivery.md).

   ![](assets/send-in-a-wf.png)

1. **Utlösta meddelanden** - Du kan [utlösa meddelanden](../send/transactional.md) från en händelse. Transactional messaging (Message Center) är den Campaign-modul som är avsedd för hantering av utlösarmeddelanden. Steg för att konfigurera och skicka transaktionsmeddelanden beskrivs på [den här sidan](../send/transactional.md)

## Kommunikationskanaler {#gs-channel}

Adobe Campaign v8 levereras med de leveranskanaler som listas nedan. Vilka kanaler som är tillgängliga i din miljö beror på ditt kontrakt. Kontrollera licensavtalet.

* **E-postkanal**: Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen. [Läs mer](../send/email.md)

* **Mobila kanaler**: Med leveranser i mobila kanaler kan du skicka personaliserade meddelanden på mobila enheter till målpopulationen. Du kan skicka [SMS](../send/sms/sms.md)- och [LINE](../send/line/line.md)-meddelanden till mobiler.

* **Mobilappskanal**: Du kan använda Adobe Campaign för att skicka anpassade och segmenterade [push-meddelanden](../send/push.md) på iOS- och Android-mobilenheter via dedikerade appar. När konfigurations- och integrationsstegen är klara kan iOS och Android levereras med Adobe Campaign. Du kan också utforma och skicka avancerade meddelanden med bilder eller videoklipp till Android-enheter.

* **Direktpostkanal**: [Direktutskick](../send/direct-mail.md) är en offlinekanal som gör att du kan skapa, anpassa och generera en extern fil som du kan dela med direktutskick. Använd den här kanalen för att samordna online- och offlinekanaler i era kundresor.

  När du förbereder ett direktutskick genererar Adobe Campaign en fil som innehåller samtliga målprofiler och den valda kontaktinformationen (exempelvis postadress).  Du kan sedan skicka den här filen till din e-postleverantör som tar hand om själva sändningen.


* **Andra kanaler**: Adobe Campaign levereras också med en telefonleveransmall som används för att skapa externa leveranser. Om du använder den här kanalen måste du implementera dedikerade metoder för att bearbeta utdatafiler. Konfigurationsstegen är desamma som för [Direct-postkanalen](../send/direct-mail.md).

  >[!NOTE]
  >
  >Telefonkanalen är inte en inbyggd kanal. Implementeringen kräver att Adobe Consulting eller en Adobe-partner är engagerade. Kontakta Adobe för mer information.

  Leveranser av typen Annan använder en specifik teknisk mall som inte utför någon process: På så sätt kan de hantera marknadsföringsåtgärder som utförs utanför Adobe Campaign-plattformen.

  Den här kanalen har ingen specifik mekanism. Det är en allmän kanal som har ett eget alternativ för extern kontodirigering, leveransmalltyp och kampanjarbetsflödesaktivitet, precis som alla andra kommunikationskanaler som finns i Adobe Campaign. Den här kanalen är avsedd endast för beskrivande syften, till exempel för att definiera leveranser för vilka du vill hålla reda på målet för en kampanj som har utförts i ett annat verktyg än Adobe Campaign.

## Leveranssätt {#types-of-deliveries}

Det finns tre typer av leveransobjekt i Campaign:

### Enskild leverans {#single-delivery}

En **leverans** är ett fristående leveransobjekt som körs en gång. Den kan dupliceras, förberedas på nytt, men så länge den är i det slutliga tillståndet (avbryts, stoppas, slutförd) kan den inte återanvändas.

Leveranser kan skapas antingen från listan över leveranser eller i ett arbetsflöde via en [Leverans](../../automation/workflow/delivery.md) -aktivitet.

Arbetsflödena innehåller också specifika leveransaktiviteter beroende på vilken typ av kanal du vill använda. Mer information om de här aktiviteterna finns i [det här avsnittet](../../automation/workflow/cross-channel-deliveries.md).

### Återkommande leverans {#recurring-delivery}

En **återkommande leverans** är tillgänglig för ett arbetsflöde. Du kan skapa en ny leverans varje gång aktiviteten körs. På så sätt slipper du skapa en ny leverans för återkommande uppgifter. Om du till exempel kör den här typen av aktivitet en gång i månaden får du 12 leveranser efter ett år.

Återkommande leveranser skapas i arbetsflöden via aktiviteten [Återkommande leverans](../../automation/workflow/recurring-delivery.md). Ett exempel på den här aktiviteten visas i det här avsnittet: [Skapa en återkommande leverans i ett målarbetsflöde](../../automation/workflow/send-a-birthday-email.md).

### Kontinuerlig leverans {#continuous-delivery}

En **kontinuerlig leverans** är tillgänglig i ett arbetsflödes kontext. Det gör att du kan lägga till nya mottagare i en befintlig leverans, vilket innebär att du slipper skapa en ny leverans varje gång den körs.

Om en information i leveransen ändras (innehåll, namn osv.) skapas ett nytt leveransobjekt vid leveranskörningen. Om ingen information har ändrats återanvänds samma leveransobjekt och leverans- och spårningsloggarna läggs till i samma objekt.

Om du till exempel kör den här typen av aktivitet en gång i månaden får du en leverans efter ett år (förutsatt att du inte har ändrat leveransen).

Kontinuerliga leveranser skapas i arbetsflöden via [Kontinuerlig leveransaktivitet](../../automation/workflow/continuous-delivery.md).

## Personalization {#personalization}

Meddelanden från Adobe Campaign kan personaliseras på olika sätt. [Läs mer om personaliseringsfunktioner](../send/personalize.md)

Du kan:

* Infoga dynamiska personaliseringsfält. [Läs mer](../send/personalization-fields.md)
* Infoga fördefinierade personaliseringsblock. [Läs mer](../send/personalization-blocks.md)
* Skapa villkorsstyrt innehåll. [Läs mer](../send/conditions.md)


## Spårning och övervakning {#gs-tracking-logs}

Att övervaka era leveranser efter att de har skickats är ett viktigt steg för att se till att era marknadsföringskampanjer är effektiva och når ut till era kunder. Du kan övervaka efter att du har skickat en leverans samt förstå hur leveransfel och karantäner hanteras.

Lär dig hur du övervakar leveranser i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=sv-SE#sending-messages){target="_blank"}
