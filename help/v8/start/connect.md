---
title: Anslut till Campaign med klientkonsolen
description: Läs om hur du installerar Campaign-klientkonsolen på din dator och ansluter till Adobe Campaign
feature: Client Console
role: User
level: Beginner
exl-id: 176cc4f0-8827-4127-9f03-7d75ac8cf917
source-git-commit: 9df599ec0a898a1af16cb92d334d50375fde86ba
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 2%

---

# Anslut till Campaign med klientkonsolen{#gs-ac-connect}

Om du vill ansluta till Campaign med klientkonsolen måste du först installera och konfigurera den.

Innan du börjar måste du:

* Kontrollera system- och verktygskompatibiliteten med Adobe Campaign i [Kompatibilitetsmatris](compatibility-matrix.md)
* Hämta webbadressen till Campaign-servern
* Skapa din Adobe ID eller hämta inloggningsuppgifter från ditt företag
* Installera Microsoft Edge Webview2-miljön på datorn. [Läs mer](#webview)


>[!NOTE]
>
>Du kan även ansluta till Campaign-webbgränssnittet med en webbläsare. Läs mer om det nya webbgränssnittet för Campaign i [den här dokumentationen](https://experienceleague.adobe.com/docs/campaign-web/v8/campaign-web-home.html){target="_blank"}.


## Installera klientkonsolen{#download-ac-console}

### Microsoft Edge Webview2, runtime {#webview}

Från version 8.4 av Campaign Classic krävs installation av Microsoft Edge Webview 2 för alla installationer av klientkonsoler.

Webbvyn installeras som standard som en del av Windows 11. Om det inte redan finns på datorn uppmanas du att hämta det från installationsprogrammet för Campaign-klientkonsolen [Microsoft Developer website](http://www.adobe.com/go/acc-ms-webview2-runtime-download){target="_blank"}. Observera att nedladdningslänken inte fungerar i webbläsaren Internet Explorer 11 eftersom Microsoft inte längre stöder det. Kontrollera att du använder en annan webbläsare för att komma åt länken.

### Ladda ned konsolen{#install-ac-console}

När du använder Campaign för första gången måste du hämta klientkonsolen och installera den.

Det finns två alternativ för att hämta klientkonsolen:

1. Som kampanjadministratör ansluter du till Adobe [Programvarudistribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html){target="_blank"}.

1. Som slutanvändare distribuerar er Campaign-administratör klientkonsolen åt er och gör den tillgänglig via en dedikerad URL.

När installationsprogrammet för klientkonsolen har hämtats installerar du det på den lokala datorn.

Observera att du inte kan ändra klientkonsolens språk när den har installerats.

## Skapa din anslutning{#create-your-connection}

När klientkonsolen har installerats följer du stegen nedan för att skapa anslutningen till programservern:

1. Starta konsolen och bläddra genom länken i det högra hörnet för att komma åt skärmen för anslutningskonfiguration.

1. Klicka **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda [`https://<machine>.<domain>.com`](https://myserver.adobe.com) skriv-URL.

1. Markera alternativet **[!UICONTROL Connect with an Adobe ID]**.

1. Klicka **[!UICONTROL Ok]** för att spara inställningarna.

Du kan lägga till så många anslutningar som behövs för att ansluta till test-, scen- och produktionsmiljöer, till exempel.

>[!NOTE]
>
>The **[!UICONTROL Add]** knappen kan du skapa **[!UICONTROL folders]** för att ordna alla dina kontakter. Bara dra och släpp varje anslutning till en mapp.

## Logga in på Adobe Campaign {#logon-to-ac}

Kampanjanvändare ansluter till Adobe Campaign-konsolen via sina Adobe ID via Adobe Identity Management System (IMS). De kan använda samma ID för alla Adobe-lösningar. Anslutningen sparas när du använder Adobe Campaign med andra lösningar. Läs mer om Adobe IMS i [den här sidan](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

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

När datorn uppgraderas till en nyare version måste du uppdatera klientkonsolen till den versionen. Det här är en god praxis och för vissa versioner är den här uppgraderingen obligatorisk. I så fall anges det i [Versionsinformation](release-notes.md).

Som användare av hanterade Cloud Service distribuerar Adobe klientkonsolen åt dig. När du ansluter till den uppgraderade miljön uppmanas du att hämta den senaste klientkonsolversionen i ett popup-fönster. Du måste acceptera den här uppgraderingen och uppdatera klientkonsolen efter begäran.

>[!CAUTION]
>
>Adobe rekommenderar att du låter alternativet vara kvar **[!UICONTROL No longer ask this question]** avmarkerat för att säkerställa att du får en varning när en ny version av konsolen är tillgänglig. Om det här alternativet väljs informeras användaren inte om att en Console-uppgradering krävs.
>



## Bevilja åtkomst för användare{#grant-access}

Med Adobe Campaign kan du definiera och hantera de rättigheter som tilldelats de olika operatorerna.

Som kampanjadministratör ansvarar du för att skapa operatorerna och dela deras inloggningsuppgifter med användarna.

Läs mer om användare och hur du definierar deras behörigheter i [det här avsnittet](gs-permissions.md).


## Webbåtkomst{#web-access}

Vissa delar av programmet kan nås via en webbläsare via ett HTML-användargränssnitt: rapportering, leveransgodkännande, instansövervakning med mera.

Webbåtkomsten har ett gränssnitt som liknar konsolen men med en reducerad uppsättning funktioner.

För en viss operator visas till exempel en kampanj med följande alternativ i konsolen:

![](assets/campaign-from-console.png)

Med tillgång till webben kommer man främst att kunna se

![](assets/campaign-from-web.png)

Webbåtkomst används också i valideringsprocessen: operatorer kan klicka på e-postmeddelandet med godkännandebegäran och ansluta till Campaign via sin webbläsare för att validera eller avvisa ett leveransinnehåll eller en budget.

Om du vill komma åt Campaign-instansen från webben är URL:en:  `https://<your adobe campaign server>:<port number>/view/home`.
