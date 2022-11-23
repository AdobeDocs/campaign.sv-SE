---
title: Upptäck arbetsytan Campaign
description: Lär dig hur du bläddrar och använder arbetsytan i Campaign
feature: Overview
role: Admin, Developer, User
level: Beginner
exl-id: a7846b95-7570-4dce-b3f4-d3cc23eefcac
source-git-commit: eed3396584940f99a865eef2358887b6bf5c4936
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# Upptäck gränssnittet för Campaign

## Åtkomst till Campaign-gränssnittet{#ui-access}

Kampanjarbetsytan är tillgänglig via [Klientkonsol](../architecture/general-architecture.md).

Lär dig hur du installerar och konfigurerar Campaign Client Console i [det här avsnittet](../start/connect.md).

![](assets/home-page.png)

Du kan också använda en webbläsare för att få tillgång till Campaign. I det här sammanhanget är bara en deluppsättning av Campaign-funktionerna tillgängliga. [Läs mer](#web-browser)

## Bläddra i användargränssnittet{#ui-browse}

När du är ansluten till Campaign kommer du åt startsidan. Bläddra bland länkarna för att komma åt funktioner. Vilka funktioner som är tillgängliga i användargränssnittet beror på vilka alternativ och behörigheter du har.

I den centrala delen av startsidan använder du länkar för att komma åt hjälpmaterial för Campaign, communityn och supportwebbplatsen.

Använd flikarna i det övre avsnittet för att bläddra bland funktionerna i Campaign-nyckeln:

![](assets/overview-home.png)

>[!NOTE]
>
>Listan över kärnfunktioner som du kan komma åt beror på dina behörigheter och din implementering.

För varje funktion har du tillgång till de viktigaste funktionerna i **[!UICONTROL Browsing]** -avsnitt. The **[!UICONTROL More]** -länken kan du komma åt alla andra komponenter.

Om du till exempel bläddrar till **[!UICONTROL Profiles and targets]** kan du komma åt mottagarlistor, prenumerationstjänster, befintliga arbetsflöden för målinriktning och genvägar för att skapa alla dessa komponenter.

![](assets/overview-list.png)

När du markerar ett element på skärmen läses det in på en ny flik så att du enkelt kan bläddra i innehållet.

![](assets/new-tab.png)

## Skapa ett element {#create-an-element}

Använd genvägar i **[!UICONTROL Create]** till vänster på skärmen för att lägga till nya element. Du kan också använda **[!UICONTROL Create]** ovanför listan för att lägga till nya element i den aktuella listan.

På leveranssidan kan du till exempel använda **[!UICONTROL Create]** för att skapa en ny leverans.

![](assets/new-recipient.png)

## Använda en webbläsare {#web-browser}

Du kan även få tillgång till en delmängd av Campaign-funktionerna via en webbläsare.

Webbgränssnittet liknar konsolgränssnittet. Från en webbläsare kan du använda samma navigerings- och visningsfunktioner som i konsolen, men du kan bara utföra en reducerad uppsättning åtgärder på kampanjer. Du kan till exempel visa och avbryta kampanjer, men du kan inte ändra dem.

![](../assets/do-not-localize/glass.png) [Läs mer om Campaign-webbåtkomst](../start/connect.md#web-access).

## Access Campaign Explorer {#ac-explorer-ui}

Bläddra i Campaign Explorer för att få tillgång till alla funktioner och inställningar i Adobe Campaign.

![](assets/explorer.png)

På den här arbetsytan kan du komma åt Utforskarträdet och bläddra bland alla funktioner och alternativ.

I det vänstra avsnittet visas Campaign Explorer-trädet där du kan bläddra bland alla komponenter och inställningar för instansen, baserat på dina behörigheter.

I det övre avsnittet visas en lista med poster i den aktuella mappen. Dessa listor är helt anpassningsbara. [Läs mer](customize-ui.md)

I det nedre avsnittet visas information om den valda posten.


## Språk{#languages}

Användargränssnittet för Campaign v8 finns på följande språk:

* Engelska (UK)
* Engelska (USA)
* Franska
* Tyska
* Japanska

Språket väljs under installationen.

>[!CAUTION]
>
>Språket kan inte ändras efter att instansen har skapats.

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
   <td> Kort datum<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>ex: 09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>ex: 25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> Kort datum med tid<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>ex: 09/25/2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>ex: 25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>
