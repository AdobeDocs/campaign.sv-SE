---
title: Kom igång med meddelandespårning
description: Läs mer om spårningsfunktioner i Adobe Campaign
feature: Monitoring, Email
role: User
level: Beginner
exl-id: f3de901f-519f-42ae-846c-f20c7cb560df
source-git-commit: 90ed82673b893b62a185227dd8cdfe80cc8f1455
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 3%

---

# Kom igång med meddelandespårning {#get-started-tracking}

Tack vare spårningsfunktionerna i Adobe Campaign kan du spåra skickade meddelanden och kontrollera mottagarnas beteende: öppna, klicka på länkar, ta bort prenumeration med mera.

Den här informationen hämtas på fliken **[!UICONTROL Tracking]** i profilen för varje mottagare av leveransen. På den här fliken visas alla URL-länkar som spårats och klickats av mottagaren som valts i listan. Detta är en ackumulering av alla URL:er som spåras i leveranser som fortfarande finns på leveransskärmen. Listan kan konfigureras och innehåller vanligtvis: den URL-adress som klickades på, datum och tid för klickningen samt det dokument där URL-adressen hittades.

Kontrollpanelen **för leverans** är också ett nyckelverktyg för att övervaka dina leveranser och potentiella problem när meddelanden skickas.

I följande diagram visas de olika stegen i dialogen mellan användaren och de olika servrarna.

<img src="assets/tracking-diagram.png" width="70%">

>[!NOTE]
>
>Spårningskonfigurationen utförs av Adobe för distributioner av hanterade molntjänster.

## Meddelandespårning {#message-tracking}

**Spårade länkar**

Du kan spåra mottagning av meddelanden och aktivering av länkar som infogats i meddelandeinnehållet för att bättre förstå mottagarnas beteende.

[Läs mer om spårade länkar](tracked-links.md)

**URL-spårning**

Spårningsalternativen kan konfigureras genom att aktivera eller inaktivera spårade URL:er.

[Läs mer om alternativ för URL-spårning](url-tracking.md)

**Spårad länkpersonalisering**

Kampanjspårningsfunktionerna gör att ni kan lägga till länkar i e-postmeddelanden som kan personaliseras och som stöder spårning.

[Läs mer om personaliserad länkspårning](personalized-links.md)

**Spårningsloggar**

Det tekniska arbetsflödet **Spårning** hämtar spårningsdata när leveransen har skickats och spårningen har aktiverats. Dessa data finns på fliken Spårning för leveransen.

[Läs mer om spårningsloggar](tracking-logs.md)

**Testa spårning**

Innan du skickar meddelanden med din spårning kan du testa spårningen på din spegelsida, e-postloggar och länkar.

[Läs mer om testning av spårning](testing-tracking.md)

## Spåra rapporter {#tracking-reports}

**Spårningsstatistik**

Den här rapporten innehåller statistik om öppningar, klick och transaktioner och gör att du kan spåra marknadsföringseffekten av leveransen.

[Läs mer om att spåra rapporter](../reporting/delivery-reports.md#tracking-indicators)

**URL:er och klickbara strömmar**

Den här rapporten innehåller en lista över besökta sidor efter en leverans.

[Läs mer om URL:er och klicka på strömmar](../reporting/delivery-reports.md#urls-and-click-streams)

**Person/personer och mottagare**

I det här exemplet är det lättare att förstå skillnaden mellan en person/en person och en mottagare i Adobe Campaign.

Läs mer om personer/personer och mottagare i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/person-people-recipients.html#reporting){target="_blank"}

**Spårningsindikatorer**

I den här rapporten kombineras nyckelindikatorer för att spåra mottagarnas beteende när de får leveransen, till exempel öppnings- och klickfrekvens och klickströmmar.

[Läs mer om spårningsindikatorer](../reporting/delivery-reports.md#tracking-indicators)

**Indikatorberäkning**

De olika tabellerna ger dig en lista över indikatorer som används i de olika rapporterna och deras beräkningsformel beroende på leveranstyp.

[Läs mer om indikatorberäkning](../reporting/metrics-calculation.md)


