---
title: Skicka SMS med Adobe Campaign
description: Kom igång med SMS i Campaign
feature: SMS
role: User, Data Engineer
level: Beginner
exl-id: e2e2922a-2058-4588-b1b5-6997f29ee663
source-git-commit: 110a2cac920ca3087f6fcb3cab8474729f6075be
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 10%

---

# Kom igång med SMS {#gs-sms-channel}

Använd Adobe Campaign för att skicka textmeddelanden till kunderna på deras mobila enheter. Du kan skapa, anpassa och förhandsgranska meddelanden i textformat från SMS-redigeraren.

För att kunna leverera SMS till mobila enheter med Adobe Campaign behöver du:

* Ett externt konto har konfigurerats på **[!UICONTROL Mobile (SMS)]**-kanalen. Lär dig hur du konfigurerar SMS-kanalen på din [infrastruktur för mellanleverantörer](sms-mid-sourcing.md). För den här konfigurationen måste du förstå de [SMPP-externa kontoparametrarna](smpp-external-account.md) och [SMS-kanalsegenskaperna](sms-channel.md).
Kontrollera SMPP-anslutningen efter konfigurationen och se hur du felsöker den om det behövs. [Läs mer](smpp-connection.md).

* En SMS-leveransmall som är korrekt länkad till det här externa kontot.


>[!NOTE]
>
>Du kan också använda Adobe Campaign för att skicka [push-meddelanden](../push.md) och [LINE](../line/line.md) till mobila enheter.


<table style="table-layout:fixed"><tr style="border: 0;">
<td>
<a href="create-sms.md">
<img alt="Skapa SMS" src="../../assets/do-not-localize/sms-sending.jpg">
</a>
<div><a href="create-sms.md"><strong>Skapa en SMS-leverans</strong>
</div>
<p>
</td>
<td>
<a href="sms-content.md">
<img alt="SMS-innehåll" src="../../assets/do-not-localize/sms-create.jpeg">
</a>
<div>
<a href="sms-content.md"><strong>Definiera ditt SMS-innehåll</strong></a>
</div>
<p></td>
<td>
<a href="sms-audience.md">
<img alt="SMS-målgrupp" src="../../assets/do-not-localize/sms-opt-out.jpg">
</a>
<div>
<a href="sms-audience.md"><strong>Välj målgruppen</strong></a>
</div>
<p>
</td>
<td>
<a href="smpp-external-account.md">
<img alt="SMS-konfiguration" src="../../assets/do-not-localize/sms-config.jpg">
</a>
<div>
<a href="smpp-external-account.md"><strong>Konfigurera SMS-kanal</strong></a>
</div>
<p>
</td>
</tr></table>
