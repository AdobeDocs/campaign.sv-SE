---
audience: user
user-guide-title: Guide för kampanjautomatisering
user-guide-description: Guide för kampanjautomatisering
feature: Overview
source-git-commit: 8ff207246bea1f476b37b1d4f2c79498362e7481
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 79%

---


# Guider för kampanjautomatisering {#automation}

+ [Guide för kampanjautomatisering](home.md)
+ Automatisera med arbetsflöden {#workflows}
   + Kom igång med arbetsflöden {#introduction}
      + [Om arbetsflöden](workflow/about-workflows.md)
      + Typer av arbetsflöden {#wf-type}
         + [Målarbetsflöden](workflow/targeting-workflows.md)
         + [Kampanjarbetsflöden](workflow/campaign-workflows.md)
         + [Tekniska arbetsflöden](workflow/technical-workflows.md)
      + [Bygg ett arbetsflöde](workflow/build-a-workflow.md)
      + [Bästa praxis](workflow/workflow-best-practices.md)
      + [Använd arbetsflödesdata](workflow/use-workflow-data.md)
   + Kör ett arbetsflöde {#executing-a-workflow}
      + [Starta ett arbetsflöde](workflow/start-a-workflow.md)
      + [Arbetsflödets livscykel](workflow/workflow-life-cycle.md)
      + [Ställ in godkännanden](workflow/define-approvals.md)
   + Övervaka arbetsflöden {#monitoring-workflows}
      + [Övervaka arbetsflödeskörning](workflow/monitor-workflow-execution.md)
      + [Övervaka tekniska arbetsflöden](workflow/monitor-technical-workflows.md)
      + [Värmekarta för arbetsflöde](workflow/heatmap.md)
   + Arbetsflödesaktiviteter {#wf-activities}
      + [Kom igång med aktiviteter](workflow/activities.md)
      + Målinriktade aktiviteter {#targeting-activities}
         + [Förteckning över målinriktningsaktiviteter](workflow/targeting-activities.md)
         + [Celler](workflow/cells.md)
         + [Ändra datakälla](workflow/change-data-source.md)
         + [Ändra dimension](workflow/change-dimension.md)
         + [CRM-koppling](workflow/crm-connector.md)
         + [Deduplicering](workflow/deduplication.md)
         + [Leveransbeskrivning](workflow/delivery-outline.md)
         + [Redigera schema](workflow/edit-schema.md)
         + [Berikning](workflow/enrichment.md)
         + [Uteslutning](workflow/exclusion.md)
         + [Inkrementell fråga](workflow/incremental-query.md)
         + [Skärningspunkt](workflow/intersection.md)
         + [Listuppdatering](workflow/list-update.md)
         + [Erbjudanden per cell](workflow/offers-by-cell.md)
         + [Erbjudandemotor](workflow/offer-engine.md)
         + [Fråga](workflow/query.md)
         + [Läslista](workflow/read-list.md)
         + [Dela](workflow/split.md)
         + [Prenumerationstjänster](workflow/subscription-services.md)
         + [Sammanslutning](workflow/union.md)
         + [Uppdatera data](workflow/update-data.md)
      + Flödeskontrollaktiviteter {#flow-control-activities}
         + [Förteckning över flödeskontrollverksamhet](workflow/flow-control-activities.md)
         + [Varning](workflow/alert.md)
         + [AND-join](workflow/and-join.md)
         + [Godkännande](workflow/approval.md)
         + [Extern signal](workflow/external-signal.md)
         + [Förgrening](workflow/fork.md)
         + [Hoppa (startpunkt och slutpunkt)](workflow/jump-start-point-and-end-point.md)
         + [Start och slut](workflow/start-and-end.md)
         + [Schemaläggare](workflow/scheduler.md)
         + [Delarbetsflöde](workflow/sub-workflow.md)
         + [Test](workflow/test.md)
         + [Tidsbegränsning](workflow/time-constraint.md)
         + [Vänta](workflow/wait.md)
      + Åtgärdsaktiviteter {#action-activities}
         + [Förteckning över åtgärdsaktiviteter](workflow/action-activities.md)
         + [Innehållshantering](workflow/content-management.md)
         + [Kontinuerlig leverans](workflow/continuous-delivery.md)
         + [Leveranser över flera kanaler](workflow/cross-channel-deliveries.md)
         + [Dataextrahering (fil)](workflow/extraction-file.md)
         + [Läsa in data (fil)](workflow/data-loading-file.md)
         + [Datainläsning (RDBMS)](workflow/data-loading-rdbms.md)
         + [Leverans](workflow/delivery.md)
         + [Leveranskontroll](workflow/delivery-control.md)
         + [Lokalt godkännande](workflow/local-approval.md)
         + [Läsa in (SOAP)](workflow/loading-soap.md)
         + [Nlserver-modul](workflow/nlserver-module.md)
         + [Återkommande leverans](workflow/recurring-delivery.md)
         + [SQL-kod och JavaScript-kod](workflow/sql-code-and-javascript-code.md)
         + [SQL-datahantering](workflow/sql-data-management.md)
         + [Uppdatera aggregat](workflow/update-aggregate.md)
      + Händelseaktiviteter {#event-activities}
         + [Lista över händelseaktiviteter](workflow/event-activities.md)
         + [Filhämtare](workflow/file-collector.md)
         + [Filöverföring](workflow/file-transfer.md)
         + [Inkommande e-postmeddelanden](workflow/inbound-emails.md)
         + [Inkommande SMS](workflow/inbound-sms.md)
         + [Webbhämtning](workflow/web-download.md)
   + Användningsfall {#use-cases}
      + [Om användningsfall för arbetsflöden](workflow/workflow-use-cases.md)
      + Leveranser {#deliveries}
         + [Använda den lokala godkännandeaktiviteten](workflow/local-approval-activity.md)
         + [Skicka ett födelsedagsmeddelande via e-post](workflow/send-a-birthday-email.md)
         + [Läs in leveransinnehåll](workflow/load-delivery-content.md)
         + [Arbetsflöde för leveranser över flera kanaler](workflow/cross-channel-delivery-workflow.md)
         + [E-postberikande med anpassade datumfält](workflow/email-enrichment-with-custom-date-fields.md)
      + Övervakning {#monitoring}
         + [Skicka en rapport till en lista](workflow/send-a-report-to-a-list.md)
         + [Övervaka dina arbetsflöden](workflow/workflow-supervision.md)
         + [Skicka personaliserade aviseringar till operatörer](workflow/send-alerts-to-operators.md)
      + Datahantering {#data-management}
         + [Koordinera datauppdateringar](workflow/coordinate-data-updates.md)
         + [Skapa en sammanfattningslista](workflow/create-a-summary-list.md)
         + [Berika data](workflow/enrich-data.md)
         + [Använd aggregat](workflow/using-aggregates.md)
         + [Använd funktionen för att sammanfoga dedupliceringaktiviteten](workflow/deduplication-merge.md)
         + [Konfigurera ett arbetsflöde för återkommande import](workflow/recurring-import-workflow.md)
      + Designfrågor {#designing-queries}
         + [Kvartalsvis listuppdatering med en inkrementell fråga](workflow/quarterly-list-update.md)
      + Fråga och filtrera {#designing-queries}
         + [Fråga mottagartabellen](workflow/querying-recipient-table.md)
         + [Fråga leveransinformation](workflow/query-delivery-info.md)
         + [Beräkna aggregat](workflow/compute-aggregates.md)
         + [Fråga med grupperingshantering](workflow/query-grouping-management.md)
         + [Fråga med en många-till-många-relation](workflow/query-many-to-many-relationship.md)
         + [Lägg till ett beräkningsfält av uppräkningstyp](workflow/adding-enumeration-type-calculated-field.md)
         + [Skapa ett filter](workflow/create-a-filter.md)
         + [Filtrera duplicerade mottagare](workflow/filter-duplicated-recipients.md)
   + Avancerade inställningar {#advanced-management}
      + [Egenskaper för arbetsflöde](workflow/workflow-properties.md)
      + [Avancerade parametrar](workflow/advanced-parameters.md)
      + [JavaScript-skript och mallar](workflow/javascript-scripts-and-templates.md)
      + [Exempel på JavaScript-kod i arbetsflöden](workflow/javascript-in-workflows.md)
      + [Åtkomst till en extern databas](workflow/accessing-an-external-database-fda.md)
      + [Hantera behörigheter](workflow/managing-rights.md)
      + [Ändra aktivitetsbilder](workflow/change-activity-images.md)
      + [Hantera tidszoner](workflow/managing-time-zones.md)
+ Kampanjorkestrering {#campaign-orchestration}
   + [Kom igång med marknadsföringskampanjer](campaigns/set-up-campaigns.md)
   + [Skapa program och kampanjer](campaigns/marketing-campaign-create.md)
   + [Skapa och konfigurera mallar](campaigns/marketing-campaign-templates.md)
   + [Lägg till leveranser](campaigns/marketing-campaign-deliveries.md)
   + [Välj målgruppen](campaigns/marketing-campaign-target.md)
   + [Hantera dokument och resurser](campaigns/marketing-campaign-assets.md)
   + [Konfigurera och hantera godkännanden](campaigns/marketing-campaign-approval.md)
   + [Återkommande och periodiska kampanjer](campaigns/recurring-periodic-campaigns.md)
   + [Övervaka dina kampanjer](campaigns/marketing-campaign-monitoring.md)
   + [Leverantörer, lager och budgetar](campaigns/providers-stocks-and-budgets.md)
+ Kampanjoptimering (tillägg){#campaign-optimization}
   + [Kom igång med olika kampanjtyper](campaign-opt/campaign-typologies.md)
   + [Filtreringsregler](campaign-opt/filtering-rules.md)
   + [Kontrollregler](campaign-opt/control-rules.md)
   + [Tryckregler](campaign-opt/pressure-rules.md)
   + [Konsekvensregler](campaign-opt/consistency-rules.md)
   + [Tillämpa regler](campaign-opt/apply-rules.md)
   + [Simuleringar i Campaign](campaign-opt/campaign-simulations.md)
+ Hantering av marknadsföringsresurser (tillägg){#mrm}
   + [Kom igång med resurshantering för marknadsföring](mrm/about-marketing-resource-management.md)
   + [Skapa och hantera uppgifter](mrm/creating-and-managing-tasks.md)
   + [Kontrollera kostnader](mrm/controlling-costs.md)
   + [Hantera marknadsföringsresurser](mrm/managing-marketing-resources.md)
   + [Diskussionsforum](mrm/discussion-forums.md)
+ Distribuerad marknadsföring (tillägg) {#distributed-marketing}
   + [Kom igång med distribuerad marknadsföring](distributed-marketing/about-distributed-marketing.md)
   + [Skapa en lokal kampanj](distributed-marketing/creating-a-local-campaign.md)
   + [Skapa en samverkanskampanj](distributed-marketing/creating-a-collaborative-campaign.md)
   + [Publicera kampanjpaketet](distributed-marketing/publishing-the-campaign-package.md)
   + [Åtkomst till kampanjer](distributed-marketing/accessing-campaigns.md)
   + [Spåra en kampanj](distributed-marketing/tracking-a-campaign.md)
   + [Användningsfall](distributed-marketing/examples.md)
+ [&lt; Tillbaka till Campaign v8-dokumentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/campaign-home)
