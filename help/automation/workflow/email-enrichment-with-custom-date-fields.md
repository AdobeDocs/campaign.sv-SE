---
product: campaign
title: E-postberikande med anpassade datumfält
description: Lär dig att förbättra e-postmeddelanden med anpassade datumfält
feature: Workflows
role: User, Developer
version: Campaign v8, Campaign Classic v7
exl-id: 2bb3443c-37d8-4d49-9be1-81217f56823c
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---

# E-postberikande med anpassade datumfält{#email-enrichment-with-custom-date-fields}



I det här exemplet vill vi skicka ett e-postmeddelande med anpassade datafält till mottagare som kommer att fira sina födelsedagar den här månaden. E-postmeddelandet innehåller en kupong som är giltig en vecka före och efter deras födelsedagar.

Vi måste rikta in oss på mottagare från en lista som ska fira sina födelsedagar den här månaden med en **[!UICONTROL Split]**-aktivitet. När du sedan använder aktiviteten **[!UICONTROL Enrichment]** fungerar det anpassade datafältet som giltighetsdatum i e-postmeddelandet för kundens specialerbjudande.

![](assets/uc_enrichment.png)

Så här skapar du det här exemplet:

1. Dra och släpp en **[!UICONTROL Read list]**-aktivitet på fliken **[!UICONTROL Targeting and workflows]** i kampanjen för att ange mottagare som mål.
1. Listan som ska bearbetas kan anges explicit, beräknas av ett skript eller lokaliseras dynamiskt enligt de alternativ som valts och parametrar som definierats här.

   ![](assets/uc_enrichment_1.png)

1. Lägg till en **[!UICONTROL Split]**-aktivitet för att skilja mottagare som ska fira sina födelsedagar den här månaden från andra mottagare.
1. Om du vill dela listan väljer du **[!UICONTROL Add a filtering condition on the inbound population]** i kategorin **[!UICONTROL Filtering of selected records]**. Klicka sedan på **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. Välj **[!UICONTROL Filtering conditions]** och klicka sedan på knappen **[!UICONTROL Edit expression]** för att filtrera månaden för mottagarens födelsedag.

   ![](assets/uc_enrichment_3.png)

1. Klicka på **[!UICONTROL Advanced Selection]** och sedan på **[!UICONTROL Edit the formula using an expression]** och lägg till följande uttryck: Month(@bornDate).
1. Markera **[!UICONTROL equal to]** i kolumnen **[!UICONTROL Operator]**.
1. Du kan filtrera villkoret ytterligare genom att lägga till månaden **[!UICONTROL Value]** för det aktuella datumet: Month(GetDate()).

   Detta skickar en fråga till mottagare vars födelsedag motsvarar den aktuella månaden.

   ![](assets/uc_enrichment_4.png)

1. Klicka på **[!UICONTROL Finish]**. Klicka sedan på **[!UICONTROL Generate complement]** i kategorin **[!UICONTROL Results]** på fliken **[!UICONTROL General]** i din **[!UICONTROL Split]**-aktivitet.

   Med resultatet **[!UICONTROL Complement]** kan du lägga till en leveransaktivitet eller uppdatera en lista. Här har vi just lagt till en **[!UICONTROL End]**-aktivitet.

   ![](assets/uc_enrichment_6.png)

Du måste nu konfigurera din **[!UICONTROL Enrichment]**-aktivitet:

1. Lägg till en **[!UICONTROL Enrichment]**-aktivitet efter din delmängd för att lägga till dina anpassade datumfält.

   ![](assets/uc_enrichment_7.png)

1. Öppna din **[!UICONTROL Enrichment]**-aktivitet. Klicka på **[!UICONTROL Add data]** i kategorin **[!UICONTROL Complementary information]**.

   ![](assets/uc_enrichment_8.png)

1. Välj **[!UICONTROL Data linked to the filtering dimension]** och sedan **[!UICONTROL Data of the filtering dimension]**.
1. Klicka på knappen **[!UICONTROL Add]**.

   ![](assets/uc_enrichment_9.png)

1. Lägg till en **[!UICONTROL Label]**. Klicka sedan på **[!UICONTROL Edit expression]** i kolumnen **[!UICONTROL Expression]**.

   ![](assets/uc_enrichment_10.png)

1. Först måste vi rikta in veckan före födelsedatumet som **Giltighetens startdatum** med följande **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Om du sedan vill skapa det anpassade datumfältet **Giltighetens slutdatum**, som är målveckan efter födelsedatumet, måste du lägga till **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`.

   Du kan lägga till en etikett i uttrycket.

   ![](assets/uc_enrichment_12.png)

1. Klicka på **[!UICONTROL Ok]**. Din berikning är nu klar.

Efter din **[!UICONTROL Enrichment]**-aktivitet kan du lägga till en leverans. I det här fallet har vi lagt till en e-postleverans för att skicka ett specialerbjudande med giltighetsdatum till kunder som firar sina födelsedagar den här månaden.

1. Dra och släpp en **[!UICONTROL Email delivery]**-aktivitet efter din **[!UICONTROL Enrichment]**-aktivitet.

   ![](assets/uc_enrichment_15.png)

1. Dubbelklicka på din **[!UICONTROL Email delivery]**-aktivitet för att börja anpassa leveransen.
1. Lägg till en **[!UICONTROL Label]** i leveransen och klicka på **[!UICONTROL Continue]**.
1. Klicka på **[!UICONTROL Save]** för att skapa din e-postleverans.
1. Kontrollera på fliken **[!UICONTROL Approval]** i e-postleveransen **[!UICONTROL Properties]** att **[!UICONTROL Confirm delivery before sending option]** är markerad.

   Starta sedan arbetsflödet för att berika den utgående övergången med målinformationen.

   ![](assets/uc_enrichment_18.png)

Nu kan du börja designa din e-postleverans med de anpassade datumfälten som skapades i aktiviteten **[!UICONTROL Enrichment]**.

1. Dubbelklicka på din **[!UICONTROL Email delivery]**-aktivitet.
1. Lägg till måltilläggen i e-postmeddelandet. Den ska finnas i följande uttryck för att konfigurera formatet för dina giltighetsdatum:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Klicka på ![](assets/uc_enrichment_16.png). Välj **[!UICONTROL Target extension]** och sedan de tidigare anpassade giltighetsdatumen med aktiviteten **[!UICONTROL Enrichment]** för att lägga till tillägget i formatetDate-uttrycket.

   ![](assets/uc_enrichment_19.png)

1. Konfigurera e-postinnehållet efter behov.

   ![](assets/uc_enrichment_17.png)

1. Förhandsgranska din e-post för att kontrollera om dina anpassade datumfält är korrekt konfigurerade

   ![](assets/uc_enrichment_20.png)

Din e-postadress är nu klar. Du kan börja skicka dina korrektur och bekräfta leveransen för att skicka dina födelsedag via e-post.
