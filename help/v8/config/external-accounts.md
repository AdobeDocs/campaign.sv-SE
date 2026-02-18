---
title: Kampanjens externa konton
description: Konfigurera externa konton för att ansluta Campaign till externa system som POP3, FDA-databaser, CRM, lagring och Adobe-lösningar.
feature: Application Settings, External Account
role: Admin
level: Beginner, Intermediate, Experienced
exl-id: 9634b576-2854-4ea9-ba0d-8efaab2c4aee
source-git-commit: 776a0e5eead9161b7e2c9d7746c72cba42ea42cb
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 4%

---


# Konfigurera dina externa konton {#config-external-accounts}

Adobe Campaign innehåller en uppsättning fördefinierade externa konton. Om du vill konfigurera anslutningar med externa system kan du skapa nya externa konton.

Externa konton används av tekniska processer som tekniska arbetsflöden eller Campaign-arbetsflöden. Om du till exempel konfigurerar en filöverföring i ett arbetsflöde eller ett datautbyte med något annat program (Adobe Target, Experience Manager, osv.) måste du välja ett externt konto.

Du kan komma åt externa konton från Adobe Campaign **[!UICONTROL Explorer]**: bläddra till **[!UICONTROL Administration]** `>` **[!UICONTROL Platform]** `>` **[!UICONTROL External accounts]**.

![](assets/external-accounts.png)


>[!CAUTION]
>
>* Som användare av hanterade molntjänster konfigureras externa konton för din instans av Adobe och får inte ändras.
>
>* I kontexten för en [Enterprise (FFDA)-distribution](../architecture/enterprise-deployment.md) hanterar ett specifikt **[!UICONTROL Full FDA]** (FFDA) externt konto anslutningen mellan den lokala databasen i Campaign och molndatabasen ([!DNL Snowflake]).
>

## Kampanjspecifika externa konton {#ac-external-accounts}

Följande tekniska konton används av Adobe Campaign för att aktivera och köra specifika processer.

### Studsa e-post {#bounce-mails-external-account}

>[!NOTE]
>
>Microsoft Exchange Online OAuth 2.0-autentisering för POP3-kapacitet är tillgänglig från och med Campaign v8.3. Mer information om hur du kontrollerar versionen finns i [det här avsnittet](../start/compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion).
>

Det externa **studs-e-postkontot** anger det externa POP3-kontot som ska användas för att ansluta till e-posttjänsten. Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returmeddelanden.

Läs mer om inkommande e-post på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/inbound-emails.html){target="_blank"}.

![](assets/bounce_external_1.png)

Så här konfigurerar du det externa kontot **[!UICONTROL Bounce mails (defaultPopAccount)]**:

* **[!UICONTROL Server]** - URL för POP3-servern.

* **[!UICONTROL Port]** - portnummer för POP3-anslutning. Standardporten är 10.

* **[!UICONTROL Account]** - Användarens namn.

* **[!UICONTROL Password]** - Lösenord för användarkonto.

* **[!UICONTROL Encryption]** - Typ av vald kryptering mellan **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** eller **[!UICONTROL POP3S]**.

* **[!UICONTROL Function]** - Inkommande e-post eller SOAP-router.

![](assets/bounce_external_2.png)

>[!CAUTION]
>
>Innan du konfigurerar ditt POP3-externa konto med Microsoft OAuth 2.0 måste du först registrera programmet i Azure-portalen. Se denna [sida](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app){target="_blank"} för mer information om detta.
>

Om du vill konfigurera en POP3-extern med Microsoft OAuth 2.0 markerar du alternativet **[!UICONTROL Microsoft OAuth 2.0]** och fyller i följande fält:

* **[!UICONTROL Azure tenant]** - Azure-id (eller klient-ID) finns i listrutan **Grundläggande** i programöversikten på Azure-portalen.

* **[!UICONTROL Azure Client ID]** - Klient-ID (eller program-ID (klient)) finns i listrutan **Grundläggande** i programöversikten på Azure-portalen.

* **[!UICONTROL Azure Client secret]** - Klienthemligt ID finns i kolumnen **Klienthemligheter** på menyn **Certifikat och hemligheter** i ditt program på Azure-portalen.

* **[!UICONTROL Azure Redirect URL]** - Omdirigerings-URL finns på menyn **Autentisering** i ditt program på Azure-portalen. Den ska sluta med följande syntax `nl/jsp/oauth.jsp`, t.ex. `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

När du har angett dina autentiseringsuppgifter klickar du på **[!UICONTROL Setup the connection]** för att slutföra konfigurationen av det externa kontot.

### Routning {#routing}

Med det externa kontot **[!UICONTROL Routing]** kan du konfigurera varje kanal som är tillgänglig i Adobe Campaign beroende på vilka paket som är installerade.

Läs mer om extern kontohantering och leveranskörning i [det här avsnittet](../architecture/architecture.md#split).

### Körningsinstans {#execution-instance}

När det gäller transaktionsmeddelanden är körningsinstansen länkad till kontrollinstansen och kopplar dem. Transaktionsmeddelandemallar distribueras till körningsinstansen. Läs mer om arkitekturen i Message Center på [den här sidan](../architecture/architecture.md#transac-msg-archi).

## Tillgång till externa systemkonton {#external-syst-external-accounts}

### Federerad dataåtkomst (FDA) {#fda-external-accounts}

Det externa kontot av typen **Extern databas** används för att ansluta till en extern databas via FDA (Federated Data Access). Läs mer om FDA-alternativet (Federated Data Access) i [det här avsnittet](../connect/fda.md).

>[!NOTE]
>
>Externa databaser som är kompatibla med Adobe Campaign v8 visas i [kompatibilitetsmatrisen](../start/compatibility-matrix.md). FDA-anslutningar använder ODBC-drivrutiner; med Adobe Campaign Managed Cloud Services konfigureras ODBC-drivrutinen och det externa kontot av Adobe.

Konfigurationsinställningarna för det externa kontot beror på databasmotorn. Med Adobe Campaign Managed Cloud Services utförs konfigurationen av externa konton av Adobe. Läs mer om den här konfigurationen i [Adobe Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/en/docs/campaign-classic/using/installing-campaign-classic/accessing-external-database/external-accounts){target="_blank"}.

#### Externt konto för databaser {#databricks-external-accounts}

Databrikens FDA-anslutning använder ODBC-drivrutinen för databaser. Från och med Campaign v8.9.1 stöder externa konton i databaser OAuth2-autentisering via tjänstens huvudnamn (icke-interaktivt klientautentiseringsflöde), vilket ger säker autentisering för federerad dataåtkomst.

Läs mer om tjänstens huvudnamn i [Microsoft-dokumentationen](https://learn.microsoft.com/en-us/azure/databricks/admin/users-groups/service-principals){target="_blank"}.

Så här konfigurerar du OAuth2-autentisering via tjänstens huvudnamn i Campaign:

1. Administratören för arbetsytan Databaser aktiverar tjänstens huvudnamn på arbetsytan Databaser och genererar autentiseringsuppgifter. Skapa en OAuth-hemlighet (används för att generera OAuth-åtkomsttoken för autentisering) om du vill tillåta åtkomst till dina Azure Database-resurser med OAuth.
2. Skapa eller redigera ett externt databankskonto i Adobe Campaign och öppna fliken **OAuth**.
3. Klistra in inloggningsuppgifterna i fälten på fliken OAuth i det externa databankskontot.
4. Använd **[!UICONTROL Test the connection]** för att validera konfigurationen.

### X (tidigare Twitter) {#twitter-external-account}

Det externa kontot av typen **Twitter** används för att ansluta Campaign till ditt X-konto och för att skicka meddelanden åt dig. Läs mer om X-integrering i [det här avsnittet](../connect/ac-tw.md).

## Externa konton för Adobe Solution Integration {#adobe-integration-external-accounts}

* **Adobe Experience Cloud** - Det **[!UICONTROL Adobe Experience Cloud]** externa kontot används för att implementera Adobe Identity Management-tjänsten (IMS) för att ansluta till Adobe Campaign. Läs mer om Adobe Identity Management-tjänsten (IMS) i [det här avsnittet](../start/connect.md#logon-to-ac).

* **Web Analytics** - Det **[!UICONTROL Web Analytics (Adobe Analytics)]** externa kontot används för att konfigurera dataöverföring från Adobe Analytics till Adobe Campaign. Läs mer om Adobe Campaign - Adobe Analytics-integrering på [den här sidan](../connect/ac-aa.md).

* **Adobe Experience Manager** - Med det **[!UICONTROL AEM]** externa kontot kan du hantera innehållet i e-postleveranser och dina formulär direkt i Adobe Experience Manager. Läs mer om Adobe Campaign - Adobe Experience Manager-integrering på [den här sidan](../connect/ac-aem.md).


## Externa konton för CRM Connector {#crm-external-accounts}

* **Microsoft Dynamics CRM** - Med det **[!UICONTROL Microsoft Dynamics CRM]** externa kontot kan du importera och exportera Microsoft Dynamics-data till Adobe Campaign. Läs mer om Adobe Campaign - Microsoft Dynamics CRM-integrering på [den här sidan](../connect/ac-ms-dyn.md).

* **Salesforce.com** - Med det **[!UICONTROL Salesforce CRM]** externa kontot kan du importera och exportera Salesforce-data till Adobe Campaign. Läs mer om Adobe Campaign - Salesforce.com CRM-integrering i [den här sidan](../connect/ac-sfdc.md).

## Externa konton för överföringsdata {#transfer-data-external-accounts}

Dessa externa konton kan användas för att importera eller exportera data till Adobe Campaign med hjälp av en **[!UICONTROL Transfer file]**-arbetsflödesaktivitet. Läs mer om **Filöverföring** i arbetsflöden på [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html){target="_blank"}.

* **FTP och SFTP** - Med det externa **FTP**-kontot kan du konfigurera och testa åtkomst till en server utanför Adobe Campaign. Om du vill konfigurera anslutningar till externa system som SFTP- eller FTP-servrar som används för filöverföringar kan du skapa egna externa konton.

  Om du vill göra det anger du den adress och de autentiseringsuppgifter som ska användas för att upprätta anslutningen till SFTP- eller FTP-servern i det här externa kontot.

  >[!NOTE]
  >
  >Från och med version 8.5 kan du nu autentisera säkert med en privat nyckel när du konfigurerar ditt externa SFTP-konto. [Läs mer om nyckelhantering](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/key-management.html){target="_blank"}.

* **Amazon Simple Storage Service (S3)** - **AWS S3**-anslutningen kan användas för att importera eller exportera data till Adobe Campaign med hjälp av en **[!UICONTROL Transfer file]** arbetsflödesaktivitet. När du konfigurerar det nya externa kontot måste du ange följande information:

   * **[!UICONTROL AWS S3 Account Server]**: Serverns URL i formatet `<S3bucket name>.s3.amazonaws.com/<s3object path>`.

   * **[!UICONTROL AWS access key ID]**: Lär dig hur du hittar ditt ID för AWS-åtkomstnyckel i [Amazon-dokumentationen](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys){target="_blank"}.

   * **[!UICONTROL Secret access key to AWS]**: Lär dig hur du hittar din hemliga åtkomstnyckel till AWS i [Amazon-dokumentationen](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/){target="_blank"}.

   * **[!UICONTROL AWS Region]**: Läs mer om AWS-regioner i [Amazon-dokumentationen](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/){target="_blank"}.

   * Med kryssrutan **[!UICONTROL Use server side encryption]** kan du lagra filen i S3-krypterat läge. Lär dig hur du hittar åtkomstnyckel-ID och hemlig åtkomstnyckel i [Amazon-dokumentationen](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys){target="_blank"}.

* **Azure Blob Storage** - Det externa **Azure**-kontot kan användas för att importera eller exportera data till Adobe Campaign med hjälp av en **[!UICONTROL Transfer file]**-arbetsflödesaktivitet. Om du vill konfigurera det externa **Azure**-kontot så att det fungerar med Adobe Campaign måste du ange följande information:

   * **[!UICONTROL Server]**: URL-adressen till Azure Blob-lagringsservern.

   * **[!UICONTROL Encryption]**: Typ av kryptering: **[!UICONTROL None]** eller **[!UICONTROL SSL]**.

   * **[!UICONTROL Access key]**: Lär dig hur du hittar **[!UICONTROL Access key]** i [Microsoft-dokumentationen](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal){target="_blank"}.

* **Microsoft Fabric** - Med det externa kontot **Microsoft Fabric** kan du importera och exportera data mellan Microsoft Fabric och Adobe Campaign med hjälp av arbetsflödesaktiviteten **[!UICONTROL Transfer file]**. Om du vill konfigurera den här integreringen anger du följande information:

   * **[!UICONTROL Server]**: URL:en till din Microsoft Fabric-lagringsserver.

   * **[!UICONTROL Application ID]**: Den unika identifieraren för programmet som används för att autentisera och få åtkomst till Microsoft Fabric-resurser.

   * **[!UICONTROL Client secret]**: Den autentiseringsnyckel eller det lösenord som är associerat med programmet, som krävs för att ansluta till Microsoft Fabric på ett säkert sätt.
