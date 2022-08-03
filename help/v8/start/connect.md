---
title: Anslut till Campaign v8
description: Lär dig hur du ansluter till Campaign v8
feature: Audiences
role: Data Engineer
level: Beginner
exl-id: 176cc4f0-8827-4127-9f03-7d75ac8cf917
source-git-commit: 6de5c93453ffa7761cf185dcbb9f1210abd26a0c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Anslut till Adobe Campaign v8{#gs-ac-connect}

Campaign Client Console är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar.

Innan du börjar måste du:

* Kontrollera system- och verktygskompatibiliteten med Adobe Campaign i [Kompatibilitetsmatris](compatibility-matrix.md)
* Hämta webbadressen till Campaign-servern
* Skapa din Adobe ID eller hämta dina användaruppgifter från ditt företag

## Hämta och installera klientkonsolen{#download-ac-console}

När du använder Campaign för första gången, eller om du behöver uppgradera till en nyare version, måste du hämta klientkonsolen och installera den.

Det finns två alternativ:

1. Som kampanjadministratör ansluter du till Adobe [Programvarudistribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) och hämta installationsprogrammet för Client Console. Sedan kan du installera den på den lokala datorn.

1. Som slutanvändare kan Adobe distribuera konsolen åt dig: När konsolen har uppdaterats uppmanas du att hämta den senaste versionen av klientkonsolen i ett popup-fönster.

>[!CAUTION]
>
>Adobe rekommenderar att du låter alternativet vara kvar **[!UICONTROL No longer ask this question]** avmarkerat för att se till att alla användare får en varning när en ny version av konsolen är tillgänglig.  Om det här alternativet väljs informeras användaren inte om nya tillgängliga versioner.

## Skapa din anslutning{#create-your-connection}

När klientkonsolen har installerats nyligen följer du stegen nedan för att skapa anslutningen till programservern:

1. Starta konsolen från Windows **[!UICONTROL Start]** -menyn på **Adobe Campaign** programgrupp.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

1. Klicka **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda [`https://<machine>.<domain>.com`](https://myserver.adobe.com) skriv URL.

1. Markera alternativet **[!UICONTROL Connect with an Adobe ID]**.

1. Klicka **[!UICONTROL Ok]** för att spara inställningarna.

Du kan lägga till så många anslutningar som behövs för att ansluta till test-, scen- och produktionsmiljöer, till exempel.

>[!NOTE]
>
>The **[!UICONTROL Add]** knappen kan du skapa **[!UICONTROL folders]** för att ordna alla dina kontakter. Bara dra och släpp varje anslutning till en mapp.

## Logga in på Adobe Campaign {#logon-to-ac}

Så här loggar du in på en befintlig instans:

1. Starta konsolen från Windows **[!UICONTROL Start]** -menyn på **Adobe Campaign** programgrupp.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

   ![](assets/connectToCampaign.png)

1. Välj den Campaign-instans som du måste logga in på.

1. Klicka på **[!UICONTROL Ok]**.

1. Du kan sedan logga in på Campaign med [din Adobe ID](#connect-ims).

   ![](assets/adobeID.png)

## Bevilja åtkomst för användare{#grant-access}

Med Adobe Campaign kan du definiera och hantera de rättigheter som tilldelats de olika operatorerna. Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar:

* Tillgång till vissa funktioner (via namngivna rättigheter).
* Tillgång till vissa element
* Skapa, ändra och/eller ta bort element (leverans, kontakter, kampanjer, grupper osv.).

Läs mer om användare och hur du definierar deras behörigheter i [det här avsnittet](permissions.md).

Som kampanjadministratör ansvarar du för att skapa operatorerna och dela deras inloggningsuppgifter med användarna.

## Anslut till Campaign med din Adobe ID{#connect-ims}

Kampanjanvändare ansluter till Adobe Campaign-konsolen via sina Adobe ID via Adobe Identity Management System (IMS). De kan använda samma ID för alla Adobe-lösningar. Anslutningen sparas när du använder Adobe Campaign med andra lösningar.

Läs mer om Adobe IMS i [den här sidan](https://helpx.adobe.com/enterprise/using/identity.html).

## Webbåtkomst{#web-access}

Vissa delar av programmet kan nås via en webbläsare via ett HTML-användargränssnitt: rapporter, leveransgodkännande, instansövervakning med mera.

Webbåtkomsten har ett gränssnitt som liknar konsolen men med en reducerad uppsättning funktioner.

För en viss operator visas en kampanj med följande alternativ i konsolen:

![](assets/campaign-from-console.png)

Med tillgång till webben kommer man främst att kunna se

![](assets/campaign-from-web.png)

Webbåtkomst används också i valideringsprocessen: -operatorer kan klicka på e-postmeddelandet med godkännandebegäran och ansluta till Campaign via webbläsaren för att validera eller avvisa ett leveransinnehåll eller en budget.

Om du vill komma åt Campaign-instansen från webben är URL:en:  `https://<your adobe campaign server>:<port number>/view/home`.
