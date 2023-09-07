---
title: Migrera kampanjoperatorer till Adobe Identity Management System (IMS)
description: Lär dig hur du migrerar kampanjoperatorer till Adobe Identity Management System (IMS)
hide: true
hidefromtoc: true
source-git-commit: 11128dcb26119383b86aa62561ec0ce1a3c138ad
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 1%

---

# Migrera kampanjoperatorer till Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Från och med Campaign v8.6 förbättras autentiseringsprocessen till Campaign v8. Alla operatorer använder [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} bara för att ansluta till Campaign. Anslutning till användare/lösenord kommer inte längre att tillåtas. Adobe rekommenderar att du utför migreringen i Campaign v8.5.2 för att smidigt kunna migrera till Campaign v8.6.

I den här artikeln beskrivs stegen som krävs för att migrera en teknisk operatör till ett tekniskt konto på Adobe Developer-konsolen.

## Vad har ändrats?{#move-to-ims-changes}

Alla vanliga användare av Campaign bör redan ansluta till Adobe Campaign klientkonsol via sina Adobe ID via Adobe Identity Management System (IMS). I vissa äldre konfigurationer var dock användar-/lösenordsanslutningar fortfarande tillgängliga. Detta är inte längre tillåtet med Campaign v8.6.

Som en del av arbetet med att stärka säkerhets- och autentiseringsprocessen anropar nu Adobe Campaign Client-programmet Campaign-API:er direkt med IMS-kontotoken. Teknisk operatörsmigrering beskrivs i en särskild artikel som finns i [den här sidan](ims-migration.md).

Den här ändringen gäller från och med Campaign v8.5.2 och kommer att **obligatoriskt** starta Campaign v8.6.


## Påverkas du?{#migrate-ims-impacts}

Om operatörer i organisationen ansluter till Campaign-klientkonsolen med hjälp av sina inloggnings-/lösenord (dvs. inbyggd autentisering) påverkas du och måste migrera dessa operatorer till Adobe IMS enligt nedan.

IMS-migrering är en nödvändig säkerhetsåtgärd för att göra dina miljöer säkra och standardiserade, eftersom de flesta andra Adobe DX-program redan använder IMS.

## Hur migrerar jag?{#ims-migration-procedure}

### Förhandskrav{#ims-migration-prerequisites}

Innan du startar migreringsprocessen måste du kontakta din Adobe-representant (Transition Manager) så att de tekniska teamen i Adobe kan migrera dina befintliga operatörsgrupper och namngivna rättigheter till Adobe Identity Management System (IMS).

### Viktiga steg {#ims-migration-steps}

Viktiga steg för migreringen visas nedan:

1. Adobe uppgraderar dina miljöer till Campaign v8.5.2.
1. Efter uppgraderingen kan du fortfarande skapa nya användare med båda metoderna, som systemspecifik användare eller med IMS.
1. Din interna Campaign-administratör måste lägga till unika e-postmeddelanden till alla inbyggda användare på Campaign-klientkonsolen och bekräfta för din Adobe Transition Manager när detta är klart. Det här steget beskrivs i [det här avsnittet](#ims-migration-id).
1. Arbeta med Adobe för att säkra ett datum för när Adobe ska köra automatiserad migrering av icke-tekniska användare (operatörer) och produktprofiler. Det här steget kräver ett timmars fönster utan driftstopp för någon av dina förekomster.
1. Din interna Campaign-administratör validerar dessa ändringar och ger en sign-off. Efter den här migreringen får du inte längre skapa någon ytterligare operator som autentiseras med användarens inloggning och lösenord.

Nu kan du planera migrering av tekniska användare till IMS enligt [den här teknologin](ims-migration.md)och bekräfta för Adobe Transition Manager när du är klar.
Adobe markerar sedan migreringen som slutförd och aktiverar flaggorna för att blockera skapandet av nya inbyggda användare och inloggningen för inbyggda användare.

## Vanliga frågor och svar? {#ims-migration-faq}

### När kan du starta migreringen? {#ims-migration-start}

En förutsättning för övergången till Adobe Identity Management System (IMS) är att du uppgraderar din miljö till Campaign v8.5.2.

Du kan starta IMS-migrering på din scenmiljö när den har uppgraderats till Campaign v8.5.2 och därefter planera för produktionsmiljön.

### Vad händer efter uppgraderingen av version 8.5.2? {#ims-migration-after-upgrade}

När dina miljöer har uppgraderats till Campaign v8.5.2 kan du utföra migrering av Adobe Identity Management System (IMS).

Det går fortfarande att skapa nya inbyggda användare tills IMS-migreringen är klar.

### När är migreringen klar? {#ims-migration-end}

När slutanvändarmigreringen och den tekniska användarmigreringen till Adobe Identity Management System (IMS) är klar måste du kontakta Adobe Transition Manager så att Adobe kan markera migreringen som slutförd och blockera användargenerering från klientkonsolen och inloggning.


### Hur skapar man användare efter migreringen? {#ims-migration-native}

När den fullständiga IMS-migreringen är klar tillämpar Adobe de begränsningar som kommer att blockera skapandet av nya inbyggda användare. Dessa begränsningar tillämpas inte förrän IMS-migreringen är klar.

För nya kunder är det inte tillåtet att skapa nya inbyggda användare från början.

Som Campaign-administratör kan du bevilja behörigheter till användare i din organisation via Adobe Admin Console och Campaign Client Console. Användare loggar in på Adobe Campaign med sin Adobe ID. Läs mer i [den här dokumentationen](../../v8/start/gs-permissions.md).

### Hur lägger jag till e-post för befintliga användare? {#ims-migration-id}

Som kampanjadministratör måste du lägga till e-post-ID:n till alla inbyggda användare från klientkonsolen. Gör så här:

1. Anslut till klientkonsolen och bläddra till **Administration > Åtkomsthantering > Operatorer**
1. Välj den operator som ska uppdateras i operatorlistan.
1. Ange e-postadressen till operatorn i dialogrutan **Kontaktpunkter** -delen i operatorformuläret.
1. Spara ändringarna.


### Hur loggar jag in på Campaign via IMS? {#ims-migration-log}

Lär dig hur du ansluter till Campaign med din Adobe ID i [det här avsnittet](../../v8/start/connect.md).