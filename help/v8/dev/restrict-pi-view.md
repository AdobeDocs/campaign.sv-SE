---
title: Begränsa PI-vy
description: Lär dig hur du begränsar PI-vyn
exl-id: 1b833745-71d7-430d-ac7d-c830c78ea232
source-git-commit: d2f4e54b0c37cc019061dd3a7b7048cd80876ac0
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Begränsa PI-vy{#restricting-pii-view}

## Översikt {#overview}

Om ni vill att marknadsföringsanvändare ska kunna få tillgång till dataposter men inte vill att de ska kunna se mottagarens personliga information, till exempel förnamn, efternamn eller e-postadress, ska ni följa riktlinjerna nedan för att skydda integriteten och förhindra att data missbrukas av vanliga kampanjoperatörer.

## Implementering {#implementation}

Ett specifikt attribut som kan tillämpas på ett element eller attribut har lagts till i scheman, det kompletterar det befintliga attributet **[!UICONTROL visibleIf]** . Attributet är: **[!UICONTROL accessibleIf]** . När det innehåller ett XTK-uttryck som är relaterat till den aktuella användarkontexten kan det utnyttja **[!UICONTROL HasNamedRight]** eller **[!UICONTROL $(login)]** , till exempel.

Du kan hitta ett exempel på ett mottagarschematillägg som visar den här användningen nedan:

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="xxl:nmsRecipientXl"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="xxl:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

Huvudegenskaperna är:

* **[!UICONTROL visibleIf]** : Döljer fälten från metadata, vilket innebär att de inte kan nås i en schemavy, kolumnmarkering eller ett uttrycksbyggare. Men detta döljer inga data. Om fältnamnet anges manuellt i ett uttryck visas värdet.
* **[!UICONTROL accessibleIf]** : Döljer data (ersätter dem med tomma värden) från den resulterande frågan. Om visibleIf är tomt får det samma uttryck som **[!UICONTROL accessibleIf]** .

Här följer konsekvenserna av att använda det här attributet i Campaign:

* Data visas inte med den generiska frågeredigeraren i konsolen,
* Data visas inte i översiktslistorna eller i postlistan (konsolen).
* Data blir skrivskyddade i detaljerad vy.
* Data kan bara användas i filter (vilket innebär att du fortfarande kan gissa värden om du använder vissa dikotomstrategier).
* Alla uttryck som byggs med ett begränsat fält blir begränsade till: lower(@email) blir lika tillgängligt som @email.
* I ett arbetsflöde kan du lägga till den begränsade kolumnen i målpopulationen som en extra kolumn i övergången, men den är fortfarande inte tillgänglig för Adobe Campaign-användare.
* När målpopulationen lagras i en grupp (lista) är de lagrade fälten desamma som datakällan.
* Data är inte tillgängliga för JS-kod som standard.

## Rekommendationer {#recommendations}

I varje leverans kopieras e-postadresser till **[!UICONTROL broadLog]** och **[!UICONTROL forecastLog]** tabeller: Därför måste även dessa fält skyddas.

Nedan visas ett exempel på ett loggtabellstillägg som implementerar detta:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!CAUTION]
>
>Begränsningen gäller endast icke-tekniska användare och isolerar inte data: en teknisk användare, med tillhörande behörigheter, kan hämta data.
