---
product: Adobe Campaign
title: Bevilja behörigheter för Campaign v8
description: Lär dig hur du tilldelar behörigheter till Campaign v8
feature: Målgrupper
role: Data Engineer
level: Beginner
exl-id: 176cc4f0-8827-4127-9f03-7d75ac8cf917
source-git-commit: 4bd67cd3e4e88015d8044f07ca95927b6d7867f3
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 1%

---

# Kom igång med behörigheter

I Adobe Campaign är användarna **operatorer** och **operatorgrupper** användarroller.

Adobe Campaign har inbyggda operatörsgrupper som Campaign Managers och Workflow Supervisors. Alla inbyggda grupper visas i [dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-groups.html?lang=en#default-groups)

Som medlem i en operatorgrupp har en användare behörighet att utföra åtgärder som kallas namngivna rättigheter och har åtkomst till data, som finns i mappar i vyn **Utforskaren**. En operator kan vara medlem i flera operatorgrupper: behörigheter och åtkomstbehörigheter är additiva.

Namngivna rättigheter ger behörigheter till:

* Utföra åtgärder
Till exempel är knappen **Analysera** i leveransredigeraren aktiverad för medlemmar i gruppen **Leveransoperatör** som har **Förbered leverans** namngiven till höger

* Åtkomst till mappar
Medlemskap i operatörsgrupper kan ge eller begränsa åtkomsträttigheter till mappar genom att ändra säkerhetsinställningarna för mappar. [Läs mer i dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-folders.html?lang=en#permissions-on-a-folder) till Campaign Classic v7. Den kan till exempel påverka: **Skriv åtkomst** för att skapa nya entiteter (som leveranser, profiler osv.), **Läs åtkomst** för att använda entiteter, **Ta bort åtkomst** för att ta bort entiteter.

**Läs** mer i dokumentationen för Campaign Classic v7:

[!DNL :arrow_upper_right:] [Inbyggda namngivna rättigheter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-named-rights.html)

[!DNL :arrow_upper_right:] [Inbyggda operatörsgrupper](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-groups.html?lang=en#default-groups)

[!DNL :arrow_upper_right:] [Steg för att konfigurera behörigheter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management.html)

[!DNL :arrow_upper_right:] [Säkerhetsinställningar för mappar](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-folders.html?lang=en#permissions-on-a-folder).