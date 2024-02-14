---
title: Förstå Campaign-komponenter och -processer
description: Förstå Campaign-komponenter och -processer
feature: Overview, Architecture, Configuration
role: User
level: Beginner
exl-id: 7db32bd8-a088-405f-9633-2968c28b13b0
source-git-commit: 79d916c4d65c0c55ec20f2f5850fec40fe4e99a3
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Förstå Campaign-komponenter och -processer {#components-and-processes}

Adobe Campaign är en lösning för flerkanalsmarknadsföring som automatiserar e-post-, mobil-, sociala och offlinekampanjer. Adobe Campaign ger er en central plats för att få tillgång till era kunddata och profiler. Använd Adobe Campaign för att samordna enhetliga upplevelser för era kunder, utforma, verkställa och personalisera er marknadsföring över alla kanaler, samtidigt som ni förbättrar kundupplevelserna på alla enheter och kontaktytor. Med Adobe Campaign kan ni hantera flera datakällor, definiera era målgruppssegment samt planera och genomföra flerstegskampanjer i flera kanaler via ett dra-och-släpp-gränssnitt för visuellt arbetsflöde.

Läs mer om Campaign-nyckelfunktioner i [den här sidan](../start/get-started.md).

## Kampanjkomponenter {#ac-components}

Adobe Campaign komponenter och global arkitektur beskrivs nedan.

![](assets/do-not-localize//ac-components.png)



### Beständigt lager{#persistance-layer}

Kampanjdatabaser används som beständiga lager och innehåller nästan all information och alla data som hanteras av Adobe Campaign. Detta inkluderar: funktionell information, som profiler, prenumerationer, innehåll, tekniska data, som leveransjobb och loggar, spårningsloggar samt arbetsdata (inköp, leads).

Databasens tillförlitlighet är av yttersta vikt eftersom de flesta Adobe Campaign-komponenter kräver åtkomst till databasen för att kunna utföra sina uppgifter (med undantag för omdirigeringsmodulen).

### Logiskt programlager{#logical-app-layer}

Kampanjens logiska programlager är enkelt att konfigurera för att tillgodose komplexa affärsbehov. Ni kan använda Campaign som en enda plattform med olika program som kombineras för att skapa en öppen och skalbar arkitektur. Varje Campaign-instans är en samling processer i programlagret, varav vissa är delade och vissa är dedikerade.

## Kampanjhanterade Cloud Service{#ac-managed-services}

Adobe Campaign v8 distribueras as a Managed Service: alla komponenter i Adobe Campaign, inklusive användargränssnittet, körningsmotorn och Campaign-databaserna är fullt värdar för Adobe, inklusive e-postkörning, spegelsidor, spårningsserver och externt riktade webbkomponenter som att avbeställa sidor/inställningscenter och landningssidor.

## Kampanjprocesser

Kampanjwebbservern styr åtkomsten till webbprocesser i Campaign. Javascript är serverspråket som används för centrala produktfunktioner och anpassning. Tomcat är back-end-motorn och är inbäddad i Campaign-produkten som en del av webbprocessen. Javascript används till exempel på JSP- eller JSSP-sidor för att återge dynamiskt innehåll.

![](assets/do-not-localize/ac-processes.png)

Kampanjklientkonsolen ansluter till webbservern med SOAP XML via HTTP. Webbservern tillhandahåller säkerhetsskiktet, skickar förfrågningarna till programlagret med JavaScript och de interna processerna i Campaign ger åtkomst till databasen med SQL.

Den övergripande kommunikationen mellan Campaign-processer beskrivs i följande fristående distributionsdiagram: alla Campaign-komponenter installeras på samma dator.

![](assets/do-not-localize//ac-standalone.png)

Användaren ansluter till Campaign-programservern med HTTP. Alla data och all information hanteras i Campaign-databasen. Om en Campaign-utvecklare utför konfigurationsändringar hämtas den i databasen. Om en marknadsförare skapar en ny kampanj hanteras all information och alla data som hör till den nya kampanjen också i databasen. När en marknadsförare kör en kampanj skickas e-postleveranser till profiler från Campaign-servern via SMTP-servern. När profiler interagerar med e-postleveranser, som att öppna e-postmeddelandet, skickas spårningsdata tillbaka till spårningsservern.

![](../assets/do-not-localize/glass.png) [Läs mer om kampanjprocesser](../architecture/general-architecture.md#dev-env).
