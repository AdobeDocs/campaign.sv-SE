---
title: Skicka SMS med Adobe Campaign
description: Kom igång med SMS i Campaign
feature: SMS
role: User, Data Engineer
level: Beginner
badge: label="Begränsad tillgänglighet" type="Informative"
exl-id: e2e2922a-2058-4588-b1b5-6997f29ee663
source-git-commit: af1d453179c2d739eca243b435dec90a4b8e2dd5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 4%

---

# Kom igång med SMS {#gs-sms-channel}

Använd Adobe Campaign för att skicka personaliserade SMS-meddelanden.

>[!IMPORTANT]
>
>Den här dokumentationen gäller Adobe Campaign v8.7.2 och senare.
>
>Om du har äldre versioner kan du läsa [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/en/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up/sms-set-up).

>[!NOTE]
>
>Med Adobe Campaign kan du även skicka push-meddelanden på mobiler via dess **Adobe Campaign Mobile App Channel (NMAC)** -alternativ. Läs mer i [det här avsnittet](../push.md).

Den enkla och enkla användningen av SMS gör det till en mycket värdefull kommunikationskanal utöver dess tillförlitlighet och oöverträffade kompatibilitet över flera miljarder terminaler.

Det finns två sätt att skicka ett SMS:

* Skicka det manuellt från en telefon. Det är det vanliga sättet att kommunicera direkt mellan människor.
* Skicka det från Internet. Så skickar Adobe Campaign meddelanden. För detta behöver ni en SMS-tjänsteleverantör som skapar en bro från Internet till mobilnätet.

I den här dokumentationen kan du se hur du konfigurerar, skickar och övervakar en SMS-leverans:

* **Konfigurera SMS-kanal**

Först måste du konfigurera SMS-kanalen på din [infrastruktur för mellanleverantörer](sms-mid-sourcing.md).

<!--The steps depend on the platform: either you have [a standalone instance](sms-standalone-instance.md) or you are in [a mid-sourcing infrastructure](sms-mid-sourcing.md).-->

För den här konfigurationen måste du förstå de [SMPP-externa kontoparametrarna](smpp-external-account.md) och [SMS-kanalsegenskaperna](sms-channel.md).

Kontrollera din [SMPP-anslutning efter den här konfigurationen och se hur du felsöker den om det behövs](smpp-connection.md).

* **Skapa din första SMS-leverans**

Så här startar du konfigurationen av SMS-leveransen:

1. Skapa leveransen och fyll i [SMS-leveransinställningarna](sms-delivery-settings.md),

1. [Definiera innehållet](sms-content.md) i leveransen,

1. [Välj målgrupp](sms-audience.md).

Steg för att definiera en målgrupp finns på [den här sidan](../../audiences/create-audiences.md).

* **Validera och skicka SMS**

När leveransen är klar:

1. [Skicka korrektur](sms-proofs.md) för att validera återgivningen och innehållet,

1. [skicka sedan till den slutliga målgruppen](sms-send.md).

* **Övervaka och spåra SMS**

[Lär dig övervaka och spåra ditt SMS](sms-monitor.md) när du har skickat meddelandet.
