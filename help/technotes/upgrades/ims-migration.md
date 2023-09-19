---
title: Migrering av tekniska användare till Adobe Developer Console
description: Lär dig hur du migrerar tekniska kampanjoperatörer till ett tekniskt konto på Adobe Developer Console
source-git-commit: 43a124dd64532ffe84ca2b300113cacc545a811a
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 0%

---

# Migrering av tekniska aktörer från Campaign till Adobe Developer Console {#migrate-tech-users-to-ims}

Från och med Campaign v8.5 förbättras autentiseringsprocessen till Campaign v8. Tekniska operatörer måste använda [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} för att ansluta till Campaign. En teknisk operator är en Campaign-användarprofil som uttryckligen har skapats för API-integrering. I den här artikeln beskrivs stegen som krävs för att migrera en teknisk operatör till ett tekniskt konto på Adobe Developer-konsolen.

## Vad har ändrats?{#ims-changes}

Kampanjens reguljära användare ansluter redan till Adobe Campaign-konsolen via sin Adobe ID via Adobe Identity Management System (IMS). Som en del av arbetet med att förstärka säkerhets- och autentiseringsprocessen anropar nu Adobe Campaign Client-programmet Campaign-API:er direkt med IMS-kontotoken.

Läs mer om autentiseringsprocessen från den nya servern till servern i [Adobe Developer Console-dokumentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

Den här ändringen gäller från och med Campaign v8.5 och kommer att **obligatoriskt** starta Campaign v8.6.


## Påverkas du?{#ims-impacts}

Om du använder Campaign-API:er måste du migrera dina tekniska operatörer till Adobe Developer Console enligt beskrivningen nedan.

## Hur migrerar jag?{#ims-migration-procedure}

Varje teknisk aktör bör ha minst ett tekniskt konto.

Viktiga steg är:

1. Skapa först det tekniska konto som motsvarar den tekniska operatören. Anta t.ex. den nya tekniska redovisningen (TA1) för den tekniska operatören (TO1).
1. Utför stegen nedan på den tekniska redovisningen TA1
   [Steg 4](#ims-migration-step-4) är valfritt och endast obligatoriskt om den tekniska operatorn har särskilda mappbehörigheter.
1. Migrera all implementering av Campaign API-integrering till det nya tekniska kontot TA1.
1. När alla kundcentrerade API:er/integrationslösningar börjar fungera fullt ut på TA1 ersätter du den tekniska operatören TO1 med det tekniska kontot TA1.

### Förhandskrav{#ims-migration-prerequisites}

Innan du startar migreringsprocessen måste du kontakta din Adobe-representant så att Adobe tekniska team kan migrera dina befintliga Operator-grupper och namngivna rättigheter till Adobe Identity Management System (IMS).

### Steg 1 - Skapa/uppdatera ditt Campaign-projekt i Adobe Developer Console{#ims-migration-step-1}

Integrationer skapas som en del av en **Projekt** i Adobe Developer Console. Läs mer om projekt i [Adobe Developer Console-dokumentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

Som Campaign v8-användare bör du redan ha ett projekt i Adobe Developer Console. Annars måste du skapa ett projekt. Steg för att skapa ett projekt är detaljerade [i Adobe Developer Console-dokumentationen](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}.

När du har tillgång till ditt Campaign-projekt kan du lägga till tjänster som API:er, Adobe Campaign och I/O Management API. För den här migreringen måste du lägga till API:er nedan i ditt projekt: **API för I/O-hantering** och **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)


### Steg 2 - Lägg till ett API i ditt projekt med Server to Server-autentisering{#ims-migration-step-2}

När projektet har skapats i Adobe Developer Console lägger du till ett API som använder autentisering från server till server. Lär dig hur du ställer in autentiseringsuppgifter för OAuth Server-till-Server i [Adobe Developer Console-dokumentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

När API:t har anslutits kan du komma åt de nyligen genererade autentiseringsuppgifterna, inklusive klient-ID och klienthemlighet, samt generera en åtkomsttoken.

### Steg 3 - Lägg till produktprofilen i projektet{#ims-migration-step-3}

Nu kan du lägga till din Campaign-produktprofil i projektet, enligt beskrivningen nedan:

1. Öppna Adobe Campaign API.
1. Klicka på **Redigera produktprofiler** knapp

   ![](assets/do-not-localize/ims-edit-api.png)

1. Tilldela alla relevanta produktprofiler till API:t, till exempel &#39;messagecenter&#39;, och spara ändringarna.
1. Gå till **Information om autentiseringsuppgifter** -fliken i projektet och kopiera **E-post för tekniskt konto** värde.

### Steg 4 - Uppdatera den tekniska operatorn i klientkonsolen {#ims-migration-step-4}

Det här steget är bara obligatoriskt om specifika mappbehörigheter eller namngivna rättigheter har definierats för den här operatorn (inte via operatorns grupp).

Nu måste du uppdatera den nyskapade tekniska operatorn i Adobe Campaign Client Console. Du måste tillämpa den befintliga mappbehörigheten för tekniska operatorer på den nya tekniska operatorn.
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

<!--

>[!CAUTION]
>
>After updating the authentication type for the technical operator, all API integrations with this technical operator will stop working. You must [update your API integrations](#ims-migration-step-6). 

To update the technical operator authentication mode to IMS, follow these steps:

1. From Campaign Client Console explorer, browse to the **Administration > Access Management > Operators**.
1. Edit the existing technical operator used for APIs.
1. Replace the **Name (login)** of this technical operator by the technical account email retrieved earlier.
1. Browse to the **Edit** button on the top left beside **File**, and select **Edit the XML source**.
1. Update the authentication mode to `ims`, as follows:

    ```javascript
    <operator 
    ...
        <access authenticationType="ims" ...
        ...
        </access>
    ...
    </operator>
    ```

1. Save your changes.

You can also update the technical operator programmatically, using SQL scripts or Campaign APIs. These modes help you automate the steps which update operator's name with associated Technical account email address and/or authentication type. 

* Use the following **SQL Script** to replace operator's name with associated email:

    ```sql
    UPDATE xtkoperator
    SET sauthenticationtype = 'ims',
            sname = '{email}'
    WHERE sname = '{name}' AND itype = 0;
    ```

* Use the following `queryDef.ExecuteQuery` **Campaign API** to fetch id of an operator for given technical operator:

    ```javascript
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <ExecuteQuery xmlns="urn:xtk:queryDef">
                <sessiontoken>{session_token}</sessiontoken>
                <entity>
                    <queryDef schema="xtk:operator" operation="select">
                        <select>
                            <node expr="@id"/>
                        </select>
                        <where>
                            <condition expr="@name='{name}'"/>
                            <condition expr="@type=0"/>
                        </where>
                    </queryDef>
                </entity>
            </ExecuteQuery>
        </soap:Body>
    </soap:Envelope>
    ```

* Use the following `session.Write` **Campaign API** to update name with given technical account email address:

    ```javascript
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <Write xmlns="urn:xtk:session">
                <sessiontoken>{session_token}</sessiontoken>
                <domDoc xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
                    <operator _operation="update" id="{id}" name="{email}" xtkschema="xtk:operator">
                        <access authenticationType="ims" />
                    </operator>
                </domDoc>
            </Write>
        </soap:Body>
    </soap:Envelope>
    ```
-->

### Steg 5 - Verifiera konfigurationen {#ims-migration-step-5}

Följ de steg som beskrivs i [Autentiseringsguide för Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} för att generera en åtkomsttoken och kopiera exempelkommandot cURL.


### Steg 6 - Uppdatera API-integreringar från tredje part {#ims-migration-step-6}

Du måste uppdatera API-integreringarna med dina tredjepartssystem.

Mer information om API-integreringssteg, inklusive en exempelkod för smidig integrering, finns i [Autentiseringsdokumentation för Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.


### Steg 7 - Ta bort den gamla tekniska operatorn {#ims-migration-step-7}


Efter migreringen av all API/anpassad kodintegrering med den tekniska kontoanvändaren. Du kan ta bort den gamla tekniska operatorn från Campaign-klientkonsolen.

### Exempel på SOAP-anrop{#ims-migration-samples}

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
