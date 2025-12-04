---
title: Övervaka era leveranser i Campaign-gränssnittet
description: Lär dig hur du får tillgång till listan över leveranser och använder kontrollpanelen för leverans för att övervaka dina leveranser
feature: Monitoring
role: User
level: Beginner
version: Campaign v8, Campaign Classic v7
source-git-commit: c4d3a5d3cf89f2d342c661e54b5192d84ceb3a75
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 2%

---

# Övervaka era leveranser i Campaign-gränssnittet {#delivery-dashboard}

Övervakning av leveranser är nödvändigt för att säkerställa att era kampanjer är effektiva och når era kunder. Adobe Campaign ger dig verktyg för att komma åt dina leveranser och övervaka deras prestanda via leveranslistan och kontrollpanelen för leveranser.

## Åtkomst till listan över leveranser {#list-of-deliveries}

Du kan komma åt leveranser från leveranslistan via noden **[!UICONTROL Campaign Management > Deliveries]** i trädet.

![](assets/deliveries-list.png)

Som standard innehåller listan över leveranser namnen och statusvärdena för leveranser som skapas i den valda noden. Här visas även antalet meddelanden som ska skickas, bearbetas och skickas.

* Antalet **[!UICONTROL Messages to send]** motsvarar antalet mottagare som är målinriktade efter analys och före leverans.
* Antalet meddelanden i kolumnen **[!UICONTROL Success]** motsvarar antalet meddelanden som skickas av servern och som tas emot av mottagarna.
* Antalet **[!UICONTROL Processed]** meddelanden motsvarar antalet mottagna meddelanden plus antalet meddelanden med fel.

>[!NOTE]
>
>Vid stora leveranser kanske du vill uppdatera dessa värden. Det gör du genom att markera leveransen i fråga och sedan högerklicka på den. Välj **[!UICONTROL Action > Recompute delivery and tracking indicators...]** och använd sedan assistenten för att uppdatera informationen.

## Översikt över kontrollpanelen för leverans {#delivery-dashboard-overview}

Kontrollpanelen **för leverans** är viktig för att övervaka dina leveranser och eventuella problem som uppstår när meddelanden skickas.

Du kan hämta information om en leverans och redigera den om det behövs. Observera att tabbinnehållet inte längre kan ändras när leveransen har skickats.

Här är den information du kan övervaka med hjälp av flera flikar som är tillgängliga på kontrollpanelen:

* [Leveranssammanfattning](#delivery-summary)
* [Leveransrapporter](#delivery-reports)
* [Leveransloggar, spegelsidor, undantag](#delivery-logs-and-history)
* [Loggar och historik för leveransspårning](#tracking-logs)
* [Leveransåtergivning](#delivery-rendering)
* [Leveransgranskning](#delivery-audit-)

![](assets/s_ncs_user_del_details.png)

**Relaterade ämnen:**

* [Förstå leveransfel](delivery-failures.md)
* [Karantänhantering](quarantines.md)
* [Bästa praxis för leverans](../start/delivery-best-practices.md)
* [Hantera leveranser](about-deliverability.md)

## Leveranssammanfattning {#delivery-summary}

Fliken **[!UICONTROL Summary]** innehåller egenskaper för leveransen: leveransstatus, kanal som används, information om avsändaren, ämne, information om körning.

## Leveransrapporter {#delivery-reports}

Med länken **[!UICONTROL Reports]**, som du kommer åt från fliken **[!UICONTROL Summary]**, kan du titta på en uppsättning rapporter som rör leveransåtgärden: allmän leveransrapport, detaljerad rapport, leveransrapport, distribution av misslyckade meddelanden, öppningsfrekvens, klick och transaktioner osv.

Innehållet på den här fliken kan konfigureras enligt dina krav. Mer information om leveransrapporter finns i [det här avsnittet](../reporting/delivery-reports.md).

![](assets/delivery-report.png)

## Leveransloggar, historik och undantag {#delivery-logs-and-history}

Fliken **[!UICONTROL Delivery]** ger en historik över förekomster i den här leveransen. Den innehåller leveransloggarna, dvs. en lista över skickade meddelanden och deras status samt tillhörande meddelanden.

För en leverans kan du till exempel bara visa mottagare med en misslyckad leverans eller en adress i karantän. Om du vill göra det klickar du på knappen **[!UICONTROL Filters]** och väljer **[!UICONTROL By state]**. Välj sedan läget i listrutan. Olika statusvärden visas på [leveransstatussidan](delivery-statuses.md).

>[!NOTE]
>
>Listan som visar leveransloggarna kan anpassas som alla listor i Campaign. Du kan till exempel lägga till en kolumn för att veta vilken IP-adress som skickade varje e-post i en leverans. Mer information om hur du konfigurerar listvisning finns i [det här avsnittet](../config/ui-settings.md#customize-lists).

![](assets/s_ncs_user_delivery_delivery_tab.png)

Med länken **[!UICONTROL Display the mirror page for this message...]** kan du visa spegelsidan för innehållet i leveransen som valts i listan i ett nytt fönster.

Spegelsidan är bara tillgänglig för leveranser för vilka HTML-innehåll har definierats. Mer information finns i [Länka till spegelsidan](mirror-page.md).

![](assets/s_ncs_user_wizard_miror_page_link.png)

## Loggar och historik för leveransspårning {#tracking-logs}

Fliken **[!UICONTROL Tracking]** visar spårningshistoriken för den här leveransen. På den här fliken visas spårningsdata för skickade meddelanden, d.v.s. alla URL:er som spåras av Adobe Campaign. Spårningsdata uppdateras varje timme.

>[!NOTE]
>
>Om spårning inte är aktiverat för en leverans visas inte den här fliken.

Spårningskonfigurationen utförs i rätt steg i leveransassistenten. Se [Konfigurera spårade länkar](tracking.md).

**[!UICONTROL Tracking]** data tolkas i leveransrapporterna. Se [det här avsnittet](../reporting/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

## Inkorgsåtergivning {#delivery-rendering}

På fliken **[!UICONTROL Inbox rendering]** kan du förhandsgranska meddelandet i de olika sammanhang där det kan tas emot och kontrollera kompatibiliteten i de flesta datorer och program.

På så sätt kan du se till att ditt meddelande visas för mottagarna på ett optimalt sätt på en mängd olika webbklienter, webbmejl och enheter.

Mer information om återgivning av inkorgar finns på [den här sidan](inbox-rendering.md)


## Leveransgranskning {#delivery-audit-}

Fliken **[!UICONTROL Audit]** innehåller leveransloggen och alla meddelanden som rör korrektur.

Med knappen **[!UICONTROL Refresh]** kan du uppdatera data. Använd knappen **[!UICONTROL Filters]** för att definiera ett filter för data.

Med särskilda ikoner kan du identifiera fel och varningar. Se [Leveransanalys](delivery-analysis.md).

På underfliken **[!UICONTROL Proofs]** kan du visa en lista över de korrektur som har skickats.

![](assets/s_ncs_user_delivery_log_tab.png)

Du kan ändra informationen som visas i det här fönstret (och informationen på flikarna **[!UICONTROL Delivery]** och **[!UICONTROL Tracking]**) genom att markera kolumnerna som ska visas. Om du vill göra det klickar du på ikonen **[!UICONTROL Configure list]** i det nedre högra hörnet. Mer information om hur du konfigurerar listvisning finns i [det här avsnittet](../config/ui-settings.md#customize-lists).

## Synkronisering av kontrollpanel för leverans {#delivery-dashboard-synchronization}

Från kontrollpanelen för leverans vill du kontrollera de bearbetade meddelandena och leveransloggarna för att vara säker på att leveransen har skickats.

Vissa indikatorer eller status kan vara felaktiga eller inte aktuella. Lösningen kan vara:

* Om leveransstatusen är felaktig kontrollerar du att alla nödvändiga godkännanden har gjorts för den här leveransen eller att de tekniska arbetsflödena **[!UICONTROL operationMgt]** och **[!UICONTROL deliveryMgt]** körs utan fel.

* Om leveransräknaren inte matchar leveransen kan du försöka att beräkna om indikatorerna genom att högerklicka på leveransen i Adobe Campaign Explorer och välja **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** för att synkronisera om. Mer information om spårningsindikatorer finns i det här [avsnittet](../reporting/delivery-reports.md#tracking-indicators).

Du kan också spåra leveranser med olika rapporter via kontrollpanelen för leverans. Mer information om detta hittar du i det här [avsnittet](../reporting/delivery-reports.md).

>[!NOTE]
>
>Som användare av hanterade molntjänster i Campaign v8 övervakas och hanteras infrastrukturen av Adobe. Kontakta Adobe kundtjänst om du får problem med leveransindikatorer eller synkronisering av kontrollpaneler.

## Felsökning av långsamma leveranser {#troubleshooting-slow-deliveries}

Om leveransen verkar ta längre tid än vanligt efter att du klickat på knappen **[!UICONTROL Send]** bör du kontrollera följande möjliga orsaker:

### Problem med IP-adressens anseende

Vissa e-postleverantörer kan ha lagt till dina IP-adresser i en blockeringslista. Kontrollera dina leveransloggar (utsändningsloggar) på fliken **[!UICONTROL Delivery]** för att se om det finns några studsmeddelanden som tyder på anseendeproblem. Mer information om anseendehantering finns i avsnittet [Leveransövervakning](monitoring-deliverability.md).

### Leveransstorlek och komplexitet

Leveransen kan vara för stor för att kunna behandlas snabbt. Detta kan inträffa med:

Omfattande JavaScript-personalisering som kräver omfattande databehandling för varje mottagare.

Leverans som väger mer än 60 kB på grund av stort HTML-innehåll, inbäddade bilder eller omfattande personalisering.

Läs [Bästa praxis för leverans](../start/delivery-best-practices.md) om du vill veta mer om riktlinjer för innehåll och bästa praxis för personalisering. Rekommenderad maxstorlek är cirka 35 kB för optimala prestanda.

### Systemprestanda

Systemproblem kan förhindra servrar från att bearbeta leveranser på ett effektivt sätt. Om du misstänker prestandaproblem bör du kontrollera i leveransloggarna om det finns timeoutfel eller kommunikationsproblem.

>[!NOTE]
>
>Som användare av hanterade molntjänster i Campaign v8 hanteras övervakning av serverinfrastrukturen av Adobe. Om du får problem med leveransen kontaktar du Adobe kundtjänst med leveransloggarna.

