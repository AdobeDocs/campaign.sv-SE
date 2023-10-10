---
product: campaign
title: Inkommande e-postmeddelanden
description: Läs mer om arbetsflödesaktiviteten för inkommande e-post
feature: Workflows, Channels Activity
role: User
exl-id: 6cc2c415-1886-4f31-8020-dbaf97a3cc43
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# Inkommande e-postmeddelanden{#inbound-emails}



The **Inkommande e-postmeddelanden** Med -aktiviteten kan du hämta och bearbeta e-postmeddelanden från en POP3-postserver.

![](assets/email_rec_edit_1.png)

Den första fliken i **Inkommande e-postmeddelanden** Med -aktivitet kan du ange parametrar för POP3-servern och ange det skript som ska köras när varje meddelande tas emot. På den andra fliken kan du tilldela aktiviteten ett schema och på den tredje fliken definieras aktivitetens förfallovillkor.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

     När det här alternativet är aktiverat kan du välja ett externt POP3-konto i stället för att ange anslutningsparametrarna. The **[!UICONTROL External account]** -fältet anger det externa POP3-konto som ska användas för att ansluta till e-posttjänsten. Det här fältet är bara synligt om alternativet Använd ett externt konto är aktiverat.

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

   Innehållet i meddelandet är tillgängligt från den globala **[!UICONTROL mailMessage]** variabel.

1. **[!UICONTROL Schedule]**

   Om du vill definiera ett schema för aktiviteten klickar du på **[!UICONTROL Scheduling]** tabb och kontrollera **[!UICONTROL Plan execution]**. Klicka på **[!UICONTROL Change]** för att konfigurera schemat.

   Schemaläggningskonfigurationen är densamma som för schemaläggningsaktiviteten. Se [Schemaläggare](scheduler.md).

1. **[!UICONTROL Expiration]**

   Du kan ange förfallotider via **[!UICONTROL Expiration]** -fliken.

   ![](assets/email_rec_edit_3.png)

   Konfigurationen är densamma som för schemaläggningsaktiviteten. Se [Förfallodatum](define-approvals.md).
