---
product: campaign
title: Inkommande SMS
description: Läs mer om arbetsflödesaktiviteten för inkommande SMS
feature: Workflows, Channels Activity
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 2c12c45b-4429-4e60-bc96-ff70a95d4c9e
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 6%

---

# Inkommande SMS{#inbound-sms}



Med aktiviteten **Inkommande SMS** kan du hämta och bearbeta textmeddelanden från ett externt konto.

## Egenskaper {#properties}

![](assets/sms_rec_edit.png)

På den första fliken i aktiviteten **Inkommande SMS** kan du ange routningsparametrar för SMS-meddelanden och ange det skript som ska köras när du tar emot varje meddelande. På den andra fliken kan du tilldela aktiviteten ett schema och på den tredje fliken definieras aktivitetens förfallovillkor.

1. **[!UICONTROL SMS routing]**: Välj det externa konto som ska användas för SMS-återställning. Externa konton konfigureras via noden **[!UICONTROL Administration > Platform > External accounts]** i trädet. [Läs mer](../../v8/config/external-accounts.md)
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

Flikarna **[!UICONTROL Script]**, **[!UICONTROL Schedule]** och **[!UICONTROL Expiry]** finns detaljerade i [Inkommande e-postmeddelanden](inbound-emails.md).
