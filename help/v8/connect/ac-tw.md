---
title: Arbeta med Campaign och X (Twitter)
description: Lär dig hur du integrerar Campaign-miljön med X (tidigare Twitter)
role: User, Admin
feature: Social Marketing
level: Beginner, Intermediate
exl-id: 5523217a-b95f-4639-b941-52eb7d5a0203
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 2%

---

# Arbeta med Campaign och X (Twitter) {#tw-ac-ovv}

Med modulen **Hantera sociala nätverk (social marknadsföring)** kan du interagera med dina kunder via X (tidigare Twitter). Använd den här funktionen för att

* Posta meddelanden och skicka DM:er - Använd Adobe Campaign Social Marketing för att publicera meddelanden på X. Du kan också skicka direktmeddelanden till alla dina följare.

* Samla in nya kontakter - Adobe Campaign Social Marketing gör det också enkelt att skaffa nya kontakter: kontakta användare och fråga dem om de vill dela sin profilinformation. Om de godkänner det återhämtar Adobe Campaign automatiskt data, vilket gör att ni kan genomföra riktade kampanjer och, när det är möjligt, implementera flerkanalsstrategier.


>[!NOTE]
>
>Som användare av hanterade Cloud Service [kontaktar du Adobe](../start/campaign-faq.md#support) för att ansluta Campaign med X. Tillägget **Hantera sociala nätverk (social marknadsföring)** måste vara installerat i din miljö, via det dedikerade paketet, och Twitternas externa konto måste konfigureras.


Om du vill konfigurera Adobe Campaign att bokföra tweets på dina X-konton delegerar du skrivåtkomst till Adobe Campaign för dessa konton. För att göra detta måste du:

1. Skapa ett X-konto och registrera dig för ett utvecklarkonto. [Läs mer](#dev-account)
1. (valfritt) Skapa ett X-testkonto för att skicka korrektur. [Läs mer](#tw-test-account)
1. Skapa ett X-program (en app per X-konto). [Läs mer](#create-an-app-on-twitter)
1. Skapa en ny tjänst för **[!UICONTROL Twitter]** (en tjänst per X-konto). [Läs mer](#create-tw-service)
1. Synkronisera ditt X-konto med Campaign. [Läs mer](#synchro-tw-accounts)

## X-utvecklarkonto {#dev-account}

Om du vill börja med den här integreringen måste du registrera dig för ett [X-utvecklarkonto](https://developer.twitter.com){target="_blank"}.

Campaign använder version 1.1 av X API. Om du vill använda den måste du ansöka om utökad åtkomst via Developer Portal. Läs mer om X-utökad åtkomst [på den här sidan](https://developer.twitter.com/en/portal/products/elevated){target="_blank"}.

## Skapa ett program på X {#create-an-app-on-twitter}

När du har godkänts med utökad åtkomst skapar du ett X-program som gör det möjligt för Adobe Campaign att skapa inlägg på ditt X-konto. Gör så här:

1. Logga in på ditt X-konto.
1. Anslut till [X-utvecklarportalen](https://developer.twitter.com/en/apps){target="_blank"}.
1. Välj **Skapa en app**.
1. Låt X-assistenten vägleda dig genom processen.
1. Om du vill tillåta Adobe Campaign att skapa inlägg på ditt konto redigerar du till **appbehörigheterna** i inställningsavsnittet för användarautentisering i din app. Välj **Läs, Skriv och Direktmeddelanden**.

   ![](assets/tw-permissions.png)

1. I avsnittet **Typ av app** väljer du **Webbapp, Automatiserad app eller Bot**. Du kan lämna fältet **Återanrops-URL** tomt och spara konfigurationen.

   ![](assets/tw-app-type.png)

1. Gå tillbaka till appkontrollpanelen, markera din app och bläddra till fliken **Tangenter och tokens**. Under **Åtkomsttoken och hemlighet** måste du återskapa din apps token och hemlighet om behörigheten **Läs, Skriv och Direktmeddelanden** inte anges. Observera att alla nycklar och token måste sparas när de skapas. Du behöver dem för att konfigurera din Campaign Twitter-tjänst.

   ![](assets/tw-permissions-check.png)


>[!NOTE]
>
>Du behöver ett program per X-konto. Därför måste du skapa ett annat testprogram för att skicka korrektur till testkontot.
>

## Skapa en Twitter i Campaign {#create-tw-service}

Om du vill länka din Campaign-instans till ditt X-konto skapar du en **Twitter**-tjänst och delegerar skrivåtkomst till Campaign.

>[!CAUTION]
>
>Skapa en **Twitter**-tjänst per X-konto. Därför måste du skapa en annan testtjänst för att skicka korrektur till ditt [testkonto](#tw-test-account).
>
>Varje **Twitter**-tjänst måste också skapas av Adobe i MID-instansen. Kontakta din Adobe-representant för att konfigurera din miljö.
>

Om du vill ange inställningar måste du ha tillgång till både din Adobe Campaign klientkonsol och dina X-appbehörigheter.

1. I **Adobe Campaign** bläddrar du till fliken **[!UICONTROL Profiles and targets]** och väljer länken **[!UICONTROL Services and Subscriptions]**
1. Skapa en ny tjänst.
1. Välj typen **[!UICONTROL Twitter]**.
1. Ange etiketten och det interna namnet på tjänsten.

   >[!CAUTION]
   >
   >Tjänstens **[!UICONTROL Internal name]** måste ha exakt samma namn som ditt X-konto.
   >

1. Som standard sparas följare i mappen **[!UICONTROL Visitors]**. Du kan välja en annan plats i fältet **[!UICONTROL Visitor folder]**. [Läs mer](../send/twitter.md#direct-tw-messages)

   ![](assets/tw-service-in-ac.png)

   >[!NOTE]
   >
   >Alternativet **[!UICONTROL Synchronize subscriptions]** är aktiverat som standard: det här alternativet återställer automatiskt listan med dina X-följare så att du kan [skicka dem direktmeddelanden](../send/twitter.md#direct-tw-messages). Synkroniseringen utförs av ett [dedikerat tekniskt arbetsflöde](#synchro-tw-accounts).

1. Kopiera innehållet i fälten **API Key** och **[API Key Secret]** från din X-app och klistra in dem i fälten **[!UICONTROL Consumer key]** och **[!UICONTROL Consumer secret]** i Campaign **Twitter** .

1. Kopiera innehållet i fälten **Åtkomsttoken** och **Åtkomsttokenhemlighet** från din X-app och klistra in dem i fälten **[!UICONTROL Access token]** och **[!UICONTROL Access token secret]** i Campaign **Twitter** -tjänsten.

1. Klicka på **[!UICONTROL Save]** i Campaign-klientkonsolen. Du har nu delegerat skrivbehörighet till Adobe Campaign.

Om du vill kontrollera inställningarna kan du:

* Redigera tjänsten **Twitter** som du just har skapat.
* Bläddra på fliken **[!UICONTROL Twitter page]**: ditt Twitter-konto ska visas.
  ![](assets/tw-page.png)

## Synkronisera ditt X-konto {#synchro-tw-accounts}

Synkroniseringen mellan Campaign och X hanteras via dedikerade tekniska arbetsflöden. Dessa arbetsflöden lagras i mappen **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**.

De stoppas som standard: du måste starta dem manuellt när du börjar använda modulen **Social marknadsföring** .

Det tekniska arbetsflödet i **[!UICONTROL Synchronization of Twitter accounts]** synkroniserar X-konton i Adobe Campaign. Det här arbetsflödet återställer listan med X-följare så att du kan skicka direktmeddelanden till dem. [Läs mer](../send/twitter.md#direct-tw-messages)

Som standard aktiveras arbetsflödet varje torsdag kl. 7.30. Du kan använda alternativet **[!UICONTROL Execute pending task(s) now]** om du vill starta arbetsflödet när du implementerar den här integreringen.  Du kan också redigera schemaläggaren för att ändra arbetsflödets utlösande frekvens. Läs mer på [den här sidan](../../automation/workflow/scheduler.md).

>[!CAUTION]
>
>Om du vill återställa listan med X-prenumeranter måste alternativet **[!UICONTROL Twitter account synchronization]** kontrolleras för den tjänst som är länkad till kontot. [Läs mer](#create-tw-service)

Följande lagras i en specifik tabell: besökstabellen. Bläddra till **[!UICONTROL Profiles and Targets > Visitors]** om du vill visa listan med X-följare.

För varje följare lagrar Adobe Campaign följande information:

* **[!UICONTROL Origin]**: Twitter
* **[!UICONTROL External ID]**: användaridentifierare
* **[!UICONTROL Username]**: användarens kontonamn
* **[!UICONTROL Full name]**: användarens namn
* **[!UICONTROL Number of friends]**: antal följare
* **[!UICONTROL Checked]**: Det här fältet anger om användaren har ett konto för verifierad Twitter

När konfigurationen är klar kan du skapa inlägg på dina X-konton och skicka direktmeddelanden till dina följare. [Läs mer](../send/twitter.md)

## Skapa ett testkonto på X {#tw-test-account}

Utöver X-kontot skapar du ett privat X-konto som kan användas för att skicka [tweet-korrektur](../send/twitter.md#send-tw-proofs). Gör så här:

1. Skapa ett nytt X-konto.
1. Öppna kontot **Inställningar**.
1. Bläddra till **Sekretess och säkerhet** och **Målgrupp och taggning** och kontrollera alternativet **Protect dina inlägg**. Dina inlägg och annan kontoinformation visas endast för personer som följer efter dig.

![](assets/do-not-localize/social_tw_test_page.png)

Konfigurera X-appen och Campaign-tjänsten så att den fungerar med det här testkontot enligt beskrivningen ovan.
