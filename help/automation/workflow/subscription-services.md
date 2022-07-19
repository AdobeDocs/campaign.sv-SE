---
product: campaign
title: Prenumerationstjänster
description: Läs mer om arbetsflödesaktiviteten för prenumerationstjänster
feature: Workflows, Targeting Activity, Subscription Services Activity
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Prenumerationstjänster{#subscription-services}



A **Prenumerationstjänster** Med aktivitet av -typ kan du skapa eller ta bort en prenumeration på en informationstjänst för den population som anges i övergången.

Om du vill konfigurera den redigerar du aktiviteten och anger dess etikett och väljer sedan den åtgärd som ska utföras (prenumeration eller avprenumeration) och den aktuella tjänsten, som i följande exempel:

![](assets/edit_service_inscription.png)

1. Ange aktivitetens etikett.
1. Välj **[!UICONTROL Generate an outbound transition]** om du vill skapa en övergång i slutet av körningen.

   I allmänhet markerar målets prenumeration på en informationstjänst slutet av målarbetsflödet, vilket är varför alternativet inte aktiveras som standard.

1. Klicka **[!UICONTROL Subscription]** eller **[!UICONTROL Unsubscription]** om du vill prenumerera eller avbryta prenumerationen på den angivna populationen till eller från den valda informationstjänsten.
1. Välj **[!UICONTROL Send a confirmation message]** för att meddela mottagarna att de prenumererar på eller avbeställer en tjänst.

   Innehållet i det här meddelandet anges i en leveransmall som är relaterad till informationstjänsten. Mer information finns i detta .

## Exempel: Prenumerera på en lista över mottagare i ett nyhetsbrev {#example--subscribe-a-list-of-recipients-to-a-newsletter}

I en och samma åtgärd syftar följande arbetsflöde till att göra en lista över mottagare som är berättigade till ett nyhetsbrev, avsett att arbeta i Paris, för att få dem att prenumerera.

Om du vill göra det måste du även utesluta mottagare som redan har prenumererat.

>[!CAUTION]
>
>Innan du prenumererar manuellt på mottagare av en tjänst kontrollerar du att mottagarna accepterar att ta emot meddelanden från dig.

![](assets/subscription_services_example.png)

1. Lägg till följande tre frågor:

   * En målgrupp för mottagare i åldern 18 till 60 år.
   * En andra målgrupp för mottagare som bor i Paris.
   * En tredje målgruppsmottagare som för närvarande inte prenumererar på nyhetsbrevet.

1. Lägg till en korsningsaktivitet för att korsreferera till de olika resultaten.
1. Om du vill kan du infoga en listuppdatering som håller listan över de senaste prenumeranterna uppdaterad.
1. Infoga en prenumerationstjänstaktivitet och dubbelklicka sedan på den för att konfigurera den.
1. Ange aktivitetsetiketten och välj **[!UICONTROL Subscription]**.

   Om du vill kan du informera mottagarna om deras nyhetsbrevprenumeration genom att kontrollera **[!UICONTROL Send a confirmation message]** box.

1. Markera den mapp som nyhetsbrevet finns i och välj sedan nyhetsbrevet i listan som visas.
1. Lämna **[!UICONTROL Generate outbound transition]** avmarkerad så att aktiviteten markerar slutet av arbetsflödet och sedan klickar du **[!UICONTROL Ok]**.

Under arbetsflödeskörningen läggs de mottagare som motsvarar alla tre frågorna till i listan och prenumereras på nyhetsbrevet.

Du kan kontrollera att prenumerationen lyckades genom att gå till **[!UICONTROL Subscription]** -fliken för dina mottagare.

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.
