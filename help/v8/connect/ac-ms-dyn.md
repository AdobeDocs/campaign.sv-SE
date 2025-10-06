---
title: Arbeta med Campaign och Microsoft Dynamics
description: Lär dig arbeta med Campaign och Microsoft Dynamics
feature: Microsoft CRM Integration
role: Admin, User
level: Beginner, Intermediate
exl-id: 4f9e8f74-27dc-482c-a83c-25623b53560f
source-git-commit: fbde111671fb972f6c96ba45eba4c8a88dbcac64
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 1%

---

# Arbeta med Campaign och Microsoft Dynamics 365{#crm-ms-dynamics}

Aktivera dina CRM-data för kommunikation över flera kanaler: lär dig hur du skickar kontakter från **Microsoft Dynamics 365** till Adobe Campaign och delar kampanjresultatdata (skickar, öppnar, klickar och studsar) tillbaka från Adobe Campaign till Microsoft Dynamics 365.

När konfigurationen är klar utförs datasynkronisering mellan system via en dedikerad arbetsflödesaktivitet. [Läs mer](crm-data-sync.md).

>[!NOTE]
>
>De Microsoft Dynamics-versioner som stöds beskrivs i Campaign [Kompatibilitetsmatrisen](../start/compatibility-matrix.md).

Följ stegen nedan för att konfigurera ett dedikerat externt konto för att importera och exportera Microsoft Dynamics 365-data till Adobe Campaign.

För varje system måste dessa steg utföras av en administratör.

>[!CAUTION]
> Steg i den här dokumentationen hjälper dig att skapa integreringar/registreringar som inbegriper tilldelning av behörigheter och/eller administratörsåtkomst. Det är ditt ansvar att se till att dessa steg följer företagets regler innan de utförs och att de utförs med omsorg.

## Konfigurera Microsoft Dynamics 365 {#config-crm-microsoft}

Om du vill ansluta Microsoft Dynamics 365 till Adobe Campaign via **webb-API** loggar du in på [Microsoft Azure Directory](https://portal.azure.com) med hjälp av en **global administratörs**-autentiseringsuppgift och följer stegen nedan:

1. Hämta ditt program-ID för Dynamics 365 (klient). [Läs mer](#get-client-id-microsoft)
1. Generera nyckelidentifierare och nyckel-ID för Microsoft Dynamics-certifikat. [Läs mer](#config-certificate-key-id)
1. Konfigurera behörigheter. [Läs mer](#config-permissions-microsoft)
1. Skapa en appanvändare. [Läs mer](#create-app-user-microsoft)
1. Koda den privata nyckeln. [Läs mer](#configure-acc-for-microsoftt)


### Hämta klient-ID för Dynamics 365 {#get-client-id-microsoft}

Om du vill hämta program-ID:t (klient) måste du registrera ett program i Azure Active Directory.

1. Bläddra till **Azure Active Directory > App Registrations** och välj **Ny registrering**.
1. Ange ett unikt namn som kan hjälpa till att identifiera en instans, till exempel **adobecampaign`<instance identifier>`**.

När du har sparat tilldelar Microsoft Azure Directory ditt program ett unikt **program-ID** (klient). Du behöver detta ID senare när du konfigurerar Dynamics 365 i Adobe Campaign.

Läs mer i [Microsoft Dynamics 365-dokumentationen](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory){target="_blank"}.

### Generera nyckelidentifierare och nyckel-ID för Microsoft Dynamics-certifikat {#config-certificate-key-id}

Du måste överföra ett certifikat för att hämta **certifikatnyckelidentifieraren (customKeyIdentifier)** och **nyckel-ID (keyId)**. Certifikat kan användas som hemligheter för att bevisa programmets identitet när en token begärs. Det kan också kallas publika nycklar.

Följ stegen nedan:

1. Bläddra till **Azure Active Directory > App Registrations** och välj det program som skapades tidigare.
1. Välj på **Certifikat och hemlighet**.
1. Klicka på **Överför certifikat** på fliken **Certifikat**
1. Överför ditt offentliga certifikat.
1. Bläddra till länken **Manifest** för att hämta **identifieraren för certifikatnyckeln (customKeyIdentifier)** och **nyckel-ID:t (keyId)**.

**Certifikatnyckelidentifieraren (customKeyIdentifier)** och **Key-ID (keyId)** behövs i Campaign för att konfigurera ditt externa Microsoft Dynamics 365 CRM-konto med hjälp av certifikatet **[!UICONTROL CRM O-Auth type]**.

+++ Så här skapar du det offentliga certifikatet

Om du vill generera certifikatet kan du använda openssl.

Exempel:

```
- openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
```

>[!NOTE]
>
>Du kan ändra antalet dagar, här `-days 365`, i kodexemplet för en längre certifikatgiltighetsperiod.

Du måste sedan koda certifikatet i base64. Det gör du genom att använda en Base64-kodare eller kommandoraden `base64 -w0 private.key` för Linux.

+++

### Konfigurera behörigheter {#config-permissions-microsoft}

**Steg 1**: Konfigurera **nödvändiga behörigheter** för det program som skapades.

1. Navigera till **Azure Active Directory > App Registrations** och välj det program som skapades tidigare.
1. Klicka på **Inställningar** överst till vänster.
1. På **Nödvändiga behörigheter** klickar du på **Lägg till** och **Välj ett API > Dynamics CRM Online**.
1. Klicka på kryssrutan **Välj**, aktivera kryssrutan **Använd Dynamics 365 som organisationsanvändare** och klicka på **Välj**.
1. Välj sedan **Manifest** på menyn **Hantera** i din app.
1. Ange egenskapen **från** till `allowPublicClient` i redigeraren `null`Manifest`true` och klicka på **Spara**.

**Steg 2**: Medgivande från bidragsadministratör

1. Navigera till **Azure Active Directory > Enterprise-program**.
1. Välj det program som du vill ge innehavaromfattande administratörsgodkännande för.
1. Välj **Behörigheter** under **Dokumentskydd** på den vänstra panelmenyn.
1. Klicka på **Bevilja administratörens samtycke**.

Mer information finns i [Azure-dokumentationen](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Skapa en appanvändare {#create-app-user-microsoft}

>[!NOTE]
>
> Det här steget är valfritt med **[!UICONTROL Password credentials]**-autentisering.

Appanvändaren är den användare som programmet som registrerats ovan kommer att använda. Alla ändringar som görs i Microsoft Dynamics med appen som registrerats ovan görs via den här användaren.

**Steg 1**: Skapa en icke-interaktiv användare i Azure Active Directory

1. Klicka på **Azure Active Directory > Användare** och sedan på **Ny användare**.
1. Ange ett egennamn som du vill använda och användarnamnet ska vara ett e-postformat.
1. Välj **Dynamics 365 Administrator** i **katalogrollen**.

**Steg 2**: Tilldela rätt licens till den skapade användaren

1. Klicka på [Admin-appen](https://portal.azure.com) från **Microsoft Azure**.
1. Gå till **Användare > Aktiva användare** och klicka på den nyskapade användaren.
1. Klicka på **Redigera produktlicenser** och välj **Dynamics 365 Customer Engagement Plan**.
1. Klicka på **Stäng**.

**Steg 3**: Skapa en programanvändare i Dynamics CRM

1. Navigera från [Microsoft Azure](https://portal.azure.com) till **Inställningar > Säkerhet > Användare**.
1. Klicka på listrutan, välj **Programanvändare** och klicka på **Nytt**.
1. Använd samma användarnamn som användaren som skapades i den aktiva katalogen ovan.
1. Tilldela **program-ID** för [det program du skapade tidigare](#get-client-id-microsoft).
1. Klicka på **Hantera roller** och välj rollen **Systemadministratör** för användaren.

## Konfigurera Campaign {#configure-acc-for-microsoft}

### Skapa anslutningen{#new-ms-dyn-external-account}

Först måste du skapa ett externt Microsoft Dynamics 365-konto.

1. Bläddra i noden **[!UICONTROL Administration > Platform > External accounts]** i Campaign Explorer och skapa ett externt konto.
1. Välj **[!UICONTROL Microsoft Dynamics CRM]** externt konto i avsnittet **Typ**.
1. Välj autentiseringsmetoden i listrutan **[!UICONTROL CRM O-Auth type]**.

   ![](assets/ms-dyn-external-account.png)

   1. Om du vill konfigurera det externa Microsoft Dynamics CRM-kontot så att det ansluter till Adobe Campaign med **lösenordsreferenser** anger du följande information:

      * **Server**: URL-adressen till din Microsoft CRM-server. Om du vill hitta URL-adressen till din Microsoft CRM-server öppnar du ditt Microsoft Dynamics CRM-konto, klickar på Dynamics 365 och väljer din app. Du kan sedan hitta din server-URL i webbläsarens adressfält, t.ex. https://myserver.crm.dynamics.com/.
      * **Konto**: Det konto som används för att logga in på Microsoft CRM.
      * **Lösenord**: Det konto som används för att logga in på Microsoft CRM.
      * **Klient-ID**: Program-ID (klient) som kan hittas från Microsoft Azure-hanteringsportalen i fältet Uppdatera din kodkategori, Klient-ID.
      * **CRM-version**: Välj Dynamics CRM 365 CRM-version.

   1. Om du vill konfigurera det externa Microsoft Dynamics CRM-kontot så att det ansluter till Adobe Campaign med ett **certifikat** anger du följande information:

      * **Server**: URL-adressen till din Microsoft CRM-server. Om du vill hitta URL-adressen till din Microsoft CRM-server öppnar du ditt Microsoft Dynamics CRM-konto, klickar på Dynamics 365 och väljer din app. Du kan sedan hitta din server-URL i webbläsarens adressfält, t.ex. https://myserver.crm.dynamics.com/.
      * **Privat nyckel**: Kopiera/klistra in den privata nyckeln, kodad base64 enligt beskrivningen i [det här avsnittet](#config-certificate-key-id).
      * **Nyckel-ID**: Nyckeln finns på fliken **Manifest** i ditt program, vilket förklaras i [det här avsnittet](#config-certificate-key-id).
      * **Anpassad nyckelidentifierare**: Identifieraren är tillgänglig på fliken **Manifest** i ditt program, vilket förklaras i [det här avsnittet](#config-certificate-key-id).
      * **Klient-ID**: Program-ID (klient) som kan hittas från Microsoft Azure-hanteringsportalen enligt beskrivningen i [det här avsnittet](#get-client-id-microsoft).
      * **CRM-version**: Välj Dynamics CRM 365 CRM-version.

1. Välj alternativet **Aktivera** om du vill aktivera kontot i Campaign.

>[!NOTE]
>
>Logga ut och sedan in på Adobe Campaign Client Console igen för att godkänna installationen.

### Markera tabeller som ska synkroniseras{#ms-dyn-create-tables}

Nu kan du konfigurera tabeller att synkronisera.

1. Klicka på **[!UICONTROL Microsoft CRM configuration wizard...]**.
1. Markera de tabeller som ska synkroniseras och starta processen.
1. Kontrollera schemat som genererats i Adobe Campaign i noden **[!UICONTROL Administration > Configuration > Data schemas]**.

>[!NOTE]
>
>Lägg till två URL:er i tillåtelselista: server-URL:en och `login.microsoftonline.com`. Kontakta din Adobe-representant för att göra detta.

## Synkronisera uppräkningar{#sfdc-enum-sync}

När schemat har skapats kan du synkronisera uppräkningar automatiskt från Dynamics 365 till Adobe Campaign.

1. Öppna assistenten från länken **[!UICONTROL Synchronizing enumerations...]**.
1. Välj den Adobe Campaign-uppräkning som matchar uppräkningen i Dynamics 365.
Du kan ersätta alla värden i en Adobe Campaign-uppräkning med dem i CRM: om du vill göra det väljer du **[!UICONTROL Yes]** i kolumnen **[!UICONTROL Replace]**.
1. Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Start]** för att börja importera uppräkningarna.
1. Bläddra i noden **[!UICONTROL Administration > Platform > Enumerations]** för att kontrollera importerade värden.

Adobe Campaign och Microsoft Dynamics 365 är nu anslutna. Du kan konfigurera datasynkronisering mellan de två systemen.

Om du vill synkronisera data mellan Adobe Campaign-data och Microsoft CRM skapar du ett arbetsflöde och använder aktiviteten **[!UICONTROL CRM connector]**.

Läs mer om datasynkronisering [på den här sidan](crm-data-sync.md).

Läs mer om uppräkningshantering i Campaign [på den här sidan](../dev/enumerations.md).

### Datatyper för fält som stöds {#ms-dyn-supported-types}

För Microsoft Dynamics 365-attributtyper som stöds/inte stöds finns följande:


| Attributtyp | Stöds |
| --------------------------------------------------------------------------------- | --------- |
| Grundläggande typer: boolesk, datetime, decimal, float, double, integer, bigint, string | Ja |
| Pengar (som dubbla) | Ja |
| memo, entityname , primarykey, uniqueidentifier (som strängar) | Ja |
| Status, picklist (vi lagrar möjliga värden i uppräkningar), state (sträng) | Ja |
| ägare (som sträng) | Ja |
| Uppslag (endast referenssökningar för en entitet) | Ja |
| kund | Nej |
| Angående | Nej |
| PartyList | Nej |
| ManagedProperty | Nej |
