---
product: campaign
title: Om leveransbarhet i Adobe Campaign Classic
description: Läs mer om hantering av slutprodukter i Adobe Campaign
feature: Deliverability
role: User
version: Campaign v8, Campaign Classic v7
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 96f1518f252be7ffa27ba8157b8a090bf4d4510d
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 4%

---

# Styr innehållet i dina meddelanden{#control-message-content}

För att vara säker på att dina e-postmeddelanden når dina mottagare och förbättrar e-postleveransen måste de följa ett antal regler. Annars kan innehållet i vissa meddelanden identifieras som skräppost. Adobe Campaign tillhandahåller flera verktyg för att se till att ditt innehåll följer dessa regler.

Följ nedanstående principer när du utformar ditt meddelandeinnehåll:

* [Avsändaradress](#sender-address): adressen måste uttryckligen identifiera avsändaren. Domänen måste ägas av och registreras hos avsändaren. Domänregistret får inte privatiseras.
* [Personalization](#personalization): Om du anpassar innehåll och definierar en sändningstid per mottagare ökar risken för att ditt meddelande öppnas.
* Bilder och text: Använd ett bra förhållande mellan text och bild (till exempel 60 % text och 40 % bilder).
* [Bryt prenumerationslänk](#opt-out) och landningssida: länken för att avsluta prenumerationen är nödvändig. Den måste vara synlig och giltig och formuläret måste vara funktionellt.
* Förhandsgranska: använd verktygen i Adobe Campaign för att kontrollera och optimera innehållet i e-postmeddelandet ([Inkorgsåtergivning](#message-responsiveness), [SpamAssets](#spamassassin)).

Fler tips om hur du kan optimera leveransen när du utformar innehåll finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html?lang=sv-SE){target="_blank"}.

>[!NOTE]
>
>Mer information om hur du redigerar e-postinnehåll finns på [sidan](defining-the-email-content.md).

## Avsändarens adress {#sender-address}

Vissa Internetleverantörer kontrollerar giltigheten för avsändaradressen (**[!UICONTROL From]**) innan de accepterar meddelanden. En felformaterad adress kan leda till att den nekas av den mottagande servern.

Du måste se till att rätt adress anges på instansnivå (meny **[!UICONTROL Tools > Advanced > deployment wizard...]**) eller i de vanligaste scenarierna.

Mer information om hur du definierar avsändarens adress finns på [sidan](defining-the-email-content.md#sender).

## Personalization {#personalization}

För att förbättra mottagarnas upplevelse och få dem att öppna ditt e-postmeddelande kan du anpassa dina meddelanden med Adobe Campaign.

Mer information om hur du använder anpassningsfält i Adobe Campaign finns i [det här avsnittet](personalization-fields.md).

## Länk och formulär för avanmälan {#opt-out}

Som standard kontrollerar en [typologiregel](../../automation/campaign-opt/apply-rules.md) om en avanmälningslänk har inkluderats och genererar en varning om den saknas när meddelandet analyseras. Du kan ändra den här regeln så att ett fel uppstår i stället för en enkel varning och stoppa en leverans utan den här länken.

Du måste kontrollera att avanmälningslänken fungerar som den ska innan du skickar iväg den. När du till exempel skickar korrekturet ska du kontrollera att länken är giltig, att formuläret är online och att värdet för fältet **[!UICONTROL No longer contact this recipient]** ändras till **[!UICONTROL Yes]** när du validerar det. Du bör göra den här kontrollen systematiskt eftersom det alltid är möjligt att göra mänskliga fel när du anger länken eller när du ändrar formuläret.

Lär dig hur du infogar en länk [för avanmälan i det här avsnittet](personalization-blocks.md#ootb-personalization-blocks).

Om ett problem upptäcks med att prenumerationen inte längre kan tas emot efter att leveransen har startats går det fortfarande att göra en manuell avanmälan (med funktionen för massuppdatering till exempel) för de mottagare som klickar på avanmälningslänken, även om de inte kunde bekräfta sitt val.

Som allmän regel ska du inte försöka hindra mottagare som vill avanmäla sig genom att kräva att de fyller i fält som e-postadress eller namn, till exempel. Formuläret ska bara ha en valideringsknapp och avstämning ska endast utföras på den krypterade identifieraren.

Begäran om ytterligare bekräftelse är inte tillförlitlig: en användare kan ha två e-postadresser som omdirigeras till samma ruta (till exempel: firstname.lastname@club.com och firstname.lastname@internet-club.com). Om mottagaren bara kommer ihåg den första adressen och vill avbeställa prenumerationen via ett meddelande som skickas till den andra, kommer formuläret att avslå detta eftersom den krypterade identifieraren och den angivna e-postadressen inte matchar.

## Inkorgsåtergivning {#message-responsiveness}

Innan du skickar ditt meddelande kan du testa hur meddelandet kommer att se ut på olika enheter. Det är för att säkerställa att den visas på ett optimalt sätt på olika webbklienter, webbmejl och enheter.

Adobe Campaign hämtar återgivningen och gör den tillgänglig i en dedikerad rapport. På så sätt kan du förhandsgranska det skickade meddelandet i olika sammanhang där det kan tas emot.

Mer information finns i [Återgivning av inkorgen](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign kan konfigureras för att fungera med SpamAssassin. Detta gör det möjligt att poängsätta e-postmeddelanden för att avgöra om ett meddelande löper risk att betraktas som skräppost av de antispam-verktyg som används vid mottagande.

Innan du påbörjar en leverans kan du med fliken **[!UICONTROL Preview]** utvärdera riskerna. Ett varningsmeddelande ger resultatet av testet.

Läs mer i det här [avsnittet](spamassassin.md).
