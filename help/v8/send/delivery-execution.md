---
title: Körning av leverans av transaktionsmeddelanden
description: Läs mer om exekvering och övervakning av transaktionsmeddelanden
feature: Transactional Messaging
role: User
level: Beginner, Intermediate
source-git-commit: c61f03252c7cae72ba0426d6edcb839950267c0a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Leveranskörning {#delivery-execution}

När anrikningen är klar och en leveransmall har länkats till händelsen skickas leveransen från körningsinstansen.

>[!NOTE]
>
>Transaktionsmeddelandena prioriteras framför annan leverans.

Alla leveranser grupperas i **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** mapp.

Som standard sorteras de i undermappar efter leveransmånad. Den här sorteringen kan ändras i meddelandemallens egenskaper.

## Övervakning av transaktionsmeddelanden {#transactional-message-monitoring}

Om du vill övervaka dina transaktionsmeddelanden ska du kontrollera [leveransloggar](send.md).

Transaktionsleveranser som skickas från körningsinstansen synkroniseras tillbaka till kontrollinstansen via ett tekniskt arbetsflöde (**[!UICONTROL Message Center execution instance]**) som går varje timme.

>[!NOTE]
>
>Leveranserna varje vecka samlar ihop händelserna baserat på den senaste händelseuppdateringen och inte på datumet då händelsen skapades. När du extraherar leveransloggar för transaktionsmeddelanden från kontrollinstansen kan det leverans-ID som är kopplat till varje leveranslogg-ID därför ändras över tiden när loggen uppdateras (till exempel när en inkommande avhoppning tas emot för händelsen).

<!--
To monitor the activity and running of the execution instance(s), see [Transactional messaging reports](transactional-messaging-reports.md).-->
