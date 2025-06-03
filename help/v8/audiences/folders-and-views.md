---
title: Mappar och vyer
description: Lär dig hur du hanterar mappar och vyer i Campaign Explorer
feature: Audiences, Profiles, Application Settings
role: User
level: Beginner, Intermediate
exl-id: 762dcacc-4aeb-4990-af01-7f793bd69170
version: Campaign v8, Campaign Classic v7
source-git-commit: a2efad26232cd380eea850a589b22b23928253e8
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 0%

---

# Hantera mappar och vyer {#folders-and-views}

Kampanjmappar är noder i utforskarträdet. Beroende på vilken typ de har innehåller de vissa typer av data.

En vy är en specifik mapp som inte innehåller några data, men som visar data som lagras fysiskt i andra mappar av samma typ. Om du t.ex. förvandlar en leveransmapp till en vy visas alla leveranser i den här mappen. Dessa data kan sedan filtreras.


>[!NOTE]
>För att skilja vyer från standardmappar visas deras namn med ljusblått i stället för svart.
>

Observera att du kan tilldela behörigheter till mappar för att begränsa åtkomsten till vissa data. [Läs mer](#restrict-access-to-a-folder)

## Bästa tillvägagångssätt vid arbete med mappar{#best-practices-folders}

* **Använd inbyggda mappar** för att göra det enklare för alla som deltar i projektet att använda, underhålla och felsöka programmet. Undvik att skapa anpassade mappstrukturer för mottagare, listor, leveranser osv., men använd standardmapparna som **Administration**, **Profiler och mål**, **Kampanjhantering**.

* **Skapa undermappar**, till exempel spara dina tekniska arbetsflöden i den inbyggda mappen **[!UICONTROL Administration > Production > Technical Workflows]** och skapa undermappar per arbetsflödestyp.

* **Definiera och tillämpa en namnkonvention**, till exempel kan du namnge arbetsflödena i alfabetisk ordning så att de visas sorterade i körningsordningen, till exempel:

  A1 - importmottagare, börjar 10:00;
A2 - importbiljetter, börjar klockan 11:00.

## Skapa en mapp{#create-a-folder}

Om du vill skapa en mapp högerklickar du på en befintlig mapp och använder snabbmenyn.

Om du vill skapa samma typ av mapp som den du valde väljer du det första alternativet på snabbmenyn. Välj till exempel **[!UICONTROL Create a new 'Recipients' folder]** från en mottagarmapp.

![](assets/create-recipient-folder.png)

Du kan dra och släppa den nya mappen för att ordna Campaign Explorer-trädet efter behov.

Om du vill skapa en annan typ av mapp högerklickar du på en befintlig mapp och väljer **[!UICONTROL Add new folder]**. Du kan skapa alla typer av mappar, beroende på vilka data som ska lagras.

![](assets/add-new-folder.png)

>[!CAUTION]
>De här ändringarna gäller alla Campaign-användare.
>

## Gör en mapp till en vy{#turn-a-folder-to-a-view}

En vy är en specifik mapp som inte innehåller några data, men som visar data som lagras fysiskt i andra mappar av samma typ.

Du kan omvandla en mapp till en vy, men mappen måste vara tom. Alla data som lagras i mappen tas bort när du förvandlar mappen till en vy.

>[!CAUTION]
>
>I en vy visas data som ger åtkomst till dem, även om data inte lagras fysiskt i visningsmappen. För att få åtkomst till innehållet måste operatorn ha rätt behörigheter i källmapparna, minst läsbehörighet.
>
>Om du vill ge åtkomst till en vy utan att ge åtkomst till källmappen, ska du inte ge läsåtkomst till den överordnade noden i källmappen.

I exemplet nedan skapar vi en ny mapp som endast visar leveranser från USA utifrån deras interna namn.

1. Skapa en **[!UICONTROL Deliveries]**-mapp och ge den namnet **USA-leveranser**.
1. Högerklicka på mappen och välj **[!UICONTROL Properties...]**.
1. Välj **[!UICONTROL This folder is a view]** på fliken **[!UICONTROL Restriction]**. Därefter visas alla leveranser i databasen.

   ![](assets/this-folder-is-a-view.png)

1. Definiera filtervillkoren från frågeredigeraren i fönstrets centrala del: bara de leveranser som motsvarar filtret visas i mappen.

   ![](assets/filter-view.png)

   >[!NOTE]
   >
   >Lär dig utforma frågor på [den här sidan](create-filters.md#advanced-filters)


>[!CAUTION]
>
>När [transaktionsmeddelanden](../send/transactional.md) hanteras får inte mapparna **[!UICONTROL Real time events]** eller **[!UICONTROL Batch events]** anges som vyer för körningsinstanserna, eftersom detta kan leda till behörighetsproblem.

## Ordna dina mappar{#organize-your-folders}

Som standard läggs en ny mapp till högst upp i hierarkin.

Bläddra på fliken **Undermappar** i en mappegenskap för att ordna dess undermappar.

Du kan flytta mapparna med pilarna till höger eller välja alternativet **[!UICONTROL Sort the sub-folders in alphabetical order]** om du vill sortera dem automatiskt.

![](assets/sort-folders.png)


## Filtrera data i en mapp{#filter-data-in-a-folder}

Om du vill filtrera data som lagras i en mapp går du till mappegenskaperna och väljer fliken Begränsning.

Mappen nedan innehåller till exempel bara kontakter med en e-postadress och vars ursprung inte har flaggats som&quot;Extern&quot; - eller är tomt.

![](assets/add-a-filter-to-a-folder.png)


## Begränsa åtkomst till en mapp{#restrict-access-to-a-folder}

Använd behörigheter i mappar för att ordna och styra åtkomsten till Campaign-data. Läs mer om behörigheter för mappar i [det här avsnittet](../start/folder-permissions.md).
