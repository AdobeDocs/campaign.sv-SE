---
title: God praxis för leverans
description: Lär dig de bästa sätten att designa och skicka leveranser med Adobe Campaign
feature: Email, Push, SMS, Direct Mail
role: User
level: Beginner
exl-id: cb6094eb-0010-4c62-9589-3b52fd60c2c2
source-git-commit: 768ebf4b350da61f0076eb9e43a16246be3b2628
workflow-type: tm+mt
source-wordcount: '2936'
ht-degree: 1%

---

# God praxis för leverans {#delivery-best-practices}

Läs om följande metodtips med leveransfunktionerna i Campaign.

## Optimera leverans {#optimize-delivery}

Innan du ens börjar skapa leveranser kan du vidta flera åtgärder för att skydda och optimera sändningsprocessen uppströms. I följande avsnitt beskrivs god praxis och rekommenderade procedurer för optimal konfiguration av Adobe Campaign.

### Plattformsprestanda

Flera faktorer kan direkt påverka serverprestanda och göra Campaign-plattformen långsammare:

* Antalet och typen för [personalisering](../send/personalize.md)-element: personalisering i e-postmeddelanden hämtar data från databasen för varje mottagare. för många personaliseringselement är mängden data som behövs för att förbereda leveransen större. Detta kan göra plattformen långsammare. Läs mer om skyddsprofiler för personalisering i [det här avsnittet](../send/personalize.md#perso-guardrails).

* Serverbelastningen: när marknadsföringsservern hanterar många olika uppgifter samtidigt kan prestandan försämras. Marknadsföringsservern måste koordinera alla inkommande och utgående data för alla leveranser för att säkerställa att data är korrekta och i tid.
För att undvika detta bör du samordna schemaläggningen av leveranser med övriga medlemmar i teamet för att säkerställa bästa möjliga prestanda.

* Arbetsflödeskörning: det är viktigt att du övervakar arbetsflödena för att undvika problem med plattformsprestanda. Följ riktlinjerna som visas [i det här dokumentet](../../automation/workflow/workflow-best-practices.md#execution-and-performance).

* Anslut till [funktionerna på Kontrollpanelen för kampanj](https://experienceleague.adobe.com/en/docs/control-panel/using/discover-control-panel/key-features){target="_blank"} för att övervaka plattformen med [funktionerna för prestandaövervakning](https://experienceleague.adobe.com/en/docs/control-panel/using/performance-monitoring/about-performance-monitoring){target="_blank"}.

#### Karantänhantering {#quarantine-management}

Det ligger i ditt bästa intresse att upprätthålla goda karantänhanteringsprocesser.

När du börjar skicka e-post på en ny plattform kan du använda en lista med adresser som inte är fullständigt kvalificerade. Om du skickar till ogiltiga adresser eller till honeypoadresser (postlådor som bara skapats för att lura skräppost) börjar detta minska din plattforms anseende. Bra processer för hantering av karantän hjälper till att: upprätthålla adresskvaliteten, undvika blockeringslista från internetleverantörer och minska felfrekvensen, påskynda leveranser och dataflöde.


Läs mer om hur du startar en ny plattform i [Adobe Deliverability Best Practices Guide](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-starting-new-platform){target="_blank"}.

Tekniska rekommendationer visas i [det här avsnittet](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations){target="_blank"}.


+++ **Läs om några metodtips**

* Om du har en lista med ogiltiga adresser rekommenderar Adobe att du importerar den till karantäntabellen via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Mottagare vars adresser sätts i karantän exkluderas som standard under leveransanalysen: de är inte riktade. Detta snabbar upp leveranserna eftersom felfrekvensen påverkar leveranshastigheten avsevärt. En e-postadress kan sättas i karantän när inkorgen är full eller om adressen inte finns.
Adobe Campaign hanterar felaktiga adresser beroende på vilken typ av fel som returneras. [Läs mer om karantäner](../send/quarantines.md)

* Vissa leverantörer av internetåtkomst betraktar automatiskt e-post som skräppost om frekvensen av ogiltiga adresser är för hög. Med karantän kan du därför undvika att läggas till i blockeringslista av dessa leverantörer.

+++



### Mekanisk för dubbel anmälan {#double-opt-in}

För att undvika att skicka meddelanden till ogiltiga adresser, begränsa felaktig kommunikation och förbättra avsändarens anseende rekommenderar Adobe att du använder en dubbel anmälningsmekanism för bekräftelse efter prenumeration. Detta bidrar till att säkerställa att mottagaren prenumererar avsiktligt.

## Använd mallar {#use-templates}

Leveransmallar ger ökad effektivitet genom färdiga scenarier för de flesta vanliga typer av aktiviteter. Med mallar kan marknadsförarna driftsätta nya kampanjer med minimal anpassning på kortare tid. [Läs mer om leveransmallar](../send/create-templates.md).

### Underdomäner och varumärken {#subdomains-and-branding}

När du hanterar flera varumärken i Adobe Campaign rekommenderar Adobe att du har en underdomän per varumärke. En bank kan till exempel ha flera underdomäner som motsvarar var och en av dess regionala myndigheter. Om en bank äger bluebank.com kan dess underdomäner vara @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com osv. Med en leveransmall per underdomän kan ni alltid använda rätt förkonfigurerade parametrar för varje varumärke, vilket undviker fel och sparar tid. Läs mer om anpassning av underdomäner i dokumentationen från [Kontrollpanelen för kampanj](https://experienceleague.adobe.com/en/docs/control-panel/using/subdomains-and-certificates/subdomains-branding){target="_blank"}.

### Konfigurera adresser {#configure-addresses}

Var noga med att följa följande riktlinjer:

* Avsändarens adress är obligatorisk för att tillåta att ett e-postmeddelande skickas. En del Internet-leverantörer (Internet Service Providers) kontrollerar avsändarens adress innan de accepterar meddelanden.
* En felformaterad adress kan leda till att den nekas av den mottagande servern. Du måste se till att rätt adress anges.
* Adressen måste uttryckligen identifiera avsändaren. Domänen måste ägas av och registreras hos avsändaren.
* Adobe rekommenderar att du skapar e-postkonton som motsvarar adresserna som angetts för leveranser och svar. Kontakta systemadministratören för meddelanden.

+++ **Steg för att konfigurera adresser i Campaign-gränssnittet**

Följ stegen nedan för att konfigurera adresser i Campaign-gränssnittet:

1. Klicka på länken **[!UICONTROL From]** i [leveransmallen](../send/create-templates.md). Ange inställningarna i fönstret **[!UICONTROL Email header parameters]**.

1. I fältet **[!UICONTROL Sender address]** kontrollerar du att adressdomänen är densamma som den underdomän som du har delegerat till Adobe. Du kan ändra den del som föregår @ men inte domänadressen.

1. I fältet **[!UICONTROL From]** använder du ett namn som är lätt att identifiera för mottagarna, till exempel ditt varumärkes namn, för att öka öppningshastigheten för dina leveranser. Om du vill förbättra mottagarens upplevelse ytterligare kan du lägga till en persons namn, till exempel&quot;Emma from Megastore&quot;.

1. I fälten **[!UICONTROL Reply address text]** används avsändarens adress som standard för svar. Adobe rekommenderar dock att man använder en befintlig riktig adress som till exempel kundtjänst för ert varumärke. Om en mottagare skickar ett svar kan kundtjänst hantera det.

### Konfigurera en kontrollgrupp {#set-up-control-group}

När leveransen har skickats kan du jämföra beteendet hos de uteslutna mottagarna med mottagarna som tog emot leveransen. Sedan kan ni mäta effektiviteten i era kampanjer. Läs mer om kontrollgrupper [det här avsnittet](../../automation/campaigns/marketing-campaign-target.md#add-a-control-group).

### Använd typografi för att tillämpa filter eller kontrollregler {#create-typologies}

En typologi innehåller kontrollregler som tillämpas under analysfasen innan ett meddelande skickas.

På fliken **[!UICONTROL Typology]** i mallens egenskaper kan du vid behov välja en anpassad typologi.

Om du till exempel vill ha bättre kontroll över utgående trafik kan du definiera vilka IP-adresser som kan användas genom att definiera en tillhörighet per underdomän och skapa en typologi per tillhörighet. Tillhörigheterna definieras i instansens konfigurationsfil. Kontakta Adobe Campaign-administratören.

Mer information om typologier finns i [det här avsnittet](../../automation/campaign-opt/campaign-typologies.md).

## Optimera ert innehåll {#optimize-content}

### Skapa personaliserat innehåll {#perso-content}

Om du vill anpassa dina meddelanden kan du använda mottagarnas data som lagras i databasen, eller som samlats in via spårning, landningssidor, prenumerationer osv. Grundläggande om Personalization presenteras i [det här avsnittet](../send/personalize.md).

+++ **Läs om några metodtips**

* Kontrollera dina personaliseringsinställningar - Kontrollera att meddelandeinnehållet är korrekt utformat för att undvika fel som kan relateras till personalisering. En Adobe Campaign-personaliseringstagg har alltid följande format: `<%=table.field%>`. Felaktig användning av parametrar i personaliseringsblock kan vara ett problem. Variabler i JavaScript bör till exempel användas på följande sätt:

  ``
  <%
  var brand = "xxx"
  %>
  ``

  Mer information om anpassningsblock finns i [det här avsnittet](../send/personalization-blocks.md).

* Förbered personaliseringsdata - Du kan förbereda personaliseringsdata i ett arbetsflöde för att förbättra analysen av leveransförberedelser. Detta bör användas särskilt om personaliseringsdata kommer från en extern tabell via FDA (Federated Data Access). Det här alternativet beskrivs i det här [här avsnittet](../send/personalization-data.md#optimize-personalization)
+++

### Bygg optimerat innehåll {#build-optimized-content}

När du skapar e-postmeddelanden bör du använda de allmänna bästa metoderna för e-postinnehåll.

+++ **Läs om några metodtips**

* Behåll designen enkel

* Tänk på mobilanvändare

* Undvik helt bildbaserade mejl

* Använda e-postsäkra teckensnitt

* Koda specialtecken

+++


### Subject line  {#subject-line-check}

Arbeta med e-postmeddelandets [ämnesrad](../send/personalization-fields.md#personalization-fields-uc) för att förbättra öppningsfrekvensen.


+++ **Läs om några metodtips**


* Undvik för långa motiv. Använd högst 50 tecken

* Undvik att använda upprepade ord som &quot;free&quot; eller &quot;offer&quot; som kan betraktas som spam

* Undvik versaler

* Använd inte specialtecken som &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

+++

### Spegelsida {#mirror-page-check}

Inkludera alltid en länk för spegelsida. Önskad position är högst upp i e-postmeddelandet. Läs mer om speglingssidan i [den här sidan](../send/mirror-page.md)

### Länk för att avbryta prenumeration {#unsub-link-check}

Länken för att avbeställa prenumerationer är viktig. Den måste vara synlig och giltig och formuläret måste vara funktionellt. Som standard kontrolleras om en avanmälningslänk har inkluderats när meddelandet analyseras av en inbyggd **[!UICONTROL Unsubscription link approval]** [typologiregel](../../automation/campaign-opt/control-rules.md) och en varning genereras om den saknas.

Lär dig hur du infogar en länk [för avanmälan i det här avsnittet](../send/personalization-blocks.md).

+++ **Använd den här bästa metoden**

Eftersom mänskliga fel alltid är möjliga bör du kontrollera att länken för avanmälan fungerar korrekt före varje gång du skickar. När du t.ex. skickar korrekturet kontrollerar du att länken är giltig, att formuläret är online och att fältet `No longer contact this recipient ` har ändrats till `Yes`.

+++

### E-poststorlek {#email-size-check}

För att undvika problem med prestanda och leverans är den rekommenderade maximala storleken på ett e-postmeddelande cirka **35 kB**. Om du vill kontrollera meddelandestorleken går du till fliken **[!UICONTROL Preview]** och väljer en testprofil. När meddelandet har genererats visas meddelandestorleken i det övre högra hörnet.


+++ **Läs om några metodtips**

* Ta bort överflödiga eller oanvända format

* Flytta en del av e-postinnehållet till en landningssida

* Minimera koden

Kontrollera att du har testat ändringarna innan du skickar det.

+++


### SMS-längd {#sms-length-check}

Som standard uppfyller antalet tecken i ett SMS GSM-system (Global System for Mobile Communications). SMS-meddelanden som använder GSM-kodning kan innehålla högst 160 tecken eller 153 tecken per SMS för meddelanden som skickas i flera delar.


+++ **Läs om några metodtips**

* Om du vill behålla alla tecken i SMS-meddelanden som de är, ska du inte aktivera transkribering för att t.ex. inte ändra egennamn.

* Om dina SMS-meddelanden innehåller många tecken som inte beaktas av GSM-standarden kan du aktivera transkribering för att begränsa kostnaderna för att skicka meddelanden. Läs mer [i det här avsnittet](../send/sms/smpp-external-account.md#smpp-transliteration).

* Du kan använda SMS-transkribering, som består i att ersätta ett tecken i ett SMS med ett annat när det tecknet inte beaktas av GSM-standarden. Observera att om du infogar anpassningsfält i innehållet i SMS-meddelandet kan det medföra tecken som GSM-kodningen inte tar hänsyn till. Som Campaign-administratör kan du aktivera teckentranskribering genom att markera motsvarande ruta på fliken SMPP-kanalinställningar i motsvarande **[!UICONTROL External account]**. [Läs mer](../send/sms/smpp-external-account.md#smpp-transliteration)

+++

### Undvik bifogade filer

Bifogade filer är fortfarande en av de vanligaste vektorerna för spridning av skadlig kod, särskilt när de skickas satsvis. Inkludera en säker länk till dokumentet i stället för att bifoga det. Detta garanterar ett extra säkerhetslager för att förhindra oavsiktlig omdistribution och minskar avsevärt riskerna för att meddelandet kommer att refuseras vid inkommande e-postgatewayar av meddelandestorlek eller säkerhetsskäl.

<!--
## Work on formatting {#formatting}

To avoid common formatting errors, check the following elements:

* Correct **date formatting**: Adobe Campaign provides date formatting functions for the JavaScript templates and XSL stylesheets. [Learn more](formatting.md#date-display)

* Usage of **authorized characters** in emails: the list of valid characters for email addresses is defined in the "XtkEmail_Characters" option. Learn how to access Campaign options [in this section](../../installation/using/configuring-campaign-options.md). To correctly handle special characters, Adobe Campaign needs to be installed in Unicode. 

* Configuration of **Email Authentication**: make sure that the email headers contain the DKIM signature. DKIM (Domain Keys Identified Mail) authentication allows the receiving email server to verify that a message was indeed sent by the person or entity it claims it was sent by, and whether the message content was altered in between the time it was originally sent (and DKIM "signed") and the time it was received. This standard typically uses the domain in the From or Sender header. For more on this, refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).-->

## Hantera bilder {#manage-images}

Här följer några specifika riktlinjer för hur du optimerar bilder för din e-postmarknadsföringskampanj.

### Förhindra blockering av bilder {#image-blocking}

Vissa e-postklienter blockerar bilder som standard, och användare kan ändra sina inställningar till att blockera bilder för att spara på dataanvändningen.  Om bilderna inte laddas ned kan hela meddelandet därför gå förlorat.

+++ För att undvika detta kan du använda dessa bästa metoder

* Undvik helt bildbaserade e-postmeddelanden. Balansera innehållet med bild och text.

* Om texten måste finnas i en bild använder du alt- och titeltext för att vara säker på att meddelandet når fram. Formatera din alt-/titeltext för att förbättra utseendet.

* Undvik att använda bakgrundsbilder eftersom de inte stöds av vissa e-postklienter.
+++

### Gör bilderna responsiva {#responsive-images}

Försök att göra bilderna responsiva och ändra storlek så att de blir synliga i alla sammanhang och på alla enheter. Observera att detta kan ha en kostnadseffekt eftersom det tar längre tid att bygga.

### Använd absoluta bildreferenser {#absolute-images}

För att vara tillgängliga utifrån måste de bilder som används i e-postmeddelanden och offentliga resurser som är kopplade till kampanjer finnas på en externt tillgänglig server.

* Från leveransassistenten kan du importera en HTML-sida som innehåller bilder eller infoga bilder direkt med redigeraren i HTML via ikonen **[!UICONTROL Image]**.

* Om bilderna inte visas kontrollerar du att bilderna är tillgängliga på servern. Det gör du genom att bläddra till fliken **Source** för leveransen. Hitta bilderna och kopiera och klistra in URL:en för varje bild i en webbläsare. Om bilderna inte visas kontaktar du IT-administratören eller tredjepartsleverantören som tillhandahåller ditt leveransinnehåll.

### Förhandsgranska och testa meddelandet {#preview-msg}

Adobe rekommenderar att du förhandsgranskar ditt meddelande för att kontrollera hur det är anpassat och hur mottagarna ser det.

I leveransassistenten kan du på underfliken **[!UICONTROL Preview]** visa återgivningen av varje innehåll för en mottagare. Anpassningsfälten och de villkorliga elementen i innehållet ersätts med motsvarande information för den valda profilen. [Läs mer](../send/preview-and-proof.md).


<!--
*  An automatic anti-spam checking is performed during each preview. In the **[!UICONTROL Preview]** sub-tab, check [SpamAssassin](spamassassin.md) spam scoring.  Click **[!UICONTROL More...]** to find out more about the warning.  Before doing so, make sure SpamAssassin is correctly installed and configured on the Adobe Campaign application server. [Learn more](../../installation/using/configuring-spamassassin.md)
-->

## Definiera rätt målgrupp {#define-the-right-audience}

Målgruppspopulationen är avgörande: skapa listor noggrant, testa e-postmeddelanden på populära e-postklienter och mobila enheter och se till att e-postlistorna är aktuella (utan okända eller föråldrade adresser). Du kan också skicka korrektur som hjälper dig att konfigurera en komplett valideringscykel. Läs mer om målgrupper i [det här avsnittet](../audiences/gs-audiences.md).

### Rikta er till rätt målgrupp {#target-the-right-audience}

När innehållet är klart måste du noga definiera vem som ska få meddelandet.

För att leveransen ska bli framgångsrik vill ni skicka det mest relevanta personaliserade innehållet till rätt mottagare. Med Adobe Campaign kan du skapa det mest korrekta målet: du kan välja mottagare utifrån deras ålder, lokalisering, vad de köpt, om de klickat på en länk i en tidigare leverans osv. Med Adobe Campaign kan du även definiera testprofiler, kontrollgrupper och startadresser för att vara säker på att målet är korrekt.

### Målmappningar {#target-mappings}

I Campaign är leveransmallarna som standard avsedda för **mottagare**. Adobe Campaign erbjuder andra målmappningar för leveranser som du kan ändra efter behov. Du kan till exempel leverera till besökare vars profiler har samlats in via sociala nätverk eller till besökare som prenumererar på en informationstjänst.

Dessa mappningar presenteras [ i det här avsnittet](../audiences/target-mappings.md).

### Externa mottagare {#external-recipients}

Du kan leverera till mottagare som lagras i en extern fil i stället för att sparas i databasen. Läs mer [i det här avsnittet](create-message.md#select-external-recipients-selecting-external-recipients).

<!--
### Send to your subscribers {#send-to-subscribers}

To send messages to the subscribers of a newsletter, you can directly target the subscribers to the corresponding information service. Learn more [in this section](../audiences/).-->

### Testa mottagare {#test-recipients-seed-addresses}

Om du vill testa leveransen använder du korrektur innan du skickar till huvudmålet.

Se till att du väljer rätt korrekturmottagare eftersom de validerar formuläret och meddelandets innehåll. Stegen för att definiera korrekturmottagare visas [i det här avsnittet](create-message.md#select-the-recipients-of-proof-messages-select-the-proof-target).


### Deduplicera adresser {#deduplicate-addresses}

Det är viktigt att undvika att ha dubbla e-postadresser, eftersom detta kan påverka ditt mål:

* Samma meddelande kan skickas mer än en gång när ett mål delas.

* Om en mottagare säger upp prenumerationen efter att ha fått ett meddelande kommer deras duplicerade profil fortfarande att få framtida meddelanden.

Borttagning av dubbletter skyddar det avsändande anseendet och garanterar en god karantänhantering.

**Relaterade ämnen:**

* [Dedupliceringsaktivitet](../../automation/workflow/deduplication.md).
* [Använd skiftläge: Använder sammanfogningsfunktionen för dedupliceringsaktiviteten](../../automation/workflow/deduplication-merge.md).


## Utför alla kontroller innan du skickar {#perform-all-checks}

När meddelandet är klart ser du till att innehållet visas korrekt på alla enheter och att det inte innehåller fel som personalisering eller brutna länkar. Innan du skickar meddelandet måste du se till att parametrarna och konfigurationen stämmer överens med leveransen.

Stegen för att validera en leverans visas [i det här avsnittet](../send/preview-and-proof.md).

<!--
### Inbox rendering {#inbox-and-email-rendering}

Inbox rendering enables you to preview your messages on major email clients, scan content and reputation, discover how recipients are reading messages.

**Tips**:

* You can view the sent message in the different contexts in which it may be received: webmail, message service, mobile, etc.

* Inbox rendering capabilities are crucial to identifying whether your email campaigns successfully make it past the filters of major ISPs (Internet Service Providers) and webmail services. Such tools send a pre-flight copy of an email to a network of test inboxes, so you can see how the message will display, or render, across these services. They may also include reports and code correction options that help you quickly identify and make fixes that improve deliverability.

Learn more [in this section](inbox-rendering.md).-->

### Korrekturmeddelanden {#proof-messages}

Genom att skicka korrektur kan du kontrollera länken för avanmälan, spegelsidan och alla andra länkar, validera meddelandet, verifiera att bilder visas, upptäcka eventuella fel osv. Du kanske också vill kontrollera din design och återgivning på olika enheter.

<!--
### Set up A/B testing deliveries {#a-b-testing-deliveries}

If you have several contents for an email delivery, you can use A/B testing to find out which version will have the biggest impact on the targeted population.

**Tips**:

* Send the different versions to some of your recipients

* Select the one with the highest success rate and send it to the rest of your target

Learn more [in this section](get-started-a-b-testing.md).-->

### Se till att ditt meddelande levereras {#make-sure-your-message-is-delivered}

Som ett sista steg kan du maximera dina chanser och utnyttja kraften i Adobe Campaign för att säkerställa att ditt budskap verkligen kommer att levereras till de relevanta mottagarna.

#### Gå igenom en valideringsprocess

Du kan definiera en fullständig valideringsprocess där Adobe Campaign-operatorer och -grupper deltar för att validera både mål- och meddelandeinnehållet. Detta säkerställer full övervakning och kontroll av kampanjens olika processer: målinriktning, innehåll, budget, extrahering och utskick av ett bevis. Beroende på deras behörigheter meddelas användare, får korrektur och kan validera eller avvisa meddelandet. Läs mer [i det här avsnittet](../../automation/campaigns/marketing-campaign-approval.md).

#### Använd vågor

Du kan stegvis öka volymen som skickas med vågor. På så sätt undviker du att meddelanden markeras som skräppost eller när du vill begränsa antalet meddelanden per dag. Med vågor kan du dela upp leveranser i flera grupper i stället för att skicka stora mängder meddelanden samtidigt. Läs mer [i det här avsnittet](../send/configure-and-send.md#sending-using-multiple-waves).

#### Prioritera meddelanden

Du kan ange avsändarordning för leveranser genom att ange prioritetsnivå. För att göra detta:

1. Redigera leveransegenskaperna och välj fliken **[!UICONTROL Delivery]**.

1. Definiera prioritetsnivån för leveransen på en skala från **[!UICONTROL Very low]** till **[!UICONTROL Very high]**.

>[!NOTE]
>
>Det går inte att definiera ordningen för att skicka meddelanden från en leverans.

<!--
#### Setup IP Affinities

To better control the outbound SMTP traffic, you can manage affinities by defining which specific IP addresses can be used for each affinity. This lets you restrict the number of emails for specific deliveries towards machines or output addresses. For example, you can use one affinity per country or sub-domain. You can then create one typology per country and link each affinity to the corresponding typology.

You can:

* Define the IP affinities in the serverConf.xml configuration file. [Learn more](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* For each IPAffinity element, declare the IP addresses that can be used. [Learn more](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In the [typology](../../campaign-opt/using/about-campaign-typologies.md) of your choice, use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the delivery server (MTA) which manages the said affinity. [Learn more](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Once the email is sent, check the header to verify which IP address the delivery was sent from. Your email administrator should help you obtain the header information.

* For SMS deliveries, make sure that the SMS channel has a dedicated affinity limited to **one** application server container. [Learn more](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>Most of these steps can only be performed by an expert user.-->

#### Använd typologier

Du kan använda typologiregler för att exkludera delar av målet baserat på specifika kriterier. Detta garanterar att de meddelanden som skickas bäst uppfyller kundernas behov och förväntningar, i enlighet med företagets kommunikationspolicy. Du kan till exempel filtrera de mottagare som är minderåriga från målet i nyhetsbrevet. Läs mer [i det här exemplet](../../automation/campaign-opt/filtering-rules.md).


## Spåra och övervaka {#track-and-monitor}

Klickade du på knappen **Skicka**? Låt oss se vad som händer. När leveransen har skickats kan du med Adobe Campaign hålla reda på skickade meddelanden och se hur mottagarna svarar på leveransen. Detta hjälper er att förbättra era framtida utskick och optimera era nästa kampanjer.

## Bildskärmsleveranser {#monitoring-deliveries}

För att kunna styra era kampanjer måste ni se till att meddelandet verkligen har levererats till mottagarna.

På kontrollpanelen för kampanjleverans kan du kontrollera bearbetade meddelanden och leveransgranskningsloggar. Du kan också styra status för meddelandena i leveransloggarna.

[Läs mer om leveransövervakning i Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/delivery-bestpractices/track-and-monitor.html){target="_blank"}


## Spåra beteende {#track-behaviour}

Om du vill veta mer om mottagarnas beteende kan du spåra hur de reagerar på en leverans: mottagning, öppning, klickningar på länkar, avbeställningar osv. I Campaign visas den här informationen på fliken **Spärra/knip** för mottagarna som leveransmålet gäller och på fliken Spårning för leveransen.

Spårning av meddelanden är aktiverat som standard. Om du vill konfigurera URL-adresser väljer du alternativet Visa URL-adresser i det nedre avsnittet av leveransassistenten. För varje URL för meddelandet kan du välja om spårning ska aktiveras.


[Läs mer om spårningsfunktioner i Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/tracking-messages/how-to-configure-tracked-links.html#sending-messages){target="_blank"}
