---
product: campaign
title: Läsa in (SOAP)
description: Läsa in (SOAP)
feature: Workflows
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 21c42a36-9a50-49b8-8a07-b041ba8b2026
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 4%

---

# Läsa in (SOAP){#loading-soap}



>[!CAUTION]
>
>Aktiviteten **Inläsning (SOAP)** är bara tillgänglig om du har modulen **FDA (Federated Data Access)** installerad. Kontrollera licensavtalet.

Aktiviteten **Inläsning (SOAP)** används utöver aktiviteten **datainläsning (RDBMS)** när det inte går att samla in data direkt via FDA i en extern databas.

Åtgärden är följande:

1. Välj mellan att använda ett XML-exempel eller en WSDL.

   Följande exempel kommer från ett tekniskt arbetsflöde i Message Center-modulen.

   ![](assets/load_soap_002.png)

1. Välj en exempelfil för ett XML-exempel. Filen analyseras för att skapa ett resultatexempel.

   För en WSDL anger du den matchande URL:en och genererar sedan skelettkoden. Den valda tjänsten och det valda samtalet uppdateras och visas automatiskt.

   ![](assets/soap_load_003.png)

1. Välj **[!UICONTROL Click here to view and edit analysis results]** för att ange varje identifierad kolumn.

   ![](assets/soap_load_001.png)

   Om du vill uppdatera exemplet väljer du **[!UICONTROL Re-analyze the example]**.

1. Du kan använda radnumret som identifierare och/eller ange att SOAP-anropet returnerar flera element.
1. Ange följande tabbskript beroende på deras funktion:

   * **[!UICONTROL Initialization]**: upprättar en SOAP-anslutning.
   * **[!UICONTROL Iteration]**: utför anropet till tjänsten SOAP. Returvärdet för den här funktionen måste vara ett XML-objekt som är kompatibelt med beskrivningen av exemplet eller WSDL.

     Koden för den här fliken anropas i en slinga av Adobe Campaign tills ett XML-objekt som är null returneras.

   * **[!UICONTROL Finalization]**: stänger anslutningen och/eller frigör andra resurser som skapats under bearbetningen.
