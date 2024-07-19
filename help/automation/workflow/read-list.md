---
product: campaign
title: Läslista
description: Läs mer om arbetsflödesaktiviteten Läs lista
feature: Workflows, Targeting Activity
role: User, Data Engineer
exl-id: 91c87f8f-bdd2-4ca1-94c2-ec9e7affc1a0
source-git-commit: 28742db06b9ca78a4e952fcb0e066aa5ec344416
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Läslista{#read-list}

Data som bearbetas i ett arbetsflöde kan komma från listor där data har förberetts eller strukturerats i förväg (efter en tidigare segmentering eller filöverföring).

Med aktiviteten **[!UICONTROL Read list]** kan du kopiera data från en lista i arbetsflödets arbetstabell, till exempel data från en fråga. Den är sedan tillgänglig i hela arbetsflödet.

Listan som ska bearbetas kan anges explicit, beräknas av ett skript eller lokaliseras dynamiskt enligt valda alternativ och parametrar definierade i en **[!UICONTROL Read list]**-aktivitet.

![](assets/list_edit_select_option_01.png)

Om listan inte uttryckligen anges måste du ange en lista som ska användas som mall för att ta reda på dess struktur.

![](assets/s_advuser_list_template_select.png)

När listmarkeringen har konfigurerats kan du lägga till ett filter med alternativet **[!UICONTROL Edit query]** för att behålla en del av populationen för nästa arbetsflöde.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>För att kunna skapa ett filter i en läslisteaktivitet måste den relevanta listan vara av typen &quot;file&quot;.

Listorna kan skapas direkt i Adobe Campaign via länken **[!UICONTROL Profiles and Targets > Lists]** på startsidan. De kan också skapas i ett arbetsflöde med aktiviteten **[!UICONTROL List update]**.

**Exempel: Uteslut en lista med sändningsadresser**

I följande exempel kan du använda en lista med e-postadresser som ska uteslutas från e-postleveransmålet.

![](assets/s_advuser_list_read_sample_1.png)

Profilerna i mappen **Nya kontakter** måste ha en leveransåtgärd som mål. De e-postadresser som ska uteslutas från målet lagras i en extern lista. I vårt exempel krävs bara information om e-postadresser för att uteslutas.

1. Mappurvalsfrågan **Nya kontakter** måste göra det möjligt att läsa in de valda profilernas e-postadresser för att kunna aktivera justering mot informationen i listan.

   ![](assets/s_advuser_list_read_sample_0.png)

1. Här lagras listan i mappen **Lists** och etiketten beräknas.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Om du vill utesluta e-postadresserna för den externa listan från huvudmålet måste du konfigurera undantagsaktiviteten och ange att mappen **Nya kontakter** innehåller de data som ska behållas. Kopplingsdata mellan den här uppsättningen och andra inkommande uppsättningar från exkluderingsaktiviteten tas bort från målet.

   ![](assets/s_advuser_list_read_sample_3.png)

   Uteslutningsregler konfigureras i det centrala avsnittet av redigeringsverktyget. Klicka på knappen **[!UICONTROL Add]** för att definiera vilken typ av undantag som ska användas.

   Du kan definiera flera undantag beroende på antalet inkommande övergångar för aktiviteten.

1. I fältet **[!UICONTROL Exclusion set]** väljer du aktiviteten **[!UICONTROL Read list]**: data i den här aktiviteten ska exkluderas från huvuduppsättningen.

   I vårt exempel har vi ett undantag för kopplingar: data i listan kommer att stämma överens med data i huvuduppsättningen via fältet som innehåller e-postadressen. Om du vill konfigurera kopplingen väljer du **[!UICONTROL Joins]** i fältet **[!UICONTROL Change dimension]**.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Markera sedan det fält som motsvarar e-postadressen i de två uppsättningarna (Source och Mål). Kolumnerna länkas sedan och de mottagare vars e-postadress finns i listan över importerade adresser exkluderas från målet.
