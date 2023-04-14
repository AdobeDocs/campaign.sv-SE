---
title: Kampanjens externa konton
description: Kampanjens externa konton
feature: Application Settings
role: Admin
level: Beginner, Intermediate, Experienced
exl-id: 9634b576-2854-4ea9-ba0d-8efaab2c4aee
source-git-commit: 7b8a9a323afc3154e250b4c70c4339d6c6c265c0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Konfigurera dina externa konton

Adobe Campaign innehåller en uppsättning fördefinierade externa konton. Om du vill konfigurera anslutningar med externa system kan du skapa nya externa konton.

Externa konton används av tekniska processer som tekniska arbetsflöden eller Campaign-arbetsflöden. Om du till exempel konfigurerar en filöverföring i ett arbetsflöde eller ett datautbyte med något annat program (Adobe Target, Experience Manager, osv.) måste du välja ett externt konto.

Du kan få åtkomst till externa konton från Adobe Campaign **[!UICONTROL Explorer]**: bläddra till **[!UICONTROL Administration]** `>` **[!UICONTROL Platform]** `>` **[!UICONTROL External accounts]**.

![](assets/external-accounts.png)


>[!CAUTION]
>* Som användare av hanterade Cloud Services konfigureras externa konton för din instans av Adobe och får inte ändras.

>
>* >När det gäller [Företagsdistribution (FFDA)](../architecture/enterprise-deployment.md), en specifik **[!UICONTROL Full FDA]** (ffda) externt konto hanterar anslutningen mellan den lokala databasen i Campaign och molndatabasen ([!DNL Snowflake]).
>


## Kampanjspecifika externa konton

Följande tekniska konton används av Adobe Campaign för att aktivera och köra specifika processer.

### Studsmeddelanden {#bounce-mails-external-account}

>[!NOTE]
Microsoft Exchange Online OAuth 2.0-autentisering för POP3-kapacitet är tillgänglig från och med Campaign v8.3. Om du vill kontrollera din version kan du läsa [det här avsnittet](../start/compatibility-matrix.md#how-to-check-your-campaign-version-and-buildversion).

The **Studsa meddelanden** externt konto anger det externa POP3-konto som ska användas för att ansluta till e-posttjänsten. Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returmeddelanden.

Läs mer om inkommande e-post i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/inbound-emails.html).

![](assets/bounce_external_1.png)

Så här konfigurerar du **[!UICONTROL Bounce mails (defaultPopAccount)]** externt konto:

* **[!UICONTROL Server]** - URL för POP3-servern.

* **[!UICONTROL Port]** - POP3-anslutningens portnummer. Standardporten är 110.

* **[!UICONTROL Account]** - Användarens namn.

* **[!UICONTROL Password]** - Lösenord för användarkonto.

* **[!UICONTROL Encryption]** - Typ av vald kryptering mellan **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** eller **[!UICONTROL POP3S]**.

   The **Studsa meddelanden** externt konto anger det externa POP3-konto som ska användas för att ansluta till e-posttjänsten. Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returmeddelanden.

* **[!UICONTROL Function]** - Inkommande e-post eller SOAP-router

![](assets/bounce_external_2.png)

>[!CAUTION]
Innan du konfigurerar ditt POP3-externa konto med Microsoft OAuth 2.0 måste du först registrera programmet i Azure-portalen. Mer information om detta hittar du på den här [sidan](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app){target="_blank"}.

Om du vill konfigurera en POP3-extern med Microsoft OAuth 2.0 ska du kontrollera **[!UICONTROL Microsoft OAuth 2.0]** och fylla i följande fält:

* **[!UICONTROL Azure tenant]** - Azure ID (eller katalog-ID) finns i **Grundläggande** listruta med programöversikt i Azure-portalen.

* **[!UICONTROL Azure Client ID]** - Klient-ID (eller program-ID) finns i **Grundläggande** listruta med programöversikt i Azure-portalen.

* **[!UICONTROL Azure Client secret]** - Klienthemligt ID finns i **Klienthemligheter** kolumn från **Certifikat och hemligheter** menyn för ditt program i Azure-portalen.

* **[!UICONTROL Azure Redirect URL]** - Omdirigerings-URL:en finns i **Autentisering** menyn för ditt program i Azure-portalen. Det ska sluta med följande syntax `nl/jsp/oauth.jsp`, t.ex. `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

   När du har angett de olika inloggningsuppgifterna kan du klicka på **[!UICONTROL Setup the connection]** för att slutföra konfigurationen av ditt externa konto.

### Dirigering {#routing}

The **[!UICONTROL Routing]** Med ett externt konto kan du konfigurera varje kanal som är tillgänglig i Adobe Campaign beroende på vilka paket som är installerade.

>[!CAUTION]
The **[!UICONTROL Internal email delivery routing]** (defaultEmailBulk) externt konto **får inte** aktiveras i Adobe Campaign v8.

### Körningsinstans {#execution-instance}

När det gäller transaktionsmeddelanden är körningsinstanserna länkade till kontrollinstansen och kopplar dem. Transaktionsmeddelandemallar distribueras till körningsinstansen. Läs mer om arkitekturen i Message Center i [den här sidan](../architecture/architecture.md#transac-msg-archi).

## Tillgång till externa systemkonton

* **Extern databas (FDA)** - **Extern databas** externt typkonto används för att ansluta till en extern databas via FDA (Federated Data Access). Läs mer om FDA-alternativet (Federated Data Access) i [det här avsnittet](../connect/fda.md).

   Externa databaser som är kompatibla med Adobe Campaign v8 listas i [Kompatibilitetsmatris](../start/compatibility-matrix.md)

* **Twitter** - **Twitter** Skriv ett externt konto som används för att ansluta Campaign till ditt twitter-konto och för att skicka meddelanden åt dig. Läs mer om Twitter integrering i [det här avsnittet](../connect/ac-tw.md).

## Externa konton för Adobe Solution Integration

* **Adobe Experience Cloud** - **[!UICONTROL Adobe Experience Cloud]** externt konto används för att implementera Adobe Identity Management-tjänsten (IMS) för att ansluta till Adobe Campaign. Läs mer om Adobe Identity Management-tjänsten (IMS) i [det här avsnittet](../start/connect.md#connect-ims).

* **Web Analytics** - **[!UICONTROL Web Analytics (Adobe Analytics)]** externt konto används för att konfigurera dataöverföring från Adobe Analytics till Adobe Campaign. Läs mer om Adobe Campaign - Adobe Analytics-integrering i [den här sidan](../connect/ac-aa.md).

* **Adobe Experience Manager** - **[!UICONTROL AEM]** Med ett externt konto kan ni hantera innehållet i era e-postleveranser samt formulären direkt i Adobe Experience Manager. Läs mer om Adobe Campaign - Adobe Analytics-integrering i [den här sidan](../connect/ac-aem.md).


## Externa konton för CRM Connector

* **Microsoft Dynamics CRM** - **[!UICONTROL Microsoft Dynamics CRM]** Med ett externt konto kan du importera och exportera Microsoft Dynamics-data till Adobe Campaign. Läs mer om Adobe Campaign - Microsoft Dynamics CRM-integrering i [den här sidan](../connect/ac-ms-dyn.md).

* **Salesforce.com** - **[!UICONTROL Salesforce CRM]** Med ett externt konto kan du importera och exportera Salesforce-data till Adobe Campaign. Läs mer om Adobe Campaign - Salesforce.com CRM-integrering i [den här sidan](../connect/ac-sfdc.md).

## Externa konton för överföringsdata

Dessa externa konton kan användas för att importera eller exportera data till Adobe Campaign med en **[!UICONTROL Transfer file]** arbetsflödesaktivitet. Läs mer om **Filöverföring** i arbetsflöden i [den här sidan](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html).

* **FTP och SFTP** - **FTP** Med ett externt konto kan du konfigurera och testa åtkomst till en server utanför Adobe Campaign. Om du vill konfigurera anslutningar med externa system som SFTP- eller FTP-servrar 898 som används för filöverföringar kan du skapa egna externa konton.

   Om du vill göra det anger du den adress och de autentiseringsuppgifter som ska användas för att upprätta anslutningen till SFTP- eller FTP-servern i det här externa kontot.

* **Amazon Simple Storage Service (S3)** - **AWS S3** kan användas för att importera eller exportera data till Adobe Campaign med en **[!UICONTROL Transfer file]** arbetsflödesaktivitet. När du konfigurerar det nya externa kontot måste du ange följande information:

   * **[!UICONTROL AWS S3 Account Server]**: URL-adressen till servern, ifylld så här:   `<S3bucket name>.s3.amazonaws.com/<s3object path>`

   * **[!UICONTROL AWS access key ID]**: Lär dig hur du hittar ditt ID för AWS-åtkomstnyckel i [Amazon-dokumentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys){target="_blank"}.

   * **[!UICONTROL Secret access key to AWS]**: Lär dig hur du hittar din hemliga åtkomstnyckel till AWS i [Amazon-dokumentation](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/){target="_blank"}.

   * **[!UICONTROL AWS Region]**: Läs mer om AWS regioner i [Amazon-dokumentation](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/){target="_blank"}.

   * The **[!UICONTROL Use server side encryption]** kan du lagra filen i S3-krypterat läge. Lär dig hur du hittar åtkomstnyckel-ID och hemlig åtkomstnyckel i [Amazon-dokumentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys){target="_blank"}.

* **Azure Blob Storage** - **Azure** externt konto kan användas för att importera eller exportera data till Adobe Campaign med en **[!UICONTROL Transfer file]** arbetsflödesaktivitet. Så här konfigurerar du **Azure** externt konto för att arbeta med Adobe Campaign måste du ange följande:

   * **[!UICONTROL Server]**: URL för din Azure Blob-lagringsserver.

   * **[!UICONTROL Encryption]**: Typ av kryptering mellan **[!UICONTROL None]** eller **[!UICONTROL SSL]**.

   * **[!UICONTROL Access key]**: Lär dig hur du hittar **[!UICONTROL Access key]** in [Microsoft-dokumentation](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal){target="_blank"}.
