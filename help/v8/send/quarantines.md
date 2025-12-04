---
title: Karantänhantering i Campaign
description: Förstå karantänhantering i Adobe Campaign
feature: Profiles, Monitoring
role: User, Developer
level: Beginner
version: Campaign v8, Campaign Classic v7
exl-id: 220b7a88-bd42-494b-b55b-b827b4971c9e
source-git-commit: c4d3a5d3cf89f2d342c661e54b5192d84ceb3a75
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 4%

---

# Karantän {#quarantine-management}

Adobe Campaign hanterar en lista med adresser i karantän för onlinekanaler (e-post, SMS, push-meddelanden). Vissa leverantörer av internetåtkomst betraktar automatiskt e-post som skräppost om frekvensen av ogiltiga adresser är för hög. Med karantän kan du därför undvika att läggas till i blockeringslista av dessa leverantörer. Dessutom bidrar karantäner till att minska SMS-kostnaderna genom att utesluta felaktiga telefonnummer från leveranser.

När deras adress eller telefonnummer sätts i karantän utesluts mottagarna från målet under leveransanalysen: du kommer inte att kunna skicka marknadsföringsmeddelanden, inklusive automatiska arbetsflödesmeddelanden, till dessa kontakter. Om dessa adresser i karantän också finns med i listor, kommer de att uteslutas när de skickas till dessa listor. En e-postadress kan sättas i karantän, till exempel när postlådan är full, om adressen inte finns eller om e-postservern inte är tillgänglig.

<!--For more on best practices to secure and optimize your deliveries, refer to [this page](delivery-best-practices.md).-->

## Karantän mot blockeringslista

**Karantän** gäller bara för en **adress**, ett **telefonnummer** eller en **enhetstoken**, men inte för själva profilen. En profil vars e-postadress är placerad i karantän kan till exempel uppdatera sin profil och ange en ny adress. Därefter kan den användas av leveransåtgärder igen. Om två profiler råkar ha samma telefonnummer, påverkas båda om numret sätts i karantän. Adresserna eller telefonnumren i karantän visas i [exkluderingsloggarna](#delivery-quarantines) (för en leverans) eller i [karantänlistan](#non-deliverable-bounces) (för hela plattformen).

>[!NOTE]
>
>När mottagare rapporterar ditt meddelande som skräppost eller svarar på ett SMS-meddelande med ett nyckelord som &quot;STOP&quot;, sätts deras adress eller telefonnummer i karantän som **[!UICONTROL Denylisted]**. Deras profil uppdateras därefter.

Å andra sidan kan **profiler** finnas på **blockeringslista** som efter en avanmälan (avanmälan) för en viss kanal: det innebär att de inte längre används som mål för någon leverans. Om en profil på blockeringslista för e-postkanalen har två e-postadresser, kommer därför båda adresserna att exkluderas från leveransen. Du kan kontrollera om det finns en profil på blockeringslista för en eller flera kanaler under **[!UICONTROL No longer contact]** på fliken **[!UICONTROL General]** i profilen. [Läs mer](../audiences/view-profiles.md)

>[!NOTE]
>
>Mottagare som avbeställt prenumerationen via metoden [&quot;mailto&quot; List-Unsubscribe ](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations#mailto-list-unsubscribe){target="_blank"} skickas inte till karantän. De har antingen avbeställt den [tjänst](../start/subscriptions.md) som är kopplad till leveransen eller skickats till blockeringslista (visas i profilens **[!UICONTROL No longer contact]** -avsnitt) om ingen tjänst har definierats för leveransen.

<!--For the mobile app channel, device tokens are quarantined.-->

## Varför skickas ett e-postmeddelande, en telefon eller en enhet till karantän {#quarantine-reason}

Adobe Campaign hanterar karantän beroende på typ av leveransfel och orsaken till detta. Dessa tilldelas vid kvalificering av felmeddelanden. Läs mer om hantering av leveransfel [på den här sidan](delivery-failures.md).

Två typer eller fel kan fångas:

* **Hårt fel**: E-postadressen, telefonnumret eller enheten skickas omedelbart till karantänen.
* **Mjukt fel**: mjuka fel ökar en felräknare och kan sätta ett e-postmeddelande, telefonnummer eller enhetstoken i karantän. Kampanjen utför [återförsök](delivery-failures.md#retries): När felräknaren når gränsvärdet sätts adressen, telefonnumret eller enhetstoken i karantän. [Läs mer](delivery-failures.md#retries).

I listan över adresser i karantän anger fältet **[!UICONTROL Error reason]** varför den valda adressen placerades i karantän. [Läs mer](#non-deliverable-bounces).


Om en användare kvalificerar ett e-postmeddelande som skräppost omdirigeras meddelandet automatiskt till en teknisk postlåda som hanteras av Adobe. Användarens e-postadress skickas sedan automatiskt till karantänen med status **[!UICONTROL Denylisted]**.    Den här statusen avser endast adressen, profilen finns inte på blockeringslista, så att användaren fortsätter att ta emot SMS-meddelanden och push-meddelanden. Läs mer om feedbackslingor i [Handboken ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops){target="_blank"} om bästa leveransmetoder.

>[!NOTE]
>
>Karantänen i Adobe Campaign är skiftlägeskänslig.    Se till att importera e-postadresser med små bokstäver så att inte e-postadresserna fortsätter att ta emot meddelanden.

## Mjuk felhantering {#soft-error-management}

I motsats till hårda fel skickar inte mjuka fel en adress till karantän omedelbart, utan i stället ökar de en felräknare. När felräknaren når gränsvärdet sätts adressen i karantän. Läs mer om återförsök och feltyper i [Om leveransfel](delivery-failures.md).

Felräknaren initieras om om det senaste allvarliga felet inträffade för mer än 10 dagar sedan. Adressstatusen ändras sedan till **[!UICONTROL Valid]** och tas bort från listan över karantän i arbetsflödet **[!UICONTROL Database cleanup]**. [Läs mer om tekniska arbetsflöden](../config/workflows.md#technical-workflows).

## Åtkomst till adresser i karantän {#access-quarantined-addresses}

Adresser i karantän kan visas för en viss leverans eller för hela plattformen.

### Karantän för leverans{#delivery-quarantines}

Karantänadresser listas under leveransförberedelsefasen i leveransloggarna på kontrollpanelen för leverans.

För varje leverans kan du även kontrollera rapporten **[!UICONTROL Delivery summary]**: den visar antalet adresser i karantän i leveransmålet och visar:

* Antalet adresser som placerats i karantän under leveransanalysen.
* Antalet adresser som placerats i karantän efter leveransåtgärden.

Läs mer om leveransrapporter i [det här avsnittet](../reporting/gs-reporting.md).

### Ej levererbara och studsadresser{#non-deliverable-bounces}

Om du vill visa listan över adresser i karantän **för hela plattformen** kan kampanjadministratörer bläddra till **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**. I det här avsnittet visas element i karantän för kanalerna **email**, **SMS** och **Push notification**.

![](assets/tech-quarantine.png)

>[!NOTE]
>
>Antalet karantän ökar med tiden. Om en e-postadress till exempel anses ha en livslängd på tre år och mottagartabellen ökar med 50 % varje år, kan ökningen av antalet karantän beräknas enligt följande:
>
>Slut på år 1: (1&#42;0.33)/(1+0.5)=22 %.
>
>Slut på år 2: ((1.22&#42;0.33)+0.33)/(1.5+0.75)=32,5 %.

Dessutom visar den inbyggda rapporten **[!UICONTROL Non-deliverables and bounces]**, som är tillgänglig från avsnittet **Reports** på den här startsidan, information om adresserna i karantän, de typer av fel som påträffats och en felfördelning per domän. Du kan filtrera data för en viss leverans eller anpassa rapporten efter behov.

Läs mer om studsadresser i [Bästa praxis-handboken för slutprodukter](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html){target="_blank"}.

### E-postadress i karantän {#quarantined-recipient}

Du kan slå upp status för e-postadressen för alla mottagare.

Det gör du genom att markera mottagarprofilen och klicka på fliken **[!UICONTROL Deliveries]**. För alla leveranser till den mottagaren kan du ta reda på om adressen misslyckades, placerades i karantän under analysen osv.

För varje mapp kan du bara visa mottagare vars e-postadress är i karantän, med det inbyggda **[!UICONTROL Quarantined email address]**-filtret, enligt nedan:

![](assets/quarantine-filter.png)


## Ta bort en adress i karantän {#remove-a-quarantined-address}

### Automatiska uppdateringar {#unquarantine-auto}

Adresser som matchar specifika villkor tas automatiskt bort från karantänlistan av det inbyggda arbetsflödet **[!UICONTROL Database cleanup]**.

Adresserna tas automatiskt bort från karantänlistan i följande fall:

* Adresser med statusen **[!UICONTROL With errors]** tas bort från karantänlistan efter en slutförd leverans.
* Adresser med statusen **[!UICONTROL With errors]** tas bort från karantänlistan om den senaste mjuka studsen inträffade för mer än 10 dagar sedan. Mer information om mjuk felhantering finns i [det här avsnittet](#soft-error-management).
* Adresser i en **[!UICONTROL With errors]**-status som studsade med felet **[!UICONTROL Mailbox full]** tas bort från karantänlistan efter 30 dagar.

Deras status ändras sedan till **[!UICONTROL Valid]**.

>[!CAUTION]
>
>Mottagare med en adress i en **[!UICONTROL Quarantine]**- eller **[!UICONTROL Denylisted]**-status tas aldrig bort, även om de får ett e-postmeddelande.

### Manuella uppdateringar {#unquarantine-manual}

Du kan också ta bort en adress manuellt från karantänlistan. Om du vill ta bort en adress från karantänen manuellt kan du ändra dess status till **[!UICONTROL Valid]** från noden **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

![](assets/tech-quarantine-status.png)

### Massuppdateringar {#unquarantine-bulk}

Du kan behöva göra satsvisa uppdateringar i karantänlistan i särskilda situationer, t.ex. vid ett avbrott i en Internet-leverantör där e-postmeddelanden felaktigt markeras som studsar eftersom de inte kan levereras till mottagaren.

Så här utför du en gruppuppdatering:

1. Skapa ett arbetsflöde och lägg till en fråga i karantäntabellen (**[!UICONTROL nms:address]**) för att filtrera påverkade mottagare
2. Använd frågevillkor för att identifiera adresser som inte ska sättas i karantän, till exempel:
   * **E-postdomänen (@domain)** är lika med den eller de berörda ISP-domänerna
   * **Uppdatera status (@lastModified)** inom tidsramen för ett avbrott
   * **Status (@status)** är lika med karantänstatus
3. Lägg till en **[!UICONTROL Update data]**-aktivitet för att ange adressstatusen till **[!UICONTROL Valid]**

Adresserna tas sedan automatiskt bort från karantänlistan av arbetsflödet **[!UICONTROL Database cleanup]** och kan inkluderas i framtida leveranser.

## Relaterade ämnen

* [Förstå leveransfel](delivery-failures.md) - Lär dig mer om olika typer av leveransfel och hur Campaign hanterar studsar
* [Övervaka leveranser](delivery-dashboard.md) - Få åtkomst till leveransloggar och övervaka leveransresultat
* [Bästa praxis för leverans](../start/delivery-best-practices.md) - Bästa metoder för att behålla god levererbarhet och undvika karantän

