---
product: Adobe Campaign
title: Bevilja behörigheter för Campaign v8
description: Lär dig hur du tilldelar behörigheter till Campaign v8
feature: Målgrupper
role: Data Engineer
level: Beginner
exl-id: 176cc4f0-8827-4127-9f03-7d75ac8cf917
source-git-commit: c61d8aa8e0a68ccc81a6141782f860daf061bc61
workflow-type: tm+mt
source-wordcount: '280'
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
Medlemskap i operatörsgrupper kan ge eller begränsa åtkomsträttigheter till mappar genom att ändra säkerhetsinställningarna för mappar. [Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-folders.html?lang=en#permissions-on-a-folder){target=&quot;_blank&quot;}. Den kan till exempel påverka: **Skriv åtkomst** för att skapa nya entiteter (som leveranser, profiler osv.), **Läs åtkomst** för att använda entiteter, **Ta bort åtkomst** för att ta bort entiteter.

**Läs** mer i dokumentationen för Campaign Classic v7:

↗️ [Inbyggda namngivna rättigheter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-named-rights.html){target=&quot;_blank&quot;}

↗️ [Inbyggda operatörsgrupper](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-groups.html?lang=en#default-groups){target=&quot;_blank&quot;}

↗️ [Steg för att konfigurera behörigheter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management.html){target=&quot;_blank&quot;}

↗️ [Säkerhetsinställningar för mappar](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-folders.html?lang=en#permissions-on-a-folder){target=&quot;_blank&quot;}