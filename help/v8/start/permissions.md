---
title: Bevilja behörigheter för Campaign v8
description: Lär dig hur du tilldelar behörigheter till Campaign v8
feature: Audiences
role: Data Engineer
level: Beginner
exl-id: 3d61abac-03df-42d3-a950-37e41a5a7756
source-git-commit: 63b53fb6a7c6ecbfc981c93a723b6758b5736acf
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 2%

---

# Kom igång med behörigheter

I Adobe Campaign är användarna **operatorer** och **operatorgrupper** användarroller.

En operator är en Adobe Campaign-användare som har behörighet att logga in och utföra åtgärder. Som standard lagras operatorer i noden **[!UICONTROL Administration > Access management > Operators]**.

Adobe Campaign har inbyggda operatörsgrupper som Campaign Managers och Workflow Supervisors. Alla inbyggda grupper listas i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-groups.html?lang=en#default-groups){target=&quot;_blank&quot;}.

Som medlem i en operatorgrupp har en användare behörighet att utföra åtgärder som kallas namngivna rättigheter och har åtkomst till data, som finns i mappar i vyn **Utforskaren**. En operator kan vara medlem i flera operatorgrupper: behörigheter och åtkomstbehörigheter är additiva.

Namngivna rättigheter ger behörigheter till:

* Utföra åtgärder
Till exempel är knappen **Analysera** i leveransredigeraren aktiverad för medlemmar i gruppen **Leveransoperatör** som har **Förbered leverans** namngiven till höger

* Åtkomst till mappar
Medlemskap i operatörsgrupper kan ge eller begränsa åtkomsträttigheter till mappar genom att ändra säkerhetsinställningarna för mappar. [Läs mer i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-folders.html?lang=en#permissions-on-a-folder){target=&quot;_blank&quot;}. Den kan till exempel påverka: **Skriv åtkomst** för att skapa nya entiteter (som leveranser, profiler osv.), **Läs åtkomst** för att använda entiteter, **Ta bort åtkomst** för att ta bort entiteter.

## Säkerhetszoner

Varje operator måste länkas till en zon för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressuppsättningarna som definieras i säkerhetszonen. Säkerhetszonskonfigurationen utförs i Adobe Campaign-serverns konfigurationsfil.

Operatorer är länkade till en säkerhetszon från sin profil i konsolen och tillgängliga i noden **[!UICONTROL Administration > Access management > Operators]**.

![](../assets/do-not-localize/speech.png)  Som användare med hanterade Cloud Services anger Adobe säkerhetszonerna åt dig. Om du vill ha mer information kan du [kontakta Adobe](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target=&quot;_blank&quot;}.

**Läs mer i dokumentationen för Campaign Classic v7**

* [Inbyggda namngivna rättigheter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-named-rights.html){target=&quot;_blank&quot;}

* [Inbyggda operatörsgrupper](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-groups.html?lang=en#default-groups){target=&quot;_blank&quot;}

* [Steg för att konfigurera behörigheter](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management.html){target=&quot;_blank&quot;}
