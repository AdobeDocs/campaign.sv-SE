---
title: Förbättrat säkerhetstillägg
description: Kom igång med tillägget Campaign Enhanced security
feature: Configuration
role: Developer
level: Experienced
hide: true
hidefromtoc: true
exl-id: 7c586836-82e1-45fb-9c28-18361572e1fa
source-git-commit: f9b064dffa0f8792e8653760cb2ac44cfdf43848
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 1%

---

# Förbättrat säkerhetstillägg {#enhanced-security}

För att göra din nätverksanslutning säkrare och ge bättre säkerhet för dina resurser, [!DNL Adobe Campaign] erbjuder en ny **Förbättrad säkerhet** tillägg.

Det här tillägget innehåller två ekosystemfunktioner:

* [Säker CMK-integrering](#secure-cmk-integration)

* [Säker VPN-tunnling](#secure-vpn-tunneling)

Dessa funktioner beskrivs nedan.

## Säker CMK-integrering {#secure-cmk-integration}

The **Integrering med Secure Customer Managed Key (CMK)** Med kan du kryptera instansen och dina data med din egen nyckel via ditt Amazon Web Services-konto (AWS).

KMS-nycklar (Key Management Service) i ditt AWS-konto som du skapar, äger och hanterar. Du har fullständig kontroll över dessa KMS-nycklar och använder dem för att kryptera och dekryptera data. Genom att göra dig ansvarig för att generera och hantera krypteringsnycklar kan du med den här kapaciteten få bättre kontroll över dem, inklusive återkallande av en nyckel.

>[!CAUTION]
>
>Om du återkallar en nyckel måste du vara medveten om effekterna. [Läs mer](#cmk-callouts)

Följ stegen nedan för att aktivera CMK-integrering med Campaign:

1. Anslut till [Amazon Web Services (AWS)](https://aws.amazon.com/){target="_blank"} konto.

1. Generera en nyckel med automatisk rotation när du använder AWS Key Management Service (KMS). [Lär dig mer](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html){target="_blank"}.

1. Använd den policy du fått från Adobe på ditt AWS-konto för att ge åtkomst till dina resurser. [Läs mer](https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-services.html){target="_blank"}. <!--link TBC-->

1. Dela [Amazon Resource Name (nyckel ARN)](https://docs.aws.amazon.com/kms/latest/developerguide/find-cmk-id-arn.html){target="_blank"} med [!DNL Adobe Campaign]. Kontakta din Adobe-representant för att göra detta. <!--or Adobe transition manager?-->

1. Skapa och testa Amazon EventBridge-reglerna för att aktivera övervakning av dina tangenter med Adobe. &#x200B; [Läs mer](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-rules.html){target="_blank"}.

## Säker VPN-tunnling {#secure-vpn-tunneling}

The **Säker VPN-tunnling (Virtual Private Network)** är ett VPN för plats-till-plats som ger säker åtkomst till dina data som överförs via ett privat nätverk, från dina lokaler till [!DNL Adobe Campaign] -instans.

<!--As it connects two networks together, it is a site-to-site VPN.-->

För att säkerställa hög tillgänglighet (HA) används två tunnlar för att undvika avbrott om ett fel inträffar i en tunnel.

Tre användningsområden stöds:

* FDA (Federated Data Access) via VPN<!--to access your on-premise database from the Campaign instance over VPN-->

* Instansinloggning via VPN från en tjock klient

* SFTP-åtkomst via VPN

>[!CAUTION]
>
>Endast lokala databaser och AWS-kompatibla VPN-enheter stöds. [Läs mer](#vpn-callouts)

Följ riktlinjerna nedan för att säkerställa att funktionen används på rätt sätt:

* Konfigurera VPN på din sida baserat på VPN-konfigurationen på Adobe.

* Håll båda tunnlarna uppe för hög tillgänglighet.

* Övervaka er sidotunnel.

* Du måste vara tunnelns initierare och vara justerad för att återinitiera anslutningen om tunneln går ner.

* Ställ in en mekanism för återförsök när du är klar om det skulle uppstå anslutningsfel.

## Guardrails {#callouts}

Vissa skyddsförslag och begränsningar som rör de förbättrade säkerhetsfunktionerna listas nedan.

* Se till att alla dina fall av säker CMK-integrering/säker VPN-tunneltrafik fungerar.

<!--* Adobe shall reach out to you or your technical team if any issue is found on your side.

* Currently, when using Enhanced security features, any communication with Adobe must be performed manually via email.-->

* Adobe kommer att övervaka

   * Din instanstillgänglighet och fortsätt med varningar om nyckeln inte är tillgänglig.

   * VPN-tunnlarna och fortsätt med varningar om något problem uppstår.

### Skydda CMK-integreringen {#cmk-callouts}

* Adobe tillhandahåller inget AWS-konto. Du måste ha ett eget AWS-konto och konfigurera det för att kunna generera och dela nyckeln med Adobe.

* Endast [AWS nyckelhanteringstjänst](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html){target="_blank"} (KMS)-nycklar stöds. Inga kundgenererade nycklar utanför KMS kan användas. &#x200B;

* Vissa driftavbrott kommer att göras för första gången. &#x200B;Hur länge driftstoppet varar beror på databasens storlek.

* När du äger och behåller nyckeln måste du kontakta Adobe om du skulle ändra nyckeln. &#x200B;

* Du kan granska nyckeln med [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html){target="_blank"} och återkalla det om det behövs. &#x200B;

* Om du återkallar, inaktiverar eller tar bort nyckeln blir dina krypterade resurser och instanser otillgängliga tills du återställer motsvarande åtgärd.

  >[!CAUTION]
  >
  >Om du inaktiverar nyckeln och inte återställer den här åtgärden inom 7 dagar kan databasen bara återställas från en säkerhetskopia.
  >
  >Om du tar bort nyckeln och inte återställer den här åtgärden inom 30 dagar tas alla dina data bort permanent och går förlorade. &#x200B;

### Skyddsräcken för säker VPN-tunnling {#vpn-callouts}

* För närvarande stöds endast lokala databaser, som<!--Richa to check the list with PM-->:

   * MySQL
   * Netezza 
   * Oracle 
   * SAP HANA 
   * SQL Server 
   * Sybase 
   * Teradata 
   * Hadoop via HiveSQL

* Endast VPN-enheter som följer AWS stöds. En lista över kompatibla enheter finns på [den här sidan](https://docs.aws.amazon.com/vpn/latest/s2svpn/your-cgw.html#example-configuration-files){target="_blank"}<!--check which list should be communicated-->.

* VPN-anslutning till tredje part eller externa leverantörer stöds inte.

* Ytterligare VPN-nätverk som hanteras av Adobe till privata molndatabaser ingår inte.
