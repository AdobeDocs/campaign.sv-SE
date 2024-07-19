---
product: campaign
title: Filhämtare
description: Läs mer om arbetsflödesaktiviteten för filinsamlaren
feature: Workflows, Data Management
role: User
exl-id: 614becf7-4cbf-40f9-a1b1-06efa054bfd9
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Filhämtare{#file-collector}



**Filinsamlaren** övervakar en eller flera filers ankomst till en katalog och aktiverar övergången för varje mottagen fil. För varje händelse innehåller en **[!UICONTROL filename]**-variabel det fullständiga namnet på den mottagna filen. De insamlade filerna flyttas till en annan katalog för arkiveringsändamål och för att säkerställa att de bara räknas en gång.

Som standard är filinsamlaren en beständig uppgift som testar förekomsten av filer vid de tidpunkter som anges i schemat.

Filerna måste finnas på den server där den servermodul som ansvarar för det här arbetsflödet körs. Om flera wfserver-moduler distribueras på en enda instans måste antingen tillhörigheten för de aktiviteter som använder dessa filer eller arbetsflödets totala tillhörighet anges.

## Egenskaper {#properties}

På den första fliken i aktiviteten **[!UICONTROL File collector]** kan du välja källkatalogen och vid behov filtrera de insamlade filerna. De andra flikarna finns på [Inkommande e-post](inbound-emails.md) (**[!UICONTROL Schedule]** och **[!UICONTROL Expiry]** flikar).

![](assets/file_collect_edit.png)

1. **Hämtar filer**

   * **[!UICONTROL Directory]**

     Katalog som innehåller de filer som ska hämtas. Den här katalogen måste skapas i förväg på servern: Om den inte finns genereras ett fel.

   * **[!UICONTROL Filter]**

     Endast filer som matchar det här filtret beaktas. De andra filerna i katalogen ignoreras. Om filtret är tomt beaktas alla filer i katalogen. Filterexempel: **&#42;.zip**, **import-&#42;.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

     Om det här alternativet är aktiverat avslutas aktiviteten när den första filen har tagits emot. Om det finns flera filer som motsvarar filtret i katalogen kommer endast en att tas med i beräkningen. Det här alternativet garanterar att endast en händelse skickas. Den fil som tas med i beräkningen är den första i listan i alfabetisk ordning.

     Om det inte finns någon fil som matchar filtret i den angivna katalogen för en oschemalagd aktivitet, och om alternativet **[!UICONTROL Process file nonexistence]** inte är aktiverat, genereras ett fel.

   * **[!UICONTROL Execution schedule]**

     Bestämmer frekvensen för filnärvarokontrollen via parametrarna på fliken **[!UICONTROL Schedule]**.

1. **Felhantering**

   Följande två alternativ är tillgängliga:

   * **[!UICONTROL Process file nonexistence]**

     Med det här alternativet initieras en speciell övergång varje gång ingen fil som matchar filtret hittas i den angivna katalogen.

     Om aktiviteten inte är schemalagd kommer den här övergången endast att aktiveras en gång.

   * **[!UICONTROL Processing errors]**

     Med det här alternativet visas en speciell övergång som aktiveras om ett fel genereras. I det här fallet ändras inte arbetsflödet till felstatus och körningen fortsätter

     Fel som beaktas är filsystemfel (filen kunde inte flyttas, katalogen kunde inte nås osv.).

     Det här alternativet bearbetar inte fel relaterade till aktivitetskonfigurationen, dvs. ogiltiga värden.

1. **Historisering**

   Se **[!UICONTROL File historization]**-steget här: [Webbhämtning](web-download.md).

Filbearbetningsordningen kan inte bestämmas. Om du vill bearbeta en uppsättning filer sekventiellt använder du alternativet **[!UICONTROL Stop as soon as a file has been processed]** och skapar en slinga. I så fall bearbetas filerna i alfabetisk ordning. Med alternativet **[!UICONTROL Process file nonexistence]** kan du slutföra iterationen.

![](assets/file_collect_loop.png)

## Utdataparametrar {#output-parameters}

* filnamn: Fullständigt filnamn. Det här är filnamnet när det har flyttats till historikkatalogen. Sökvägen är därför annorlunda, men namnet är också annorlunda om det redan finns en annan fil med samma namn i katalogen. Utbyggnaden behålls.
