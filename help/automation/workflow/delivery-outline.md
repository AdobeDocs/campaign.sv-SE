---
product: campaign
title: Leveransbeskrivning
description: Läs mer om arbetsflödesaktiviteten Disposition
feature: Workflows, Targeting Activity
role: User
exl-id: 3c06b329-b2d8-4ac8-ab9b-3ab3e525d109
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 1%

---

# Leveransbeskrivning{#delivery-outline}

Med **leveransdispositionen** kan du använda en disposition i ett kampanjarbetsflöde. Dispositionen måste ha skapats i kampanjen i förväg.

Om du vill konfigurera aktiviteten behöver du bara markera den disposition du vill ha samt det planerade kontaktdatumet. Du kan lägga till filtreringsregler genom att lägga till typologier eller typologiregler.

## Exempel: Infoga ett erbjudande via en leveransdisposition {#example--inserting-an-offer-via-a-delivery-outline}

Med aktiviteten **leveransdisposition**, som är tillgänglig i kampanjarbetsflödena, kan du presentera erbjudanden som refereras i en leveransdisposition från den pågående kampanjen.

>[!NOTE]
>
>Paketet **Interaction** måste vara installerat.

1. Lägg till en dispositionsaktivitet för leverans i ett arbetsflöde innan du lägger till en leveransaktivitet.
1. I dispositionsaktiviteten för leverans anger du den disposition du vill använda.
1. Fyll i de tillgängliga fälten efter leverans.
1. Det finns två möjliga fall:

   * Om du vill ringa erbjudandemotorn markerar du kryssrutan **[!UICONTROL Restrict the number of propositions selected]**. Ange erbjudandeutrymme och antalet offerter som ska presenteras i leveransen.

     Anbudsvikterna och reglerna för rätt till uppgradering kommer att beaktas av erbjudandemotorn.

   * Om du inte markerar kryssrutan visas alla erbjudanden i leveransdispositionen utan att du behöver ringa till erbjudandemotorn.

   Förhandsgranskningen tar hänsyn till antalet erbjudanden som anges i leveransen. När du kör ett arbetsflöde är det numret som anges i leveransdispositionen som beaktas.

   ![](assets/int_compo_offre_wf1.png)
