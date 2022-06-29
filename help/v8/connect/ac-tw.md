---
title: Arbeta med Campaign och Twitter
description: Lär dig hur ni kan integrera er Campaign-miljö med Twitter
role: Data Engineer
level: Beginner
hide: true
hidefromtoc: true
exl-id: 5523217a-b95f-4639-b941-52eb7d5a0203
source-git-commit: 8eb92dd1cacc321fc79ac4480a791690fc18511c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Arbeta med Campaign och Twitter{#tw-ac-ovv}

The **Hantera sociala nätverk (social marknadsföring)** så att ni kan interagera med kunderna via Twitter. Använd den här funktionen för att:

* Skicka meddelanden - Använd Adobe Campaign Social Marketing för att publicera meddelanden på Twitter. Du kan också skicka direktmeddelanden till alla dina följare.

* Samla in nya kontakter - Adobe Campaign Social Marketing gör det också enkelt att skaffa nya kontakter: kontakta användare och fråga dem om de vill dela sin profilinformation. Om de godkänner det återhämtar Adobe Campaign automatiskt data, vilket gör att ni kan genomföra riktade kampanjer och, när det är möjligt, implementera flerkanalsstrategier.

![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Services [kontakta Adobe](../start/campaign-faq.md#support) för att ansluta Campaign till Twitter. The  **Hantera sociala nätverk (social marknadsföring)** -modulen måste installeras i din miljö via det dedikerade paketet.


Om du vill konfigurera Adobe Campaign att publicera tweets på dina Twitter-konton delegerar du skrivåtkomst till Adobe Campaign för dessa konton. Så här gör du:

1. Skapa ett Twitter-konto
1. Skapa ett test-Twitter-konto för att skicka korrektur
1. Skapa ett Twitter-program (en app per Twitter-konto)
1. Skapa en ny tjänst för **[!UICONTROL Twitter]** (en tjänst per Twitter-konto)

## Skapa ett testkonto på Twitter {#tw-test-account}

Skapa ett privat Twitter-konto som kan användas för att skicka dokument, utöver Twitter-kontot [tweet-korrektur](../send/twitter.md#send-tw-proofs). Följ stegen nedan för att göra detta:

1. Skapa ett nytt Twitter-konto.
1. Åtkomst till kontot  **Inställningar**.
1. Bläddra till **Integritet och säkerhet** och **Målgrupp och taggning** och kontrollera **Protect dina tweets** alternativ. Dina tweets och annan kontoinformation är bara synliga för personer som följer efter dig.

![](assets/social_tw_test_page.png)

## Skapa ett program i Twitter {#create-an-app-on-twitter}

Skapa ett Twitter-program så att Adobe Campaign kan publicera tweets på ditt Twitter-konto.  Följ stegen nedan för att göra detta:

1. Logga in på ditt Twitter-konto.
1. Anslut till [Twitter utvecklarportal](https://developer.twitter.com/en/apps).
1. Välj **Skapa en app**.
1. Låt Twitter assistent hjälpa dig genom processen.

   Om du vill att Adobe Campaign ska kunna publicera tweets på ditt konto kan du redigera på **Behörigheter** -fliken i programmet och välj **Läs och skriv** för **Åtkomst** -avsnitt. I **Inställningar** måste du också lämna **Återanrops-URL** fältet är tomt.

   ![](assets/social_tw_app.png)

>[!NOTE]
>
>Du behöver ett program per Twitter-konto. Därför måste du skapa ett annat testprogram för att skicka korrektur till testkontot.

## Skapa en Twitter-tjänst i Campaign {#create-tw-service}

Om du vill länka din Campaign-instans till ditt Twitter-konto skapar du en **Twitter** och delegera skrivåtkomst till Campaign.

Om du vill ange inställningar måste du ha tillgång till både Adobe Campaign-konsolen och ett Twitter-konto:

1. Öppna **Twitter** och från [sidan Projekt och program](https://developer.twitter.com/en/portal/projects-and-apps)väljer du programmet som skapades tidigare. Öppna **Programbehörigheter**.

   ![](assets/social_tw_service.png)

   Redigera **Tangenter och variabler** -fliken för att komma åt din appinformation.

1. I **Adobe Campaign**, bläddra till **[!UICONTROL Profiles and targets]** och väljer **[!UICONTROL Services and Subscriptions]** link
1. Skapa en ny tjänst.
1. Välj **[!UICONTROL Twitter]** typ.

   >[!NOTE]
   >
   >The **[!UICONTROL Synchronize subscriptions]** är aktiverat som standard: Med det här alternativet återställs automatiskt listan med dina Twitter-följare så att du kan [skicka direktmeddelanden till dem](../send/twitter.md#direct-tw-messages). Synkronisering utförs av en [dedikerat tekniskt arbetsflöde](#synchro-tw-accounts).

1. Ange etiketten och det interna namnet på tjänsten.

   >[!CAUTION]
   >
   >The **[!UICONTROL Internal name]** måste ha exakt samma namn som ditt Twitter-konto.

   Om du vill kontrollera inställningarna kan du:

   * Klicka på knappen **[!UICONTROL Save]**.
   * I översikten över tjänster väljer du **Twitter** som du just har skapat.
   * Bläddra i **[!UICONTROL Twitter page]** tab: ditt Twitter-konto ska visas.

1. Som standard sparas följare i **[!UICONTROL Visitors]** mapp. Du kan välja en annan plats på **[!UICONTROL Visitor folder]** fält. [Läs mer](../send/twitter.md#direct-tw-messages)

1. Kopiera innehållet i Twitter **[!UICONTROL Consumer Key (API Key)]** och **[!UICONTROL Consumer Secret (API Secret)]** fält och klistra in dem i **[!UICONTROL Consumer key]** och **[!UICONTROL Consumer secret]** fält i din kampanj **Twitter** service.

1. Kopiera innehållet i Twitter **[!UICONTROL Access Token]** och **[!UICONTROL Access Token Secret]** fält och klistra in dem i **[!UICONTROL Access token]** och **[!UICONTROL Access token secret]** fält i din kampanj **Twitter** service.

1. Klicka på i Campaign-klientkonsolen **[!UICONTROL Save]**. Du har nu delegerat skrivbehörighet till Adobe Campaign.


>[!NOTE]
>
>Skapa en **Twitter** per Twitter-konto. Därför måste du skapa en annan testtjänst för att skicka korrektur till testkontot.

## Synkronisera ditt Twitter-konto {#synchro-tw-accounts}

Synkroniseringen mellan Campaign och Twitter hanteras via dedikerade tekniska arbetsflöden. Dessa arbetsflöden lagras i **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** mapp.

De stoppas som standard: du måste starta dem manuellt när du börjar använda **Social marknadsföring** -modul.

The **[!UICONTROL Twitter account synchronization]** tekniskt arbetsflöde synkroniserar Twitter-konton i Adobe Campaign. Det här arbetsflödet återställer listan med Twitter-följare så att du kan skicka direktmeddelanden till dem. [Läs mer](../send/twitter.md#direct-tw-messages)

Som standard aktiveras arbetsflödet varje torsdag kl. 7.30. Du kan använda **[!UICONTROL Execute pending task(s) now]** möjlighet att starta arbetsflödet när som helst när du implementerar den här integreringen.  Du kan också redigera schemaläggaren för att ändra arbetsflödets utlösande frekvens. Läs mer i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/flow-control-activities/scheduler.html){target=&quot;_blank&quot;}.

>[!CAUTION]
>
>Om du vill återställa listan över prenumeranter på Twitter **[!UICONTROL Twitter account synchronization]** alternativet måste kontrolleras för den tjänst som är länkad till kontot. [Läs mer](#create-tw-service)

Följande lagras i en specifik tabell: besökstabellen. Om du vill visa en lista över Twitter följare går du till **[!UICONTROL Profiles and Targets > Visitors]**.

För varje följare lagrar Adobe Campaign följande information:

* **[!UICONTROL Origin]**: det sociala nätverkets namn (Twitter)
* **[!UICONTROL External ID]**: användar-ID
* **[!UICONTROL User name]**: användarens kontonamn
* **[!UICONTROL Full name]**: användarens namn
* **[!UICONTROL Language]**: användarspråk
* **[!UICONTROL Number of friends]**: antal följare
* **[!UICONTROL Time zone]**: användartidszon
* **[!UICONTROL Verified]**: det här fältet anger om användaren har ett verifierat Twitter-konto

När konfigurationen är klar kan du publicera tweets på dina Twitter-konton och skicka direktmeddelanden till dina följare. [Läs mer](../send/twitter.md)
