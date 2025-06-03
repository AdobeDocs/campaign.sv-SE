---
title: Förstå Campaign-komponenter och -processer
description: Förstå Campaign-komponenter och -processer
feature: Overview, Architecture, Configuration
role: User
level: Beginner
exl-id: 7db32bd8-a088-405f-9633-2968c28b13b0
source-git-commit: e4f6c70ecdcf7414b5f49a43933cfd1c967a0905
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Förstå Campaign-komponenter och -processer {#components-and-processes}

Adobe Campaign är en lösning för flerkanalsmarknadsföring som automatiserar e-post-, mobil-, sociala och offlinekampanjer. Adobe Campaign ger er en central plats för att få tillgång till era kunddata och profiler. Använd Adobe Campaign för att samordna enhetliga upplevelser för era kunder, utforma, verkställa och personalisera er marknadsföring över alla kanaler, samtidigt som ni förbättrar kundupplevelserna på alla enheter och kontaktytor. Med Adobe Campaign kan ni hantera flera datakällor, definiera era målgruppssegment samt planera och genomföra flerstegskampanjer i flera kanaler via ett dra-och-släpp-gränssnitt för visuellt arbetsflöde.

Läs mer om Campaign-nyckelfunktioner på [den här sidan](../start/get-started.md).

## Kampanjkomponenter {#ac-components}

Adobe Campaign komponenter och global arkitektur beskrivs nedan.

![](assets/do-not-localize//ac-components.png)

### Presentationslager{#presentation-layer}

Du kan få åtkomst till Adobe Campaign via en Rich-klient, en Thin-klient eller en API-integrering.

* Rich Client

  Campaign Rich Client är ett program som kan kommunicera med Adobe Campaign programserver via standardprotokoll för Internet, som SOAP och HTTP. [Läs mer om Campaign Client Console](../start/connect.md).

* Tunn klient

  Med Adobe Campaign webbåtkomstfunktioner får du tillgång till en delmängd av Campaign-funktionerna via en webbläsare, med hjälp av ett HTML-användargränssnitt. Använd det här webbgränssnittet för att få åtkomst till rapporter, kontrollera och validera meddelanden, få åtkomst till kontrollpaneler med mera.  [Läs mer om Campaign Web Access](../start/connect.md).

* Externa program med API:er

  I vissa fall kan systemet anropas från externa program med hjälp av API:erna för webbtjänster som exponeras via SOAP-protokollet. [Läs mer om Campaign-API:er](../dev/api.md).

### Beständigt lager{#persistance-layer}

Kampanjdatabaser används som beständiga lager och innehåller nästan all information och alla data som hanteras av Adobe Campaign. Detta inkluderar: funktionell information, som profiler, prenumerationer, innehåll, tekniska data, som leveransjobb och loggar, spårningsloggar samt arbetsdata (inköp, leads).

Databasens tillförlitlighet är av yttersta vikt eftersom de flesta Adobe Campaign-komponenter kräver åtkomst till databasen för att kunna utföra sina uppgifter (med undantag för omdirigeringsmodulen).

### Logiskt programlager{#logical-app-layer}

Kampanjens logiska programlager är enkelt att konfigurera för att tillgodose komplexa affärsbehov. Ni kan använda Campaign som en enda plattform med olika program som kombineras för att skapa en öppen och skalbar arkitektur. Varje Campaign-instans är en samling processer i programlagret, varav vissa är delade och vissa är dedikerade.

## Kampanjhanterade molntjänster{#ac-managed-services}

Adobe Campaign v8 är driftsatt i as a Managed Service: alla komponenter i Adobe Campaign, inklusive användargränssnittet, körningsmotorn och Campaign-databaserna är fullt värdar för Adobe, inklusive e-postkörning, spegelsidor, spårningsserver och externt riktade webbkomponenter som sidan/inställningscentret och landningssidorna.

## Kampanjprocesser

Kampanjwebbservern styr åtkomsten till webbprocesser i Campaign. Javascript är serverspråket som används för centrala produktfunktioner och anpassning. Tomcat är back-end-motorn och är inbäddad i Campaign-produkten som en del av webbprocessen. Javascript används till exempel på JSP- eller JSSP-sidor för att återge dynamiskt innehåll.

![](assets/do-not-localize/ac-processes.png)

Campaign Client Console ansluter till webbservern med hjälp av SOAP XML via HTTP. Webbservern tillhandahåller säkerhetsskiktet, skickar förfrågningarna till programlagret med JavaScript och de interna processerna i Campaign ger åtkomst till databasen med SQL.

<!--The overall communication between Campaign processes are described in the following standalone deployment diagram: all Campaign components are installed in the same machine.

![](assets/do-not-localize//ac-standalone.png) -->

Användaren ansluter till Campaign-programservern med HTTP. Alla data och all information hanteras i Campaign-databasen. Om en Campaign-utvecklare utför konfigurationsändringar hämtas den i databasen. Om en marknadsförare skapar en ny kampanj hanteras all information och alla data som hör till den nya kampanjen också i databasen. När en marknadsförare kör en kampanj skickas e-postleveranser till profiler från Campaign-servern via SMTP-servern. När profiler interagerar med e-postleveranser, som att öppna e-postmeddelandet, skickas spårningsdata tillbaka till spårningsservern.

[Läs mer om Campaign-processer](../architecture/general-architecture.md#dev-env).
