---
title: Visa befintliga profiler i Campaign
description: Lär dig hur du får åtkomst till kontaktdata i Campaign
feature: Audiences, Profiles
role: User
level: Beginner
exl-id: 03f7a736-e0b9-4216-9550-507f10e6fcf6
version: Campaign v8, Campaign Classic v7
source-git-commit: ec1b41ccf532b044e75c69e795eabfb19a523ec2
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 2%

---

# Visa befintliga profiler {#view-profiles}

Bläddra till **[!UICONTROL Profiles and targets]** för att få åtkomst till mottagare som lagras i Adobe Campaign-databasen.

Från den här sidan kan du [skapa ny mottagare](create-profiles.md), redigera en befintlig mottagare och komma åt dess profilinformation.

![](assets/profiles-and-targets.png)

Om du vill ha mer avancerade profiländringar öppnar du Campaign-trädet från länken **[!UICONTROL Explorer]** på Adobe Campaign hemsida.

![](assets/recipients-in-explorer.png)


>[!CAUTION]
>
>Den inbyggda mottagarskärmen definieras via ett XML-schema och dess tillhörande form. XML-schemat lagras i noden **[!UICONTROL Administration > Configuration > Data schemas]** i Adobe Campaign Explorer-trädet. Endast expertanvändare får göra ändringar i dessa scheman.
>

## Redigera en profil {#edit-a-profiles}

Välj en profil om du vill visa information på en ny flik.

![](assets/edit-a-profile.png)

Data som rör profiler grupperas i flikar. Dessa flikar och deras innehåll beror på dina specifika inställningar och installerade paket.

För en vanlig inbyggd mottagare kan du använda följande flikar:

* **[!UICONTROL General]**, för alla allmänna profildata. Den innehåller i synnerhet efternamn, förnamn, e-postadress, e-postformat osv.

  På den här fliken lagras även flaggan **opt-out** för profilen: när alternativet **[!UICONTROL No longer contact (by any channel)]** är markerat är profilen på blockeringslista. Den här informationen läggs till i kontaktinformationen om mottagaren till exempel klickade på länken för att avbryta prenumerationen i ett nyhetsbrev. Mottagaren är inte längre riktad mot någon kanal (e-post, direktreklam osv.). Mer information finns på [den här sidan](../send/quarantines.md).

* **Kontaktinformation**, som innehåller den valda profilens direkte-postadress.

  På den här skärmen kan du kontrollera adressens kvalitetsindex och hur många fel adressen innehåller. Den här informationen används direkt av direktreklamleverantören, baserat på antalet fel som påträffats under tidigare leveranser, och kan inte ändras manuellt.

* **Annat**, för specifika fält som kan anpassas och fyllas i beroende på dina behov.

  Använd snabbmenyn **[!UICONTROL Field properties…]** om du vill ändra namnen på fälten och definiera deras format.

  ![](assets/other-tab-field-properties.png)

  Ange de nya inställningarna enligt nedan:

  ![](assets/change-field-properties.png)

  Kontrollera uppdateringen i användargränssnittet:

  ![](assets/other-tab-updated.png)


  >[!CAUTION]
  >Ändringarna gäller för alla mottagare.
  >


* **Prenumerationer**, för alla aktiva prenumerationer på tjänster. Använd fliken **Historik** för att få information om prenumerationer och prenumerationer för den här kontakten.

  ![](assets/subscription-tab.png)

  Läs mer om prenumerationer [i det här avsnittet](../start/subscriptions.md).

* **Leveranser**, för alla leveransloggar för den valda profilen. Använd den här fliken för att få åtkomst till kontaktens marknadsföringshistorik: etiketter, datum och status för alla leveransåtgärder som riktas till profilen via alla kanaler.


* **Spårning**, för alla spårningsloggar för den valda profilen. Den här informationen används för att spåra profilbeteende efter leveranser. På den här fliken visas den kumulativa summan av alla URL:er som spåras i leveranser. Listan är konfigurerbar och innehåller vanligtvis: klickad URL-adress, datum och tid för klickningen samt dokumentet som innehöll URL-adressen

  Läs mer om spårning av [i det här avsnittet](../start/tracking.md).
