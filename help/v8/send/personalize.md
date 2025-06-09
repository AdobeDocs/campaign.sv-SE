---
title: Kom igång med personalisering
description: Lär dig anpassa meddelandeinnehåll
feature: Personalization
role: User
level: Beginner
exl-id: 1da45746-4d69-415b-a793-9a08ce80091d
source-git-commit: 3ac2976839f084761ba56647b282062d8d457ff2
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 5%

---

# Kom igång med personalisering {#personalize-content}

För att få ut så mycket som möjligt av alla marknadsföringskampanjer ger Adobe Campaign er ett sätt att leverera anpassat innehåll som talar till kunderna på deras nivå. Utifrån profildata kan personalisering användas för att skapa en anpassad upplevelse för olika grupper och individer: du kan anpassa dina meddelanden till varje specifik mottagare genom att utnyttja de data och den information du har om dem. Det kan vara deras förnamn, intressen, var de bor, vad de har köpt och mycket annat.

Adobe Campaign förenklar personaliseringen: du kan visa olika typer av innehåll som är anpassat för varje mottagare med en enda [meddelandemall](create-templates.md). I transaktionsmeddelandena, t.ex. inköpsbekräftelse eller e-postmeddelanden om att kunden har lämnat en kundvagn, ska du inkludera produktlistningsinformation för varje enskild person i en enda e-postmall.


## Personalization strategier {#personalization-strategy}

Använd Campaign för att skapa dynamiskt innehåll och skicka personaliserade meddelanden. Personalization funktioner kan kombineras för att förbättra era budskap och skapa en anpassad användarupplevelse.

Du kan anpassa meddelandeinnehållet genom att:

* Infogar dynamiska **anpassningsfält**

  Anpassningsfält används för personalisering på första nivån av dina meddelanden. Du kan välja vilket fält som helst tillgängligt i databasen från personaliseringsredigeraren. För en leverans kan du välja vilket fält som helst som är relaterat till mottagaren, meddelandet eller leveransen. Dessa attribut kan infogas på ämnesraden eller i meddelandetexten. [Läs mer](personalization-fields.md).

  Följande syntax infogar mottagarens ort i ditt innehåll: &lt;%= mottagare.location.city %>.

* Infoga fördefinierade **innehållsblock**

  Campaign innehåller en uppsättning personaliseringsblock som innehåller en specifik återgivning som du kan infoga i dina leveranser. Du kan till exempel lägga till en logotyp, ett hälsningsmeddelande eller en länk till meddelandets spegelsida. Innehållsblock är tillgängliga från ett dedikerat tävlingsbidrag via personaliseringsredigeraren. [Läs mer](personalization-blocks.md).

* Skapa **villkorligt innehåll**

  Konfigurera villkorsstyrt innehåll för att lägga till dynamisk personalisering baserat på mottagarens profil till exempel. Textblock och/eller bilder infogas när ett visst villkor är true. [Läs mer](conditions.md).

<!--* Add **personalized offers**
    
    Insert personalized offers in your message content, depending on the recipient location, the current weather, or the last purchase order.
-->


## Skyddsutkast och rekommendationer{#perso-guardrails}

### Personalization timeout {#perso-timeout}

Om du vill förbättra leveransskyddet kan du ange en tidsgräns för personaliseringsfasen.

På fliken **[!UICONTROL Delivery]** i **[!UICONTROL Delivery properties]** väljer du ett maxvärde i sekunder för alternativet **[!UICONTROL Maximum personalization run time]**.

Om personaliseringsfasen överskrider den maximala tid som du anger i det här fältet avbryts processen under förhandsgranskningen eller sändningen och leveransen misslyckas.

Standardvärdet är 5 sekunder.

Om du ställer in det här alternativet på 0 kommer det inte att finnas någon tidsgräns för personaliseringsfasen.


### Interna variabler{#internal-variables}

Följande variabler är interna variabler som kan användas för personalisering, men som inte får ändras: **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **position**.


## Självstudievideo {#personalization-video}

Förstå de olika typerna av dynamiskt innehåll och lär dig hur du skapar och använder personaliseringsblock och villkorssatser i en leverans.


>[!VIDEO](https://video.tv.adobe.com/v/3452872?quality=12&captions=swe)
