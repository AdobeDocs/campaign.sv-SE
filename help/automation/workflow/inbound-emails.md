---
product: campaign
title: Inkommande e-postmeddelanden
description: Läs mer om arbetsflödesaktiviteten för inkommande e-post
feature: Workflows, Channels Activity
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 6cc2c415-1886-4f31-8020-dbaf97a3cc43
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---

# Inkommande e-postmeddelanden{#inbound-emails}



Med aktiviteten **Inkommande e-post** kan du hämta och bearbeta e-postmeddelanden från en POP3-e-postserver.

![](assets/email_rec_edit_1.png)

På den första fliken i aktiviteten **Inkommande e-post** kan du ange parametrarna för POP3-servern och ange det skript som ska köras när varje meddelande tas emot. På den andra fliken kan du tilldela aktiviteten ett schema och på den tredje fliken definieras aktivitetens förfallovillkor.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

     När det här alternativet är aktiverat kan du välja ett externt POP3-konto i stället för att ange anslutningsparametrarna. Fältet **[!UICONTROL External account]** anger det externa POP3-konto som ska användas för att ansluta till e-posttjänsten. Det här fältet är bara synligt om alternativet Använd ett externt konto är aktiverat.

     Om det här alternativet inte är markerat måste du ange följande parametrar:

     ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

        Namn på POP3-servern.

      * **[!UICONTROL POP3 account]**

        Användarens namn.

      * **[!UICONTROL Password]**

        Lösenord för användarkonto.

      * **[!UICONTROL Port]**

        Portnummer för POP3-anslutning. Standardporten är 10.

   * **[!UICONTROL Stop as soon as email is processed]**

     Med det här alternativet kan du bearbeta e-postmeddelanden en i taget. Aktiviteten aktiverar endast övergången en gång och slutför sedan bearbetningen, vilket lämnar obearbetade meddelanden på servern.

1. **[!UICONTROL Script]**

   Skriptet låter dig bearbeta meddelandet och utföra olika åtgärder som är beroende av meddelandets innehåll. Skriptet körs för varje meddelande och kan avgöra vilken åtgärd som ska utföras för meddelanden (lämna eller ta bort meddelandet) och aktivering av den utgående övergången.

   Returkoden måste vara något av följande värden:

   * 1 - Tar bort meddelandet från servern och aktiverar den utgående övergången.
   * 2 - Lämnar meddelandet på servern och aktiverar den utgående övergången.
   * 3 - Tar bort meddelandet från servern.
   * 4 - Lämnar meddelandet på servern.

   Innehållet i meddelandet är tillgängligt från den globala variabeln **[!UICONTROL mailMessage]**.

1. **[!UICONTROL Schedule]**

   Om du vill definiera ett schema för aktiviteten klickar du på fliken **[!UICONTROL Scheduling]** och markerar **[!UICONTROL Plan execution]**. Klicka på knappen **[!UICONTROL Change]** för att konfigurera schemat.

   Schemaläggningskonfigurationen är densamma som för schemaläggningsaktiviteten. Se [Schemaläggaren](scheduler.md).

1. **[!UICONTROL Expiration]**

   Du kan definiera förfallotider på fliken **[!UICONTROL Expiration]**.

   ![](assets/email_rec_edit_3.png)

   Konfigurationen är densamma som för schemaläggningsaktiviteten. Se [Förfallodatum](define-approvals.md).
