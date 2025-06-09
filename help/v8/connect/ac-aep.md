---
title: Dela och synka målgrupper och profilattribut med Adobe Experience Platform
description: Lär dig hur du synkroniserar Adobe Experience Platform målgrupper och profilattribut med Campaign
feature: Experience Platform Integration
role: Data Engineer
level: Beginner
exl-id: 21cf5611-ccaa-4e83-8891-a1a2353515aa
source-git-commit: ea37b72efd03afb212c060f809b6ba077b996701
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Dela och synka målgrupper med Adobe Experience Platform {#gs-ac-aep}

Adobe Campaign hanterade Cloud Service Destination- och Source-anslutningar möjliggör smidig integrering mellan Adobe Campaign och Adobe Experience Platform. Med den här integreringen kan du

* Skicka Adobe Experience Platform-målgrupper till Adobe Campaign och skicka tillbaka leverans- och spårningsloggar till Adobe Experience Platform för analysändamål,
* Lägg in Adobe Experience Platform-profilattribut i Adobe Campaign och ha en synkroniseringsprocess så att de kan uppdateras regelbundet.

## Skicka Adobe Experience Platform-målgrupper till Campaign {#audiences}

De viktigaste stegen för att skicka Adobe Experience Platform-målgrupper till Adobe Campaign och skicka tillbaka leverans- och spårningsloggar är följande:

* Använd en **målanslutning** från Adobe Campaign Managed Cloud Services för att skicka Experience Platform-segment till Adobe Campaign:

   1. Öppna Adobe Experience Platform Destinations-katalogen och skapa en ny **[!UICONTROL Adobe Campaign Managed Cloud Services]**-anslutning.
   1. Ange information om Campaign-instansen som ska användas och välj **[!UICONTROL Audience sync]** som synkroniseringstyp.

      ![](assets/aep-audience-sync.png){width="800" align="center"}

   1. Markera de segment som ska skickas till Adobe Campaign.
   1. Konfigurera de attribut som du vill exportera till målgruppen.
   1. När flödet har konfigurerats är de valda målgrupperna tillgängliga för aktivering i Adobe Campaign.

      ![](assets/aep-destination.png){width="800" align="center"}

  Detaljerad information om hur du konfigurerar målet finns i [Adobe Campaign Managed Cloud Services-anslutningsdokumentationen](https://www.adobe.com/go/destinations-adobe-campaign-managed-cloud-services-en){target="_blank"}

* Använd en **Source-anslutning** från Adobe Campaign Managed Cloud Services för att skicka Adobe Campaign leverans- och spårningsloggar till Adobe Experience Platform:

  Det gör du genom att konfigurera en ny Adobe Campaign Managed Cloud Services **Source-anslutning** så att Campaign-händelser importeras till Adobe Experience Platform. Ange information om Campaign-instansen och det schema som ska användas, välj en datauppsättning där data ska hämtas och konfigurera sedan fälten som ska hämtas. [Lär dig hur du skapar en Adobe Campaign Managed Cloud Services-källanslutning](https://www.adobe.com/go/sources-campaign-ui-en)

  ![](assets/aep-logs.png){width="800" align="center"}

## Synkronisera profilattribut mellan Adobe Experience Platform och Adobe Campaign {#profile}

Genom att ansluta Adobe Campaign till Adobe Experience Platform kan du lägga in ytterligare profilattribut som är kopplade till en profil på Adobe Experience Platform och som har en synkroniseringsprocess så att de uppdateras i Adobe Campaign-databasen.

Anta till exempel att du hämtar värden för anmälan och avanmälan i Adobe Experience Platform. Med den här anslutningen kan du föra över dessa värden till Adobe Campaign och ha en synkroniseringsprocess så att de uppdateras regelbundet.

>[!NOTE]
>
>Synkronisering av profilattribut är tillgängligt för profiler som redan finns i Adobe Campaign-databasen.

De viktigaste stegen för att synkronisera Adobe Experience Platform-profilattribut med Adobe Campaign är följande:

1. Öppna Adobe Experience Platform Destinations-katalogen och skapa en ny **[!UICONTROL Adobe Campaign Managed Cloud Services]**-anslutning.
1. Ange information om Campaign-instansen som ska användas och välj **[!UICONTROL Profile sync (Update only)]** som synkroniseringstyp.

   ![](assets/aep-profile-sync.png){width="800" align="center"}

1. Markera de segment som ska uppdateras till Adobe Campaign-databasen.
1. Konfigurera de profilattribut som du vill uppdatera till Adobe Campaign.
1. När flödet har konfigurerats synkroniseras de valda profilattributen med Adobe Campaign och uppdateras för alla profiler som är avsedda för de segment som har konfigurerats i målet.

Detaljerad information om hur du konfigurerar målet finns i [Adobe Campaign Managed Cloud Services-anslutningsdokumentationen](https://www.adobe.com/go/destinations-adobe-campaign-managed-cloud-services-en){target="_blank"}