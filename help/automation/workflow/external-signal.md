---
product: campaign
title: Extern signal
description: Läs mer om arbetsflödesaktiviteten för externa signaturer
feature: Workflows
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 45cb95ec-77bf-4bab-895f-b94f6ce660fd
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# Extern signal{#external-signal}



Med aktiviteten **Extern signal** kan du utlösa körning av en uppsättning uppgifter i ett arbetsflöde enligt ett schema.

När en aktivitet av typen &quot;Extern signal&quot; aktiveras pausas den oavbrutet eller tills den angivna tidsperioden är slut. Övergången aktiveras av SOAP anrop **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** Parametern **[!UICONTROL complete]** tillåter att aktiviteten slutförs, så den kommer inte att reagera på efterföljande anrop.

Mer information om funktionen PostEvent finns i onlinedokumentationen för SOAP.

Du kan konfigurera aktiviteten för att definiera händelser om ingen signal tas emot. Om du vill göra det redigerar du aktiviteten och klickar på fliken **[!UICONTROL Expiration]**. Klicka på knappen **[!UICONTROL Insert]** för att skapa och konfigurera en händelse.

![](assets/edit_signal.png)

Konfigurationen av förfallodatum anges i [Förfallodatum](define-approvals.md).

I fältet **Fördröjning** kan du ange en förfallofördröjning i valfria enheter. Se [Vänta](wait.md).

Varje rad motsvarar en typ av förfallodatum och sammanfaller med en övergång.

![](assets/external_sign_diag.png)
