---
title: Migrering av tekniska användare till Adobe Developer Console
description: Lär dig hur du migrerar tekniska kampanjoperatörer till ett tekniskt konto på Adobe Developer Console
hide: true
hidefromtoc: true
source-git-commit: d52744e1d798447bb6b90909607e42082f7eeaf5
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---

# Migrering av tekniska aktörer från Campaign till Adobe Developer Console {#migrate-tech-users-to-ims}

Som en del i arbetet med att stärka säkerhets- och autentiseringsprocessen, från och med Campaign v8.5, förbättras autentiseringsprocessen till Campaign v8. Tekniska operatörer kan nu använda [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} to connect to Campaign. Learn more about the new server to server authentication process in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

En teknisk operator är en Campaign-användarprofil som uttryckligen har skapats för API-integrering. I den här artikeln beskrivs stegen som krävs för att migrera en teknisk operatör till ett tekniskt konto via Adobe Developer-konsolen.


## Påverkas du?{#ims-impacts}

Om du gör API-anrop från ett externt system till Campaign till antingen deras Campaign Marketing-instans eller Real Time Message Center-instans, måste du migrera de tekniska operatörerna till tekniska konton via Adobe Developer Console enligt beskrivningen nedan.

Den här ändringen gäller från och med Campaign v8.5.


## Migreringsprocess {#ims-migration-procedure}

Följ stegen nedan för att skapa tekniska konton i Adobe Developer Console och använd sedan de nya kontona för att kunna ändra autentiseringsmetoderna för alla dina externa system som gör API-anrop i Adobe Campaign.

En översikt över stegen är:

* Skapa ett projekt i Adobe Developer Console
* Tilldela lämpliga API:er till det nyskapade projektet
* Bevilja nödvändiga kampanjproduktprofiler för projektet
* Uppdatera dina API:er för att använda de nya inloggningsuppgifterna för det tekniska kontot
* Ta bort äldre tekniska operatorer från Campaign-instansen

### Krav för migreringen{#ims-migration-prerequisites}

För att kunna skapa tekniska konton som ersätter de tekniska operatorerna måste villkoret att det finns rätt kampanjproduktprofiler i Admin Console för alla Campaign-instanser valideras. Du kan läsa mer om produktprofiler i Adobe-konsolen i [Adobe Developer Console-dokumentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

För API-anrop till Message Center-instansen/instanserna bör en produktprofil ha skapats under uppgraderingen till Campaign v8.5 eller under etableringen av instansen. Den här produktprofilen heter:

`campaign - <your campaign instance> - messagecenter`

Om du redan har använt IMS-baserad autentisering för användaråtkomst till Campaign bör de produktprofiler som behövs för API-anropen redan finnas i Admin Console. Om du använder en anpassad operatörsgrupp i Campaign för API-anrop till Marketing-instansen måste du skapa produktprofilen i Admin Console.

I andra fall måste du kontakta din Adobe Transition Manager så att Adobe tekniska team kan migrera dina befintliga Operator-grupper och namngivna behörigheter till produktprofilerna i Admin Console.


### Steg 1 - Skapa ett Campaign-projekt i Adobe Developer Console {#ims-migration-step-1}

Integrationer skapas som en del av en **Projekt** i Adobe Developer Console. Läs mer om projekt i [Adobe Developer Console-dokumentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

Du kan använda vilket projekt som helst som du har skapat tidigare eller skapa ett nytt projekt. Stegen för att skapa ett projekt beskrivs i [Adobe Developer Console-dokumentation](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}. Du hittar de viktigaste stegen nedan

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

Om du vill skapa ett nytt projekt klickar du **Skapa nytt projekt** från huvudskärmen i Adobe Developer Console.

![](assets/New-Project.png)

Du kan använda **Redigera projekt** om du vill byta namn på projektet.


### Steg 2 - Lägg till API:er i projektet {#ims-migration-step-2}

Från den nya projektskärmen lägger du till de API:er som behövs för att kunna använda det här projektet som ett tekniskt konto för dina API-anrop till Adobe Campaign.

Så här lägger du till API:er i projektet:

1. Klicka på **Lägg till API** för att välja de API:er som ska läggas till i projektet.
   ![](assets/do-not-localize/ims-updates-01.png)
1. Markera och lägg till Adobe Campaign API i ditt projekt genom att markera kryssrutan i det övre högra hörnet av Adobe Campaign-kortet som visas när du håller muspekaren över kortet
   ![](assets/do-not-localize/ims-updates-02.png)
1. Klicka **Nästa** längst ned på skärmen.

### Steg 3 - Välj autentiseringstyp  {#ims-migration-step-3}

I **Konfigurera API** väljer du autentiseringstyp. **OAuth Server-till-server** Autentisering krävs för det här projektet. Se till att det är markerat och klicka på **Nästa** längst ned på skärmen.

![](assets/do-not-localize/ims-updates-03.png)

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### Steg 4 - Välj produktprofiler {#ims-migration-step-4}

Så som beskrivs i avsnittet Krav måste du tilldela rätt produktprofiler som ska användas i projektet. I det här steget måste du välja den eller de produktprofiler som ska användas av det tekniska konto som skapas.

Om det här tekniska kontot används för att göra API-anrop till Message Center-instansen måste du välja produktprofilen Adobe som slutar med `messagecenter`.

För API-anrop till Marketing-instansen/-instanserna väljer du den produktprofil som motsvarar instansen och operatörsgruppen.

Klicka på **Spara konfigurerat API** längst ned på skärmen.

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### Steg 5 - Lägg till API:t för I/O-hantering i ditt projekt {#ims-migration-step-5}


Klicka på **[!UICONTROL + Add to Project]** och välja **[!UICONTROL API]** i det övre vänstra hörnet av skärmen för att kunna lägga till API:t för I/O-hantering i det här projektet.

![](assets/do-not-localize/ims-updates-04.png)

I **Lägg till ett API** skärm, bläddra nedåt för att hitta **API för I/O-hantering** kort. Markera den genom att klicka i kryssrutan som visas när du för muspekaren över kortet. Klicka sedan på **Nästa** längst ned på skärmen.

![](assets/do-not-localize/ims-updates-05.png)


I **Konfigurera API** OAuth Server-till-Server-autentiseringen finns redan. Klicka **Spara konfigurerat API** längst ned på skärmen.


![](assets/do-not-localize/ims-updates-06.png)

Detta tar dig tillbaka till projektskärmen i I/O Management API för det nyskapade projektet. Klicka på projektnamnet längst upp på skärmen så kommer du tillbaka till sidan Projektinformation.


### Steg 6 - Verifiera projektkonfigurationen {#ims-migration-step-6}

Granska projektet för att se till att det ser likadant ut som nedan med **API för I/O-hantering** och **ADOBE CAMPAIGN API** visas i avsnittet Produkter och tjänster och **OAuth Server-till-server** i delen Autentiseringsuppgifter.

![](assets/do-not-localize/ims-updates-07.png)


### Steg 7 - Verifiera konfigurationen {#ims-migration-step-7}

Följ de steg som beskrivs i [Autentiseringsguide för Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} för att generera en åtkomsttoken och kopiera exempelkommandot cURL. Du kan skapa ett SOAP-anrop med dessa autentiseringsuppgifter för att testa att du kan autentisera och ansluta till Adobe Campaign-instansen/instanserna korrekt. Vi rekommenderar att du utför den här valideringen innan du gör alla ändringar i API-integreringarna från tredje part.

### Steg 8 - Uppdatera API-integreringar från tredje part {#ims-migration-step-8}

Du måste nu uppdatera av API-integreringarna och ringa in Adobe Campaign för att använda det nya tekniska kontot.

Mer information om API-integreringssteg, inklusive en exempelkod för smidig integrering, finns i [Autentiseringsdokumentation för Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

Nedan visas exempel på SOAP-anrop som visar före och efter migreringsanrop för tredjepartssystem.

När migreringsprocessen har uppnåtts och validerats uppdateras Soap-anropen enligt nedan:



* Före migreringen: det fanns inget stöd för token för åtkomst till tekniska konton.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```

* Efter migreringen: det finns stöd för token för åtkomst till tekniska konton. Åtkomsttoken förväntas anges i `Authorization` sidhuvud som Bearer-token. Användning av sessionstoken bör ignoreras här, vilket visas i exemplet nedan för SOAP-anrop.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  Authorization: Bearer <IMS_Technical_Token_Token>
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken></urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```



### Steg 9 - (valfritt) Uppdatera den tekniska kontooperatören i Campaign Client Console {#ims-migration-step-9}

Det här steget är valfritt och endast tillgängligt i Marketing Instance(erna), inte i någon Message Center-instans. Om specifika mappbehörigheter eller namngivna rättigheter har definierats för den tekniska operatören, men inte via de tilldelade operatörsgrupperna. Du måste nu uppdatera den nyskapade tekniska kontoanvändaren i Admin Console för att ge mappbehörigheter eller namngivna rättigheter som krävs.

Observera att den tekniska kontoanvändaren INTE finns i Adobe Campaign förrän minst ett API-anrop görs till Campaign-instansen, då IMS skapar användaren i Campaign. Om du inte kan hitta de tekniska användarna i Campaign kontrollerar du att du har lyckats skicka ett API-anrop enligt instruktionerna [i steg 7](#ims-migration-step-7).

1. Om du vill använda ändringarna för den nya tekniska kontoanvändaren letar du reda på dem i Campaign-klientkonsolen via e-postadress. Den här e-postadressen skapades under stegen för att skapa projekt och autentisering ovan.

   Du kan hitta den här e-postadressen genom att klicka på **OAuth Server-till-server** rubrik i **Referenser** -delen av projektet.

   ![](assets/do-not-localize/ims-updates-07.png)

   Bläddra nedåt på skärmen Autentiseringsuppgifter för att hitta e-postadressen för det tekniska kontot **och klicka på **Kopiera** -knappen.

   ![](assets/do-not-localize/ims-updates-08.png)

1. Nu måste du uppdatera den nyskapade tekniska operatorn i Adobe Campaign Client Console. Du måste tillämpa den befintliga mappbehörigheten för tekniska operatorer på den nya tekniska operatorn.

   Så här uppdaterar du operatorn:

   1. Bläddra från Campaign Client Console Explorer till **Administration > Åtkomsthantering > Operatorer**.
   1. Få åtkomst till den befintliga tekniska operatorn som används för API:er.
   1. Bläddra till mappbehörigheterna och kontrollera rättigheterna.
   1. Använd samma behörigheter för den nyskapade tekniska operatorn. Operatörens e-postadress är **E-post för tekniskt konto** värdet kopierades tidigare.
   1. Spara ändringarna.


>[!CAUTION]
>
>Den nya tekniska operatorn måste ha gjort minst ett API-anrop som ska läggas till i Campaign Client Console.
>

### Steg 10 - Ta bort den gamla tekniska operatorn från Adobe Campaign {#ims-migration-step-10}

När du har migrerat alla tredjepartssystem för att använda det nya tekniska kontot med IMS-autentisering kan du ta bort den gamla tekniska operatorn från Campaign Client Console.

Du gör detta genom att logga in på Campaign Client Console och navigera till **Administration > Åtkomsthantering > Operatorer** och hitta de gamla tekniska användarna och ta bort dem.
