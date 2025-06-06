---
product: campaign
title: Filöverföring
description: Läs mer om arbetsflödesaktiviteten Filöverföring
feature: Workflows, Data Management
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 794de398-f35d-4c2b-af29-d6fd38eb9394
source-git-commit: 4cbccf1ad02af9133d51933e3e0d010b5c8c43bd
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 1%

---

# Filöverföring{#file-transfer}

Med aktiviteten **Filöverföring** kan du ta emot eller skicka filer, testa om det finns filer eller lista över filer på en server. Det protokoll som används är antingen Azure Blob Storage, Amazon Simple Storage Service (S3), FTP eller SFTP.
Med S3, Azure Blob Storage eller SFTP-anslutning kan du även importera segmentdata till Adobe Campaign med Adobe kunddataplattform i realtid. Mer information finns i [dokumentationen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=sv-SE){target="_blank"}.

## Egenskaper {#properties}

Använd listrutan för fältet **[!UICONTROL Action]** för att välja åtgärd för aktiviteten.

![](assets/file_transfert_action.png)

Konfigurationen beror på den valda åtgärden.

1. **Tar emot filer**

   Om du vill ta emot filer som lagras på en fjärrserver väljer du **[!UICONTROL File download]** i fältet **[!UICONTROL Action]**. Du måste ange dess URL i det relevanta fältet.

   ![](assets/file_transfert_edit.png)

   Markera **[!UICONTROL Use an external account]** om du vill välja ett konto från Azure Blob Storage-, S3-, FTP- eller SFTP-konton som konfigurerats i noden **[!UICONTROL Administration > Platform > External accounts]** i trädet. Ange sedan vilken katalog på servern som innehåller de filer som ska hämtas.

   ![](assets/file_transfert_edit_external.png)

1. **Filöverföring**

   Om du vill skicka en fil till en server väljer du **[!UICONTROL File upload]** i fältet **[!UICONTROL Action]**. Du måste ange målservern i avsnittet **[!UICONTROL Remote server]** i redigeraren. Parametrarna är desamma som för inkommande filer. Se ovan.

   Källfilen kan komma från föregående aktivitet. I det här fallet måste alternativet **[!UICONTROL Use the file generated by the previous activity]** väljas.

   ![](assets/file_transfert_edit_send.png)

   Detta kan även gälla en eller flera andra filer. Om du vill markera dem avmarkerar du alternativet och klickar sedan på **[!UICONTROL Insert]**. Ange åtkomstsökvägen till filen som ska skickas. Klicka på **[!UICONTROL Insert]** igen om du vill lägga till en annan fil. Filerna har nu sina egna flikar.

   ![](assets/file_transfert_source.png)

   Använd pilarna för att ändra tabbordningen. Detta gäller den ordning som filerna skickas till servern i.

   Med alternativet **[!UICONTROL Keep history of files sent]** kan du spåra skickade filer. Den här historiken är tillgänglig från katalogen.

1. **Testa om filen finns**

   Om du vill testa om det finns en fil väljer du alternativet **[!UICONTROL Test to see if file exists]** i fältet **[!UICONTROL Action]**. Konfigurationen för fjärrservern är densamma som för filhämtning. Mer information finns i det här [avsnittet](#properties).

   ![](assets/file_transfert_edit_test.png)

1. **Lista över filer**

   Om du vill visa filerna väljer du alternativet **[!UICONTROL File listing]** i fältet **[!UICONTROL Action]**. Konfigurationen för fjärrservern är densamma som för mottagande filer. Mer information finns i det här [avsnittet](#properties).

   Alternativet **[!UICONTROL List all files]**, som är tillgängligt när du väljer åtgärden **[!UICONTROL File listing]**, gör att du kan lagra alla filer som finns på servern i händelsevariabeln **vars filnamn** avgränsas med `\n` tecken.

Det finns två möjliga alternativ för alla filöverföringsalternativ:

* Alternativet **[!UICONTROL Process missing file]** lägger till en övergång som aktiveras om det inte finns någon fil i den angivna katalogen.
* Alternativet **[!UICONTROL Process errors]** finns detaljerat i [Bearbetningsfel](monitor-workflow-execution.md#processing-errors).

Med länken **[!UICONTROL Advanced parameters...]** kan du komma åt följande alternativ:

![](assets/file_transfert_advanced.png)

* **[!UICONTROL Delete the source files after transfer]**

  Raderar filerna på fjärrservern. Om alternativet inte är markerat kontrollerar du att du manuellt övervakar storleken på ditt arkiverade innehåll i SFTP-katalogen.

* **[!UICONTROL Use SSL]**

  Gör att du kan använda en säker anslutning via SSL-protokollet under filöverföringar.

* **[!UICONTROL Display the session logs]**

  Gör att du kan återställa loggarna för Azure Blob Storage, S3, FTP eller SFTP och inkludera dem i arbetsflödesloggarna.

* **[!UICONTROL Disable passive mode]**

  Gör att du kan ange anslutningsporten som ska användas för dataöverföring.

Länken **[!UICONTROL File historization settings...]** ger åtkomst till alternativen som beskrivs i [Webbhämtning](web-download.md) (**[!UICONTROL File historization]** steg).

## Indataparametrar {#input-parameters}

* filnamn

  Den skickade filens fullständiga namn.

## Utdataparametrar {#output-parameters}

* filnamn

  Fullständigt namn på mottagen fil om alternativet **[!UICONTROL Use the file generated by the previous activity]** har valts.
