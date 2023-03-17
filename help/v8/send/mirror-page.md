---
title: Lägg till en länk till spegelsidan
description: Lär dig hur du skapar en länk till spegelsidan
feature: Email
role: User
level: Beginner
source-git-commit: edb099b3e882d857752af76798012ccd1c5a99be
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Om sidan för e-postspegling{#mirror-page}

Spegelsidan är en onlineversion av ditt e-postmeddelande.

De flesta e-postklienter återger bilder utan problem, men vissa förinställningar kan undvika att visa bilder av säkerhetsskäl. Användare kan bläddra till den spegelsida som finns i ett e-postmeddelande, t.ex. om de får problem med återgivningen eller om det finns skadade bilder när de försöker visa dem i sin inkorg. Vi rekommenderar även att du tillhandahåller en onlineversion av tillgänglighetsskäl eller för att uppmuntra social delning.

Spegelsidan som genererats av Adobe Campaign innehåller alla personaliseringsdata.

## Lägg till en länk till spegelsidan{#link-to-mirror-page}

Det är bra att infoga en länk till spegelsidan. Den här länken kan till exempel vara Visa det här e-postmeddelandet i webbläsaren och finns ofta i sidhuvudet eller sidfoten i ett e-postmeddelande.

I Adobe Campaign kan du infoga en länk till spegelsidan i e-postinnehållet med den dedikerade **personaliseringsblock**. Spegelsidan genereras som standard bara om länken infogas i innehållet i meddelandet.

<!--For more on personalization blocks insertion, refer to [Personalization blocks](personalization-blocks.md).-->

## Generering av spegelsida{#mirror-page-generation}

Som standard genereras spegelsidan automatiskt av Adobe Campaign om e-postinnehållet inte är tomt, och om det innehåller en länk till spegelsidan (även Spegellänk).

Du kan styra genereringsläget för e-postspeglingssidan. Alternativ finns i leveransegenskaperna. Så här öppnar du de här alternativen:

1. Bläddra till **[!UICONTROL Validity]** -fliken i e-postegenskaperna.
1. I **Hantering av spegelsidor** -avsnittet, kontrollera **[!UICONTROL Mode]** nedrullningsbar lista.

![](assets/mirror-page-generation.png)

Förutom standardläget finns följande alternativ:

* **[!UICONTROL Force the generation of the mirror page]**: Använd det här läget för att generera spegelsidan även om ingen länk till spegelsidan infogas i leveransen.
* **[!UICONTROL Do not generate the mirror page]**: Använd det här läget för att undvika att en spegelsida genereras, även om länken finns i leveransen.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: Använd det här alternativet för att aktivera åtkomst till spegelsidans innehåll, med personaliseringsdata, i leveransloggfönstret. Så här kommer du åt den här spegelsidan: när leveransen är klar öppnar du den och bläddrar till **[!UICONTROL Delivery]** -fliken. Välj en mottagare och klicka på **[!UICONTROL Display the mirror page for this message...]** länk. Spegelsidan visas på en ny flik.

