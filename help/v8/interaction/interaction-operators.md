---
title: Operatorprofiler
description: Skapa operatorer för erbjudandehantering
feature: Interaction, Offers
role: User, Admin
level: Beginner
exl-id: 865ddb84-3373-45e0-849d-9d3c92455d22
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 4%

---

# Operatorprofiler {#operator-profiles}

Två typer av operatorer kan använda Campaign Interaction: **Erbjudandehanterare** och **Leveransansvariga**. Var och en av dem har specifika behörigheter och begränsningar. Läs mer om Campaign-operatorer och behörigheter i [den här sidan](../start/gs-permissions.md).

* The **[!UICONTROL Offer manager]** skapar och underhåller erbjudanden.
* The **[!UICONTROL Delivery manager]** godkänner och använder erbjudanden

## Skapa en Offer Manager-operator{#offer-manager}

1. Skapa en operator. [Läs mer](../start/manage-permissions.md#add-users)
1. Gå till **[!UICONTROL Groups and named rights]** fönster, klicka **[!UICONTROL Add]** och väljer **[!UICONTROL Offer manager]** grupp.

Behörigheter som är kopplade till erbjudandehanterare beskrivs [här](../start/manage-permissions.md#ootb-productprofiles)

## Skapa en leveranshanteraroperator {#delivery-manager}

1. Skapa en operator. [Läs mer](../start/manage-permissions.md#add-users)
1. Gå till **[!UICONTROL Groups and named rights]** flik, klicka **[!UICONTROL Add]** och väljer **[!UICONTROL Delivery manager]** grupp.

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
