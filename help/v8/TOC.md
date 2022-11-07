---
audience: end-user
user-guide-title: Campaign v8
description: Dokumentation om Campaign v8
breadcrumb-title: Kampanjöversikt
title: Kampanjdokument v8
source-git-commit: 43e515339a2483e82910603daf6009cad63eeeae
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 25%

---


# Adobe Campaign v8-dokumentation {#campaign-v8}

+ [Dokumentation om Campaign v8](campaign-home.md)
+ Releaser och senaste uppdateringar {#releases}
   + [Tidig versionsinformation](start/e-release-notes.md)
   + [Versionsinformation](start/release-notes.md)
   + [Guardrails](start/ac-guardrails.md)
   + [Kända fel](start/known-issues.md)
   + [Kompatibilitetsmatris](start/compatibility-matrix.md)
+ Kom igång {#new}
   + [Kom igång med Adobe Campaign](start/get-started.md)
   + [Viktiga möjligheter](start/whats-new.md)
   + [Komponenter och processer](start/ac-components.md)
   + [Anslut till Campaign](start/connect.md)
   + Kampanjgränssnitt {#ac-ui}
      + [Upptäck gränssnittet Campaign](start/campaign-ui.md)
      + [Anpassa Campaign-gränssnittet](start/customize-ui.md)
      + [Hantera mappar och vyer](audiences/folders-and-views.md)
   + [Från Classic v7 till v8](start/v7-to-v8.md)
   + [Vanliga frågor och svar ](start/campaign-faq.md)
+ Campaign Management {#campaigns}
   + [Kom igång med kampanjer](start/campaigns.md)
   + [Kampanjsamordning - dokumentation](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html)
   + Skicka meddelanden{#send}
      + [Kom igång med meddelanden](start/create-message.md)
      + [Arbeta med leveransmallar](send/create-templates.md)
      + E-post {#emails}
         + [Designa och validera e-postmeddelanden](send/email.md)
         + [Skicka och övervaka e-post](send/send.md)
      + [SMS](send/sms.md)
      + [Push-meddelanden](send/push.md)
      + [LINE-meddelanden](send/line.md)
      + [Direktmeddelande](send/direct-mail.md)
      + [Twitter](send/twitter.md)
      + [Transaktionsmeddelanden](send/transactional.md)
      + Fel, studsar och karantän{#failures}
         + [Karantän](send/quarantines.md)
         + [Leveransfel](send/delivery-failures.md)
      + [Tidsoptimering för sändning](send/predictive.md)
      + [Hantera prenumerationer](start/subscriptions.md)
+ Profil- och målgruppshantering {#audience}
   + [Kom igång med profiler och målgrupper](audiences/gs-audiences.md)
   + [Arbeta med målgrupper](start/audiences.md)
   + [Åtkomstprofiler](audiences/view-profiles.md)
   + Lägg till profiler {#add-profiles}
      + [Skapa profiler manuellt](audiences/create-profiles.md)
      + [Importera profiler från en fil](audiences/import-profiles.md)
      + [Arbeta med externa profiler](audiences/external-profiles.md)
      + [Samla in profildata i webbformulär](audiences/collect-profiles.md)
      + [Arbeta med målmappningar](audiences/target-mappings.md)
   + Skapa målgrupper {#create-audiences}
      + [Skapa en lista med kontakter](audiences/create-audiences.md)
      + [Skapa och hantera filter](audiences/create-filters.md)
   + [Dela målgrupper med Adobes lösningar](start/shared-audiences.md)
   + [Bästa praxis](audiences/audiences-best-practices.md)
+ Innehållshantering {#content}
   + [Designa webbprogram och formulär](dev/webapps.md)
+ Integritet och säkerhetshantering {#privacy}
   + [Hantera förfrågningar om användarens information](start/privacy.md)
   + [Riktlinjer för säkerhet](config/security.md)
+ Beslutshantering {#offers}
   + [Kom igång med interaktion i realtid](interaction/interaction.md)
   + [Miljö och arkitektur](interaction/interaction-architecture.md)
   + [Bästa praxis](interaction/interaction-best-practices.md)
   + Definiera inställningar{#interaction-settings}
      + [Skapa operatorer](interaction/interaction-operators.md)
      + [Skapa miljöer](interaction/interaction-env.md)
      + [Skapa fördefinierade filter](interaction/interaction-predefined-filters.md)
      + [Skapa erbjudandeplatser](interaction/interaction-offer-spaces.md)
   + [Skapa en erbjudandekatalog](interaction/interaction-offer-catalog.md)
   + [Skapa ett erbjudande](interaction/interaction-offer.md)
   + [Skicka ett erbjudande (utgående)](interaction/interaction-send-offers.md)
   + Presentera ett erbjudande (inkommande){#inbound}
      + [Kontext](interaction/interaction-present-offers.md)
      + [Ring ett erbjudande på en webbsida](interaction/interaction-integration.md)
      + [Hantera anonyma interaktioner](interaction/anonymous-interactions.md)
   + [Rapporter och historik](interaction/interaction-tracking.md)
   + [Användningsfall](interaction/interaction-use-cases.md)
+ Rapportering och analys {#analytics}
   + [Spåra och övervaka](start/tracking.md)
   + Arbeta med rapporter{#reports}
      + [Kom igång med rapporter](reporting/gs-reporting.md)
      + Skapa kuber{#cubes}
         + [Kom igång med kuber](reporting/gs-cubes.md)
         + [Skapa en kub](reporting/cube-indicators.md)
         + [Skapa rapporter med kuber](reporting/cube-tables.md)
         + [Anpassa kuber](reporting/customize-cubes.md)
      + Inbyggda rapporter{#ac-reports}
         + [Lista med inbyggda rapporter](reporting/built-in-reports.md)
         + [Globala rapporter](reporting/global-reports.md)
         + [Leveransrapporter](reporting/delivery-reports.md)
         + [Inbyggd måttberäkning](reporting/metrics-calculation.md)
      + [Anpassade rapporter](reporting/custom-reports.md)
+ Datahantering {#data}
   + [Kom igång med arbetsflöden](config/workflows.md)
   + [Importera data](start/import.md)
   + [Arbetsflödesdokumentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html)
+ Integreringar {#connect}
   + [Connect Campaign med andra lösningar](connect/integration.md)
   + [Campaign + Experience Platform](connect/ac-aep.md)
   + [Campaign + Journey Optimizer](connect/ac-ajo.md)
   + [Campaign + Analytics](connect/ac-aa.md)
   + [Campaign + Experience Manager](connect/ac-aem.md)
   + [Campaign + Target](connect/ac-at.md)
   + [Kampanj + utlösare för Experience Cloud](connect/ac-triggers.md)
   + [Campaign + Twitter](connect/ac-tw.md)
   + [Kampanj + extern databas](connect/fda.md)
   + Campaign + din CRM {#ac-crm}
      + [Kom igång med CRM-anslutningar](connect/crm.md)
      + [Arbeta med Campaign och SFDC](connect/ac-sfdc.md)
      + [Arbeta med Campaign och Microsoft Dynamics](connect/ac-ms-dyn.md)
      + [Synkronisera data](connect/crm-data-sync.md)
+ Administration {#admin}
   + [Behörigheter](start/permissions.md)
   + [Kontrollpanelen](config/self-service.md)
+ Arkitektur och konfiguration {#config}
   + Arkitektur {#architecture}
      + [Globala principer](architecture/general-architecture.md)
      + [Arkitektur](architecture/architecture.md)
      + Driftsättning av FDA Snowflake {#fda}
         + [Vad är FDA-Snowflake?](architecture/fda-deployment.md)
      + Företagsdistribution (FFDA) {#ffda}
         + [Vad är Campaign FFDA?](architecture/enterprise-deployment.md)
         + Egenskaper {#ffda-characteristics}
            + [Nyckelhantering och unicitet](architecture/keys.md)
            + [Nya API:er](architecture/new-apis.md)
            + [API-mellanlagringsmekanism](architecture/staging.md)
            + [Replikeringsmekanism](architecture/replication.md)
   + Implementering {#implement}
      + [Implementeringssteg](start/implement.md)
      + [Anpassa instansen](dev/customize.md)
      + [Bästa praxis för datamodell](dev/datamodel-best-practices.md)
   + Konfiguration {#configuration}
      + [E-postinställningar](config/email-settings.md)
      + [Inställningar för transaktionsmeddelanden](config/transactional-msg-settings.md)
      + [Integrera Campaign SDK:er med er app](config/push-config.md)
      + [Externa konton](config/external-accounts.md)
+ Resurser för utvecklare {#developer}
   + [Kampanjdatamodell](dev/datamodel.md)
   + Scheman och formulär {#shemas-forms}
      + [Arbeta med scheman](dev/schemas.md)
      + [Skapa scheman](dev/create-schema.md)
      + [Utöka scheman](dev/extend-schema.md)
      + [Filterscheman](dev/filter-schema.md)
      + [Schemastruktur](dev/schema-structure.md)
      + [Databasmappning](dev/database-mapping.md)
      + [Begränsa PI-vy](dev/restrict-pi-view.md)
      + [Använd en anpassad mottagartabell](dev/custom-recipient.md)
      + [Uppdatera databasen](dev/update-database-structure.md)
      + [Inmatningsformulär](dev/forms.md)
   + [Kampanj-API:er](dev/api.md)
+ [Kontrollpanelen i Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv)
+ [Guide för kampanjautomatisering](https://experienceleague.adobe.com/docs/campaign/automation/home.html)
