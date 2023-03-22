---
title: Bevilja behörigheter för Campaign v8
description: Lär dig hur du tilldelar behörigheter till Campaign v8
feature: Permissions
role: User, Admin
level: Beginner
exl-id: 3d61abac-03df-42d3-a950-37e41a5a7756
source-git-commit: 1baeb8827a0eab4f9487bb5e5afe4d779e00efe4
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 4%

---

# Kom igång med behörigheter

I Adobe Campaign är **operatorer** och **operatorgrupper** representerar användarroller.

En operator är en Adobe Campaign-användare som har behörighet att logga in och utföra åtgärder. Som standard lagras operatorer i **[!UICONTROL Administration > Access management > Operators]** nod.

Adobe Campaign har inbyggda operatörsgrupper som Campaign Managers och Workflow Supervisors. Läs mer om behörigheter i [det här avsnittet](../start/gs-permissions.md)

Som medlem i en operatorgrupp har en användare behörighet att utföra åtgärder som kallas namngivna rättigheter och har tillgång till data, som finns i mappar i **Utforskaren** vy. En operator kan vara medlem i flera operatorgrupper: behörigheter och åtkomstbehörigheter är additiva.

Namngivna rättigheter ger behörigheter till:

* Utför t.ex. **Analysera** knappen i leveransredigeraren är aktiverad för medlemmar i **Leveransoperatör** grupp som har **Förbered leverans** Namngiven höger

* Åtkomst till mappar Medlemskap i Operator Groups kan ge eller begränsa åtkomsträttigheter till mappar genom att ändra säkerhetsinställningarna för mappar. Läs mer i [den här sidan](../start/folder-permissions.md). Den kan till exempel påverka: **Skrivåtkomst** skapa nya enheter (såsom leveranser, profiler osv.), **Läsbehörighet** att använda enheter, **Ta bort åtkomst** för att ta bort enheter.

## Säkerhetszoner

Varje operator måste länkas till en zon för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressuppsättningarna som definieras i säkerhetszonen. Säkerhetszonskonfigurationen utförs i Adobe Campaign-serverns konfigurationsfil.

Operatorer är länkade till en säkerhetszon från sin profil i konsolen, som är tillgänglig i **[!UICONTROL Administration > Access management > Operators]** nod.

![](../assets/do-not-localize/speech.png)  Som användare med hanterade Cloud Services anger Adobe säkerhetszonerna åt dig. Mer information finns i [kontakta Adobe](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

**Läs mer**

* [Inbyggda namngivna rättigheter](../start/gs-permissions.md)

* [Steg för att konfigurera behörigheter](../start/manage-permissions.md)
