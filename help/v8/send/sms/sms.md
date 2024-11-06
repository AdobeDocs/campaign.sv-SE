---
title: Skicka SMS med Adobe Campaign
description: Kom igång med SMS i Campaign
feature: SMS
role: User, Data Engineer
level: Beginner
exl-id: e2e2922a-2058-4588-b1b5-6997f29ee663
source-git-commit: bb77b915f50b31d8d91e25da6fa86aa15b03bba4
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 2%

---

# Kom igång med SMS {#gs-sms-channel}

Med Adobe Campaign kan ni leverera personaliserad SMS på mobiler.

För SMS-meddelanden kan du skapa, ändra och anpassa meddelanden endast i textformat. Du kan även förhandsgranska dina SMS-meddelanden innan de skickas.

>[!NOTE]
>
>Du kan också använda Adobe Campaign för att skicka [LINE](../../send/line.md)-meddelanden med text, bilder och länkar.

För att kunna leverera SMS till en mobiltelefon med Adobe Campaign behöver du:

* Ett externt konto har konfigurerats på **[!UICONTROL Mobile (SMS)]**-kanalen eller på **[!UICONTROL LINE]**-kanalen.
* En SMS-leveransmall som är korrekt länkad till det här externa kontot.

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
