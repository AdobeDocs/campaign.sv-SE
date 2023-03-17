---
product: campaign
title: Kontinuerlig leverans
description: Kontinuerlig leverans
feature: Workflows, Channels Activity
exl-id: e3ad6d92-8d53-4098-90fd-cfed29f2e56e
source-git-commit: edb099b3e882d857752af76798012ccd1c5a99be
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 9%

---

# Kontinuerlig leverans{#continuous-delivery}



A **Kontinuerlig leverans** kan du lägga till nya mottagare i en befintlig leverans. Med den här leveranstypen slipper du skapa en ny leverans varje gång: Det här läget är ofta mer effektivt, särskilt när det gäller meddelanden om låga volymer eller meddelanden som skickas ut vid behov.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#continuous-delivery-video)

På en leveransmallnivå kan du ange ett skript för att beräkna etiketten (och kampanjmappen) för den associerade leveransen. Om skriptet beräknar en leverans som inte finns än, skapas den direkt.

![](assets/edit_diffusion_fil.png)

The **[!UICONTROL Process errors]** I visas en viss övergång som aktiveras om ett fel genereras. I det här fallet försätts arbetsflödet inte i felläge och fortsätter med körningen.

Fel som beaktas är filsystemfel (filen kunde inte flyttas, katalogen kunde inte nås osv.).

Det här alternativet bearbetar inte fel relaterade till aktivitetskonfigurationen, dvs. ogiltiga värden.

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

Endast när **[!UICONTROL Specified by the inbound event]** är markerat.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som uppstår vid leverans. **[!UICONTROL tableName]** är namnet på den tabell som memorerar målets identifierare, **[!UICONTROL schema]** är schemat för populationen (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Övergången som är associerad med komplementet har samma parametrar.

## Så ställer du in en kontinuerlig leverans

I det här avsnittet beskrivs hur du konfigurerar en kontinuerlig leverans.

The **kontinuerlig leverans** Med kan du lägga till nya mottagare i en befintlig leverans och undvika att du måste skapa en ny leverans varje gång en ny mottagare läggs till. Du kan uppdatera den kreativa informationen direkt i kampanjarbetsflödet och den uppdaterar mallen i leveransmallens resursmapp.

En kontinuerlig leverans skapar en enda leverans- och leveranslogg (broadLog) och spårningsloggar som refererar till att en leverans läggs till varje gång den körs.

![Kontinuerlig leverans](assets/delivery_continuous.jpg)

## Videokurs {#continuous-delivery-video}

Den här videon visar hur du konfigurerar en kontinuerlig leverans med en stegvis frågeställning.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

Det finns ytterligare utbildningsvideor för Campaign [här](https://experienceleague.adobe.com/docs/campaign-learn/tutorials/getting-started/introduction-to-adobe-campaign.html){target="_blank"}.
