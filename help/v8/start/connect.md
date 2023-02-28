---
title: Anslut till Campaign v8
description: Lär dig hur du ansluter till Adobe Campaign v8 och installerar konsolen på datorn för enklare åtkomst.
feature: Client Console
role: User
level: Beginner
exl-id: 176cc4f0-8827-4127-9f03-7d75ac8cf917
source-git-commit: f381a2ec91b7179a51d91f9b7414ea39db03cd71
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 4%

---

# Anslut till Adobe Campaign v8{#gs-ac-connect}

Campaign Client Console är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar. Läs mer om Campaign Client Console [på den här sidan](ac-components.md#presentation-layer).

Innan du börjar måste du:

* Kontrollera system- och verktygskompatibiliteten med Adobe Campaign i [Kompatibilitetsmatris](compatibility-matrix.md)
* Hämta webbadressen till Campaign-servern
* Skapa din Adobe ID eller hämta dina användaruppgifter från ditt företag
* Installera Microsoft Edge Webview2-miljön på datorn (från version Campaign Classic 8.4). [Läs mer](#webview)

## Installation av Microsoft Edge Webview2 {#webview}

Från version 8.4 av Campaign Classic krävs installation av Microsoft Edge Webview 2 för alla konsolinstallationer.

Webbvyn installeras som standard som en del av operativsystemet Windows 11. Om det inte redan finns på datorn uppmanas du att hämta det från Campaign Console Installer [Microsoft Developer website](http://www.adobe.com/go/acc-ms-webview2-runtime-download){target="_blank"}. Observera att nedladdningslänken inte fungerar i webbläsaren Internet Explorer 11 eftersom Microsoft inte längre stöder det. Kontrollera att du använder en annan webbläsare för att komma åt länken.

## Hämta och installera klientkonsolen{#download-ac-console}

När du använder Campaign för första gången, eller om du behöver uppgradera till en nyare version, måste du hämta klientkonsolen och installera den.

Det finns två alternativ:

1. Som kampanjadministratör ansluter du till Adobe [Programvarudistribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html){target="_blank"} och hämta installationsprogrammet för Client Console. Sedan kan du installera den på den lokala datorn.

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

>[!NOTE]
>
>För kampanjversioner med klassisk version 8.4 kan Adobe Campaign-klientkonsolen begära proxyautentiseringsuppgifter två gånger under proxyautentiseringen. Detta beror på att Microsoft Edge Webview2 inte sparar proxyautentiseringsuppgifter i cache-/lösenordsarkivet, till skillnad från Internet Explorer.

## Bevilja åtkomst för användare{#grant-access}

Med Adobe Campaign kan du definiera och hantera de rättigheter som tilldelats de olika operatorerna.

Som kampanjadministratör ansvarar du för att skapa operatorerna och dela deras inloggningsuppgifter med användarna.

Läs mer om användare och hur du definierar deras behörigheter i [det här avsnittet](gs-permissions.md).


## Anslut till Campaign med din Adobe ID{#connect-ims}

Kampanjanvändare ansluter till Adobe Campaign-konsolen via sina Adobe ID via Adobe Identity Management System (IMS). De kan använda samma ID för alla Adobe-lösningar. Anslutningen sparas när du använder Adobe Campaign med andra lösningar.

Läs mer om Adobe IMS i [den här sidan](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

## Webbåtkomst{#web-access}

Vissa delar av programmet kan nås via en webbläsare via ett HTML-användargränssnitt: rapporter, leveransgodkännande, instansövervakning med mera.

Webbåtkomsten har ett gränssnitt som liknar konsolen men med en reducerad uppsättning funktioner.

För en viss operator visas en kampanj med följande alternativ i konsolen:

![](assets/campaign-from-console.png)

Med tillgång till webben kommer man främst att kunna se

![](assets/campaign-from-web.png)

Webbåtkomst används också i valideringsprocessen: -operatorer kan klicka på e-postmeddelandet med godkännandebegäran och ansluta till Campaign via webbläsaren för att validera eller avvisa ett leveransinnehåll eller en budget.

Om du vill komma åt Campaign-instansen från webben är URL:en:  `https://<your adobe campaign server>:<port number>/view/home`.
