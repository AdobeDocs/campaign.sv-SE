---
product: campaign
title: Marknadsföringskampanjresurser, dokument och leveransdispositioner
description: Läs mer om kampanjdokument och leveransdispositioner för marknadsföring
feature: Campaigns
role: User
exl-id: 352f6cd5-777d-413d-af79-6f53444b336f
source-git-commit: c3f4ad0b56dd45d19eebaa4d2f06551c8fecac1d
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# Hantera resurser och dokument {#manage-assets-documents}

Du kan associera olika dokument med en kampanj: rapporter, foton, webbsidor, diagram osv. Dessa dokument kan ha vilket format som helst.

I en kampanj kan du även hänvisa till andra saker, som kampanjkuponger, specialerbjudanden som gäller ett visst varumärke eller en viss butik, osv. När dessa element ingår i en disposition kan de kopplas till en direktutskick. [Läs mer](#associating-and-structuring-resources-linked-via-a-delivery-outline).


>[!CAUTION]
>
>Den här funktionen är utformad för små resurser och dokument.

<!--
>[!NOTE]
>
>If you are using Campaign Marketing Resource Management module, you can also manage a library of marketing resources that are available for several users for collaborative work. [Learn more](../../mrm/using/managing-marketing-resources.md).
-->

## Lägga till dokument {#add-documents}

Dokument kan kopplas på kampanjnivå (sammanhangsberoende dokument) eller på programnivå (allmänna dokument).

Fliken **[!UICONTROL Documents]** innehåller:

* Listan över alla dokument som krävs för innehållet (mall, bilder osv.) som kan laddas ned lokalt av Adobe Campaign-operatörer med lämpliga rättigheter,
* Dokument som innehåller information för routern, om sådan finns.

Dokumenten är länkade till programmet eller kampanjen via fliken **[!UICONTROL Edit > Documents]**.

![](assets/op_add_document.png)

Du kan också lägga till ett dokument till en kampanj från den dedikerade länken på kontrollpanelen.

![](assets/add_a_document_in_op.png)

Klicka på ikonen **[!UICONTROL Detail...]** om du vill visa innehållet i en fil och lägga till information:

![](assets/add_document_details.png)

I kontrollpanelen grupperas dokument som är kopplade till kampanjen i avsnittet **[!UICONTROL Document(s)]**, som i följande exempel:

![](assets/edit_documents.png)

De kan också redigeras och ändras i den här vyn.

## Använd leveransdispositioner {#delivery-outlines}

En leveransöversikt är en strukturerad uppsättning element (dokument, butiker, kampanjkuponger osv.) som skapats av företaget och för en viss kampanj. Det används i samband med direktreklam.

Dessa element grupperas i leveranskonturer och varje leveransdisposition kopplas till en leverans. Den refereras i extraheringsfilen som skickas till **tjänstleverantören** för att kunna kopplas till leveransen. Du kan till exempel skapa en leveransdisposition som refererar till en enhet och de marknadsföringsbroschyrer som används i den.

För en kampanj kan du strukturera externa element som ska associeras med leveransen enligt vissa kriterier: relaterad enhet, kampanjerbjudande, inbjudan till en lokal händelse osv.

>[!CAUTION]
>
>Leveranskonturer är begränsade till direktreklamkampanjer.

### Skapa en leveransdisposition {#create-an-outline}

Om du vill skapa en leveransdisposition klickar du på underfliken **[!UICONTROL Delivery outlines]** på fliken **[!UICONTROL Edit > Documents]** i den aktuella kampanjen.

![](assets/add-a-delivery-outline.png)


>[!NOTE]
>
>Om du inte kan se den här fliken är den här funktionen inte tillgänglig för kampanjen, eller så är direktreklam inte aktiverad i din instans. Se [kampanjmallskonfigurationen](marketing-campaign-templates.md#campaign-templates) eller licensavtalet.

Klicka sedan på **[!UICONTROL Add a delivery outline]** och skapa en hierarki med konturer för kampanjen:

1. Högerklicka på trädets rot och välj **[!UICONTROL New > Delivery outlines]**.
1. Högerklicka på konturen som du just har skapat och välj **[!UICONTROL New > Item]** eller **[!UICONTROL New > Personalization fields]**.

![](assets/del-outline-add-new-item.png)

En disposition kan innehålla objekt, anpassningsfält och erbjuder:

* Objekten kan till exempel vara fysiska dokument som refereras och beskrivs här och bifogas till leveransen.
* Med personaliseringsfält kan du skapa personaliseringselement för leveranser i stället för mottagare. Det är därför möjligt att skapa värden som ska användas i leveranser för ett specifikt mål (välkomsterbjudande, rabatt osv.) De skapas i Adobe Campaign och importeras till dispositionen via länken **[!UICONTROL Import personalization fields...]**.

  ![](assets/del-outline-perso-field.png)

  De kan också skapas direkt i dispositionen genom att klicka på ikonen **[!UICONTROL Add]** till höger om listzonen.

  ![](assets/add-del-outline-button.png)


### Markera en kontur {#select-an-outline}

För varje leverans kan du välja den disposition som ska kopplas från det avsnitt som är reserverat för extraheringsdispositionen, som i följande exempel:

![](assets/select-delivery-outline.png)

Den markerade dispositionen visas sedan i fönstrets nedre del. Du kan redigera den med ikonen till höger om fältet eller ändra den med hjälp av listrutan:

![](assets/delivery-outline-selected.png)

På fliken **[!UICONTROL Summary]** i leveransen visas även den här informationen:

![](assets/delivery-outline-in-dashboard.png)

### Extraheringsresultat {#extraction-result}

I den fil som extraheras och skickas till tjänsteleverantören, namnet på konturen och, i förekommande fall, dess egenskaper (kostnad, beskrivning osv.) läggs till i innehållet enligt informationen i exportmallen som är kopplad till tjänsteleverantören.

I följande exempel läggs etiketten, den uppskattade kostnaden och beskrivningen av dispositionen som är kopplad till leveransen till i extraheringsfilen.

![](assets/campaign-export-template.png)

Exportmodellen måste vara kopplad till den tjänsteleverantör som valts för den aktuella leveransen. Se [det här avsnittet](providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).
