---
title: Arbeta med Campaign och Microsoft Dynamics
description: Lär dig hur du arbetar med Campaign och Microsoft Dynamics
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 4f9e8f74-27dc-482c-a83c-25623b53560f
source-git-commit: 6de5c93453ffa7761cf185dcbb9f1210abd26a0c
workflow-type: tm+mt
source-wordcount: '1366'
ht-degree: 1%

---

# Arbeta med Campaign och Microsoft Dynamics 365{#crm-ms-dynamics}

Aktivera dina CRM-data för kommunikation över flera kanaler: lära dig hur du överför kontakter från **Microsoft Dynamics 365** till Adobe Campaign och dela kampanjresultatdata (skickar, öppnar, klickar och studsar) tillbaka från Adobe Campaign till Microsoft Dynamics 365.

När konfigurationen är klar utförs datasynkronisering mellan system via en dedikerad arbetsflödesaktivitet. [Läs mer](crm-data-sync.md).

>[!NOTE]
>
>De Microsoft Dynamics-versioner som stöds finns detaljerade i Campaign [Kompatibilitetsmatris](../start/compatibility-matrix.md).

Följ stegen nedan för att konfigurera ett dedikerat externt konto för att importera och exportera Microsoft Dynamics 365-data till Adobe Campaign.

För varje system måste dessa steg utföras av en administratör.

>[!CAUTION]
> Steg i den här dokumentationen hjälper dig att skapa integreringar/registreringar som inbegriper tilldelning av behörigheter och/eller administratörsåtkomst. Det är ditt ansvar att se till att dessa steg följer företagets regler innan de utförs och att de utförs med omsorg.

## Konfigurera Microsoft Dynamics 365 {#config-crm-microsoft}

Koppla Microsoft Dynamics 365 till Adobe Campaign via **Webb-API**, logga in på [Microsoft Azure-katalog](https://portal.azure.com) med **Global administratör** och följ stegen nedan:

1. Hämta ditt program-ID för Dynamics 365 (klient). [Läs mer](#get-client-id-microsoft)
1. Generera nyckelidentifierare och nyckel-ID för Microsoft Dynamics-certifikat. [Läs mer](#config-certificate-key-id)
1. Konfigurera behörigheter. [Läs mer](#config-permissions-microsoft)
1. Skapa en appanvändare. [Läs mer](#create-app-user-microsoft)
1. Koda den privata nyckeln. [Läs mer](#configure-acc-for-microsoftt)


### Hämta klient-ID för Dynamics 365 {#get-client-id-microsoft}

Om du vill hämta program-ID:t (klient) måste du registrera ett program i Azure Active Directory.

1. Bläddra till **Azure Active Directory > App Registrations** och markera **Ny registrering**.
1. Ange ett unikt namn som kan hjälpa till att identifiera en instans, till exempel **adobecampaign`<instance identifier>`**.

När du har sparat tilldelas en unik **Program-ID (klient)** till appen. Du behöver detta ID senare när du konfigurerar Dynamics 365 i Adobe Campaign.

Läs mer i [Microsoft Dynamics 365-dokumentation](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory){target=&quot;_blank&quot;}.

### Generera nyckelidentifierare och nyckel-ID för Microsoft Dynamics-certifikat {#config-certificate-key-id}

För att få **Identifierare för certifikatnyckel (customKeyIdentifier)** och **Nyckel-ID (keyId)** måste du överföra ett certifikat. Certifikat kan användas som hemligheter för att bevisa programmets identitet när en token begärs. Det kan också kallas publika nycklar.

Följ stegen nedan:

1. Bläddra till **Azure Active Directory > App Registrations** och välj programmet som skapades tidigare.
1. Välj på **Certifikat och hemlighet**.
1. Från **Certifikat** flik, klicka på **Överför certifikat**
1. Överför ditt offentliga certifikat.
1. Bläddra till **Manifest** länk för att hämta **Identifierare för certifikatnyckel (customKeyIdentifier)** och **Nyckel-ID (keyId)**.

The **Identifierare för certifikatnyckel (customKeyIdentifier)** och **Nyckel-ID (keyId)** behövs i Campaign för att konfigurera ditt externa Microsoft Dynamics 365 CRM-konto med hjälp av certifikatet **[!UICONTROL CRM O-Auth type]**.

+++ Så här skapar du det offentliga certifikatet

Om du vill generera certifikatet kan du använda openssl.

Exempel:

```
- openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
```

>[!NOTE]
>
>Du kan ändra antalet dagar här `-days 365`, i kodexemplet för en längre certifikatgiltighetsperiod.

Du måste sedan koda certifikatet i base64. Om du vill göra det kan du använda hjälp av en Base64-kodare eller kommandoraden `base64 -w0 private.key` för Linux.

+++

### Konfigurera behörigheter {#config-permissions-microsoft}

**Steg 1**: Konfigurera **Nödvändiga behörigheter** för programmet som skapades.

1. Navigera till **Azure Active Directory > App Registrations** och välj programmet som skapades tidigare.
1. Klicka **Inställningar** överst till vänster.
1. På **Nödvändiga behörigheter**, klicka **Lägg till** och **Välj ett API > Dynamics CRM Online**.
1. Klicka **Välj**, aktivera **Använd Dynamics 365 som organisationsanvändare** kryssruta och klicka **Välj**.
1. Välj sedan **Manifest** under **Hantera** -menyn.
1. Från **Manifest** redigeraren, ange `allowPublicClient` egenskap från `null` till `true` och klicka **Spara**.

**Steg 2**: Medgivande från bidragsadministratör

1. Navigera till **Azure Active Directory > Enterprise Applications**.
1. Välj det program som du vill ge innehavaromfattande administratörsgodkännande för.
1. Välj **Behörigheter** under **Säkerhet**.
1. Klicka **Medgivande från bidragsadministratör**.

Mer information finns i [Azure-dokumentation](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Skapa en appanvändare {#create-app-user-microsoft}

>[!NOTE]
>
> Det här steget är valfritt med **[!UICONTROL Password credentials]** autentisering.

Appanvändaren är den användare som programmet som registrerats ovan kommer att använda. Alla ändringar som görs i Microsoft Dynamics med den app som registrerats ovan görs via den här användaren.

**Steg 1**: Skapa en icke-interaktiv användare i azure Active Directory

1. Klicka **Azure Active Directory > Användare** och klicka **Ny användare**.
1. Ange ett egennamn som du vill använda och användarnamnet ska vara ett e-postformat.
1. Välj **Dynamics 365-administratör** i **Katalogroll**.

**Steg 2**: Tilldela den skapade användaren en korrekt licens

1. Från [Microsoft Azure](https://portal.azure.com), klicka på **Administratörsapp**.
1. Gå till **Användare > Aktiva användare** och klicka på den nyskapade användaren.
1. Klicka på **Redigera produktlicenser** och väljer **Dynamics 365 Customer Engagement Plan**.
1. Klicka **Stäng**.

**Steg 3**: Skapa en programanvändare i Dynamics CRM

1. Från [Microsoft Azure](https://portal.azure.com), navigera till **Inställningar > Dokumentskydd > Användare**.
1. Klicka på listrutan och välj **Programanvändare** och klicka **Nytt**.
1. Använd samma användarnamn som användaren som skapades i den aktiva katalogen ovan.
1. Tilldela **Program-ID** for [det program du skapade tidigare](#get-client-id-microsoft).
1. Klicka på **Hantera roller** och väljer **Systemadministratör** till användaren.

## Konfigurera Campaign {#configure-acc-for-microsoft}

### Skapa anslutningen{#new-ms-dyn-external-account}

Först måste du skapa det externa kontot för Microsoft Dynamics 365.

1. Bläddra i **[!UICONTROL Administration > Platform > External accounts]** noden i Campaign Explorer och skapa ett externt konto.
1. Välj **[!UICONTROL Microsoft Dynamics CRM]** externt konto i **Typ** -avsnitt.
1. Välj autentiseringsmetod i dialogrutan **[!UICONTROL CRM O-Auth type]** nedrullningsbar lista.

   ![](assets/ms-dyn-external-account.png)

   1. Så här konfigurerar du det externa Microsoft Dynamics CRM-kontot för att ansluta till Adobe Campaign med **Lösenordsreferenser**, lämna följande uppgifter:

      * **Server**: URL till din Microsoft CRM-server. Om du vill hitta URL-adressen till din Microsoft CRM-server öppnar du ditt Microsoft Dynamics CRM-konto och klickar sedan på Dynamics 365 och väljer din app. Du kan sedan hitta din server-URL i webbläsarens adressfält, t.ex. https://myserver.crm.dynamics.com/.
      * **Konto**: Det konto som används för att logga in på Microsoft CRM.
      * **Lösenord**: Det konto som används för att logga in på Microsoft CRM.
      * **Klient-ID**: Program-ID (klient) som finns på Microsoft Azure-hanteringsportalen i fältet Uppdatera din kodkategori, Klient-ID.
      * **CRM-version**: Välj Dynamics CRM 365 CRM-version.
   1. Så här konfigurerar du det externa Microsoft Dynamics CRM-kontot att ansluta till Adobe Campaign med en **Certifikat**, lämna följande uppgifter:

      * **Server**: URL till din Microsoft CRM-server. Om du vill hitta URL-adressen till din Microsoft CRM-server öppnar du ditt Microsoft Dynamics CRM-konto och klickar sedan på Dynamics 365 och väljer din app. Du kan sedan hitta din server-URL i webbläsarens adressfält, t.ex. https://myserver.crm.dynamics.com/.
      * **Privat nyckel**: Kopiera/klistra in den privata nyckeln, kodad base64 enligt anvisningarna i [det här avsnittet](#config-certificate-key-id).
      * **Nyckel-ID**: Nyckeln finns i **Manifest** -fliken i ditt program, enligt anvisningarna i [det här avsnittet](#config-certificate-key-id).
      * **Anpassad nyckel-ID**: Identifieraren finns i **Manifest** -fliken i ditt program, enligt anvisningarna i [det här avsnittet](#config-certificate-key-id).
      * **Klient-ID**: Program-ID (klient) som kan hittas från Microsoft Azure-hanteringsportalen enligt beskrivningen i [det här avsnittet](#get-client-id-microsoft).
      * **CRM-version**: Välj Dynamics CRM 365 CRM-version.


1. Välj **Aktivera** möjlighet att aktivera kontot i Campaign.

>[!NOTE]
>
>Logga ut och sedan in på Adobe Campaign-konsolen igen för att godkänna installationen.

### Markera tabeller som ska synkroniseras{#ms-dyn-create-tables}

Nu kan du konfigurera tabeller att synkronisera.

1. Klicka på **[!UICONTROL Microsoft CRM configuration wizard...]**.
1. Markera de tabeller som ska synkroniseras och starta processen.
1. Kontrollera schemat som genererats i Adobe Campaign i **[!UICONTROL Administration > Configuration > Data schemas]** nod.

>[!NOTE]
>
>Lägg till två URL:er i tillåtelselista: server-URL och `login.microsoftonline.com`. Kontakta din Adobe-representant för att göra detta.

## Synkronisera uppräkningar{#sfdc-enum-sync}

När schemat har skapats kan du synkronisera uppräkningar automatiskt från Dynamics 365 till Adobe Campaign.

1. Öppna assistenten från  **[!UICONTROL Synchronizing enumerations...]** länk.
1. Välj den Adobe Campaign-uppräkning som matchar uppräkningen i Dynamics 365.
Du kan ersätta alla värden i en Adobe Campaign-uppräkning med dem i CRM: för att göra detta väljer du **[!UICONTROL Yes]** i **[!UICONTROL Replace]** kolumn.
1. Klicka **[!UICONTROL Next]** och sedan **[!UICONTROL Start]** för att börja importera uppräkningarna.
1. Bläddra i **[!UICONTROL Administration > Platform > Enumerations]** nod för att kontrollera importerade värden.

Adobe Campaign och Microsoft Dynamics 365 är nu anslutna. Du kan konfigurera datasynkronisering mellan de två systemen.

Om du vill synkronisera data mellan Adobe Campaign-data och Microsoft CRM skapar du ett arbetsflöde och använder **[!UICONTROL CRM connector]** aktivitet.

Läs mer om datasynkronisering [på den här sidan](crm-data-sync.md).

### Datatyper för fält som stöds {#ms-dyn-supported-types}

För Microsoft Dynamics 365 finns följande attributtyper som stöds/inte stöds:


| Attributtyp | Stöds |
| --------------------------------------------------------------------------------- | --------- |
| Grundläggande typer: boolean, datetime, decimal, float, double, integer, bigint , string | Ja |
| Pengar (som dubbla) | Ja |
| memo, entityname , primarykey, uniqueidentifier (som strängar) | Ja |
| Status, picklist (vi lagrar möjliga värden i uppräkningar), state (sträng) | Ja |
| ägare (som sträng) | Ja |
| Uppslag (endast referenssökningar för en enhet) | Ja |
| kund | Nej |
| Angående | Nej |
| PartyList | Nej |
| ManagedProperty | Nej |
