---
product: Adobe Campaign
title: Kampanjinteraktionsoperatorer
description: Skapa operatorer för erbjudandehantering
feature: Översikt
role: Data Engineer
level: Beginner
source-git-commit: 5363950db5092bc7e0a72a0823db1132a17dda33
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---


# Operatorprofiler {#operator-profiles}

Två typer av operatorer kan använda Campaign Interaction: **Erbjudandehanterare** och **Leveranshanterare**. Var och en av dem har specifika behörigheter och begränsningar. Läs mer om Campaign-operatorer och -behörigheter i [den här sidan](../start/permissions.md).

* **[!UICONTROL Offer manager]** skapar och underhåller erbjudanden.
* **[!UICONTROL Delivery manager]** godkänner och använder erbjudanden

## Skapa en Offer Manager-operator{#offer-manager}

1. Skapa en ny operator.

   [!DNL :arrow_upper_right:] Steg för att skapa en operator i Campaign finns i dokumentationen för  [Campaign Classic v7.](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-operators.html)

1. Gå till fönstret **[!UICONTROL Groups and named rights]**, klicka på **[!UICONTROL Add]** och välj gruppen **[!UICONTROL Offer manager]**.

Med de rättigheter som tilldelats till erbjudandehanteraren kan de utföra följande uppgifter:

* Ändra **[!UICONTROL Design]**-miljöer.
* Visa **[!UICONTROL Live]**-miljöer.
* Konfigurera administrationsfunktioner (fördefinierade blanksteg och filter).
* Skapa och ändra kategorier.
* Skapa erbjudanden.
* Konfigurera berättigande för erbjudanden.
* Godkänn erbjudanden.

Observera att om erbjudanden används i ett arbetsflöde måste operatorn läggas till i operatorgruppen **[!UICONTROL Administrator]** eller **[!UICONTROL Offer managers]** för att arbetsflödet ska kunna köras.

>[!NOTE]
>
>En **erbjudandehanterare** kan bara godkänna ett erbjudande om ingen granskare har angetts, eller om han/hon har deklarerats som granskare i erbjudandemallen som erbjudandet baserades på.

## Skapa en leveranshanteraroperator {#delivery-manager}

1. Skapa en ny operator.

   [!DNL :arrow_upper_right:] Steg för att skapa en operator i Campaign finns i dokumentationen för  [Campaign Classic v7.](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/permissions/access-management-operators.html)

1. Gå till fönstret **[!UICONTROL Groups and named rights]**, klicka på **[!UICONTROL Add]** och välj gruppen **[!UICONTROL Delivery manager]**.

De rättigheter som tilldelats leveransansvarig är/gör det möjligt för dem att utföra följande uppgifter:

* Visa **[!UICONTROL Live]**-miljöer.
* Visa och ändra erbjudandekategorier.
* Godkänn erbjudanden om han/hon har angetts som en av dess granskare.

   >[!NOTE]
   >
   >En **leveranshanterare** kan bara godkänna ett erbjudande om han/hon har deklarerats som granskare under konfigurationen av erbjudandet.

## Behörighetsmatris per interaktionsoperator {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Erbjudandehanterare (Design-miljö)</strong><br /> </td> 
   <td> <strong>Erbjudandehanterare (Live-miljö)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trädstrukturnivå</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erbjudanden som redigeras / Live-erbjudanden<br /> </td> 
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
   <td> Fördefinierade erbjudandefilter<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologi<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Regler för typologi<br /> </td> 
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
   <td> Erbjudanden som redigeras / Live-erbjudanden<br /> </td> 
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
   <td> Fördefinierade erbjudandefilter<br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologi<br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Regler för typologi<br /> </td> 
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
