---
title: Bästa praxis för kampanjsäkerhet
description: Kom igång med de effektivaste strategierna för kampanjsäkerhet
exl-id: 1d593c8e-4b32-4902-93a7-7b18cef27cac
source-git-commit: 6de5c93453ffa7761cf185dcbb9f1210abd26a0c
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Bästa praxis för kampanjsäkerhet {#ac-security}

På Adobe tar vi säkerheten i er digitala upplevelse på stort allvar. Säkerhetsrutinerna är djupt integrerade i vår interna programutveckling och våra processer och verktyg för drift och följs noggrant av våra funktionsövergripande team för att förebygga, upptäcka och hantera incidenter på ett snabbt sätt.

Dessutom hjälper vårt samarbete med partners, ledande forskare, säkerhetsforskningsinstitutioner och andra branschorganisationer oss att hålla oss uppdaterade med de senaste hoten och säkerhetsluckorna och vi införlivar regelbundet avancerad säkerhetsteknik i de produkter och tjänster vi erbjuder.

## Sekretess

Konfiguration och skärpning av sekretess är en viktig del av säkerhetsoptimeringen. Här följer några tips om sekretess:

* Protect dina kunders personuppgifter (PI) genom att använda HTTPS i stället för HTTP
* Använd [Begränsning av PI-vy](../dev/restrict-pi-view.md) skydda integriteten och förhindra att data används på fel sätt
* Kontrollera att krypterade lösenord är begränsade
* Protect de sidor som kan innehålla personlig information, t.ex. spegelsidor, webbtillämpningar osv.

![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Services arbetar Adobe tillsammans med dig för att implementera dessa konfigurationer i din miljö.

## Personalisering

När du lägger till anpassade länkar till ditt innehåll bör du alltid undvika att ha en personalisering i värdnamnsdelen av webbadressen för att undvika eventuella säkerhetsbrister. Följande exempel får aldrig användas i alla URL-attribut &lt;`a href="">` eller `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

## Databegränsning

Du måste se till att de krypterade lösenorden inte är tillgängliga för en autentiserad användare med låg behörighet. Det finns två sätt: begränsa åtkomsten till lösenordsfält eller till hela entiteten.

Med den här begränsningen kan du ta bort lösenordsfält, men låta det externa kontot vara tillgängligt från gränssnittet för alla användare. Läs mer i [den här sidan](../dev/restrict-pi-view.md).

1. Gå in **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.

1. Skapa ett nytt **[!UICONTROL Extension of a schema]**.

1. Välj **[!UICONTROL External Account]** (extAccount).

1. På den sista skärmen kan du redigera ditt nya srcSchema för att begränsa åtkomsten till alla lösenordsfält:

   Du kan ersätta huvudelementet (`<element name="extAccount" ... >`) av:

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Så din utökade srcSchema kan se ut så här:

   ```
   <...>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   <...> 
   ```

   >[!NOTE]
   >
   >Du kan ersätta `$(loginId) = 0 or $(login) = 'admin'` av `hasNamedRight('admin')` om du vill att alla användare med administratörsbehörighet ska kunna se dessa lösenord.


## Åtkomsthantering

Åtkomshantering är en viktig del av säkerhetsbehärskningen. Här är några av de bästa sätten:

* Skapa tillräckligt många säkerhetsgrupper
* Kontrollera att alla operatorer har rätt åtkomsträttigheter
* Undvik att använda admin-operatorn och undvik att ha för många operatorer i admin-gruppen

![](../assets/do-not-localize/book.png) Läs mer i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/access-management.html?lang=en#webapp-operator){target=&quot;_blank&quot;}

## Riktlinjer för kodning

När du utvecklar i Adobe Campaign (arbetsflöden, Javascript, JSSP osv.) ska du alltid följa dessa riktlinjer:

* **Skript**: försök att undvika SQL-satser, använd parametriserade funktioner i stället för strängsammanfogning, undvik SQL-injektion genom att lägga till de SQL-funktioner som ska användas i tillåtelselista.

* **Skydda datamodellen**: använda namngivna rättigheter för att begränsa operatoråtgärder, lägga till systemfilter (sysFilter)

* **Lägga till bildtexter i webbprogram**: lägga till bilder på era offentliga landningssidor och prenumerationssidor.

![](../assets/do-not-localize/book.png) Läs mer i [Adobe Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/scripting-coding-guidelines.html?lang=en#installing-campaign-classic){target=&quot;_blank&quot;}
