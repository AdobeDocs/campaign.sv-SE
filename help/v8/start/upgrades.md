---
title: Kampanjversioner och uppgraderingar
description: Läs mer om Campaign-versioner och uppgraderingar
feature: Release Notes
role: User
level: Beginner
exl-id: 04bda36f-051f-41a3-84b3-6af3c5e34ab2
source-git-commit: a779f243b0ba13dc3fcb7839377ca8766e5f7841
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 10%

---

# Versioner och uppgraderingar {#upgrades}

## Kampanjversioner {#versions}

Adobe Campaign släpper regelbundet produktversioner som förbättrar prestanda, säkerhet, logik och användbarhet i er Campaign-infrastruktur.

Dessa uppgraderingar kan vara:

* **Viktiga uppgraderingar**, från en större version till en annan, till exempel från v7 till v8. Dessa uppgraderingar innehåller nya funktioner, förbättringar, kompatibilitets- och säkerhetsuppdateringar samt korrigeringar.
* **Mindre uppgraderingar**, från en mindre version till en annan, till exempel från v8.5 till v8.6. Dessa uppgraderingar innehåller förbättringar, kompatibilitets- och säkerhetsuppdateringar samt korrigeringar.
* **Patch upgrades**, från en patch-version till en annan, till exempel från v8.5.1 till v8.5.2. Dessa uppgraderingar innehåller säkerhetsuppdateringar och korrigeringar.

Detaljerad information om varje ny version finns i [Versionsinformation](release-notes.md).

För att konfigurationen ska bli stabil rekommenderar Adobe att du installerar **exakt samma version** på alla era kampanjservrar. Om inte annat anges i [Versionsinformation](release-notes.md)måste klientkonsolen vara aktiverad **exakt samma version** som serverinstansen. Lär dig hur du uppgraderar din klientkonsol [på den här sidan](../start/connect.md#upgrade-ac-console).

När en ny Campaign-version är tillgänglig uppgraderas din infrastruktur av Adobe utan någon ytterligare åtgärd som kund hos Campaign Managed Services.

Observera att du som kund måste se till att du använder de senaste versionerna av systemen som stöds i [Kompatibilitetsmatris](compatibility-matrix.md).


## Vanliga frågor och svar {#upgrades-faq}

### Hur kontrollerar jag Campaign-versionen? {#version}

Om du vill kontrollera vilken Campaign-version du har går du till **Hjälp > Om...** från klientkonsolen.

![](assets/ac-version.png)

Du kommer åt följande information:

* The **version** numret på klientkonsolen och programservern. I exemplet ovan är versionen 8.1.5 för både klientkonsolen och programservern.
* SHA-talet mellan parenteser.
* Länk till Adobe kundtjänst.
* Länkar till Adobe sekretesspolicy, användarvillkor och cookies-policy.

### Hur får jag information om releasen av en ny version? {#upgrades-0}

Nya versioner och vilka ändringar de gör visas i [Versionsinformation](release-notes.md). När en ny version är tillgänglig kontaktar Adobe dig och uppgraderar dina miljöer.

Om du vill få information om nya releaser för Experience Cloud kan du prenumerera på [Produktuppdatering Adobe Priority](https://www.adobe.com/se/subscription/priority-product-update.html){target="_blank"}.

Du kan också besöka [Campaign Community](https://experienceleaguecommunities.adobe.com/t5/custom/page/page-id/Community-TopicsPage?style=all&amp;sort=date&amp;order=desc&amp;filters=adobe-campaign-classic-community&amp;topic=Campaign+v8){target="_blank"} för att få information om uppdateringar.


### Varför behöver min organisation den här uppgraderingen? {#upgrades-1}

Genom att uppgradera din infrastruktur till den senaste versionen kan du säkerställa att ditt konto är skyddat mot sårbarheter och att du använder den uppdaterade prestandatekniken.

Normalt innebär en uppgradering till den senaste versionen följande:

* Förbättrad säkerhet

  Säkerheten kräver konstant fokus och förebyggande underhåll. Säkerhetsrisker är aktuella och kan inte ignoreras: varje uppgradering för Campaign förbättrar säkerheten. Dessa uppgraderingar måste tillämpas på alla era Campaign-instanser och även på klientkonsolen. En kombination av tekniker används för att driva Adobe Campaign att samarbeta och leverera värde. All denna teknik måste hållas uppdaterad?

* Förbättrat stöd

  De flesta kritiska problemen löses faktiskt med uppgraderingar och kan undvikas. Regelbundna uppgraderingar hjälper till att minska utmaningarna och öka effektiviteten genom att eliminera dessa utmaningar. Arbetsvolymen för kundtjänst minskar, vilket ger snabbare lösningar och mer uppmärksamhet åt de problem som inte är relaterade till uppgraderingar.


* Bättre underhåll och stabilitet

  Med tiden kan Adobe Campaign-teamet hitta sätt att förbättra produktens stabilitet och prestanda samt åtgärda kända fel. Uppgraderingen håller instansen uppdaterad med dessa förbättringar och eliminerar vanliga utmaningar som organisationer som upplever snabb tillväxt och/eller komplexitet i sina Campaign-instanser ställs inför. Förbättringar i teknikstacken Campaign känns både i marknadsförings- och IT-team i organisationen.


### Hur ser uppgraderingen ut och när släpps den? {#upgrades-2}

Om ditt konto har identifierats som en v8-kund som behöver uppgradera till en ny version meddelar Adobe dig direkt.

Adobe-teamet är här för att leda och vägleda organisationen genom den här resan. Vi har organiserat ett team med dedikerade kundtjänstrepresentanter, produktchefer, ingenjörer och TechOps-specialister samt produktkonsulter för att hjälpa till och säkerställa att upplevelsen är smidig.
