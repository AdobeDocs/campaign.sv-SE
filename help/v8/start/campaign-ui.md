---
title: Upptäck gränssnittet för Campaign
description: Lär dig hur du bläddrar i och använder användargränssnittet i Campaign
feature: Overview
role: User
level: Beginner
exl-id: a7846b95-7570-4dce-b3f4-d3cc23eefcac
source-git-commit: 9d5a2ca1e9858a727377b8afa6bdd7e3761c1b56
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 1%

---

# Upptäck användargränssnittet {#ui-client-console}

Du får åtkomst till Adobe Campaign via klientkonsolen eller webbgränssnittet. Du kan också använda API:er för att hantera data och utföra åtgärder på Campaign-plattformen.

>[!CAUTION]
>
>Den här dokumentationen fokuserar på användning av Campaign Client-konsolen. Om du använder användargränssnittet för Campaign-webben kan du läsa [den här dokumentationen](https://experienceleague.adobe.com/docs/campaign-web/v8/campaign-web-home.html?lang=sv-SE){target="_blank"}.

* **Klientkonsol** - Campaign-klientkonsolen är ett systemspecifikt program som kommunicerar med Adobe Campaign-programservern via standardInternetprotokoll som SOAP och HTTP. Campaign-klientkonsolen centraliserar alla funktioner och inställningar och kräver minimal bandbredd eftersom den är beroende av ett lokalt cacheminne. Kampanjklientkonsolen är utformad för enkel driftsättning och kan distribueras från en webbläsare, uppdateras automatiskt och kräver ingen specifik nätverkskonfiguration eftersom den bara genererar HTTP(S)-trafik. [Läs mer](#ui-access)

  Lär dig hur du installerar och konfigurerar Campaign-klientkonsolen i [det här avsnittet](../start/connect.md).

* **Webbanvändargränssnitt** - Från och med version 8.6.1 av Campaign v8 har du nu tillgång till en webbmiljö som är tillgänglig via det centrala Adobe Experience Cloud-användargränssnittet. Sedan kan du ansluta till Adobe Campaign från en webbläsare. Med det nya gränssnittet kan ni skapa, hantera och utföra viktiga marknadsföringsåtgärder. Alla Campaign-funktioner är dock inte tillgängliga. [Läs mer](#ac-web-ui).

  >[!AVAILABILITY]
  >
  >Användargränssnittet för Campaign-webben är bara tillgängligt för användare som ansluter till Adobe Campaign med sin Adobe ID. Läs mer om [Adobe Identity Management System (IMS)](https://helpx.adobe.com/se/enterprise/using/identity.html){target="_blank"}.
  >

* **Webbåtkomst** - Med Adobe Campaign webbåtkomstfunktioner kan du komma åt en delmängd av Campaign-funktionerna i en webbläsare med hjälp av ett HTML-användargränssnitt. Använd det här webbgränssnittet för att få åtkomst till rapporter, kontrollera och validera meddelanden, få åtkomst till kontrollpaneler med mera.  Läs mer om Campaign Web Access [i det här avsnittet](../start/connect.md#web-access).

* **API:er** - För att åtgärda fler användningsfall kan systemet anropas från externa program med hjälp av de webbtjänstAPI:er som exponeras via SOAP-protokollet. Läs mer om Campaign-API:er [på den här sidan](../dev/api.md).


## Arbeta med klientkonsolen {#ui-access}

Campaign-klientkonsolen är ett inbyggt program som kommunicerar med Adobe Campaign-programservern via standardprotokoll för Internet, som SOAP och HTTP. Campaign-klientkonsolen centraliserar alla funktioner och inställningar och kräver minimal bandbredd eftersom den är beroende av ett lokalt cacheminne. Kampanjklientkonsolen är utformad för enkel driftsättning och kan distribueras från en webbläsare, uppdateras automatiskt och kräver ingen specifik nätverkskonfiguration eftersom den bara genererar HTTP(S)-trafik.  [Läs mer om Campaign-klientkonsolen](../start/connect.md). Du kan växla till Campaign-webbgränssnittet från det dedikerade kortet på klientkonsolens startsida.

![](assets/web-ui.png)


>[!NOTE]
>
>Om det nya åtkomstkortet inte visas kontrollerar du att följande fält inte är tomma i ditt externa Adobe Experience Cloud-konto: **Server**, **Klient**, **Återanropsserver** och **Associationsmärke**.


Du kan också använda en webbläsare för att få tillgång till Campaign. I det här sammanhanget är bara en deluppsättning av Campaign-funktionerna tillgängliga. [Läs mer](#web-browser)

### Bläddra i gränssnittet {#ui-browse}

När du är ansluten till Campaign-klientkonsolen öppnar du hemsidan. Bläddra bland länkarna för att komma åt funktioner. Vilka funktioner som är tillgängliga i gränssnittet beror på vilka alternativ och behörigheter du har.

I den centrala delen av startsidan använder du länkar för att komma åt hjälpmaterial för Campaign, communityn och supportwebbplatsen. Använd de centrala korten för att bläddra i det nya användargränssnittet för Campaign-webben och i Campaign Control-panelen.

Bläddra bland flikarna i det övre avsnittet för att komma åt funktioner för Campaign-nyckeln:

![](assets/overview-home.png)

>[!NOTE]
>
>Listan över kärnfunktioner som du kan komma åt beror på dina behörigheter och din implementering.

För varje funktion kan du komma åt uppsättningen med nyckelfunktioner i avsnittet **[!UICONTROL Browsing]**. Med länken **[!UICONTROL More]** kan du komma åt alla andra komponenter.

Om du till exempel bläddrar till fliken **[!UICONTROL Profiles and targets]** kan du komma åt mottagarlistor, prenumerationstjänster, befintliga arbetsflöden för målinriktning och genvägar för att skapa alla dessa komponenter.

![](assets/overview-list.png)

När du markerar ett element på skärmen läses det in på en ny flik så att du enkelt kan bläddra i innehållet.

![](assets/new-tab.png)

### Skapa ett element {#create-an-element}

Använd genvägar i avsnittet **[!UICONTROL Create]** till vänster på skärmen för att lägga till nya element. Du kan också använda knappen **[!UICONTROL Create]** ovanför listan för att lägga till nya element i den aktuella listan.

Använd till exempel knappen **[!UICONTROL Create]** på leveranssidan för att skapa en ny leverans.

![](assets/new-recipient.png)

<!--
## Use a web browser {#web-browser}

You can also access a subset of Campaign capabilities through the a web browser.

The web access interface is similar to the console interface. From a browser, you can use the same navigation and display features as in the console, but you can perform only a reduced set of actions on campaigns. For example, you can view and cancel campaigns, but you cannot modify campaigns. 

[Learn more about Campaign web access](../start/connect.md#web-access).-->

### Access Campaign Explorer {#ac-explorer-ui}

Bläddra i Campaign Explorer för att få tillgång till alla funktioner och inställningar i Adobe Campaign.

![](assets/explorer.png)

På den här arbetsytan kan du komma åt Utforskarträdet och bläddra bland alla funktioner och alternativ.

* I det vänstra avsnittet visas Campaign Explorer-trädet där du kan bläddra bland alla komponenter och inställningar för instansen, baserat på dina behörigheter. Du kan lägga till och anpassa mappar enligt beskrivningen på [den här sidan](../audiences/folders-and-views.md).

* I det övre avsnittet visas en lista med poster i den aktuella mappen. Dessa listor är helt anpassningsbara. [Läs mer](../config/ui-settings.md)

* I det nedre avsnittet visas information om den valda posten.


## Kampanjwebbgränssnitt {#ac-web-ui}

Från och med version 8.6.1 av Campaign v8-klientkonsolanvändare har du nu tillgång till en webbmiljö som är tillgänglig via Adobe Experience Cloud centrala användargränssnitt. Experience Cloud är Adobe integrerade program, produkter och tjänster för digital marknadsföring. Från det intuitiva gränssnittet får du snabbt tillgång till dina molnprogram, produktfunktioner och tjänster.

![Adobe Campaign hemsida för webbanvändargränssnitt](assets/ac-web-home.png)

>[!AVAILABILITY]
>
>Användargränssnittet för Campaign-webben är bara tillgängligt för användare som ansluter till Adobe Campaign med sin Adobe ID. Läs mer om [Adobe Identity Management System (IMS)](https://helpx.adobe.com/se/enterprise/using/identity.html){target="_blank"}.
>

Läs mer om det nya webbanvändargränssnittet för Campaign i [den här dokumentationen](https://experienceleague.adobe.com/docs/campaign-web/v8/campaign-web-home.html?lang=sv-SE){target="_blank"}. Du kan även gå till sidan [Vanliga frågor och svar](https://experienceleague.adobe.com/sv/docs/campaign-web/v8/start/faq){target="_blank"} i dokumentationen för Campaign-webbanvändargränssnittet.

Ytterligare och avancerade funktioner, konfigurationer och inställningar är bara tillgängliga i klientkonsolen. Läs mer om funktioner som är tillgängliga i båda användargränssnitten [ i dokumentationen för användargränssnittet för Campaign ](https://experienceleague.adobe.com/docs/campaign-web/v8/start/capability-matrix.html?lang=sv-SE){target="_blank"}.


## Språk som stöds {#languages}

Vilka språk som stöds beror på användargränssnittet.

* För klientkonsolgränssnittet i Campaign v8 är följande språk som stöds:

   * Engelska (UK)
   * Engelska (USA)
   * Franska
   * Tyska
   * Japanska


  >[!CAUTION]
  >
  >Språket väljs under installationen och kan inte ändras efteråt.

* För språk som stöds för Campaign-webbgränssnittet [finns den här sidan](https://experienceleague.adobe.com/docs/campaign-web/v8/start/connect-to-campaign.html?lang=sv-SE#language-pref){target="_blank"}.


Språk påverkar datum- och tidsformat.

De största skillnaderna mellan amerikansk engelska och brittisk engelska är:

<table> 
 <thead> 
  <tr> 
   <th> Format<br /> </th> 
   <th> Engelska (USA)<br /> </th> 
   <th> Engelska (EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> Veckan börjar på söndag<br /> </td> 
   <td> Veckan börjar på måndag<br /> </td> 
  </tr> 
  <tr> 
   <td> Kort datum <br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>ex: 09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>ex: 25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> Kort datum med tiden <br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>ex: 09/25/2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>ex: 25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>
