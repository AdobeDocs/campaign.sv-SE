---
product: Adobe Campaign
title: Lär dig hur du ansluter till Campaign v8
description: Anslut till Campaign v8
feature: Målgrupper
role: Data Engineer
level: Beginner
exl-id: 176cc4f0-8827-4127-9f03-7d75ac8cf917
source-git-commit: 03585f0c1514a80b0b0cba5a2d05fa3f44398405
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 4%

---

# Anslut till Adobe Campaign v8{#gs-ac-connect}

Campaign Client Console är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar.

Innan du börjar måste du:

* Kontrollera system- och verktygskompatibiliteten med Adobe Campaign i [kompatibilitetsmatrisen](compatibility-matrix.md)
* Hämta webbadressen till Campaign-servern
* Hämta inloggningsuppgifter

## Hämta och installera klientkonsolen

När du använder Campaign för första gången, eller om du behöver uppgradera till en nyare version, måste du hämta klientkonsolen och installera den.

Det finns två alternativ:

1. Som kampanjadministratör ansluter du till Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/encampaign.html) och hämtar installationsprogrammet för klientkonsolen. Sedan kan du installera den på den lokala datorn.

1. Som slutanvändare kan Adobe distribuera konsolen åt dig: När konsolen har uppdaterats uppmanas du att hämta den senaste versionen av klientkonsolen i ett popup-fönster.

>[!CAUTION]
>
>Adobe rekommenderar att du låter alternativet **[!UICONTROL No longer ask this question]** vara avmarkerat för att se till att alla användare får meddelanden när en ny version av konsolen är tillgänglig.  Om det här alternativet väljs informeras användaren inte om nya tillgängliga versioner.

## Skapa din anslutning

När klientkonsolen har installerats nyligen följer du stegen nedan för att skapa anslutningen till programservern:

1. Starta konsolen från Windows **[!UICONTROL Start]**-menyn i **Adobe Campaign**-programgruppen.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

1. Klicka på **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda URL-adressen [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

1. Om Adobe Identity Management System (IMS) är konfigurerat för din organisation kontrollerar du alternativet **[!UICONTROL Connect with an Adobe ID]**.

1. Klicka på **[!UICONTROL Ok]** för att spara inställningarna.

Du kan lägga till så många anslutningar som behövs för att ansluta till test-, scen- och produktionsmiljöer, till exempel.

>[!NOTE]
>
>Med knappen **[!UICONTROL Add]** kan du skapa **[!UICONTROL folders]** för att ordna alla dina anslutningar. Bara dra och släpp varje anslutning till en mapp.

## Logga in på Adobe Campaign

Så här loggar du in på en befintlig instans:

1. Starta konsolen från Windows **[!UICONTROL Start]**-menyn i **Adobe Campaign**-programgruppen.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

1. Välj den Campaign-instans som du måste logga in på.

1. Klicka på **[!UICONTROL Ok]**.

1. Ange dina inloggningsuppgifter och klicka på **[!UICONTROL LOG IN]**.

   ![](assets/sign-in-v8.png)

Beroende på din konfiguration kan dina autentiseringsuppgifter vara:

* tillhandahålls av er Campaign-administratör som beviljade er åtkomst
* din Adobe ID

## Bevilja åtkomst för användare

Med Adobe Campaign kan du definiera och hantera de rättigheter som tilldelats de olika operatorerna. Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar:

* Tillgång till vissa funktioner (via namngivna rättigheter).
* Tillgång till vissa element
* Skapa, ändra och/eller ta bort element (leverans, kontakter, kampanjer, grupper osv.).

Läs mer om användare och hur du definierar deras behörigheter i [det här avsnittet](permissions.md).

Som kampanjadministratör ansvarar du för att skapa operatorerna och dela deras inloggningsuppgifter med användarna.

## Anslut till Campaign med din Adobe ID{#connect-ims}

Kampanjanvändare kan ansluta till Adobe Campaign-konsolen med sin Adobe ID via Adobe Identity Management System (IMS). Implementeringen har följande fördelar:

* Samma ID kan användas för alla Experience Cloud-lösningar.
* Anslutningen sparas när Adobe Campaign används med olika integreringar.
* Starkare lösenordshanteringsprincip.
* Använda Federated ID-konton (extern ID-leverantör).

[!DNL :speech_balloon:] Som användare av Managed Cloud Services  [kontaktar du ](campaign-faq.md#support) Adobe implementera Adobe IMS med Campaign.

## Anslut till Campaign med din LDAP-inloggning

Adobe Campaign kan konfigureras så att användaren kommer åt plattformen via sin LDAP-autentisering.

[!DNL :speech_balloon:] Som användare av hanterade Cloud Services  [kontaktar du ](campaign-faq.md#support) Adobe för att konfigurera LDAP-integrering med Campaign.


## Webbåtkomst{#web-access}

Vissa delar av programmet kan nås via en enkel webbläsare via ett HTML-användargränssnitt: Kampanjpanel, kubrapportering, instansövervakning med mera.

[!DNL :arrow_upper_right:] Läs mer om webbåtkomst i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/campaign-workspace/adobe-campaign-workspace.html?lang=en#console-and-web-access)

Webbåtkomsten har ett gränssnitt som liknar konsolen, men med en reducerad uppsättning funktioner.

För en viss operator visas till exempel en kampanj med följande alternativ i konsolen:

![](assets/campaign-from-console.png)

Med tillgång till webben kommer man främst att kunna se

![](assets/campaign-from-web.png)

Webbåtkomst används också i valideringsprocessen: -operatorer kan klicka på e-postmeddelandet med godkännandebegäran och ansluta till Campaign via webbläsaren för att validera eller avvisa ett leveransinnehåll eller en budget.

[!DNL :arrow_upper_right:] Läs om hur du konfigurerar och hanterar godkännanden i dokumentationen för  [Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/orchestrate-campaigns/marketing-campaign-approval.html?lang=en#orchestrating-campaigns)
