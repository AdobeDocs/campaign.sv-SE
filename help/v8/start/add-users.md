---
title: Bevilja behörigheter för Campaign v8
description: Lär dig hur du tilldelar behörigheter till Campaign v8
feature: Permissions
role: User, Admin
level: Beginner
exl-id: 3d61abac-03df-42d3-a950-37e41a5a7756
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 2%

---

# Kom igång med behörigheter

I Adobe Campaign är användarna **operatorer** och **operatorgrupper** användarroller.

En operator är en Adobe Campaign-användare som har behörighet att logga in och utföra åtgärder. Som standard lagras operatorer i noden **[!UICONTROL Administration > Access management > Operators]**.

Adobe Campaign har inbyggda operatörsgrupper som Campaign Managers och Workflow Supervisors. Läs mer om behörigheter i [det här avsnittet](../start/gs-permissions.md)

Som medlem i en operatorgrupp har en användare behörighet att utföra åtgärder som kallas namngivna rättigheter och har åtkomst till data, som finns i mappar i **Utforskaren** -vyn. En operator kan vara medlem i flera användargrupper: rättigheter och åtkomstbehörigheter är additiva.

Namngivna rättigheter ger behörigheter till:

* Utföra åtgärder
Knappen **Analysera** i leveransredigeraren aktiveras till exempel för medlemmar i gruppen **Leveransoperatör** som har namnet **Förbered leverans** till höger

* Åtkomst till mappar
Medlemskap i operatörsgrupper kan ge eller begränsa åtkomsträttigheter till mappar genom att ändra säkerhetsinställningarna för mappar. Läs mer på [den här sidan](../start/folder-permissions.md). Det kan till exempel påverka: **Skrivåtkomst** för att skapa nya entiteter (som leveranser, profiler osv.), **Läsåtkomst** för att använda entiteter, **Ta bort åtkomst** för att ta bort entiteter.

## Säkerhetszoner

Varje operator måste länkas till en zon för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressuppsättningarna som definieras i säkerhetszonen. Säkerhetszonskonfigurationen utförs i Adobe Campaign-serverns konfigurationsfil.

Operatorer är länkade till en säkerhetszon från sin profil i konsolen, som är tillgänglig i noden **[!UICONTROL Administration > Access management > Operators]**.

>[!NOTE]
>
>Som användare av hanterade molntjänster anger Adobe säkerhetszonerna åt dig. [Kontakta Adobe](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"} om du vill ha mer information.

**Läs mer**

* [Inbyggda namngivna rättigheter](../start/gs-permissions.md)

* [Steg för att konfigurera behörigheter](../start/manage-permissions.md)
