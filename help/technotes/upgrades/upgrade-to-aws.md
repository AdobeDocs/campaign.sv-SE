---
title: Uppgradering av infrastruktur för e-postutskick av kampanj
description: Uppgradering av infrastruktur för e-postutskick av kampanj
exl-id: f01e38ad-490e-4389-af5e-87beef533eb0
source-git-commit: 5ab598d904bf900bcb4c01680e1b4730881ff8a5
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 1%

---

# Uppgradering av infrastruktur för e-postutskick av kampanj {#migrate-infra-to-aws}

## Vad kommer att uppgraderas?{#aws-changes}

Som en del av vårt pågående arbete med att tillhandahålla en användarupplevelse i toppklass håller vi på att uppgradera vår e-posttjänst.

## Påverkas du?{#aws-impact}

Ändringen påverkar:

* Adobe Campaign Classic Managed Services
* Adobe Campaign Managed Cloud Services-kunder
* Adobe Campaign Standard On-demand-kunder

## När kommer uppgraderingen att ske?{#aws-timeline}

Uppgraderingarna av utvecklings- och mellanlagringsmiljöerna påbörjades i **oktober 2023**.

Uppgraderingarna av produktionsmiljöerna började **januari 2024**.

## Vad ska man förvänta sig?{#impact}

* Längden på varje uppgraderingsvåg varierar beroende på antalet påverkade Campaign-instanser. När en produktionsuppgraderingsvåg planeras kommer meddelandet att innehålla den beräknade varaktigheten.

* Kampanjinstanser, både i fas- och produktionsmiljöer, kan inte skicka e-post under uppgraderingsfönstret. Andra Campaign-funktioner förväntas inte påverkas.

## Vanliga frågor och svar {#aws-faq}

* **Är den här uppgraderingen obligatorisk?**

  Ja. Som Campaign-kund kräver din e-postsändningsfunktion att du använder en e-postsändningsinfrastruktur.

* **Vilka kunder riktar sig till den här uppgraderingen?**

  Miljöerna kommer att uppgraderas för alla Campaign-kunder som nämns ovan.

* **Vad är den förväntade nedtiden?**

  Längden på varje uppgraderingsvåg kan variera beroende på antalet påverkade Campaign-instanser. När en produktionsuppgraderingsvåg är schemalagd kommer meddelandet att innehålla en beräknad varaktighet.

* **Behöver kunden några åtgärder för att uppgradera?**

  Ingen åtgärd krävs. Adobe sköter uppgraderingsprocessen som körs automatiskt.

* **Vilken testning krävs av kunderna?**

  Vi förväntar oss inte att kunderna ska testa något i samband med uppgraderingsevenemanget. Om något problem uppstår kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/sv?support-solution=Campaign#support){target="_blank"}.


* **Kan jag begära en ändring av datum/tid för den schemalagda säkerhetsuppgraderingsplatsen?**

  Nej. Vi kan inte hantera eventuella begärda ändringar av det befintliga schemat eftersom detta troligtvis kommer att störa det tilldelade uppgraderingsevenemanget för en annan kund.

Om du har andra frågor kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/sv?support-solution=Campaign#support){target="_blank"}.
