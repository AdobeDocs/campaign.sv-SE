---
product: campaign
title: Extern signal
description: Läs mer om arbetsflödesaktiviteten för externa signaturer
feature: Workflows
role: User
exl-id: 45cb95ec-77bf-4bab-895f-b94f6ce660fd
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# Extern signal{#external-signal}



The **Extern signal** Med -aktivitet kan du utlösa körning av en uppsättning uppgifter i ett arbetsflöde enligt ett schema.

När en aktivitet av typen &quot;Extern signal&quot; aktiveras pausas den oavbrutet eller tills den angivna tidsperioden är slut. Övergången aktiveras av SOAP-anropet **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** The **[!UICONTROL complete]** -parametern gör att aktiviteten kan slutföras så att den inte svarar på efterföljande anrop.

Mer information om funktionen PostEvent finns i onlinedokumentationen för SOAP-anrop.

Du kan konfigurera aktiviteten för att definiera händelser om ingen signal tas emot. Det gör du genom att redigera aktiviteten och klicka på **[!UICONTROL Expiration]** -fliken. Klicka på **[!UICONTROL Insert]** för att skapa och konfigurera en händelse.

![](assets/edit_signal.png)

Konfigurationen av förfallodatum finns i [Förfallodatum](define-approvals.md).

The **Fördröjning** I kan du ange en förfallotid i valfri enhet. Se [Vänta](wait.md).

Varje rad motsvarar en typ av förfallodatum och sammanfaller med en övergång.

![](assets/external_sign_diag.png)
