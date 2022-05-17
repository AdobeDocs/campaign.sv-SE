---
title: Kampanjens externa konton
description: Kampanjens externa konton
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 9634b576-2854-4ea9-ba0d-8efaab2c4aee
source-git-commit: d2f4e54b0c37cc019061dd3a7b7048cd80876ac0
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 4%

---

# Konfigurera dina externa konton

Adobe Campaign innehåller en uppsättning fördefinierade externa konton. Om du vill konfigurera anslutningar med externa system kan du skapa nya externa konton.

Externa konton används av tekniska processer som tekniska arbetsflöden eller Campaign-arbetsflöden. Om du till exempel konfigurerar en filöverföring i ett arbetsflöde eller ett datautbyte med något annat program (Adobe Target, Experience Manager, osv.) måste du välja ett externt konto.

Du kan få åtkomst till externa konton från Adobe Campaign **[!UICONTROL Explorer]**: bläddra till **[!UICONTROL Administration]** `>` **[!UICONTROL Platform]** `>` **[!UICONTROL External accounts]**.

![](assets/external-accounts.png)


>[!CAUTION]
>
>En specifik **[!UICONTROL Full FDA]** (ffda) externt konto hanterar anslutningen mellan den lokala databasen i Campaign och molndatabasen ([!DNL Snowflake]).
>
>Som användare av hanterade Cloud Services konfigureras det här externa kontot för din instans av Adobe. Den får inte ändras.


## Kampanjspecifika externa konton

Följande tekniska konton används av Adobe Campaign för att aktivera och köra specifika processer.

![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Services konfigurerar Adobe alla kampanjspecifika externa konton åt dig.

* **Studsa e-post (POP3)**

   The **Studsa meddelanden** externt konto anger det externa POP3-konto som ska användas för att ansluta till e-posttjänsten. Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returmeddelanden.

   ![](../assets/do-not-localize/book.png) Läs mer om inkommande e-post i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/event-activities/inbound-emails.html){target=&quot;_blank&quot;}

* **Dirigering**

   The **[!UICONTROL Routing]** Med ett externt konto kan du konfigurera varje kanal som är tillgänglig i Adobe Campaign beroende på vilka paket som är installerade.

   >[!CAUTION]
   >
   >The **[!UICONTROL Internal email delivery routing]** (defaultEmailBulk) externt konto **får inte** aktiveras i Adobe Campaign v8.

* **Körningsinstans**

   När det gäller transaktionsmeddelanden är körningsinstanserna länkade till kontrollinstansen och kopplar dem. Transaktionsmeddelandemallar distribueras till körningsinstansen.

   ![](../assets/do-not-localize/glass.png) Läs mer om arkitekturen i Message Center i [den här sidan](../dev/architecture.md#transac-msg-archi).

## Tillgång till externa systemkonton

* **Extern databas (FDA)**

   Använd **Extern databas** skriv ett externt konto för att ansluta till en extern databas via FDA.

   Externa databaser som är kompatibla med Adobe Campaign v8 listas i [Kompatibilitetsmatris](../start/compatibility-matrix.md)

   ![](../assets/do-not-localize/glass.png) Läs mer om FDA-alternativet (Federated Data Access) i [det här avsnittet](../connect/fda.md).

## Externa konton för Adobe Solution Integration

* **Adobe Experience Cloud**

   The **[!UICONTROL Adobe Experience Cloud]** externt konto används för att implementera Adobe IMS för att ansluta till Adobe Campaign-konsolen med en Adobe ID.

   ![](../assets/do-not-localize/glass.png) Läs mer om Adobe Identity Management-tjänsten (IMS) i [det här avsnittet](../start/connect.md#connect-ims).

* **Webbanalys**

   Använd **[!UICONTROL Web Analytics (Adobe Analytics)]** externt konto för att konfigurera dataöverföring från Adobe Analytics till Adobe Campaign.

   ![](../assets/do-not-localize/glass.png) Läs mer om Adobe Campaign - Adobe Analytics-integrering i [den här sidan](../connect/ac-aa.md).

   ![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Services [kontakta Adobe](../start/campaign-faq.md#support) för att integrera Adobe Analytics med Campaign.

   * **Adobe Experience Manager**
   The **[!UICONTROL AEM]** Med ett externt konto kan ni hantera innehållet i era e-postleveranser samt formulären direkt i Adobe Experience Manager.

   ![](../assets/do-not-localize/glass.png) Läs mer om Adobe Campaign - Adobe Analytics-integrering i [den här sidan](../connect/ac-aem.md).

   ![](../assets/do-not-localize/speech.png)  Som användare av hanterade Cloud Services [kontakta Adobe](../start/campaign-faq.md#support) för att integrera Adobe Experience Manager med Adobe Campaign.


## Externa konton för CRM Connector

* **Microsoft Dynamics CRM**

   The **[!UICONTROL Microsoft Dynamics CRM]** Med ett externt konto kan du importera och exportera Microsoft Dynamics-data till Adobe Campaign.

   ![](../assets/do-not-localize/glass.png) Läs mer om Adobe Campaign - Microsoft Dynamics CRM-integrering i [den här sidan](../connect/crm.md).

   Med **[!UICONTROL Web API]** distributionstyp och **[!UICONTROL Password credentials]** autentisering måste du ange följande information:

   * **[!UICONTROL Account]**: Det konto som används för att logga in på Microsoft CRM.

   * **[!UICONTROL Server]**: URL till din Microsoft CRM-server.

   * **[!UICONTROL Client identifier]**: Klient-ID som kan hittas från Microsoft Azure-hanteringsportalen i **[!UICONTROL Update your code]** kategori, **[!UICONTROL Client ID]** fält.

   * **[!UICONTROL CRM version]**: CRM-version mellan **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** eller **[!UICONTROL Dynamics CRM 2016]**.
   Med **[!UICONTROL Web API]** distributionstyp och **[!UICONTROL Certificate]** autentisering måste du ange följande information:

   * **[!UICONTROL Server]**: URL till din Microsoft CRM-server.

   * **[!UICONTROL Private Key (Base64 encoded)]**: Privat nyckel kodad till Base64

   * **[!UICONTROL Custom Key identifier]**

   * **[!UICONTROL Key ID]**

   * **[!UICONTROL Client identifier]**: Klient-ID som kan hittas från Microsoft Azure-hanteringsportalen i **[!UICONTROL Update your code]** kategori, **[!UICONTROL Client ID]** fält.

   * **[!UICONTROL CRM version]**: CRM-version mellan **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** eller **[!UICONTROL Dynamics CRM 2016]**.


* **Salesforce.com**

   The **[!UICONTROL Salesforce CRM]** Med ett externt konto kan du importera och exportera Salesforce-data till Adobe Campaign.

   Om du vill konfigurera det externa Salesforce CRM-kontot så att det fungerar med Adobe Campaign måste du ange följande information:

   * **[!UICONTROL Account]**: Det konto som används för att logga in i Salesforce CRM.

   * **[!UICONTROL Password]**: Lösenord som används för att logga in i Salesforce CRM.

   * **[!UICONTROL Client identifier]**: Lär dig hur du hittar din klientidentifierare i [den här sidan](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Security token]**: Lär dig hur du hittar din säkerhetstoken i [den här sidan](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL API version]**: Välj version av API:t. För det här externa kontot måste du konfigurera Salesforce CRM med konfigurationsguiden.

## Externa konton för överföringsdata

Dessa externa konton kan användas för att importera eller exportera data till Adobe Campaign med en **[!UICONTROL Transfer file]** arbetsflödesaktivitet.

![](../assets/do-not-localize/book.png) Läs mer om filöverföring i arbetsflöden i [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/event-activities/file-transfer.html){target=&quot;_blank&quot;}

* **FTP och SFTP**

   The **FTP** Med ett externt konto kan du konfigurera och testa åtkomst till en server utanför Adobe Campaign. Om du vill konfigurera anslutningar med externa system som SFTP- eller FTP-servrar 898 som används för filöverföringar kan du skapa egna externa konton.
Om du vill göra det anger du den adress och de autentiseringsuppgifter som ska användas för att upprätta anslutningen till SFTP- eller FTP-servern i det här externa kontot.

* **Amazon Simple Storage Service (S3)**

   The **AWS S3** kan användas för att importera eller exportera data till Adobe Campaign med en **[!UICONTROL Transfer file]** arbetsflödesaktivitet. När du konfigurerar det nya externa kontot måste du ange följande information:

   * **[!UICONTROL AWS S3 Account Server]**: URL-adressen till servern, ifylld så här:   ```<S3bucket name>.s3.amazonaws.com/<s3object path>```

   * **[!UICONTROL AWS access key ID]**: Lär dig hur du hittar ditt ID för AWS-åtkomstnyckel i [Amazon-dokumentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

   * **[!UICONTROL Secret access key to AWS]**: Lär dig hur du hittar din hemliga åtkomstnyckel till AWS i [Amazon-dokumentation](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

   * **[!UICONTROL AWS Region]**: Läs mer om AWS regioner i [Amazon-dokumentation](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

   * The **[!UICONTROL Use server side encryption]** kan du lagra filen i S3-krypterat läge. Lär dig hur du hittar åtkomstnyckel-ID och hemlig åtkomstnyckel i [Amazon-dokumentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

* **Azure Blob Storage**

   The **Azure** externt konto kan användas för att importera eller exportera data till Adobe Campaign med en **[!UICONTROL Transfer file]** arbetsflödesaktivitet. Så här konfigurerar du **Azure** externt konto för att arbeta med Adobe Campaign måste du ange följande:

   * **[!UICONTROL Server]**: URL för din Azure Blob-lagringsserver.

   * **[!UICONTROL Encryption]**: Typ av kryptering mellan **[!UICONTROL None]** eller **[!UICONTROL SSL]**.

   * **[!UICONTROL Access key]**: Lär dig hur du hittar **[!UICONTROL Access key]** in [Microsoft-dokumentation](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
