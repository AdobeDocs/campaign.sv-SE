---
title: Inbyggda rapporter från Adobe Campaign
description: Inbyggda rapporter
feature: Reporting
role: User
exl-id: b63e6905-3bd4-4de4-9e7e-7638e5fc1192
source-git-commit: 1a0b473b005449be7c846225e75a227f6d877c88
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 1%

---

# Inbyggda rapporter från Adobe Campaign {#ootb-reports}

På den här sidan finns en lista över Adobe Campaign inbyggda rapporter, deras innehåll och sammanhang. Adobe Campaign tillhandahåller ett antal inbyggda rapporter som är tillgängliga via klientkonsolen eller en webbläsare.

Följande typer av rapporter är tillgängliga:

* Rapporter om hela plattformen. [Läs mer](global-reports.md).
* Leveransrapporter. [Läs mer](delivery-reports.md).

Du kommer åt inbyggda rapporter från Campaigns hemsida, den dedikerade rapportkontrollpanelen eller leveranslistan. Hur rapporten visas i användargränssnittet beror på sammanhanget.

En lista med viktiga rapporter finns på startsidan, så att du snabbt kan komma åt leveransdata. Listan kan ändras efter dina behov. Du kan även lära dig hur du lägger till egna rapporter i **[!UICONTROL Reports]** -fliken.

Mer information om dessa anpassade konfigurationer finns i [Campaign Classic v7 - dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/creating-new-reports/configuring-access-to-the-report.html).


## Åtkomst till inbyggda rapporter {#access-ootb-reports}

Få tillgång till inbyggda rapporter för Campaign:

1. Välj **[!UICONTROL Reports]** i Adobe Campaign gränssnitt.

   ![](assets/reporting-access-from-home.png)

1. Använd sökfälten för att filtrera de visade rapporterna.

1. Klicka sedan på den rapport som du vill visa.

   ![](assets/edit-a-report.png)

1. Klicka på **[!UICONTROL Back]** länken längst upp på skärmen tar dig tillbaka till rapportlistan.

   ![](assets/back-button.png)

Rapporter som är specifika för en kampanj eller leverans är tillgängliga via respektive instrumentpanel.

![](assets/reporting-on-delivery.png)

Principen är densamma för listor, tjänster, erbjudanden osv. enligt nedan:

![](assets/reporting-on-offer.png)


## Rapporter om leveranser {#reports-on-deliveries}

De inbyggda rapporterna från Adobe Campaign finns i tabellen nedan.

Mer information om innehållet i dessa rapporter finns i [det här avsnittet](delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Användaraktiviteter (receiveActivity)<br /> </td> 
   <td> Uppdelning av öppningar, klick och transaktioner efter tidsperiod.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveransflöde (dataflöde)<br /> </td> 
   <td> Leverera dataflödesdiagram i meddelanden/timme och Mbit/s.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Fel och studsar (fel)<br /> </td> 
   <td> studsar och icke-levererbara produkter utifrån orsak och domän.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårningsindikatorer (deliveryFeedback)<br /> </td> 
   <td> Sammanfattning av nyckelindikatorer för att spåra mottagarnas beteende.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårningsindikatorer (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Spåra indikatorer för leverans till en mobilapplikation.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Webbläsare (browserStatistics)<br /> </td> 
   <td> Statistik över webbläsare som används av mottagare som klickat i meddelanden.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Delning till sociala nätverk (deliveryForward)<br /> </td> 
   <td> Delningsaktivitet och statistik för e-postöppning.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Snabbklickningar (hoturls)<br /> </td> 
   <td> Visar meddelandet och klickfrekvensen som ligger ovanpå.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Hypotesrapport (deliveryHypothesis)<br /> </td> 
   <td> Visar en sammanfattning av mått för leveranssätt.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveransstatistik (statistikPerDelivery)<br /> </td> 
   <td> Statistik (bearbetade meddelanden, levererade meddelanden, hårda studsar, mjuka studsar, klick, avbeställningar) per e-postdomän.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Delningsaktivitetsstatistik (forwardActivities)<br /> </td> 
   <td> Analys av delningsaktiviteter, öppningar och prenumerationer per tidsperiod.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårningsstatistik (trackingStatistics)<br /> </td> 
   <td> Öppna, klicka och rapportera transaktionsräntor.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveranssammanfattning (leveransSending)<br /> </td> 
   <td> Sammanfattning av leveransindikatorer: mål, uteslutning och skickade meddelanden.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveranssammanfattning (deliveryStatistics)<br /> </td> 
   <td> Sammanfattningstabell för valda leveranser: Mål, undantag och skickade meddelanden.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> Operativsystem (osStatistics)<br /> </td> 
   <td> Statistik över operativsystem som används av mottagare som klickat i ett meddelande.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktivitetsfrekvens (deliveryFeedbackSocial)<br /> </td> 
   <td> Leveransreaktivitet och reaktionsnedbrytning.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
  <tr> 
   <td> URL:er och klickdataflöde (topUrlDelivery)<br /> </td> 
   <td> De flesta reaktiva URL:er och associerade klickströmmar.<br /> </td> 
   <td> nms:leverans<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporter om kampanjer {#reports-on-campaigns}

Rapporter om kampanjer rör data i **nms:operation** tabell.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Användaraktiviteter (operationRecipientActivity)<br /> </td> 
   <td> Uppdelningen av öppningar, klick och transaktioner efter tidsperiod beror på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveransdataflöde (operationThrottput)<br /> </td> 
   <td> Diagram över leveransflöde, i e-post/timme och Mbit/s, beror på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampanjutgifter (budgetOperationExpenses)<br /> </td> 
   <td> Visar kampanjradsobjekten i detalj, beroende på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Fel och studsar (operationErrors)<br /> </td> 
   <td> Satser och icke-levererbara produkter utifrån orsak och domän är beroende av Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetExplorerOperation)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader är beroende av MRM.<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårningsindikatorer (operationFeedback)<br /> </td> 
   <td> Översikt över nyckelspårningsindikatorer: Öppningar, klick och transaktioner beror på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Delning till sociala nätverk (operationForward)<br /> </td> 
   <td> Delningsaktivitet och statistik för e-postöppning beror på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Hypotesrapport (operationHypothesis)<br /> </td> 
   <td> Visar sammanfattningen av hypotesmått för kampanjleveranser, beroende på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Delningsaktivitetsstatistik (forwardActivityOpt)<br /> </td> 
   <td> Analys av delningsaktiviteter, öppningar och prenumerationer per tidsperiod beror på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveranssammanfattning (operationStatistics)<br /> </td> 
   <td> Översiktstabell över kampanjleveranser: Mål, undantag och skickade meddelanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL:er och klickdataflöde (operationTopUrlDelivery)<br /> </td> 
   <td> De flesta reaktiva URL:er och associerade klickströmmar är beroende av Campaign.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporter om tjänster {#reports-on-services}

Rapporterna om tjänster rör uppgifterna i **nms:service** tabell.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Fläktförvärv (socialAcquisitionsByWebapp)<br /> </td> 
   <td> Vilka webbprogram aktiverade köp av potentiella kunder? Tillägget för social marknadsföring används.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning av prenumerationer (mobileAppDistribution)<br /> </td> 
   <td> Uppdelningen av aktiva prenumerationer per mobilprogram beror på tillägget Mobilappskanal.<br /> </td> 
  </tr> 
  <tr> 
   <td> Prenumerationsspårning (subscriptionsProgress)<br /> </td> 
   <td> Utveckling av prenumerationer på informationstjänster<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktivitetsfrekvens (socialReactionRate)<br /> </td> 
   <td> Vilka är reaktivitetsfrekvenserna för de senaste leveranserna? Tillägget för social marknadsföring används.<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktivitetsfrekvens (mobileAppReactivityRate)<br /> </td> 
   <td> Reaktivitetsfrekvensen för de senaste leveranserna beror på mobilappens kanaltillägg.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Budgetrapporter {#budget-reports}

De inbyggda rapporterna från Adobe Campaign finns i tabellen nedan.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Kostnader kopplade till program (budgetProgramCost)<br /> </td> 
   <td> Uppdelning av programkostnader.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Budgetutveckling (budgetEvolution)<br /> </td> 
   <td> Utveckling av budgetkostnader per åtagandenivå.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Kumulativ utveckling av budgeten (budgetCumulativeEvolution)<br /> </td> 
   <td> Utveckling av de kumulerade budgetkostnaderna uppdelade efter kommatecken<br /> lagnivå. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetUtforskarenBudget)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (BudgetExplorer)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetExplorerPlan)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetExplorerProgram)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Sammanfattning av budget(er) (budget)<br /> </td> 
   <td> Översikt över de viktigaste kostnaderna, utgiftskategorierna och budgetarna.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporter om simuleringar {#reports-on-simulations}

Rapporter om simuleringar rör uppgifterna i **nms:simulering** tabell.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Detalj för simuleringsundantag (dlvSimuLossesDetail)<br /> </td> 
   <td> Detaljerad tabell över alla orsaker till uteslutning.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning av erbjudanden efter rangordning (offerSimulationRanking)<br /> </td> 
   <td> Uppdelning av erbjudanden i simuleringen, efter rangordning.<br /> </td> 
  </tr> 
  <tr> 
   <td> Simuleringssammanfattning (dlvSimuLossesSummary)<br /> </td> 
   <td> Sammanfattning av simuleringsvolymer och undantag.<br /> </td> 
  </tr> 
  <tr> 
   <td> Överlappningsstatistik (dlvSimuOverlapping)<br /> </td> 
   <td> Leveransmål för överlappande volymer.<br /> </td> 
  </tr> 
  <tr> 
   <td> Sammanfattning av undantag på grund av simuleringen (dlvSimuLossesSimu)<br /> </td> 
   <td> Tabell över undantag på grund av simuleringen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporter om webbprogram {#reports-on-web-applications}

Rapporter om webbprogram gäller data i **nms:WebApp** tabell.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Dokumentation (surveyDictionary)<br /> </td> 
   <td> Beskrivningen av undersökningsstrukturen beror på tillägget Survey Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> Main (surveyProperties)<br /> </td> 
   <td> Undersökningsegenskaper<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning av svar (surveyDistribution)<br /> </td> 
   <td> Uppdelning av svar på frågor.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Andra rapporter {#other-ootb-reports}

Följande rapporter finns också inbyggda. Mer information finns i dokumentet om de funktioner som berörs.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandeanalys (offerAnalysis)<br /> </td> 
   <td> Analys av erbjudandet per datum och kanal beror på interaktionstillägget.<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> Effektiv återmarknadsföring (remarketingEffect)<br /> </td> 
   <td> Mätning av återmarknadsföringens effektivitet<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Historik över förvärv av sociala potentiella kunder (socialVisitorStatistics)<br /> </td> 
   <td> Historiken över Twitter och Facebook kundvärvningar beror på tillägget för social marknadsföring.<br /> </td> 
   <td> nms:besökare<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårning av senaste förslag (recentPropositions)<br /> </td> 
   <td> Spårning av offerter i realtid<br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
