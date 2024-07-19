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
ht-degree: 2%

---

# Operatorprofiler {#operator-profiles}

Två typer av operatorer kan använda kampanjinteraktion: **Erbjudandehanterare** och **Leveransansvariga**. Var och en av dem har specifika behörigheter och begränsningar. Läs mer om Campaign-operatorer och behörigheter på [den här sidan](../start/gs-permissions.md).

* **[!UICONTROL Offer manager]** skapar och underhåller erbjudanden.
* **[!UICONTROL Delivery manager]** godkänner och använder erbjudanden

## Skapa en Offer Manager-operator{#offer-manager}

1. Skapa en operator. [Läs mer](../start/manage-permissions.md#add-users)
1. Bläddra till fönstret **[!UICONTROL Groups and named rights]**, klicka på **[!UICONTROL Add]** och markera gruppen **[!UICONTROL Offer manager]**.

Behörigheter som är associerade med erbjudandehanterare beskrivs [här](../start/manage-permissions.md#ootb-productprofiles)

## Skapa en leveranshanteraroperator {#delivery-manager}

1. Skapa en operator. [Läs mer](../start/manage-permissions.md#add-users)
1. Bläddra till fliken **[!UICONTROL Groups and named rights]**, klicka på **[!UICONTROL Add]** och markera gruppen **[!UICONTROL Delivery manager]**.

De rättigheter som tilldelats leveransansvariga gör det möjligt för dem att utföra följande uppgifter:

* Visa **[!UICONTROL Live]**-miljöer.
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
   <td> <strong>Erbjudandehanteraren (designmiljö)</strong><br /> </td> 
   <td> <strong>Erbjudandehanteraren (Live-miljö)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trädstrukturnivå</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erbjudanden som redigeras / Live-erbjudanden <br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Mottagare - miljö <br /> </td> 
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
   <td> fördefinierade erbjudandefilter<br /> </td> 
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
   <td> Erbjud katalog <br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekategori <br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Leveranshanteraren (designmiljö)</strong><br /> </td> 
   <td> <strong>Leveranshanteraren (Live-kuvert.)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trädstrukturnivå</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erbjudanden som redigeras / Live-erbjudanden <br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Mottagare - miljö <br /> </td> 
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
   <td> fördefinierade erbjudandefilter<br /> </td> 
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
   <td> Erbjud katalog <br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekategori <br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
 </tbody> 
</table>
