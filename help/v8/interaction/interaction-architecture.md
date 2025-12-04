---
title: Förstå arkitekturen för kampanjinteraktion
description: Grundläggande om arkitektur för kampanjinteraktion
feature: Interaction, Offers
role: Developer
level: Beginner
exl-id: 7a710960-7e41-4462-bd5e-18e874aa46f8
source-git-commit: 00d9c3229b7bbabfec3b1750ae84978545fdc218
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# Förstå kampanjinteraktionsmiljöer och -arkitektur

## Miljöer {#environments}

Det finns två miljöer för varje målinriktningsdimension som används vid hantering av erbjudanden:

* En **design**-miljö där erbjudandehanteraren tar hand om att skapa och kategorisera erbjudanden, redigera dem och starta godkännandeprocessen så att de kan användas. Reglerna för varje kategori, erbjudandeutrymmet som erbjudandena kan presenteras på och de fördefinierade filter som används för att definiera ett erbjudandes behörighet definieras också i den här miljön.

  Kategorier kan också publiceras manuellt i onlinemiljön.

  Processen för att godkänna erbjudanden beskrivs i avsnittet [.](interaction-offer.md#approve-offers)

* En **live**-miljö där godkända erbjudanden från designmiljön samt de olika erbjudandeutrymmena, filtren, kategorierna och reglerna som är konfigurerade i designmiljön finns. Under ett anrop till erbjudandemotorn kommer motorn alltid att använda erbjudanden från den aktiva miljön.

Erbjudandet gäller endast de erbjudanden som valts under godkännandeprocessen. Därför kan ett erbjudande vara direktsänt men oanvändbart på ett erbjudande som också är direktsänt.

## Inkommande och utgående interaktioner {#interaction-types}

Adobe Campaign Interaction Module föreslår två typer av interaktioner:

* **inkommande** interaktioner, initierade av en kontakt. [Läs mer](interaction-present-offers.md)
* **utgående** interaktioner, initierade av en kampanjleveranshanterare. [Läs mer](interaction-send-offers.md)

Dessa två typer av interaktioner kan utföras antingen i **enställigt läge** (erbjudandet beräknas för en enskild kontakt) eller i **gruppläge** (erbjudandet beräknas för en uppsättning kontakter). I allmänhet utförs inkommande interaktioner i enställigt läge och utgående interaktioner utförs i batchläge. Det kan dock finnas vissa undantag, till exempel för [transaktionsmeddelanden](../send/transactional.md), där den utgående interaktionen utförs i enställigt läge.

Så snart ett erbjudande kan eller måste presenteras (enligt de konfigurationer som gjorts) spelar erbjudandemotorn rollen som mellanhand: den beräknar automatiskt bästa möjliga erbjudande för en kontakt bland de tillgängliga genom att kombinera de data som tas emot om kontakten och de olika regler som kan tillämpas enligt applikationen.

![](assets/architecture_interaction2.png)

## Distribuerad arkitektur

**Interaction** -modulen implementeras i en distribuerad arkitektur för att kunna stödja skalbarhet och tillhandahålla dygnet runt-service på den inkommande kanalen. Den här typen av arkitektur används redan med [Message Center](../architecture/architecture.md#transac-msg-archi) och består av flera instanser:

* en eller flera kontrollinstanser som är dedikerade till den utgående kanalen och som innehåller bas för design av marknadsföring och miljö
* en eller flera körningsinstanser som är dedikerade till inkommande kanal

![](assets/interaction_powerbooster_schema.png)

Kontrollinstanser är dedikerade till den inkommande kanalen och innehåller katalogversionen online. Alla instanser av exekvering är oberoende och dedikerade till ett kontaktsegment (till exempel en exekveringsinstans per land). Anrop till erbjudandemotorn måste utföras direkt på körningen (en specifik URL per körningsinstans). Eftersom synkroniseringen mellan instanser inte är automatisk måste interaktioner från samma kontakt skickas via samma instans.

### Synkronisering {#synchronization}

Synkronisering av erbjudanden utförs via paket. I körningsinstanser föregås alla katalogobjekt av det externa kontonamnet. Detta innebär att flera kontrollinstanser (till exempel utvecklings- och produktionsinstanser) kan stödjas på samma körningsinstans.

>[!CAUTION]
>
>Använd korta och explicita interna namn.

Erbjudandena distribueras automatiskt och publiceras sedan på körnings- och kontrollinstanser.

Erbjudanden som tas bort i designmiljön är inaktiverade på alla onlineförekomster. Föråldrade offerter och erbjudanden tas automatiskt bort i alla instanser efter tömningsperioden (som anges i varje instans distributionsassistent) och glidperioden (som anges i de inkommande förslagens typologiregler).

![](assets/interaction_powerbooster_schema2.png)

Ett arbetsflöde skapas för varje miljö och ett externt konto för förslagssynkronisering. Synkroniseringsfrekvensen kan justeras för varje miljö och externt konto.

Du måste känna till följande synkroniseringsmekanismer:

* Om du använder funktionen för säkerhetskopiering från en anonym miljö till en identifierad miljö måste dessa två miljöer finnas i samma körningsinstans.
* Synkroniseringen mellan flera körningsinstanser utförs inte i realtid. Interaktioner av samma kontakt måste skickas till samma instans. Kontrollinstansen måste dedikeras till den utgående kanalen (ingen realtid).
* Marknadsföringsdatabasen synkroniseras inte automatiskt. Marknadsföringsdata som används i viktnings- och berättigandereglerna måste dupliceras i körningsinstanser. Den här processen kommer inte som standard, du måste utveckla den under integreringsperioden.
* Propositionssynkronisering utförs uteslutande av FDA-anslutning.
* Om du använder Interaction och Message Center på samma instans, synkroniseras i båda fallen via FDA-protokollet.

### Paketkonfiguration {#packages-configuration}

Alla schematillägg som är direkt länkade till **Interaktion** (erbjudanden, erbjudanden, mottagare osv.) måste distribueras på körningsinstanserna.

Paketet **Interaction** är installerat på alla instanser (kontroll och körning). Det finns ytterligare två paket: ett paket för kontrollinstanserna och ett för varje körningsinstans.

>[!NOTE]
>
>När paketet installeras blir **long**-typfälten i tabellen **nms:proposition**, till exempel förslags-ID, **int64**-typfält. Den här typen av data beskrivs i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/schema-reference/schema-structure.html#mapping-the-types-of-adobe-campaign-dbms-data){target="_blank"}.

Varaktigheten för datalagring konfigureras för varje instans (via fönstret **[!UICONTROL Data purge]** i distributionsguiden). För körningsinstanser måste denna period motsvara det historiska djup som krävs för att typologiregler (glidande period) och regler för stödberättigande ska kunna beräknas.

På kontrollinstanserna:

1. Skapa ett externt konto per körningsinstans:

   ![](assets/interaction_powerbooster1.png)

   * Fyll i etiketten och lägg till ett kort och explicit internt namn.
   * Markera **[!UICONTROL Execution instance]**.
   * Markera alternativet **[!UICONTROL Enabled]**.
   * Slutför anslutningsparametrarna för körningsinstansen.
   * Alla körningsinstanser måste länkas till ett ID. Detta ID tilldelas när du klickar på knappen **[!UICONTROL Initialize connection]**.
   * Kontrollera vilken typ av program som används: **[!UICONTROL Message Center]**, **[!UICONTROL Interaction]** eller båda.
   * Ange det FDA-konto som används. En operator måste skapas för körningsinstanserna och måste ha följande läs- och skrivrättigheter i databasen för instansen i fråga:

     ```
     grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
     grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
     ```

   >[!NOTE]
   >
   >IP-adressen för kontrollinstansen måste auktoriseras för körningsinstanserna.

1. Konfigurera miljön:

   ![](assets/interaction_powerbooster2.png)

   * Lägg till listan med körningsinstanser.
   * För var och en av dem anger du synkroniseringsperiod och filtervillkor (till exempel per land).

     >[!NOTE]
     >
     >Om du råkar ut för ett fel kan du läsa arbetsflödena för synkronisering och visa meddelanden. Dessa finns i programmets tekniska arbetsflöden.

Om bara en del av marknadsföringsdatabasen dupliceras på körningsinstanserna av optimeringsskäl kan du ange ett begränsat schema som är länkat till miljön, så att användarna bara kan använda data som är tillgängliga på körningsinstanserna. Du kan skapa ett erbjudande med data som inte är tillgängliga för körningsinstanser. För att kunna göra detta måste du inaktivera regeln för de andra kanalerna genom att begränsa den här regeln för den utgående kanalen (**[!UICONTROL Taken into account if]**-fältet).

![](assets/ita_filtering.png)

### Underhållsalternativ {#maintenance-options}

Här är en lista över underhållsalternativ som är tillgängliga för kontrollinstansen:

>[!CAUTION]
>
>Dessa alternativ får endast användas för särskilda underhållsfall.

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`**: det senaste datumet då en miljö synkroniserades på en given instans.
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`**: det senaste datumet som offerter från ett givet schema synkroniserades från en instans till en annan.
* **`NmsInteraction_MapWorkflowId`**: Ett alternativ som innehåller listan över alla synkroniseringsarbetsflöden som har genererats.

Följande alternativ är tillgängligt för körningsinstanser:

**NmsExecutionInstanceId**: alternativ som innehåller instans-ID:t.

### Paketinstallation {#packages-installation}

Om din instans inte tidigare hade paketet **Interaction** behövs ingen migrering. Som standard kommer förslagstabellen att vara 64 bitar efter att paketen har installerats.

>[!CAUTION]
>
>Beroende på volymen av befintliga förslag i din instans kan den här åtgärden ta en stund.

* Om instansen har små eller inga förslag behövs ingen manuell ändring av förslagstabellen. Ändringen görs när paket installeras.
* Om instansen har många förslag är det bättre att ändra strukturen på förslagstabellen innan du installerar kontrollpaketen och kör dem. Vi rekommenderar att du kör frågorna under en period med låg aktivitet.

>[!NOTE]
>
>Om du har utfört specifika konfigurationer i förslagstabellen, anpassar du frågorna därefter.


Det finns två metoder:

**Arbetstabell** (rekommenderas)

```
CREATE TABLE NmsPropositionRcp_tmp AS SELECT * FROM nmspropositionrcp WHERE 0=1;
ALTER TABLE nmspropositionrcp_tmp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
INSERT INTO nmspropositionrcp_tmp SELECT * FROM nmspropositionrcp;
DROP TABLE nmspropositionrcp;
CREATE INDEX proposition_id ON NmsPropositionRcp (ipropositionid);
CREATE INDEX nmspropositionrcp_deliveryid ON NmsPropositionRcp (ideliveryid);
CREATE INDEX nmspropositionrcp_lastmodified ON NmsPropositionRcp (tslastmodified);
CREATE INDEX nmspropositionrcp_offerid ON NmsPropositionRcp (iofferid);
CREATE INDEX nmspropositionrcp_offerspaceid ON NmsPropositionRcp (iofferspaceid);
CREATE INDEX nmspropositionrcp_recipientidid ON NmsPropositionRcp (irecipientid);
ALTER TABLE nmspropositionrcp_tmp RENAME TO nmspropositionrcp;
```

**Ändra tabell**

```
ALTER TABLE nmspropositionrcp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
```
