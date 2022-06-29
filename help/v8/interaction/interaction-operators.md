---
title: Operatorprofiler
description: Skapa operatorer för erbjudandehantering
feature: Interaction, Offers
role: Data Engineer
level: Beginner
exl-id: 865ddb84-3373-45e0-849d-9d3c92455d22
source-git-commit: 8eb92dd1cacc321fc79ac4480a791690fc18511c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Operatorprofiler {#operator-profiles}

Två typer av operatorer kan använda Campaign Interaction: **Erbjudandeansvariga** och **Leveransansvariga**. Var och en av dem har specifika behörigheter och begränsningar. Läs mer om Campaign-operatorer och behörigheter i [den här sidan](../start/permissions.md).

* The **[!UICONTROL Offer manager]** skapar och underhåller erbjudanden.
* The **[!UICONTROL Delivery manager]** godkänner och använder erbjudanden

## Skapa en Offer Manager-operator{#offer-manager}

1. Skapa en operator.

   ![](../assets/do-not-localize/book.png) Steg för att skapa en operator i Campaign beskrivs i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-operators.html)

1. Gå till **[!UICONTROL Groups and named rights]** fönster, klicka **[!UICONTROL Add]** och väljer **[!UICONTROL Offer manager]** grupp.

Med de rättigheter som tilldelats till erbjudandehanteraren kan de utföra följande uppgifter:

* Ändra **[!UICONTROL Design]** miljöer.
* Visa **[!UICONTROL Live]** miljöer.
* Konfigurera administrationsfunktioner (fördefinierade blanksteg och filter).
* Skapa och ändra kategorier.
* Skapa erbjudanden.
* Konfigurera berättigande för erbjudanden.
* Godkänn erbjudanden.

Om erbjudanden används i ett arbetsflöde måste operatorn läggas till i **[!UICONTROL Administrator]** eller **[!UICONTROL Offer managers]** operatörsgrupp för att köra arbetsflödet.

>[!NOTE]
>
>**Erbjudandeansvariga** kan bara godkänna ett erbjudande om ingen granskare har angetts, eller om de har deklarerats som granskare i erbjudandemallen.

## Skapa en leveranshanteraroperator {#delivery-manager}

1. Skapa en operator.

   ![](../assets/do-not-localize/book.png) Steg för att skapa en operator i Campaign beskrivs i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-operators.html)

1. Gå till **[!UICONTROL Groups and named rights]** fönster, klicka **[!UICONTROL Add]** och väljer **[!UICONTROL Delivery manager]** grupp.

De rättigheter som tilldelats leveransansvariga gör det möjligt för dem att utföra följande uppgifter:

* Visa **[!UICONTROL Live]** miljöer.
* Visa och ändra erbjudandekategorier.
* Godkänn erbjudanden om de är deras granskare.

   >[!NOTE]
   >
   >**Leveransansvariga** kan bara godkänna ett erbjudande om de har deklarerats som granskare i erbjudandekonfigurationen.

## Behörighetsmatris per interaktionsoperator {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Erbjudandehanterare (designmiljö)</strong><br /> </td> 
   <td> <strong>Erbjudandehanterare (Live-miljö)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trädstrukturnivå</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erbjudanden som redigeras/Live-erbjudanden<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Mottagare - miljö<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Blanksteg<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> fördefinierade filter för erbjudanden<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologi<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologiregler<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekatalog<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekategori<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Delivery manager (Design-kuvert)</strong><br /> </td> 
   <td> <strong>Delivery manager (Live-kuvert)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trädstrukturnivå</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erbjudanden som redigeras/Live-erbjudanden<br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Mottagare - miljö<br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Blanksteg<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> fördefinierade filter för erbjudanden<br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologi<br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologiregler<br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekatalog<br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekategori<br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
 </tbody> 
</table>
