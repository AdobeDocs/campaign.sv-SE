---
title: SMS Skicka-korrektur
description: Lär dig hur du skickar korrektur för en SMS-leverans
feature: SMS
role: User
level: Beginner, Intermediate
version: Campaign v8, Campaign Classic v7
exl-id: d2ec4d92-7f00-47c8-98e6-0613d6387de0
source-git-commit: f75b95faa570d7c3f59fd8fb15692d3c3cbe0d36
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Skicka ett bevis på SMS-leverans {#sms-proof}

Adobe rekommenderar starkt att du skapar en leveransvalideringscykel. Se till att innehållet godkänns innan du skickar det till mottagarna.

Du kan skicka ett bevis för SMS-leveransen för att validera den:

1. Klicka på knappen **[!UICONTROL Send a proof]** så öppnas ett fönster

   ![](assets/proof_targeting.png){zoomable="yes"}

   Det finns flera lägen för att skicka ett korrektur:

   * **[!UICONTROL Definition of a specific proof target]**: låter dig fråga med filter om adresserna i databasen är korrekturmål
   * **[!UICONTROL Substitution of the address]**: gör att du kan ange dina testadresser och använda målmottagardata för att validera innehållet. Ersättningsadresserna kan anges manuellt eller väljas i listrutan. Den associerade [uppräkningen](../../config/enumerations.md) är **[!UICONTROL Substitution address (rcpAddress)]**.
Som standard utförs ersättningen slumpmässigt, men du kan välja en specifik mottagare från huvudmålet via ikonen **[!UICONTROL Detail]**.
   * **[!UICONTROL Seed addresses]**: gör att du kan komma åt dirigerade adresser som korrekturmål. Dessa adresser kan importeras från en fil eller anges manuellt.
   * **[!UICONTROL Specific target and Seed addresses]**: gör att du kan kombinera startadresser och adresser från mottagaren.

1. När du har valt din **[!UICONTROL Targeting mode]** lägger du till korrekturadresser enligt den

   I exemplet nedan väljer vi **[!UICONTROL Definition of a specific proof target]** och lägger till en mottagare:

   ![](assets/proof_recipient.png){zoomable="yes"}

1. Klicka på knappen **[!UICONTROL Analyze]**.
Adobe Campaign utför alla kontroller innan vi validerar sändningen av bevis. När analysen är klar kan du klicka på knappen **[!UICONTROL Confirm delivery]**.

   ![](assets/proof_analyze.png){zoomable="yes"}

1. Klicka på knappen **[!UICONTROL Confirm delivery]** om du vill skicka ett bevis på din SMS-leverans.

Om allt är rätt i det här skedet kan du gå vidare och [skicka SMS-leveransen till målgruppen](sms-audience.md).
