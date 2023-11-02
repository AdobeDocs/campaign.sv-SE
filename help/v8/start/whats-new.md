---
title: Nyheter i Campaign v8
description: Upptäck nyckelfunktionerna i Adobe Campaign v8, nyheter och vad du kan förvänta dig av den senaste versionen.
feature: Overview, Release Notes
role: User
level: Beginner
exl-id: 7771a02c-ebd4-48b6-b25e-6b6e420ad493
source-git-commit: f577ee6d303bab9bb07350b60cf0fa6fc9d3a163
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 5%

---

# Nyheter i Adobe Campaign v8? {#ac-gs-what-is-new}

Adobe Campaign v8 är utformat för marknadsförare i flera kanaler som behöver den bästa molnlösningen för kanalövergripande kampanjhantering i storföretagsskala. Den erbjuder robusta ETL- och datahanteringsfunktioner för att hjälpa till att utforma och strukturera den perfekta kampanjen. Dess orkestreringsmotor ger möjlighet till multitouch-marknadsföring med fokus på batchbaserade resor. Den levereras också tillsammans med en skalbar meddelandeserver i realtid som gör det möjligt för marknadsföringsteamen att skicka fördefinierade meddelanden baserat på en totalbelastning från alla IT-system för exempelvis lösenordsåterställning, orderbekräftelse, e-kvitto och mycket annat.

Adobe Campaign v8 har avsevärda förbättringar vad gäller infrastruktur, säkerhet, leveransbarhet och övervakning.

![](assets/home-page.png)

## Viktiga möjligheter{#key-capabilities}

Viktiga funktioner listas nedan.

### Central arbetsflödeshantering{#central-wf-mgt}

Förbättra hastighet och skala för alla delar av era marknadsföringskampanjer, från att skapa segment och förbereda meddelanden till leverans.

Adobe Campaign gör det enkelt för er att synkronisera era era kanaler med ett enda lättanvänt gränssnitt för kampanjsamordning. Så era onlinekanaler - som e-post, webben, mobiler och sociala kanaler - matchar era offlinekanaler, inklusive direktreklam, callcenter, butiker och så vidare. Det ger er möjlighet att ge era kunder en enhetlig och sammanhangsberoende upplevelse i både digitala och traditionella kanaler. Adobe Campaign gör det enkelt att leverera innehåll till alla vägar kunderna kan ta - i alla kanaler.

![](../assets/do-not-localize/glass.png) [Läs mer om Campaign-arbetsflöden](../config/workflows.md)

### Personlig e-postmarknadsföring {#perso-email-mkt}

Skapa personaliserade och sammanhangsberoende e-postmeddelanden som överensstämmer med resten av kundupplevelsen.

Med Adobe Campaign kan ni göra era e-postmeddelanden bättre, mer personaliserade och mer lönsamma. E-postmeddelanden är enkla att skapa och enkla att leverera. Campaign v8 ger er flexibilitet att utforma, personalisera, testa, förfina och förbättra alla meddelanden ni skickar.

![](../assets/do-not-localize/glass.png) [Läs mer om personaliseringsfunktioner](create-message.md)

### Kunddatahantering {#customer-data-mgt}

Se hela bilden av era kunder så att ni snabbt kan skapa personaliserade kampanjer i storföretagsskala.

Adobe Campaign hjälper er att skapa kundprofiler utifrån data som samlats in i alla era kanaler. Med den här profilen kan ni samordna kampanjer i alla kanaler. Genom att koppla samman alla era marknadsföringskanaler kan ni anpassa den resa varje kund ska ta på det sätt som passar dem bäst.

![](../assets/do-not-localize/glass.png) [Läs mer om hantering av kunddata](audiences.md)

### Kampanjhantering i toppklass {#best-in-campaign-mgt}

Adobe Campaign v8 ger marknadsförarna förstklassiga funktioner för att planera, lansera och mäta kampanjer i olika kanaler.

Funktionerna inkluderar en integrerad profil som ger en samlad bild av kunden. Datahantering och segmentering för att bygga upp målgrupper i stor skala. Hantering av flerkanaliga arbetsflöden för automatisering av kampanjer i flera kanaler och flervågor. Integrerad e-post som minskar beroendet av kostsamma ESP. Rapportering och analys för att förstå kundbeteende och kampanjresultat.

![](../assets/do-not-localize/glass.png) [Läs mer om kampanjhantering](campaigns.md)


### Anslutningar till Adobe Experience Platform {#connection-to-aep}

Adobe Campaign v8 stöder dataanslutningar med Real-Time CDP och Adobe Experience Platform, så att man kan utnyttja den enhetliga kundprofilen i realtid.

Dessutom är Adobe Campaign v8 integrerat med realtidsfunktionerna för resesamordning så att marknadsförarna kan återanvända samma mallar och leveransfunktioner i Adobe Campaign för att engagera kunderna i realtid. Dessa investeringar kommer att optimera Adobe Campaign kundupplevelse och frigöra nya användningsfall som möjligheten att lägga till individuella kundresor i realtid till kampanjer.

Ni kan också konfigurera prediktiv optimering av sändningstiden och prediktiv poängsättning med Journey AI samt öka antalet öppna samtal, antalet klick och intäkterna.

![](../assets/do-not-localize/glass.png) [Läs mer om Campaign-integreringar](../connect/integration.md)


### Hanterade Cloud Service {#acms-desc}

Adobe Campaign v8 är tillgänglig som en hanterad Cloud Service som ger proaktiv tillsyn, snabb varning och servicestyrning.

Adobe Managed Cloud Service ger marknadsförarna en smidigare, säkrare och skalbar lösning för kanalövergripande kampanjhantering med en låg total ägandekostnad. Det nya erbjudandet kombinerar tjänster med proaktiv tillsyn och snabb varning.

>[!NOTE]
>
>Den nya molnarkitekturen gör att Campaign kan effektivisera processer, minska kostnaderna, hantera risker och förbättra datasäkerheten. Din Campaign v8-miljö har ett dedikerat VPC (Virtual Private Cloud) som är förkonfigurerat för dig.

### Hastighet och skala {#speed-scale}

Adobe Campaign kan nu utnyttja molnbaserade databastekniker för att dramatiskt förbättra sin skala och hastighet.

[Campaign v8 Enterprise](../architecture/enterprise-deployment.md) ger begreppet **Fullständig federerad dataåtkomst** (FFDA): alla data är nu fjärranslutna till molndatabasen. Med det här nya erbjudandet förenklar Campaign v8 datahanteringen: inget index krävs i molndatabasen. Du behöver bara skapa tabellerna, kopiera data så kan du börja. [!DNL Snowflake] är Campaign Cloud-databasen, vilket ger er snabbhet och uthållighet: ingen överbelastning av systemaktivitetens toppar. Cloud-databastekniken kräver inget specifikt underhåll för att garantera prestandanivån.

![](../assets/do-not-localize/glass.png) [Läs mer om företagsdistribution (FFDA)](../architecture/enterprise-deployment.md)

>[!CAUTION]
>
>* Campaign v8 är **endast** finns som hanterad Cloud Service och kan inte distribueras på plats eller i hybridmiljöer.
>
>* Automatisk migrering från en befintlig Campaign Classic v7-miljö är inte tillgänglig än.


## Självbetjäningsadministratörsgränssnitt{#self-service-admin}

Som produktadministratör kan du hantera inställningar och spåra användningen av var och en av era Campaign v8-instanser med **Kampanjkontrollpanelen**.

Via ett intuitivt användargränssnitt kan administratörer övervaka användningen av nyckelresurser, utföra avancerade uppgifter som IP-adresser som tillåter listning, SFTP-lagringsövervakning, nyckelhantering med mera. Det här självbetjäningsgränssnittet ger dig större flexibilitet och hjälper dig att:

* Gör ändringar av inställningarna själv utan att kontakta Adobe Support
* Konfigurera inställningar baserat på olika affärsbehov vid olika tidpunkter
* kontrollera åtkomstinställningarna efter behov för att förbättra säkerheten

![](assets/subdomain1.png)

![](../assets/do-not-localize/glass.png) [Läs mer om Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html){target="_blank"}


