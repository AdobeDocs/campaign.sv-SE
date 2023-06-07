---
title: Kom igång med profiler och målgrupper i Campaign
description: Lär dig hur du skapar och hanterar profiler och målgrupper i Campaign
feature: Audiences, Profiles
role: User
level: Beginner
exl-id: 43483085-8aa6-47e6-89e7-9211e37beaa4
source-git-commit: 290f4e9a0d13ef49caacb7a128ccc266bafd5e69
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 11%

---

# Kom igång med profiler och målgrupper{#gs-profiles-and-audiences}

Profiler är kontakter som lagras i Campaign-databasen, till exempel kunder, prenumeranter på en tjänst eller potentiella kunder. Det finns många sätt att skaffa profiler och bygga upp databasen: onlinesamling via webbformulär, manuell eller automatisk import av textfiler, replikering med företagsdatabaser eller andra informationssystem. Med Adobe Campaign kan ni införliva marknadsföringshistorik, inköpsinformation, preferenser, CRM-data och alla relevanta PI-data i en samlad vy för att analysera och vidta åtgärder. Profilerna innehåller all information som krävs för att målinrikta, kvalificera och spåra individer.



En profil är en post i **nmsRecipient** tabell eller en extern tabell som lagrar alla profilattribut, t.ex. förnamn, efternamn, e-postadress, cookie-ID, kund-ID, mobil-ID eller annan information som är relevant för en viss kanal. Andra tabeller som är länkade till mottagartabellen innehåller profilrelaterade data, till exempel leveransloggtabellen som innehåller poster för alla leveranser som skickas till mottagare. Läs mer om inbyggda profiler och mottagartabeller i [det här avsnittet](../dev/datamodel.md#ootb-profiles).

![](assets/recipients-in-explorer.png)

I Adobe Campaign **mottagare** är standardprofiler för att skicka leveranser (e-post, SMS, osv.).

Med mottagardata som lagras i databasen kan du filtrera målet som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

Om du vill fylla Adobe Campaign med profildata kan du:

* [importera datafiler](../start/import.md) från en extern datakälla, t.ex. ett CRM-system, eller en platt fil
* [skapa webbformulär](../dev/webapps.md) för att kunderna ska kunna ange sin egen information och skapa en egen profil
* [mappa till en extern databas](../connect/fda.md) var profiler lagras
* ange profiler manuellt i klientkonsolen enligt nedan:

![](assets/create-profile.png)

<!--You can also select your message audience in an external file: recipients are stored not in the database, but in files. These are known as “external” deliveries. These contacts can be imported or not in Adobe Campaign. [Learn more](external-profiles.md).-->

När du har importerat dem kan du skapa målgrupper för att skicka meddelanden. Lär dig skapa målgrupper [i det här avsnittet](create-audiences.md).