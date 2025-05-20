---
title: Kom igång med anpassade externa kanaler
description: Lär dig skapa och skicka anpassade externa kanaler med Adobe Campaign Web
role: User
level: Beginner, Intermediate
source-git-commit: 4a62c551c43cd5a4866df36cce10e294f35db363
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# Kom igång med anpassade externa kanaler {#gs-custom-channel}

Med Adobe Campaign kan ni skapa anpassade externa kanaler som är integrerade med tredje part. Du kan sedan ordna och köra leveranser baserat på dessa kanaler.

Leveransskapande och -sändning kan utföras både i klientkonsolen och i webbgränssnittet. Den anpassade externa kanalen utförs dock bara i klientkonsolen.

Mer information om hur du skapar och skickar en leverans baserad på en anpassad extern kanal finns på [sidan](https://experienceleague.adobe.com/docs/campaign-web/v8/msg/gs-custom-channel.html).

Så här skapar du en ny extern anpassad kanal i klientkonsolen:

1. Konfigurera schemat, [läs mer](#configure-schema)
1. Skapa ett nytt externt konto, [läs mer](#create-ext-account)
1. Skapa en ny leveransmall, [läs mer](#create-template)

## Konfigurera schemat{#configure-schema}

Först måste du konfigurera schemat för att lägga till den nya kanalen i listan över tillgängliga kanaler.

1. I Campaign Explorer väljer du **Administration** > **Konfiguration** > **Datascheman**.

1. Skapa ett schematillägg för att utöka uppräkningen messageType med den nya kanalen.

   Exempel:

   ```
   <enumeration basetype="byte" default="mail" label="Channel" name="messageType">
   <value desc="My Webpush" img="ncm:channels.png" label="My Webpush" name="webpush"
          value="122"/>
   </enumeration>
   ```

   ![](assets/cus-schema.png){zoomable="yes"}

## Skapa ett nytt externt konto{#create-ext-account}

Sedan måste du skapa ett nytt externt routningskonto.

1. Välj **Administration** > **Plattform** > **Externa konton** i Campaign Explorer.

1. Skapa ett nytt externt konto.

1. Markera kanalen och ändra leveransläget till **Extern**.

   ![](assets/cus-ext-account.png){zoomable="yes"}

## Skapa en ny leveransmall{#create-template}

Nu skapar vi den nya mallen som är kopplad till den nya kanalen.

1. Välj **Resurser** > **Mallar** > **Leveransmallar** i Campaign Explorer.

1. Skapa en ny mall.

1. Klicka på **Egenskaper** och välj rätt mapp och routning.

   ![](assets/cus-template.png){zoomable="yes"}

Den nya kanalen är nu tillgänglig. Du kan skapa och köra leveranser baserat på den här kanalen.


