---
title: Anslut till Campaign v8
description: Lär dig hur du ansluter till Adobe Campaign v8 och installerar konsolen på datorn för enklare åtkomst.
feature: Client Console
role: User
level: Beginner
exl-id: 176cc4f0-8827-4127-9f03-7d75ac8cf917
source-git-commit: 24ecf598d3d01f7fb59c70e1c8c81e9c086e653e
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 2%

---

# Anslut till Adobe Campaign v8{#gs-ac-connect}

Om du vill börja arbeta med Campaign måste du installera och konfigurera klientkonsolen.

Klientkonsolen är ett inbyggt program som kommunicerar med Adobe Campaign-programservern via vanliga Internetprotokoll, till exempel SOAP och HTTP. Campaign Client Console centraliserar alla funktioner och inställningar och kräver minimal bandbredd eftersom den är beroende av ett lokalt cacheminne. Campaign Client Console är utformad för enkel driftsättning och kan distribueras från en webbläsare, uppdateras automatiskt och kräver ingen specifik nätverkskonfiguration eftersom den bara genererar HTTP(S)-trafik.

Innan du börjar måste du:

* Kontrollera system- och verktygskompatibiliteten med Adobe Campaign i [kompatibilitetsmatrisen](compatibility-matrix.md)
* Hämta webbadressen till Campaign-servern
* Skapa din Adobe ID eller hämta inloggningsuppgifter från ditt företag
* Installera Microsoft Edge Webview2 runtime på datorn. [Läs mer](#webview)

## Installera klientkonsolen{#download-ac-console}

### Microsoft Edge Webview2, runtime {#webview}

Från Campaign Classic 8.4-versionen krävs installation av Microsoft Edge Webview 2 för alla installationer av klientkonsolen.

Webbvyn installeras som standard som en del av Windows 11. Om det inte redan finns på datorn uppmanas du att hämta det från [Microsoft Developer-webbplatsen](http://www.adobe.com/go/acc-ms-webview2-runtime-download){target="_blank"}. Observera att nedladdningslänken inte fungerar i webbläsaren Internet Explorer 11 eftersom Microsoft inte längre stöder det. Kontrollera att du använder en annan webbläsare för att komma åt länken.

### Ladda ned konsolen{#install-ac-console}

När du använder Campaign för första gången måste du hämta klientkonsolen och installera den.

Det finns två alternativ för att hämta klientkonsolen:

1. Som kampanjadministratör ansluter du till Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html){target="_blank"}.

1. Som slutanvändare distribuerar er Campaign-administratör klientkonsolen åt er och gör den tillgänglig via en dedikerad URL.

När installationsprogrammet för klientkonsolen har hämtats installerar du det på den lokala datorn.

Observera att du inte kan ändra klientkonsolens språk när den har installerats.

## Skapa din anslutning{#create-your-connection}

När klientkonsolen har installerats följer du stegen nedan för att skapa anslutningen till programservern:

1. Starta konsolen och bläddra genom länken i det högra hörnet för att komma åt skärmen för anslutningskonfiguration.

1. Klicka på **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda URL-typen `https://<machine>.<domain>.com`.

1. Markera alternativet **[!UICONTROL Connect with an Adobe ID]**.

1. Klicka på **[!UICONTROL Ok]** om du vill spara inställningarna.

Du kan lägga till så många anslutningar som behövs för att ansluta till test-, scen- och produktionsmiljöer, till exempel.

>[!NOTE]
>
>Med knappen **[!UICONTROL Add]** kan du skapa **[!UICONTROL folders]** för att ordna alla dina anslutningar. Bara dra och släpp varje anslutning till en mapp.

## Logga in på Adobe Campaign {#logon-to-ac}

Kampanjanvändare ansluter till Adobe Campaign-konsolen med sin Adobe ID via Adobe Identity Management System (IMS). De kan använda samma ID för alla Adobe-lösningar. Anslutningen sparas när du använder Adobe Campaign med andra lösningar. Läs mer om Adobe IMS på [den här sidan](https://helpx.adobe.com/se/enterprise/using/identity.html){target="_blank"}.

Så här loggar du in på en instans:

1. Starta konsolen och bläddra genom länken i det högra hörnet för att komma åt skärmen för anslutningskonfiguration.

   ![](assets/connectToCampaign.png)

1. Välj den Campaign-instans som du måste logga in på.

1. Klicka på **[!UICONTROL Ok]**.

Sedan kan du logga in på Campaign med din Adobe ID.

![](assets/adobeID.png)

>[!NOTE]
>
>Eftersom Microsoft Edge Webview2 inte sparar proxyautentiseringsuppgifter kan konsolen be dig autentisera två gånger vid den första anslutningen.

## Uppgradera din klientkonsol{#upgrade-ac-console}

När ditt system uppgraderas till en nyare version måste du uppdatera din klientkonsol till den versionen. Det här är en god praxis och för vissa versioner är den här uppgraderingen obligatorisk. I så fall nämns det i [versionsinformationen](release-notes.md).

Som användare av hanterade molntjänster distribuerar Adobe klientkonsolen åt dig. När du ansluter till den uppgraderade miljön uppmanas du att hämta den senaste versionen av klientkonsolen i ett popup-fönster. Du måste acceptera den här uppgraderingen och uppdatera klientkonsolen efter begäran.

>[!CAUTION]
>
>Adobe rekommenderar att du låter alternativet **[!UICONTROL No longer ask this question]** vara avmarkerat för att vara säker på att du får ett meddelande när en ny version av konsolen är tillgänglig. Om det här alternativet väljs informeras användaren inte om att en Console-uppgradering krävs.
>



## Bevilja åtkomst för användare{#grant-access}

Med Adobe Campaign kan du definiera och hantera de rättigheter som tilldelats de olika operatorerna.

Som kampanjadministratör ansvarar du för att skapa operatorerna och dela deras inloggningsuppgifter med användarna.

Läs mer om användare och hur du definierar deras behörigheter i [det här avsnittet](gs-permissions.md).


## Öppna Campaign med en webbläsare {#connect-web-ac}

### Webbgränssnitt {#connect-web-ui}

Från och med Campaign v8.6 har du tillgång till det nya **Campaign-webbgränssnittet** som är tillgängligt via den centrala Adobe Experience Cloud-miljön. Experience Cloud är Adobe integrerade program, produkter och tjänster för digital marknadsföring. Från det intuitiva gränssnittet får du snabbt tillgång till dina molnprogram, produktfunktioner och tjänster.

>[!AVAILABILITY]
>
>Användargränssnittet för Campaign-webben är bara tillgängligt för användare som ansluter till Adobe Campaign med sin Adobe ID. Läs mer om [Adobe Identity Management System (IMS)](https://helpx.adobe.com/se/enterprise/using/identity.html){target="_blank"}.
>

Lär dig hur du ansluter till Adobe Experience Cloud och kommer åt Adobe Campaign webbgränssnitt [på den här sidan](campaign-ui.md#ac-web-ui).

Läs mer i [Adobe Campaign webbgränssnittsdokumentation](https://experienceleague.adobe.com/sv/docs/campaign-web/v8/campaign-web-home){target="_blank"}.

### Webbåtkomst {#web-access}

Vissa delar av programmet kan nås via en webbläsare via ett HTML-gränssnitt: rapportering, leveransgodkännande, instansövervakning med mera.

Webbåtkomsten har ett gränssnitt som liknar konsolen men med en reducerad uppsättning funktioner.

För en viss operator visas till exempel en kampanj med följande alternativ i konsolen:

![](assets/campaign-from-console.png)

Med tillgång till webben kommer man främst att kunna se

![](assets/campaign-from-web.png)

Webbåtkomst används också i valideringsprocessen: operatorer kan klicka på e-postmeddelandet med godkännandebegäran och ansluta till Campaign via sin webbläsare för att validera eller avvisa ett leveransinnehåll eller en budget.

Om du vill komma åt Campaign-instansen från webben är URL:en: `https://<your adobe campaign server>:<port number>/view/home`.
