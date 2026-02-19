---
title: Förbättrat säkerhetstillägg för kampanj
description: Riktlinjer för säker konfiguration för Campaign-tillägget Förbättrat skydd
feature: Configuration
role: Developer
level: Experienced
exl-id: 7c586836-82e1-45fb-9c28-18361572e1fa
source-git-commit: 925f8152d28f60f876c5ef4420064fa0d71cdb9d
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 2%

---


# Förbättrat säkerhetstillägg för kampanj {#enhanced-security}

Den här sidan är en del av Adobe [offentligt tillgängliga rekommenderade riktlinjer för säker konfiguration](security.md#public-guidance) för Campaign v8.

[!DNL Adobe Campaign] erbjuder ett nytt **Förbättrat skydd**-tillägg för att göra din nätverksanslutning säkrare och ge bättre säkerhet för dina resurser.

Det här tillägget innehåller två ekosystemfunktioner:

* [Integrering med Secure Customer Managed Key (CMK)](#secure-cmk-integration)

* [Säker VPN-tunnling (Virtual Private Network)](#secure-vpn-tunneling)

Dessa funktioner beskrivs nedan.

Vissa skyddsförslag och begränsningar som rör Förbättrade säkerhetsfunktioner listas på den här sidan. Dessutom måste du se till att alla dina fall av säker CMK-integrering/säker VPN-tunneltrafik fungerar.

När dessa funktioner är implementerade övervakar Adobe:

* Din instanstillgänglighet och fortsätt med varningar om nyckeln inte är tillgänglig.

* VPN-tunnlarna och fortsätt med varningar om något problem uppstår.

## Säker integrering av kundhanterad nyckel {#secure-cmk-integration}

Med integreringen **Secure Customer-Managed Key (CMK)** kan du kryptera vilande data med din egen nyckel via ditt Amazon Web Services-konto (AWS).

KMS-nycklar (Key Management Service) i ditt AWS-konto som du skapar, äger och hanterar. Du har fullständig kontroll över dessa KMS-nycklar och använder dem för att kryptera och dekryptera data. Genom att göra dig ansvarig för att generera och hantera krypteringsnycklar kan du med den här kapaciteten få bättre kontroll över dem, inklusive återkallande av en nyckel.

>[!CAUTION]
>
>Om du återkallar en nyckel måste du vara medveten om effekterna. [Läs mer](#cmk-callouts)

Följ stegen nedan för att aktivera CMK-integrering med Campaign:

1. Anslut till ditt [Amazon Web Services (AWS)](https://aws.amazon.com/){target="_blank"}-konto.

1. Generera en nyckel med automatisk rotation när du använder AWS Key Management Service (KMS). [Lär dig hur](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html){target="_blank"}.

1. Använd den policy du fått av Adobe på ditt AWS-konto för att ge åtkomst till dina resurser. [Läs mer](https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-services.html){target="_blank"}. <!--link TBC-->

1. Dela ditt [Amazon-resursnamn (nyckel ARN)](https://docs.aws.amazon.com/kms/latest/developerguide/find-cmk-id-arn.html){target="_blank"} med [!DNL Adobe Campaign]. Kontakta Adobe om du vill göra det. <!--or Adobe transition manager?-->

1. Skapa och testa Amazon EventBridge-reglerna för att aktivera övervakning av dina nycklar i Adobe. &#x200B; [Läs mer](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-rules.html){target="_blank"}.


### Skyddsritningar och begränsningar {#cmk-callouts}

Följande skyddsutkast och begränsningar gäller för CMK-integreringen med Adobe Campaign v8:

* Adobe tillhandahåller inget [Amazon Web Services (AWS)](https://aws.amazon.com/){target="_blank"}-konto. Du måste ha ett eget AWS-konto och konfigurera det för att kunna generera och dela nyckeln med Adobe.

* Endast [KMS-nycklar (AWS Key Management Service](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html){target="_blank"}) stöds. Inga kundgenererade nycklar utanför KMS kan användas. &#x200B;

* Under den första konfigurationen förväntas driftstopp. &#x200B;Hur länge driftstoppet varar beror på databasens storlek.

* Som kund äger och underhåller ni nyckeln. Du måste kontakta Adobe om din nyckel ändras. &#x200B;

* Du kan granska nyckeln med [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html){target="_blank"} och återkalla den om det behövs. &#x200B;

* Om du återkallar, inaktiverar eller tar bort nyckeln blir dina krypterade resurser och instanser otillgängliga tills du återställer motsvarande åtgärd.

  >[!CAUTION]
  >
  >Om du inaktiverar nyckeln och inte återställer den här åtgärden inom 7 dagar kan databasen bara återställas från en säkerhetskopia.
  >
  >Om du tar bort nyckeln och inte återställer den här åtgärden inom 30 dagar tas alla dina data bort permanent och går förlorade. &#x200B;

## Säker tunnling av virtuella privata nätverk {#secure-vpn-tunneling}

**VPN-tunnling (Secure Virtual Private Network)** är ett VPN för plats-till-plats som ger säker åtkomst till data som överförs via ett privat nätverk, från dina platser till instansen [!DNL Adobe Campaign].

<!--As it connects two networks together, it is a site-to-site VPN.-->

För att säkerställa hög tillgänglighet (HA) används två tunnlar för att undvika avbrott om ett fel inträffar i en tunnel.

Tre användningsområden stöds:

* FDA (Federated Data Access) via VPN för att komma åt din lokala databas från Campaign-instansen via VPN

* Instansinloggning via VPN från en tjock klient

* SFTP-åtkomst via VPN

>[!CAUTION]
>
>Lokala databaser och molndatabaser stöds. [Läs mer](#vpn-databases)

Följ riktlinjerna nedan för att säkerställa att funktionen används på rätt sätt:

* Konfigurera VPN på din sida baserat på VPN-konfigurationen på Adobe-sidan.

* Håll båda tunnlarna uppe för hög tillgänglighet.

* Övervaka er sidotunnel.

* Du måste vara tunnelns initierare och vara justerad för att återinitiera anslutningen om tunneln går ner.

* Ställ in en mekanism för återförsök när du är klar om det skulle uppstå anslutningsfel.

### Databaser och enheter som stöds {#vpn-databases}

Följande lokala databaser stöds:

* MySQL
* Netezza
* Oracle
* SAP HANA
* SQL Server
* Sybase
* Teradata
* Hadoop via HiveSQL
* PostgreSQL

Molndatabaser stöds. Se [kompatibilitetsmatrisen](../start/compatibility-matrix.md#FederatedDataAccessFDA).

>[!NOTE]
>
>* VPN-anslutning till tredje part eller externa leverantörer stöds inte.
>
>* Ytterligare VPN-nätverk som hanteras av Adobe till privata molndatabaser ingår inte.
