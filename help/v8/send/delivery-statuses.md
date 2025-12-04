---
title: Leveransstatus
description: Läs mer om de statusar som finns på kontrollpanelen för leverans
feature: Monitoring, Deliverability
role: User
level: Beginner
version: Campaign v8, Campaign Classic v7
source-git-commit: c4d3a5d3cf89f2d342c661e54b5192d84ceb3a75
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---

# Leveransstatus {#delivery-statuses}

När en leverans har skickats visar kontrollpanelen en status som gör att du kan övervaka om sändningen har lyckats. Möjliga statusar beskrivs i avsnittet nedan.

![](assets/delivery-status.png)

Mer information om olika leveransfel som du kan träffa på och hur du löser dem finns i [Om leveransfel](delivery-failures.md).

**Relaterade ämnen:**

* [Skicka och övervaka e-postmeddelanden](send.md)
* [Förstå leveransfel](delivery-failures.md)
* [Kom igång med leverans](about-deliverability.md)

## Lista över leveransstatus {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> Status <br /> </th> 
   <th> Definitioner och lösningar<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Skickat <br /> </td> 
   <td> Leveransen skickades korrekt till meddelandeleverantören (men mottagaren tog inte emot den).<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorerad<br /> </td> 
   <td> Leveransen skickades inte till mottagaren på grund av ett fel med deras adress. Den fanns antingen på blockeringslista, i karantän, inte tillhandahållen eller en dubblett. <br /> </td> 
  </tr> 
  <tr> 
   <td> Misslyckades<br /> </td> 
   <td> Leveransen kunde inte nå mottagaren på grund av en ogiltig adress eller en fullständig inkorg, till exempel. Den kan även länkas till ett problem med personaliseringsblock eftersom de kan generera fel när scheman inte matchar leveransmappningen. Se <a href="delivery-failures.md" target="_blank">Om leveransfel</a><br /> </td> 
  </tr>
  <tr> 
   <td> Väntande<br /> </td> 
   <td> Leveransen är klar att skickas och kommer att bearbetas av leveransservern (MTA). Se <a href="#pending-status" target="_blank">Väntande status</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ej tillämpligt<br /> </td> 
   <td> Leveransen har tagits med i beräkningen av servern (MTA) men har inte bearbetats.<br /> </td> 
  </tr>  
  <tr> 
   <td> Leveransen har avbrutits <br /> </td> 
   <td> Leveransen avbröts av en operator.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tjänsteleverantören <br /> har tagit hänsyn till </td> 
   <td> För SMS-leveranser har SMS-tjänstleverantören tagit emot leveransen.<br /> För e-postleveranser har meddelandet vidarebefordrats från Campaign till MTA (Mail Transfer Agent).</td> 
  </tr> 
  <tr> 
   <td> Mottaget på mobilen <br /> </td> 
   <td> Mottagaren tog emot SMS på sin mobila enhet.<br /> </td> 
  </tr>
  <tr> 
   <td> Skickat till tjänstleverantören <br /> </td> 
   <td> Leveransen skickades till SMS-tjänstleverantören men har inte tagits emot än.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Förberedd <br /> </td> 
   <td> Mellanliggande status används endast för externa anslutningar som mobilkanalen. Det följer statusen Väntande och är den externa kopplingen som avgör följande status.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Mer information om hur du optimerar leveransen av dina Adobe Campaign-e-postmeddelanden finns i [det här avsnittet](about-deliverability.md). Mer information om leveransmöjligheterna finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv).

## Väntande status {#pending-status}

När du har bekräftat leveransen kan du se att leveransstatus är **[!UICONTROL Pending]**. Den här statusen innebär att körningsprocessen väntar på att vissa resurser ska vara tillgängliga.

Statusen **[!UICONTROL Pending]** kan först innebära att din leverans har schemalagts och väntar tills det angivna datumet. Mer information finns i avsnittet [Planerad leverans som skickar](configure-and-send.md#schedule-delivery-sending).

Om leveransen inte skickas och dess status är **[!UICONTROL Pending]** kan det bero på:

* **För många kampanjer körs samtidigt**

  Gränsen för samtidiga kampanjer har definierats i alternativet **[!UICONTROL NmsOperation_LimitConcurrency]**. Standardvärdet är 10.

  Som användare av hanterade molntjänster kan du arbeta med Adobe för att justera den här gränsen vid behov. Läs mer om alternativen i [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/appendices/configuring-campaign-options.html){target="_blank"}.

* **Problem med resurstillgänglighet**

  MTA (Message Transfer Agent) kanske väntar på att resurser ska bli tillgängliga innan leveransen bearbetas.

>[!NOTE]
>
>Som användare av hanterade molntjänster i Campaign v8 övervakas och hanteras MTA-infrastrukturen av Adobe. Om du får problem med väntande leveranser kontaktar du Adobe kundtjänst.

**Relaterade ämnen:**

* [Skicka och övervaka e-postmeddelanden](send.md#email-monitoring)
* [Förstå leveransfel](delivery-failures.md)
* [Övervaka er kampanjmiljö](../start/monitor.md#monitor-deliveries)

