---
product: campaign
title: Skapa en lokal kampanj
description: Skapa en lokal kampanj
feature: Distributed Marketing
role: User
exl-id: b46530b5-cb81-40d7-b596-c7685359782a
source-git-commit: 567c2e84433caab708ddb9026dda6f9cb717d032
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 1%

---

# Skapa en lokal kampanj{#creating-a-local-campaign}



En lokal kampanj är en instans som skapats från en mall som refereras i listan med **[!UICONTROL campaign packages]** med **specifikt körningsschema**. Syftet är att tillgodose ett lokalt kommunikationsbehov med hjälp av en kampanjmall som har konfigurerats och konfigurerats av den centrala enheten. De viktigaste stegen för att genomföra en lokal åtgärd är följande:

**För den centrala enheten**

1. Skapa en lokal kampanjmall.
1. Skapa ett kampanjpaket från en mall.
1. Publicera ett kampanjpaket.
1. Godkänner order.

**För den lokala enheten**

1. Beställa kampanjen.
1. Kör kampanjer.

## Skapa en lokal kampanjmall {#creating-a-local-campaign-template}

Om du vill skapa ett kampanjpaket måste du först skapa **kampanjmall** via **[!UICONTROL Resources > Templates]** nod.

Om du vill skapa en ny lokal mall duplicerar du standardmallen **[!UICONTROL Local campaign (opLocal)]** mall.

![](assets/mkg_dist_local_op_creation.png)

Ge kampanjmallen ett namn och fyll i de tillgängliga fälten.

![](assets/mkg_dist_local_op_creation1.png)

Klicka på **[!UICONTROL Edit]** klickar du på **[!UICONTROL Advanced campaign parameters...]** länk.

![](assets/mkt_distr_4.png)

### Webbgränssnitt {#web-interface}

I **Distribuerad marknadsföring** kan du välja typ av webbgränssnitt och ange standardvärden och parametrar som ska anges när en lokal enhet placerar en order.

Webbgränssnittet motsvarar ett formulär som ska fyllas i av den lokala enheten när kampanjen beställs.

Välj vilken typ av webbgränssnitt som ska användas för kampanjer som skapas från mallen:

![](assets/mkt_distr_1.png)

Det finns fyra typer av webbgränssnitt:

* **[!UICONTROL By brief]** : lokal entitet måste tillhandahålla en beskrivning som beskriver kampanjkonfigurationerna. När ordern har godkänts konfigurerar och kör den centrala enheten kampanjen som helhet.

  ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** : lokal enhet har åtkomst till ett webbformulär där den, beroende på vilken mall som används, kan redigera innehållet, målet, dess maximala storlek samt datum för skapande och extrahering med hjälp av anpassningsfält. Lokal enhet kan utvärdera mål- och förhandsgranskningsinnehållet från det här webbformuläret.

  ![](assets/mkt_distr_8.png)

  Formuläret som erbjuds anges i ett webbprogram som måste väljas i en nedrullningsbar lista på menyn **[!UICONTROL web Interface]** i mallens **[!UICONTROL Advanced campaign parameters...]** länk. Se [Skapa en lokal kampanj (per formulär)](examples.md#creating-a-local-campaign--by-form-).

  >[!NOTE]
  >
  >Webbprogrammet som används i det här exemplet är ett exempel. Du måste skapa ett specifikt webbprogram för att kunna använda ett formulär.

  ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** : lokal entitet har åtkomst till kampanjparametrar i extranätet (inte Adobe Campaign). De här parametrarna är identiska med parametrarna i en **lokal kampanj (per formulär)**.
* **[!UICONTROL Pre-set]** : lokal enhet beställer kampanj med standardformuläret, utan att lokalisera den.

  ![](assets/mkt_distr_5.png)

### Standardvärden {#default-values}


Välj **[!UICONTROL Default values]** som ska fyllas i av lokala enheter. Exempel:

* Kontakt- och extraktionsdatum.
* målegenskaper (ålderssegment osv.).

![](assets/mkg_dist_local_op_creation2.png)

Slutför **[!UICONTROL Parent marketing program]** och **[!UICONTROL Charge]** fält.

![](assets/mkg_dist_local_op_creation3.png)

### Godkännanden {#approvals}

Från **[!UICONTROL Advanced parameters for campaign entry]** kan du ange maximalt antal granskare.

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

Granskare anges av den lokala enheten när kampanjen beställs.

![](assets/mkt_distr_5.png)

Ange 0 om du inte vill namnge granskare för en kampanj.

### Dokument {#documents}

Du kan tillåta lokala entitetsoperatorer att länka dokument (textfiler, kalkylblad, bilder, kampanjbeskrivningar osv.) till den lokala kampanjen när ordern skapas. The **[!UICONTROL Advanced parameters for campaign entry...]** kan du begränsa antalet dokument. Om du vill göra det anger du det maximala antalet i dialogrutan **[!UICONTROL Number of documents]** fält.

![](assets/s_advuser_mkg_dist_local_docs.png)

När du beställer ett kampanjpaket föreslår formuläret att du länkar så många dokument som anges i motsvarande fält i mallen.

![](assets/s_advuser_mkg_dist_add_docs.png)

Om du inte vill visa ett dokumentöverföringsfält anger du **[!UICONTROL 0]** i **[!UICONTROL Number of documents]** fält.

>[!NOTE]
>
>The **[!UICONTROL Advanced parameters for campaign entry]** kan inaktiveras genom kontroll **[!UICONTROL Do not display the page used to enter the campaign parameters]**.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### Arbetsflöde {#workflow}

I **[!UICONTROL Targeting and workflows]** skapar du ett kampanjarbetsflöde som samlar in **[!UICONTROL Default values]** som anges i **[!UICONTROL Advanced campaign parameters...]** och skapar leveranserna.

![](assets/mkg_dist_local_op_creation4b.png)

Dubbelklicka på **[!UICONTROL Query]** aktivitet som konfigurerar den enligt angivet **[!UICONTROL Default values]**.

![](assets/mkt_dist_local_campaign_localize_query.png)

### Leverans {#delivery}

I **[!UICONTROL Audit]** klickar du på **[!UICONTROL Detail...]** -ikonen för att visa **[!UICONTROL Scheduling]** för vald leverans.

![](assets/mkg_dist_local_op_creation4c.png)

The **[!UICONTROL Scheduling]** Med -ikonen kan du konfigurera leveransens kontakt- och körningsdatum.

![](assets/mkg_dist_local_op_creation4d.png)

Konfigurera vid behov maxstorleken för leveransen:

![](assets/mkg_dist_local_op_creation4e.png)

Hitta HTML. Till exempel i **[!UICONTROL Delivery > Current order > Additional fields]**, använder du **[!UICONTROL Age segment]** för att hitta leveransen enligt målets ålder.

![](assets/mkt_dist_local_campaign_localize_html.png)

Spara kampanjmallen. Du kan nu använda den från **[!UICONTROL Campaign packages]** visa i **[!UICONTROL Campaigns]** genom att klicka på **[!UICONTROL Create]** -knappen.

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>Kampanjmallar och deras allmänna konfiguration finns i [den här sidan](../campaigns/marketing-campaign-templates.md).

## Skapa kampanjpaketet {#creating-the-campaign-package}

För att kampanjmallen ska bli tillgänglig för lokala enheter måste den läggas till i listan. För att göra detta måste centralmyndigheten skapa ett nytt paket.

Använd följande steg:

1. I **[!UICONTROL Navigation]** i **Kampanjer** klickar du på **[!UICONTROL Campaign packages]** länk.
1. Klicka på knappen **[!UICONTROL Create]**.

   ![](assets/mkg_dist_add_an_entry.png)

1. I avsnittet ovanför fönstret kan du välja [tidigare](#creating-a-local-campaign-template) angiven kampanjpaketmall.

   Som standard är **[!UICONTROL New local campaign package (localEmpty)]** -mall används för lokala kampanjer.

1. Ange etikett, mapp och körningsschema för kampanjpaketet.

### Datum {#dates}

Start- och slutdatumen definierar kampanjens synlighetsperiod i listan över kampanjpaket.

Tillgänglighetsdatumet är det datum då kampanjen blir tillgänglig för lokala enheter (att beställa).

>[!CAUTION]
>
>Om en lokal enhet inte reserverar kampanjen före deadline kommer den inte att kunna använda den.

Denna information finns i det meddelande som skickas till lokala myndigheter, vilket visas nedan:

![](assets/s_advuser_mkg_dist_local_notif.png)

### Målgrupp {#audience}

För en lokal kampanj kan den centrala enheten ange vilka lokala enheter som berörs genom att kontrollera **[!UICONTROL Limit the package to a set of local entities]**.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### Ytterligare inställningar {#additional-settings}

När paketet har sparats kan den centrala enheten redigera det från **[!UICONTROL Edit]** -fliken.

![](assets/mkg_dist_edit_kit.png)

Från **[!UICONTROL General]** kan den centrala enheten

* konfigurera granskare av kampanjpaket från **[!UICONTROL Approval parameters...]** länk,
* Granska körningsplanen.
* lägga till eller ta bort lokala entiteter.

>[!NOTE]
>
>Som standard kan varje enhet beställa en **lokal kampanj** bara en gång.
>   
>Kontrollera **[!UICONTROL Enable multiple creation]** möjlighet att tillåta att flera lokala kampanjer skapas från kampanjpaketet.

![](assets/mkg_dist_local_op_multi_crea.png)

### Meddelanden {#notifications}

När en kampanj blir tillgänglig eller när tidsgränsen för registrering nås, skickas ett meddelande till operatörerna i den lokala meddelandegruppen. Mer information finns i [Organisationsenheter](about-distributed-marketing.md#organizational-entities).

## Beställa en kampanj {#ordering-a-campaign}

Kampanjpaket blir tillgängliga för lokala enheter när de har godkänts och implementeringsperioden har startats. Lokala enheter får ett e-postmeddelande som meddelar dem om att ett nytt kampanjpaket är tillgängligt (så snart som dess tillgänglighetsdatum har nåtts).

>[!NOTE]
>
>Om vissa lokala entiteter angavs när kampanjpaketet skapades är det de enda som får ett meddelande. Om ingen lokal enhet har angetts får alla lokala enheter ett meddelande.

![](assets/mkg_dist_local_op_notification.png)

För att kunna använda en kampanj som erbjuds av den centrala enheten måste den lokala enheten beställa den.

Så här beställer du en kampanj:

1. Klicka **[!UICONTROL Order campaign]** i meddelandet eller motsvarande knapp i Adobe Campaign.

   Ange ditt ID och lösenord för att beställa kampanjen. Gränssnittet består av en uppsättning sidor som definieras i ett webbprogram.

1. Ange nödvändig information på den första sidan (ordningsetikett och kommentar) och klicka på **[!UICONTROL Next]**.

   ![](assets/mkg_dist_subscribe_step1.png)

1. Slutför de tillgängliga parametrarna och godkänn ordern.

1. Ett meddelande skickas till chefen för den organisationsenhet som den lokala enheten tillhör för att godkänna ordern.

   ![](assets/mkg_dist_subscribe_step3.png)

1. Informationen returneras till de lokala och centrala enheterna. Lokala enheter kan bara visa sina egna order, men den centrala enheten kan visa alla order från vilken lokal enhet som helst, vilket visas nedan:

   ![](assets/mkg_dist_subscribe_central_view.png)

   Operatorer kan visa orderinformation:

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   The **[!UICONTROL Edit]** -fliken innehåller information som anges av den lokala enheten när kampanjen beställs.

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. Ordern måste godkännas av den centrala enhet som ska färdigställas.

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   Mer information finns i [Godkännandeprocess](#approval-process) -avsnitt.

1. Den lokala operatorn meddelas sedan om att kampanjen är tillgänglig: kampanjtillgängligheten finns i listan över kampanjpaket i **Kampanjer** -fliken. Kampanjen kan sedan användas. Mer information finns i [Åtkomst till kampanjer](accessing-campaigns.md).

   The **[!UICONTROL Start targeting with order approval]** gör att den lokala enheten kan köra kampanjen så snart ordern har godkänts.

   ![](assets/mkg_dist_local_op_catalog_use.png)

## Godkänna en order {#approving-an-order}

Den centrala enheten måste godkänna en kampanjorder för att bekräfta den.

The **[!UICONTROL Campaign orders]** översikt, via **Kampanjer** kan du visa status för kampanjorder och godkänna dem.

>[!NOTE]
>
>Lokala enheter kan ändra ordern tills den har godkänts.

### Godkännandeprocess {#approval-process}

#### E-postmeddelande {#email-notification}

När en kampanj beställs av en lokal enhet meddelas dess granskare via e-post, vilket visas nedan:

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>Välja granskare visas i [Granskare](#reviewers) -avsnitt. De kan godkänna eller avvisa ordern.

![](assets/mkg_dist_command_valid_web.png)

#### Godkänn via klientkonsolen {#approving-via-the-adobe-campaign-console}

Beställningen kan också godkännas via Client Console i kampanjorderöversikten. Om du vill godkänna en beställning markerar du den och klickar på **[!UICONTROL Approve the order]**.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>Kampanjen kan fortfarande redigeras och konfigureras om fram till kampanjens tillgänglighetsdatum. Lokala enheter kan också avvisa kampanjen genom att klicka på **[!UICONTROL Cancel]** -knappen.

#### Skapa en kampanj {#creating-a-campaign}

När en kampanjorder har godkänts kan den konfigureras och köras av den lokala enheten.

![](assets/mkg_dist_mutual_op_created.png)

Mer information finns i [Åtkomst till kampanjer](accessing-campaigns.md).

### Avslå ett godkännande {#rejecting-an-approval}

Operatören som ansvarar för godkännandet kan avvisa en order eller ett kampanjpaket.

![](assets/mkg_dist_do_not_valid.png)

Om granskaren avvisar en order skickas det relevanta meddelandet automatiskt till de berörda lokala enheterna, där kommentaren från den aktör som avvisade godkännandet visas.

Information visas på sidan med kampanjpaket eller på sidan med kampanjorder. Om de har åtkomst till Adobe Campaign Client Console informeras lokala enheter om detta refusering.

![](assets/mkg_dist_do_not_valid_view.png)

De kan visa den relaterade kommentaren i kampanjpaketets **[!UICONTROL Edit]** -fliken.

![](assets/mkg_dist_do_not_valid_tab.png)

### Granskare {#reviewers}

Varje gång ett godkännande krävs meddelas granskarna via e-post.

För varje lokal enhet väljs granskarna ut för godkännande av kampanjorder och kampanjgodkännande. Mer information om hur du väljer lokala granskare finns i [Organisationsenheter](about-distributed-marketing.md#organizational-entities).

>[!NOTE]
>
>För att detta val ska kunna göras måste ordergodkännandet inte gälla än.

### Avbryta en order {#canceling-an-order}

Centrala myndigheten kan annullera en order med **[!UICONTROL Delete]** på orderkontrollpanelen.

![](assets/mkg_dist_local_op_cancel.png)

Detta avbryter kampanjen i **[!UICONTROL Campaign orders]** vy.
