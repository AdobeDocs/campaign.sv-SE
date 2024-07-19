---
title: Funktioner för förutsägande användarengagemang
description: Lär dig använda prediktiv sändningstid och engagemangsbedömning
feature: Send Time Optimization
role: User
level: Beginner
exl-id: 648fefcc-6476-4af8-9f0d-c9a87a7a3019
source-git-commit: 77ec01aaba1e50676bed57f503a9e4e8bb1fe54c
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 64%

---

# Optimering vid sändning och prediktiv poängsättning för engagemang{#optimize-message-delivery}

Med hjälp av AI och maskininlärning kan Adobe Campaign Scoring (Send-Time Optimization) och Predictive Engagement Scoring analysera och förutse öppningsfrekvenser, optimala sändningstider och sannolika bortfall baserat på historiska interaktionsvärden.

Adobe Campaign erbjuder två nya maskininlärningsmodeller: [Predictive Send Time Optimization](#predictive-send) och [Predictive Engagement Scoring](#predictive-scoring). Dessa två modeller är maskininlärningsmodeller som är specifika för att designa och leverera bättre kundresor.

>[!CAUTION]
>
>Den här funktionen är inte tillgänglig som en del av produkten. Det är endast tillgängligt för Adobe Campaign Managed Cloud Services-kunder som kör Adobe Campaign Classic v7 eller Adobe Campaign v8.
>
>För implementering krävs att Adobe Consulting används. Om du vill veta mer kan du kontakta din Adobe-representant.
>


## Prediktiv optimering av sändningstid{#predictive-send}

Med prediktiv optimering av sändningstid förutspås vilken som är den bästa sändningstiden för varje mottagarprofil för e-postöppningar eller -klick och för push-meddelanden-öppningar. För varje mottagarprofil anger poängen den bästa sändningstiden för varje veckodag och vilken veckodag som är bäst att använda för bästa resultat.

I modellen Predictive Send-Time Optimization finns det två undermodeller:

* Förutsägbar sändningstid för att öppnas är den bästa tidpunkt då ett meddelande ska skickas till kunden för att maximera chansen att det öppnas

* Förutsägbar sändningstid för att klickas på är den bästa tidpunkt då ett meddelande ska skickas till kunden för att maximera chansen att kunden klickar


**Modellindata**: Leveransloggar, spårningsloggar och profilattribut (ej PII)

**Modellutdata**: Bästa tiden att skicka ett meddelande (för öppningar och klick)

Utdatainformation:

* Beräkna den bästa tidpunkten på dagen för att skicka ett e-postmeddelande. Detta inom 7 dagar i en vecka med 1 timmes intervall (t.ex.: 09:00, 10:00, 11:00)
* Modellen visar den bästa dagen i veckan och den bästa timmen på den dagen
* Varje optimal tid beräknas två gånger: en gång för att maximera öppningsfrekvensen och en gång för att maximera klickfrekvensen
* 16 fält ges (14 för veckodagar och 2 för hela veckan):
   * den bästa tiden att skicka ett e-postmeddelande för att optimera klick för måndag – värden mellan 0 och 23
   * den bästa tiden att skicka ett e-postmeddelande för att optimera öppningar för måndag – värden mellan 0 och 23
   * ...
   * den bästa tiden att skicka ett e-postmeddelande för att optimera klick för söndag – värden mellan 0 och 23
   * den bästa tiden att skicka ett e-postmeddelande för att optimera öppningar för söndag – värden mellan 0 och 23
   * ...
   * den bästa dagen att skicka ett e-postmeddelande för att optimera öppningarna för hela veckan – måndag till söndag
   * den bästa tiden att skicka ett e-postmeddelande för att optimera öppningar för hela veckan – värden mellan 0 och 23


Prediktiv optimering av sändningstid lagras på profilnivå:

![](assets/sto-schema.png)


>[!NOTE]
>
>Modellen behöver minst en månads data för att ge ett bra resultat. Dessa prediktiva funktioner gäller endast e-post- och push-kanaler.
>


## Prediktiv poängsättning för engagemang {#predictive-scoring}

Predictive Engagement Scoring förutser sannolikheten för att en mottagare engagerar sig i ett meddelande samt sannolikheten för att avanmäla sig inom 7 dagar efter nästa e-postutskick. Sannolikheten för detta delas upp ytterligare i grupper efter den förväntade nivån av engagemang med ert innehåll: högt, medelhögt eller lågt. Dessa modeller ger också en percentil för avbruten risk för kunderna för att förstå var en viss kunds rangordning är i förhållande till andra.

Med förutsägande engagemangsbedömning kan du:

* **Välja en målgrupp**: genom att använda frågeaktiviteten kan du välja målgruppen som ska interagera med ett visst meddelande
* **Exkludera en målgrupp**: genom att använda frågeaktiviteten kan du ta bort målgruppen för att avbryta prenumerationen
* **Anpassa**: personalisera meddelanden baserat på nivå av engagemang (mycket engagerade användare får ett annat budskap än de som inte är engagerade)

I den här modellen används flera olika poäng för att ange:

* **Engagemangsbedömning per öppning/engagemangsbedömning per klick**: det här värdet matchar sannolikheten för att en prenumerant ska interagera med ett visst meddelande (öppna eller klicka). Värdena kan ligga mellan 0,0 och 1,0.
* **Sannolikheten att avbryta prenumerationen**: det här värdet matchar sannolikheten för att mottagaren avbeställer e-postkanalen när ett e-postmeddelande öppnas. Värdena kan ligga mellan 0,0 och 1,0.
* **Kvarhållningsnivå**: det här värdet rangordnar användare på tre nivåer: låg, medel och hög. Högt värde är mest sannolikt att stanna kvar hos varumärket och lågt värde är mest sannolikt att avbryta prenumerationen.
* **Procentuell rangordning för kvarhållning**: profilrangordning beträffande sannolikheten att avbryta prenumerationen. Värdena kan ligga mellan 0,0 och 1,0. Om kundlojaliteten till exempel är 0,953 stannar den här mottagaren troligtvis kvar med varumärket och är mindre benägen att avbryta prenumerationen än 95,3 % av alla mottagare.

>[!NOTE]
>
>Dessa förutsägande funktioner gäller endast för e-postleveranser.
>
>Modellen behöver minst en månads data för att ge ett bra resultat.

**Indata från modellen**: leveransloggar, spårningsloggar och specifika profilattribut

**Utdata från modellen**: ett profilattribut som beskriver profilens poäng och kategori
