---
title: Åtkomstspårningsloggar
description: Lär dig hur du får åtkomst till och tolkar spårningsloggar
feature: Monitoring
role: User
level: Beginner
exl-id: df494786-5950-4646-aa9c-4dde45845057
source-git-commit: 5b23be4cb8f0896d2482e525e416713b1a6c4514
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Åtkomstspårningsloggar {#accessing-the-tracking-logs}

När leveransen har skickats och spårningen aktiverats ansvarar det tekniska arbetsflödet för **[!UICONTROL Tracking]** för att hämta spårningsdata. Den körs som standard varje timme.

## Visa spårning i mottagarprofiler {#recipient-tracking}

Den här informationen visas på fliken **[!UICONTROL Tracking]** i profilen för mottagare som leveransmålet gäller, som i följande exempel:

![](assets/s_ncs_user_select_tracking_tab_from_recipient.png)

På den här fliken visas alla URL:er som spåras och klickas av mottagaren, inklusive:

* Den URL som klickades på
* Datum och tid för klickningen
* Leveransen som URL:en hittades i
* Annan relevant spårningsinformation

Ni kan filtrera och sortera informationen för att analysera mottagarnas beteende och identifiera engagemangsmönster.

## Visa spårning i leveranser {#delivery-tracking}

Spårningsinformation är också tillgänglig via fliken **[!UICONTROL Tracking]** i leveransen.

![](assets/s_ncs_user_select_tracking_tab_from_del.png)

På den här fliken kan du visa:

* **[!UICONTROL Tracking statistics]**: ger en översikt över öppningar, klickningar och andra spårningshändelser
* **[!UICONTROL URLs and click streams]**: visar vilka länkar som klickades och hur många gånger
* **[!UICONTROL Hot clicks]**: visar en visuell representation av var mottagare klickade i meddelandet
* **[!UICONTROL Tracking logs]**: innehåller detaljerade, individuella spårningsposter

## Felsökningsspårning {#troubleshooting}

>[!NOTE]
>
>Om du inte kan se fliken **[!UICONTROL Tracking]** för en leverans innebär det att spårning inte har aktiverats. Mer information om hur du konfigurerar spårning finns i [det här avsnittet](tracked-links.md).

### Kontrollera det tekniska arbetsflödet för uppföljning {#check-tracking-workflow}

Det tekniska arbetsflödet för spårning måste köras för att samla in spårningsdata. Du hittar det tekniska arbetsflödet för spårning i mappen **[!UICONTROL Administration > Production > Technical workflows]**.

Så här verifierar du arbetsflödet:

1. Öppna arbetsflödet för **[!UICONTROL Tracking]**
1. Kontrollera det senaste körningsdatumet
1. Kontrollera att det inte finns några fel i arbetsflödesloggarna

Kontakta systemadministratören om arbetsflödet inte körs eller om det finns fel.

## Verifiera datainsamling för spårning

När en leverans med spårning aktiverat har skickats:

1. Vänta tills spårningsarbetsflödet körs (som standard varje timme)
1. Öppna leveransen och gå till fliken **[!UICONTROL Tracking]**
1. Kontrollera att spårningsdata visas
1. Om inga data visas kontrollerar du att:
   * Spårning aktiverades i leveransinställningarna
   * Det tekniska arbetsflödet för spårning körs
   * Mottagarna öppnade e-postmeddelandet och klickade på länkar

## Relaterade ämnen {#related-topics}

* [Lär dig konfigurera spårade länkar](tracked-links.md)
* [Lär dig hur du testar spårning](testing-tracking.md)
* [Läs spårningsrapporter](../reporting/delivery-reports.md#tracking-indicators)

