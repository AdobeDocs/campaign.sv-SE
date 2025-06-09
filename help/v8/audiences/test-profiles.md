---
title: Skapa testprofiler i Campaign
description: Lär dig skapa och hantera testprofiler i Adobe Campaign
feature: Audiences, Profiles, Seed Address, Proofs
role: User
level: Beginner
exl-id: 878b5963-100c-4dd7-97a0-c59a62c493b1
source-git-commit: e4f6c70ecdcf7414b5f49a43933cfd1c967a0905
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 0%

---

# Skapa och hantera testprofiler {#create-test-profiles}

## Vad är en startadress? {#gs-seeds}

Testprofiler skapas som dirigerade adresser. De används för målmottagare som inte matchar de definierade målvillkoren. Med dirigerade adresser kan du förhandsgranska och testa personaliseringen och återgivningen innan du skickar leveransen genom att skicka korrektur.

Startadresserna har följande fördelar:

* Slumpmässig ersättning av fält med data från mottagarprofiler: Detta gör att du bara kan ange e-postadressen, till exempel i avsnittet dirigerad adress, och låta Campaign automatiskt fylla i de andra fälten från profilen. Läs mer i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-seed-addresses/use-case--selecting-seed-addresses-on-criteria.html?lang=en){target="_blank"}.
* När du använder ett arbetsflöde med datahanteringsfunktioner kan ytterligare data som bearbetas i leveranser anges på dirigeringsadressnivå för att framtvinga värden: detta innebär att slumpmässiga värden ersätts.
* Seed-adresser exkluderas automatiskt från rapporter om följande leveransstatistik: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Seed-adresser läggs till i målet för leveranser genom att importeras eller skapas direkt i leveransen eller kampanjen.

>[!NOTE]
>
>Seed-adresser skapas inte i mottagartabellen, utan i en separat tabell. Om du utökar mottagartabellen med nya data måste du utöka både dirigerade adresstabellen och samma data. I annat fall kommer de utökade fälten inte att beaktas för dirigerade adresser.
>
>Ett exempel på hur du utökar startadresstabellen finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-seed-addresses/use-case--selecting-seed-addresses-on-criteria.html){target="_blank"}.

## Skapa dirigerade adresser

Seed-adresser hanteras inte via standardprofiler och standardmål, men i en dedikerad nod i Adobe Campaign Explorer: **[!UICONTROL Resources > Campaign management > Seed addresses]**. Du kan skapa undermappar för att ordna startadresserna.

Med Adobe Campaign kan ni också skapa mallar för dirigerade adresser som importeras till leveranser eller kampanjer och som anpassas utifrån de specifika behoven hos de aktuella leveranserna och kampanjerna. Se [Skapa dirigerade adressmallar](#creating-seed-address-templates).

### Definiera adresser {#defining-addresses}

Så här skapar du dirigerade adresser:

1. Klicka på knappen **[!UICONTROL New]** ovanför listan med dirigerade adresser.
1. Ange data som är länkade till adressen i matchande fält på fliken **[!UICONTROL Recipient]**. De tillgängliga fälten motsvarar standardfälten i leveransmottagarnas profiler (nms:mottagartabell): namn, förnamn, e-post osv.

   >[!NOTE]
   >
   >Adressetiketten fylls automatiskt i med det efternamn och förnamn som du har definierat.
   >
   >Du behöver inte ange alla fält på varje flik när du skapar en startadress. Personaliseringselement som saknas anges slumpmässigt under leveransanalysen.

1. På fliken **[!UICONTROL Address fields]** anger du de värden som ska infogas i leveransloggarna under analysfasen i tabellen **[!UICONTROL nms:broadLog]**.

1. På fliken **[!UICONTROL Additional data]** anger du de personaliseringsdata som används för leveranser som har skapats i arbetsflödena för datahantering och som du vill tilldela ett specifikt värde till.

   Kontrollera att ytterligare måldata har definierats med ett alias som börjar med @ i arbetsflödesaktiviteten **[!UICONTROL Enrichment]**. Annars kan du inte använda dem på rätt sätt med dina dirigerade adresser i leveransaktiviteten.

### Skapa mallar för dirigerade adresser {#creating-seed-address-templates}

Du kan skapa adressmallar som kan importeras och ändras för varje leverans. Processen är densamma som när du definierar en ny dirigeringsadress. Den enda skillnaden är att adresser för startadressmallar måste lagras i en mapp av typen &quot;Mall&quot;.

### Säljadresser för direktreklam {#direct-mail-seed-addresses}

För [direkta e-postleveranser](../send/direct-mail.md) läggs startadresser till under extraheringen och blandas i utdatadokumentet.

För direktreklam måste extraheringsfilformatet uppfylla följande begränsningar:

* Det får inte använda alternativet **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.

* Om elementsamlingar extraheras kommer dessa fält att ha ett tomt värde för startadresserna, såvida inte alternativet **[!UICONTROL Single row (expert user)]** har valts.

## Lägga till dirigerade adresser i en leverans{#seed-addresses-in-a-delivery}

Om du vill lägga till specifika dirigerade adresser för en leverans klickar du på länken **[!UICONTROL To]** och väljer fliken **[!UICONTROL Seed addresses]**.

Det finns tre möjliga insättningslägen:

1. Ange enskilda dirigeringsadresser.  Det gör du genom att klicka på knappen **[!UICONTROL Add]** och definiera innehållet i adressfälten. Upprepa för varje adress.

1. Importera [startadressmallar](#creating-seed-address-template) och anpassa dem efter dina behov. Om du vill göra det klickar du på länken **[!UICONTROL Import seed templates...]** och väljer den mapp som innehåller adressmallarna.

   När de har lagts till kan du dubbelklicka på dem eller klicka på knappen **[!UICONTROL Detail...]** för att anpassa innehållet i varje adress.

1. Skapa ett villkor för att dynamiskt markera de kontrolladresser som ska infogas. Det gör du genom att klicka på länken **[!UICONTROL Edit the dynamic condition...]** och sedan ange parametrar för val av dirigeringsadress. Du kan t.ex. inkludera alla dirigerade adresser i en viss mapp eller dirigerade adresser som tillhör en viss avdelning i organisationen.

   Ett exempel på detta finns i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/using-seed-addresses/use-case--selecting-seed-addresses-on-criteria.html){target="_blank"}.

För leveranser kan du också anpassa hur adresser infogas i extraheringsfilen. Som standard infogas de i utdatafilens sorteringsordning, men du kan välja att infoga dem i slutet eller början av filen, eller slumpmässigt bland mottagarna av huvudmålet.

## Lägga till dirigerade adresser i en kampanj {#seed-addresses-in-a-campaign}

Om du vill lägga till dirigerade adresser till ett mål för en kampanj väljer du åtgärden och klickar på fliken **[!UICONTROL Edit]**.

Klicka på länken **[!UICONTROL Advanced campaign settings...]** och sedan på fliken **[!UICONTROL Seed addresses]**. Startadresserna som infogats från kampanjen läggs till i målet för varje leverans i kampanjen.

## Fröadresser och anpassad tabell {#using-an-external-recipient-table}

Om leveranstabellen är en extern tabell måste du göra ytterligare konfigurationer. Schemat **[!UICONTROL nms:seedmember]** måste utökas. En flik läggs till i startadresserna för att definiera lämpliga fält

Om du i det här fallet vill lägga till dirigerade adresser till leveransen anger du lämpliga fält direkt på matchande flik eller importerar adressmallarna.

<!--The **nms:seedMember** schema extension is [this section](../../configuration/using/seed-addresses.md).-->
