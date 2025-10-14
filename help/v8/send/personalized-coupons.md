---
product: campaign
title: Personaliserade kuponger
description: Lär dig skapa och infoga skräddarsydda kuponger
feature: Personalization
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 96f1518f252be7ffa27ba8157b8a090bf4d4510d
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 1%

---

# Personaliserade kuponger{#personalized-coupons}

Genom att lägga till kuponger i leveranserna kan mottagarna få bättre värde för produkter och tjänster. Du kan använda Campaign-kupongmodulen för att skapa en uppsättning kuponger som du förväntar dig ska läggas till kommande marknadsföringserbjudanden. När du är redo att skapa en leverans tilldelar du tillämpliga kuponger. Eftersom kuponger är giltiga för en viss period är en tilldelad kupong unikt kopplad till leveransmeddelandet. Dessutom bekräftar Campaign att det finns tillräckligt många kuponger för antalet meddelanden innan leveransen skickas.

>[!AVAILABILITY]
>
>Kuponghantering är inte tillgängligt i Campaign v8 i samband med en företagsdistribution (FFDA). Läs mer i [Kampanjdokumentation v8](../architecture/enterprise-deployment.md).

Kuponghantering bygger på ett paket som måste installeras. Kontrollera **[!UICONTROL Administration > Configuration > Package management > Installed packages.]** för att bekräfta att du har kuponghantering

Kupongdata kan importeras och exporteras med CSV- och XML-format. [Läs mer](../../platform/using/get-started-data-import-export.md).

## Skapa en kupong {#creating-a-coupon}

Modulen Kuponghantering ger två alternativ när du skapar kuponger:

* **Anonym**: En allmän kupong för utvalda mottagare eller listor med mottagare.
* **Individual**: En anpassad kupong för utvalda mottagare.

Innan du följer stegen nedan bör du kontrollera vilken typ av kupong du vill skapa.

1. Gå till **[!UICONTROL Resources > Campaign management > Coupons]** i Campaign-trädet.

   ![](assets/deliv_coup_01.png)

1. Klicka på knappen **[!UICONTROL New]**.
1. Ange kupongnamnet i fältet **[!UICONTROL Label]**. En unik kod har angetts automatiskt i **[!UICONTROL Coupon code]**. Du kan behålla koden eller ange en ny.

   ![](assets/deliv_coup_02.png)

1. Välj **[!UICONTROL Start date]** och **[!UICONTROL End date]** om du vill ange den period under vilken kupongen är giltig.
1. I **[!UICONTROL Coupon type]** väljer du Anonym eller Enskild.

   **[!UICONTROL Anonymous coupons]** : En anonym kupong är identisk för alla mottagare. Bekräfta att Anonym är valt på menyn **Kupongtyp** och klicka på **Spara** för att generera kupongen.

   **[!UICONTROL Individual coupons]** : En enskild kupong kan anpassas ytterligare med ytterligare kupongkoder. Till exempel skapas en individuell kupong för försäljning i en sportutrustningsbutik. Listan över mottagare är dock lång och de delar inte samma entusiasm för en enda sport. Du kan lägga till kodnamn för den enskilda kupongen baserat på en sport (t.ex. fotboll, fotboll, baseboll osv.) och skicka varje kod till tillämpliga mottagare.

   1. När du väljer Individual visas en ny flik, Kuponger, längst ned till vänster. Gå till fliken **[!UICONTROL Coupons]** och klicka på **[!UICONTROL Add]**.
   1. Ange en unik kod för den enskilda kupongen när du uppmanas till det i popup-fönstret.
   1. Klicka på **[!UICONTROL Save]** för att generera kupongen.

   Mer information om fliken Kuponger finns i [Konfigurera enskilda kuponger](#configuring-individual-coupons).

   >[!NOTE]
   >
   >Enskilda kuponger kan importeras i grupp. Mer information om import och export finns i [det här avsnittet](../../platform/using/get-started-data-import-export.md).

### Konfigurera enskilda kuponger {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

Fliken Kuponger är bara tillgänglig med enskilda kuponger. När en kupong har associerats med en leverans visas följande information på fliken Kuponger:

* **[!UICONTROL Status]** : Kupongtillgänglighet.
* **[!UICONTROL Redeemed on]** : Datumet då kupongen löses in.
* **[!UICONTROL Channel]** : Den kanal som användes för att skicka kupongen.
* **[!UICONTROL Address]** : Mottagarnas e-postadresser.

Värden för **[!UICONTROL status]**, **[!UICONTROL channel]** och **[!UICONTROL address]** slutförs automatiskt. Värdena för **[!UICONTROL redeemed on]** har dock inte återställts av Campaign. De kan slutföras genom att en fil som innehåller information om kuponginlösen importeras.

## Infoga en kupong i en e-postleverans {#inserting-a-coupon-into-an-email-delivery}

I exemplet nedan skapas leveransen från hemsidan. Detaljerade instruktioner om hur du skapar en leverans finns i [det här avsnittet](about-email-channel.md). Du kan också lägga till en kupong i en leverans i ett arbetsflöde.

1. Gå till **[!UICONTROL Campaigns]** och välj **[!UICONTROL Deliveries]**.
1. Klicka på **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. Ange ett namn i **[!UICONTROL Label]** och klicka på **[!UICONTROL Continue]**.
1. Klicka på **[!UICONTROL To]** för att lägga till mottagare.
1. Klicka på **[!UICONTROL Add]** för att välja mottagare för leveransen. När du har valt mottagare klickar du på **[!UICONTROL Ok]** för att återgå till leveransen.

   ![](assets/deliv_coup_05.png)

1. Ange ett ämne och lägg till innehåll i meddelandet.

   ![](assets/deliv_coup_06.png)

1. Klicka på **[!UICONTROL Properties]** i verktygsfältet och välj fliken **[!UICONTROL Advanced]**.
1. Klicka på mappikonen för **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. Välj kupongen och klicka på **[!UICONTROL Ok]**. Klicka på **[!UICONTROL Ok]** igen.

   ![](assets/deliv_coup_08.png)

1. Klicka på meddelandet för att välja var du vill placera kupongen.

   ![](assets/deliv_coup_09.png)

1. Klicka på personaliseringsikonen och välj något av följande baserat på kupongtyp:

   * Anonym kupong: **[!UICONTROL Coupon > Coupon code]**

     ![](assets/deliv_coup_10.png)

   * Individuell kupong: **[!UICONTROL Coupon value > Coupon code]**

     ![](assets/deliv_coup_11.png)

     Kupongen infogas i meddelandet som kod i stället för det namn du tilldelade. Koden används i Campaign-objektets datamodell.

   ![](assets/deliv_coup_12.png)

1. Kör ett test för att bekräfta namnet som du tilldelade kupongen. Gå till fliken **[!UICONTROL Preview]** och klicka på **[!UICONTROL Test personalization]**. Välj en mottagare för testet.

   ![](assets/deliv_coup_13.png)

   Efter testet ska kupongen visas som det tilldelade namnet i stället för koden.

   ![](assets/deliv_coup_14.png)

1. Klicka på **[!UICONTROL Send]** i verktygsfältet och välj hur du vill skicka leveransen.

   ![](assets/deliv_coup_15.png)

1. Klicka på **[!UICONTROL Analyze]**. Om analysloggen bekräftar att det finns tillräckligt med kuponger för alla mottagare klickar du på **[!UICONTROL Confirm delivery]** för att skicka den.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>Instruktioner om hur du hanterar otillräckliga kuponger för en leverans finns i [Hantera otillräckliga kuponger](#managing-insufficient-coupons)

Så här bekräftar du att leveransen lyckades:

1. Gå till **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1. Klicka på fliken **[!UICONTROL Deliveries]**.

   ![](assets/deliv_coup_17.png)

   Statusen läses som **[!UICONTROL Finished]** för en slutförd leverans.

>[!NOTE]
>
>Som standard använder kuponghanteringsmodulen en **nms:recipient**-tabell. [Läs mer](../../configuration/using/about-data-model.md#default-recipient-table).
>
>Lär dig hur du använder en anpassad mottagartabell [på den här sidan](../../configuration/using/about-custom-recipient-table.md).

## Hantera otillräckliga kuponger {#managing-insufficient-coupons}

Leveransanalysen avbryts om det finns färre kuponger än meddelanden. I så fall kan du importera fler kuponger eller begränsa antalet meddelanden. Följ instruktionerna nedan om du vill begränsa antalet meddelanden.

1. Gå till e-postleveransfönstret.
1. Klicka på **[!UICONTROL To]**.
1. Gå till fliken **[!UICONTROL Select target]** i **[!UICONTROL Exclusions]**.

   ![](assets/deliv_coup_18.png)

1. Klicka på **[!UICONTROL Edit]** i avsnittet med undantagsinställningar.
1. Ange antalet meddelanden som du vill skicka i **[!UICONTROL Limit delivery to...messages]** och klicka på **[!UICONTROL Ok]**. Du kan skicka leveransen.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>När du hanterar ett begränsat antal kuponger kan du med ett leveransarbetsflöde dela upp leveransen baserat på dina kriterier. Det är ett bra alternativ om du vill skicka kuponger till en utvald population utan att begränsa målet.
