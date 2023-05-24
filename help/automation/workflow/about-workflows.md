---
product: campaign
title: Om arbetsflöden
description: Automatisera processerna med arbetsflöden, hantera data och målgrupper, skicka meddelanden med mera.
feature: Workflows
exl-id: 297aa4e3-b672-46b5-9016-5accee8568b8
source-git-commit: 190707b8b1ea5f90dc6385c13832fbb01378ca1d
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 26%

---

# Kom igång med arbetsflöden{#gs-workflows}

## Om arbetsflöden{#about-workflows}

Adobe Campaign har en arbetsflödesmodul som gör att du kan ställa in alla processer och uppgifter i olika moduler på programservern. I den omfattande grafiska miljön kan du utforma processer såsom segmentering, kampanjkörning, filhantering och mänskligt deltagande osv. Arbetsflödesmotorn kör och spårar dessa processer.

Du kan till exempel använda ett arbetsflöde för att ladda ned en fil från en server, expandera den och sedan importera poster som finns i databasen i Adobe Campaign.

Ett arbetsflöde kan även innefatta en eller flera operatörer som ska meddelas eller som kan göra val och godkänna processer. På så sätt kan du skapa en leveransinstruktion, tilldela en eller flera operatörer uppgiften att arbeta med innehåll, ange mål och godkänna korrekturer innan leveransen påbörjas.

Arbetsflöden sker i olika sammanhang och under olika faser av kampanjhanteringsprocessen.

Adobe Campaign använder arbetsflöden för att

* Designa arbetsflöden för målinriktning. [Läs mer](#targeting-workflows)
* Samordna flerkanalskampanjer. [Läs mer](#campaign-workflows)
* Utför tekniska processer som rensning, dataspårning, beräkningar med mera. [Läs mer](#technical-workflows)

Ett arbetsflöde är en processdefinition: arbetsflödesdiagrammet, som är en representation av vad som ska hända. Ett arbetsflöde är också en instans av den här processen: en arbetsflödesinstans, vilket är en representation av vad som faktiskt händer.

Arbetsflödesmallen beskriver de olika uppgifter som ska utföras och hur de länkas samman. Uppgiftsmallarna kallas aktiviteter och representeras av ikoner. De länkas ihop av övergångar.

![](assets/example1.png)

## Nyckelobjekt

Varje arbetsflöde innehåller:

* **[!UICONTROL Activities]**

   En aktivitet beskriver en uppgiftsmall. De olika aktiviteterna som är tillgängliga visas i diagrammet med ikoner. Varje typ har gemensamma egenskaper och specifika egenskaper. Alla aktiviteter har till exempel ett namn och en etikett, men bara **[!UICONTROL Approval]** aktiviteten har ett uppdrag.

   I ett arbetsflödesdiagram kan en viss aktivitet producera flera uppgifter, särskilt när det finns en slinga eller återkommande (periodiska) åtgärder.

   Alla arbetsflödesaktiviteter listas i [det här avsnittet](activities.md), inklusive användningsfall och prover.

* **[!UICONTROL Transitions]**

   Med övergångar kan du länka aktiviteter och definiera deras sekvens. En övergång länkar en källaktivitet till en målaktivitet. Det finns flera typer av övergångar, som är beroende av källaktiviteten. Vissa övergångar har ytterligare parametrar som längd, villkor eller filter.

   En övergång som inte är länkad till en målaktivitet får färgen orange och pilhuvudet visas som en romb.

   >[!NOTE]
   >
   >Ett arbetsflöde som innehåller oavslutade övergångar kan fortfarande köras: ett varningsmeddelande genereras och arbetsflödet pausas när övergången är klar, men det genererar inget fel. Det är alltså möjligt att starta ett arbetsflöde utan att det är färdigt och att lägga till i det när du går vidare.

   Mer information om hur du skapar ett arbetsflöde finns i [det här avsnittet](build-a-workflow.md).

* **[!UICONTROL Worktables]**

   Arbetstabellen innehåller all information som övergången innehåller. Varje arbetsflöde använder flera arbetstabeller. Data som förmedlas i dessa tabeller kan accelereras och användas under arbetsflödets hela livscykel, så länge de inte rensas. Det går att tömma tabeller som inte behövs varje gång arbetsflödet är passivat och eventuellt under körningen av de största arbetsflödena för att undvika att servern överbelastas.

   Läs mer om arbetsflödesdata och tabeller i [det här avsnittet](use-workflow-data.md).

## Relaterade avsnitt

I dessa avsnitt hittar du vägledning och bästa metoder för att automatisera processer med arbetsflöden:

* Läs mer om arbetsflödesaktiviteter i [den här sidan](use-workflow-data.md).
* Lär dig hur du skapar ett arbetsflöde i [det här avsnittet](build-a-workflow.md).
* Upptäck hur du använder arbetsflöden för att importera data i Campaign i [det här avsnittet](campaign-workflows.md)..
* De effektivaste strategierna för arbetsflöden beskrivs i [den här sidan](workflow-best-practices.md).
* Hitta vägledning om arbetsflödeskörning i [det här avsnittet](start-a-workflow.md).
* Lär dig övervaka arbetsflöden i [den här sidan](monitor-workflow-execution.md).
* Lär dig hur du ger användare åtkomst att använda arbetsflöden i [den här sidan](managing-rights.md).
