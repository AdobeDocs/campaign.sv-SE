---
product: campaign
title: Kom igång med distribuerad marknadsföring
description: Kom igång med distribuerad marknadsföring
feature: Distributed Marketing
source-git-commit: 2b1dec4b9c456df4dfcebfe10d18e0ab01599275
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 0%

---

# Kom igång med distribuerad marknadsföring{#about-distributed-marketing}



Adobe Campaign erbjuder **Distribuerad marknadsföring** ansökan om genomförande av samverkanskampanjer mellan centrala enheter (huvudkontor, marknadsavdelningar osv.) och lokala enheter (säljställen, regionala organ osv.). Detta samarbete bygger på en delad arbetsyta som kallas **[!UICONTROL list of campaign packages]**, där centralt skapade kampanjmallar och instanser erbjuds lokala enheter.

Den centrala enheten tillhandahåller kampanjer som lokala enheter kan använda. Kampanjer materialiseras av paket som representerar antingen lokala kampanjer eller samarbetskampanjer. För att kunna använda en kampanj måste den lokala enheten beställa den och ordern måste godkännas.

>[!CAUTION]
>
>Modulen Distribuerad marknadsföring är en **Campaign** alternativ. Kontrollera licensavtalet.

## Terminologi {#terminology}

* **Centrala enheter**

   Centrala enheter består av marknadsföringsoperatörer som ansvarar för att specificera kommunikation och hjälpa lokala enheter att genomföra marknadsföringskampanjer.

   Den distribuerade marknadsföringsmodulen gör det möjligt för den centrala enheten att:

   * skapa marknadsföringskampanjer för lokala enheter,
   * öka de lokala enheternas grad av självbestämmande när det gäller val av kommunikation, målgruppsanpassning, innehåll m.m. mellan kunder och potentiella kunder.
   * hantera och kontrollera kostnader,
   * hantera ett nätverk av myndigheter.

* **Lokala enheter**

   Lokala enheter kan vara myndigheter, butiker eller grupper av specifika lokala aktörer (nationella eller regionala chefer, varumärkesansvariga osv.).

   Distribuerad marknadsföring ger lokala enheter större självständighet samtidigt som man optimerar kostnaderna för att genomföra kampanjen.

* **Lokalisering**

   Lokalisering är en lokal enhets förmåga att ändra mål och innehåll för en kampanj. Möjlig lokaliseringsnivå beror på kampanjtypen och dess implementering.

* **Lista över kampanjpaket**

   Listan över kampanjpaket innehåller kampanjer som är tillgängliga för lokala entiteter.

* **Kampanjpaket**

   Mall (eller kampanjinstans) som har skapats av en central enhet och gjorts tillgänglig för en uppsättning lokala enheter.

* **Lokal kampanj**

   En lokal kampanj är en instans som skapats från en mall som refereras i listan med **[!UICONTROL campaign packages]** med **specifikt körningsschema**. Syftet är att tillgodose ett lokalt kommunikationsbehov med hjälp av en kampanjmall som har konfigurerats och konfigurerats av den centrala enheten.

   Den lokala enhetens grad av självbestämmande beror på det genomförande som används.

   Se [Skapa en lokal kampanj](creating-a-local-campaign.md).

* **Samverkande kampanj**

   En samverkanskampanj är en kampanj vars **körningsschema har definierats** av den centrala enhet som den lokala enheten får använda. Innehållet är detsamma för varje lokal enhet, men kostnaderna delas. Delta genom att lokala enheter prenumererar på samarbetskampanjen.

   * **[!UICONTROL Collaborative campaign (by form)]**: rekommenderas för kampanjer som omfattar upp till 300 lokala enheter. Den lokala enheten kan ange fördefinierade parametrar för målinriktning och innehållspersonalisering i ett webbformulär. Formuläret kan vara ett Adobe Campaign-formulär eller ett externt formulär (extranät-klient). En funktionell administratör kan definiera och konfigurera formuläret baserat på en formulärmall som definieras av integratorn. För att kunna beställa kampanjen behöver den lokala enheten bara webbåtkomst.
   * **[!UICONTROL Collaborative campaign (by campaign)]**: Rekommenderas för kampanjer som riktar sig till dussintals lokala enheter. Den här typen av kampanj skapar underordnade kampanjer för varje lokal enhet. När **[!UICONTROL collaborative campaign (by campaign)]** godkänns av den centrala enheten, görs kampanjen tillgänglig för den lokala enheten, som kan ändra den. Körningen synkroniseras automatiskt mellan överordnade och underordnade kampanjer. Den lokala enheten måste ha tillgång till en instans för att kunna beställa en kampanj och delta i den.
   * **[!UICONTROL Collaborative campaign (by target approval)]**: Rekommenderas för kampanjer som riktar sig till flera tusen lokala enheter. Lokal enhet tar emot en kontaktlista som har fördefinierats av den centrala enheten. Den lokala enheten avgör om vissa kontakter ska behållas eller inte baserat på kampanjinnehållet via ett webbformulär. Lokala enheter dras från listan med valda kontakter. För att delta i kampanjen behöver den lokala enheten bara tillgång till webben.
   * **[!UICONTROL Collaborative campaign (simple)]**: Detta läge garanterar kompatibilitet med specifika körningsprocesser i tidigare versioner.

   Se [Skapa en samverkanskampanj](creating-a-collaborative-campaign.md).

**Beställa kampanjpaket**

Om en lokal enhet registrerar för en kampanj görs detta i en order som grupperar all information som är relativ till kampanjlokaliseringen.

## Arbetsyta {#workspace}

Listan med kampanjpaket finns i **Kampanjer** tab: klicka på **[!UICONTROL Campaign packages]** länk.

![](assets/mkg_dist_home_local_op.png)

I det här fönstret kan alla lokala operatörer visa kampanjer som är tillgängliga för deras lokala myndighet.

När det gäller centrala myndigheter visar det här fönstret alla paket som är tillgängliga i listan över kampanjpaket och erbjuder ytterligare länkar för redigering av listan.

## Operatörer och enheter {#operators-and-entities}

Börja med att ange operatorer för centrala och lokala enheter via **[!UICONTROL Access management]** mapp.

![](assets/s_advuser_mkg_dist_tree.png)

### Operatorer {#operators}

Du måste skapa centrala och lokala operatorer.

Centrala operatorer måste tillhöra **[!UICONTROL Central management]** operatorgruppen eller har **[!UICONTROL CENTRAL]** namngiven höger.

Lokala operatorer måste tillhöra **[!UICONTROL Local management]** operatorgruppen eller har **[!UICONTROL LOCAL]** namngiven höger. De måste också vara kopplade till sin lokala enhet.

![](assets/s_advuser_mkg_dist_local_create.png)

### Organisationsenheter {#organizational-entities}

Om du vill skapa en organisationsenhet klickar du på **[!UICONTROL Administration > Access management > Organizational entities]** och klicka på **[!UICONTROL New]** -ikonen ovanför listan med enheter.

![](assets/s_advuser_mkg_dist_local_list.png)

Varje organisationsenhet innehåller identifieringsinformation (etikett, internt namn, kontaktinformation osv.) och grupper som deltar i ordergodkännandeprocessen. Dessa definieras i **[!UICONTROL Notifications and approvals]** i **[!UICONTROL General]** -fliken.

* Definiera en paketmeddelandegrupp: -operatorer i den här gruppen får ett meddelande varje gång ett nytt paket läggs till i listan över kampanjpaket och varje gång en kampanj blir tillgänglig.
* Välj den grupp med granskare som ansvarar för att godkänna order, dvs. de som ansvarar för att godkänna kampanjer som beställts av den lokala enheten.
* Slutligen väljer du den grupp med granskare som ansvarar för att godkänna den lokala kampanjen (mål, innehåll, budget osv.). Den här gruppen kan läggas till när du beställer en kampanj, beroende på mallen.

>[!NOTE]
>
>Godkännandeprocessen presenteras i [Godkännandeprocess](creating-a-local-campaign.md#approval-process) -avsnitt.

## Implementering {#implementation}

Distribuerade marknadsföringskampanjer skapas och publiceras av den centrala enheten. De får användas av både lokala och centrala enheter efter behov.

Implementeringsproceduren beror på vilken typ av kampanjpaket som används och delegeringsnivåerna för den lokala enheten.

### Integreringsuppgifter {#integrator-side}

1. Skapa lokala enheter.
1. Länka mottagare med operatorer som hanterar lokala enheter.

   ![](assets/mkg_dist_local_entity_association.png)

1. Ange rättigheter och bläddringsregler för lokala entiteter
1. Ange den uppsättning fält som krävs för kampanjlokalisering:

   * Måldefinition och maximal storlek.
   * innehållsdefinition,
   * exekveringsplan (kontaktdatum och extraktionsdatum), **endast för lokala operatorer**,
   * tillägg av orderschema med alla nödvändiga ytterligare fält.

1. Skapa ett webbformulär (Adobe eller extranät) som gör att du kan visa lokaliseringsparametrar, utvärdera mål och budget samt förhandsgranska innehållet och godkänna ordern.

   För **samverkanskampanjer (genom målgodkännande)** skapar du tabellen där godkännandena för varje lokal enhet sparas.

### Funktionella administratörsuppgifter {#functional-administrator-side}

Dessa steg måste utföras när varje kampanj skapas.

1. Uppdatera formuläret med fälten som används för kampanjlokalisering.
1. Skapa en instans från en lämplig kampanjmall (samarbetskampanj) eller duplicera kampanjmallen (lokal kampanj).
1. Konfigurera kampanjen med lokaliseringsfälten och formulärreferensen.
1. Publicera kampanjen.

### Lokala operatoruppgifter {#local-operator-side}

Dessa steg måste utföras för varje kampanj.

1. När du har fått ett meddelande om kampanjpaketets tillgänglighet anger du kampanjens plats (valfritt).
1. Utvärdera målet, budgeten osv.
1. Förhandsgranska kampanjinnehåll.
1. Beställ kampanjen.
