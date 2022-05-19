---
title: Visa befintliga profiler i Campaign
description: Lär dig hur du får åtkomst till kontaktdata i Campaign
feature: Audiences, Profiles
role: Data Engineer
level: Beginner
exl-id: 03f7a736-e0b9-4216-9550-507f10e6fcf6
source-git-commit: 6de5c93453ffa7761cf185dcbb9f1210abd26a0c
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# Visa befintliga profiler{#view-profiles}

Bläddra till **[!UICONTROL Profiles and targets]** för att få åtkomst till mottagare som lagras i Adobe Campaign-databasen.

Från den här sidan kan du [skapa ny mottagare](create-profiles.md), redigera en befintlig mottagare och få tillgång till dess profilinformation.

![](assets/profiles-and-targets.png)

Om du vill ha mer avancerade profiländringar kan du gå till Campaign-trädet från **[!UICONTROL Explorer]** på Adobe Campaign hemsida.

![](assets/recipients-in-explorer.png)


>[!CAUTION]
>
>Den inbyggda mottagarskärmen definieras via ett XML-schema och dess tillhörande form. XML-schemat lagras i **[!UICONTROL Administration > Configuration > Data schemas]** noden i Adobe Campaign Explorer-trädet. Endast expertanvändare får göra ändringar i dessa scheman.

## Redigera en profil{#edit-a-profiles}

Välj en profil om du vill visa information på en ny flik.

![](assets/edit-a-profile.png)

Data som rör profiler grupperas i flikar. Dessa flikar och deras innehåll beror på dina specifika inställningar och installerade paket.

För en vanlig inbyggd mottagare kan du använda följande flikar:

* **[!UICONTROL General]** för alla allmänna profildata. Den innehåller i synnerhet efternamn, förnamn, e-postadress, e-postformat osv.

   Den här fliken lagrar även **avanmäl dig** profilflagga: när **[!UICONTROL No longer contact (by any channel)]** om du väljer det här alternativet visas profilen till blockeringslista. Den här informationen läggs till i kontaktinformationen om mottagaren till exempel klickade på länken för att avbryta prenumerationen i ett nyhetsbrev. Mottagaren är inte längre riktad mot någon kanal (e-post, direktreklam osv.). Mer information finns på [den här sidan](../send/quarantines.md).

* **Kontaktinformation**, som innehåller den valda profilens e-postadress.

   På den här skärmen kan du kontrollera adressens kvalitetsindex och hur många fel adressen innehåller. Den här informationen används direkt av direktreklamleverantören, baserat på antalet fel som påträffats under tidigare leveranser och kan inte ändras manuellt.

* **Övriga**, för specifika fält som kan anpassas och fyllas i efter behov.

   Använd **[!UICONTROL Field properties…]** snabbmeny för att ändra fältnamnen och definiera deras format.

   ![](assets/other-tab-field-properties.png)

   Ange de nya inställningarna enligt nedan:

   ![](assets/change-field-properties.png)

   Kontrollera uppdateringen i användargränssnittet:

   ![](assets/other-tab-updated.png)


   >[!CAUTION]
   >Ändringarna gäller alla mottagare.


* **Prenumerationer**, för alla aktiva prenumerationer på tjänster. Använd **Historik** om du vill ha information om prenumerationer och prenumerationer för den här kontakten.

   ![](assets/subscription-tab.png)

   Läs mer om prenumerationer [i det här avsnittet](../start/subscriptions.md).

* **Leveranser**, för alla leveransloggar för den valda profilen. Använd den här fliken för att få åtkomst till kontaktens marknadsföringshistorik: etiketter, datum och status för alla leveransåtgärder som riktas till profilen via alla kanaler.


* **Spårning**, för alla spårningsloggar för den valda profilen. Den här informationen används för att spåra profilbeteende efter leveranser. På den här fliken visas den kumulativa summan av alla URL:er som spåras i leveranser. Listan är konfigurerbar och innehåller vanligtvis: klickad URL, datum och tid för klickningen samt dokumentet som innehöll URL:en

   Läs mer om spårning [i det här avsnittet](../start/tracking.md).


## Aktiva profiler {#active-profiles}

Aktiva profiler är de profiler som räknas i faktureringssyfte.

Fakturering gäller endast profiler som **aktiv**. En profil anses vara aktiv om profilen har delats eller kommunicerats med via någon kanal under de senaste 12 månaderna.

En profil som har valts av flera leveranser räknas bara en gång.

Antal aktiva profiler är tillgängligt för **Marknadsföringsinstanser** endast. Den är inte tillgänglig för körningsinstanser, vilket innebär MID-instanser (mellanleverantörer) och RT-instanser (Message Center/Real-time Messaging).

>[!NOTE]
>
>Du kan också övervaka antalet aktiva profiler på instansen direkt från Campaign-kontrollpanelen. Mer information finns i [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html).
