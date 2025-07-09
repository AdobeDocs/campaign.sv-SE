---
title: SMS-leveransinställningar
description: Lär dig hur du konfigurerar en SMS-leverans
feature: SMS
role: User
level: Beginner, Intermediate
exl-id: c4d500ef-2339-491f-9ae2-9bfaf72088a9
source-git-commit: 6f29a7f157c167cae6d304f5d972e2e958a56ec8
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# SMS-leveransinställningar {#sms-settings}

>[!IMPORTANT]
>
>Denna dokumentation gäller Adobe Campaign v8.7.2 och senare. Om du vill växla från den gamla till den nya SMS-anslutningen läser du i den här [technote](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/sms-migration){target="_blank"}
>
>Om du har äldre versioner kan du läsa [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/sv/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up/sms-set-up){target="_blank"}.

De tekniska inställningar som krävs för en SMS-leverans är:

* Det SMPP-externa kontot för meddelanderoutning. [Läs mer](smpp-external-account.md#smpp-connection-settings)
* Konfigurera fliken SMS. [Lär dig hur](#sms-tab)

Du kan konfigurera alla dessa i en leveransmall för att undvika att göra inställningarna för varje SMS-leveransskapande.

## Konfigurera fliken SMS {#sms-tab}

![](assets/send_settings.png){zoomable="yes"}

Här är den information du behöver för att fylla i formuläret. Varje fält förklaras nedan:

* **[!UICONTROL Sender address]**

  Det här fältet är valfritt. Det tillåter åsidosättande av avsändaradress (oADC). Innehållet i det här fältet placeras i fältet *source_addr* i PDU:n SUBMIT_SM.

  Fältet är begränsat till 21 tecken av SMPP-specifikationen, men vissa leverantörer kan tillåta längre värden. Observera också att mycket strikta begränsningar kan tillämpas i vissa länder (längd, innehåll, tillåtna tecken, ...), så du kan behöva dubbelkontrollera att det innehåll du placerar här är giltigt. Var särskilt försiktig när du använder anpassade fält.

  Om det här fältet lämnas tomt används värdet för Source-nummerfältet som är definierat i det externa kontot i stället. Om båda värdena är tomma lämnas fältet *source_addr* tomt.

* **[!UICONTROL Service or program ID]**

  >[!NOTE]
  >
  >Funktionen rekommenderas inte. Tillvalsparametrar för SMPP ger en mycket mer flexibel implementering.
  >
  >Båda funktionerna kan inte användas samtidigt.

  I kombination med den matchande externa kontoinställningen tillåter att en valfri parameter skickas med varje MT. I det här fältet definieras värdedelen i TLV.

* **[!UICONTROL Transmission mode]**

  Det här fältet anger vilken typ av SMS du vill överföra: normala meddelanden eller flash-meddelanden som lagras på mobilen eller SIM-kortet. Den här inställningen överförs i det valfria fältet dest_addr_subunit i PDU:n SUBMIT_SM.

   * **Flash** anger värdet till 1. Det skickar ett flash-meddelande som visas på mobilen och inte lagras i minnet.
   * **Normal** anger värdet till 0. Det skickar ett normalt meddelande.
   * **Spara på mobilen** anger värdet till 2. Den instruerar telefonen att lagra SMS:et i det interna minnet.
   * **Spara vid terminal** anger värdet till 3. Telefonen uppmanas att lagra SMS:et på SIM-kortet.

* **[!UICONTROL Priority, Communication type]**

  Dessa fält ignoreras av den utökade SMPP-kopplingen.

* **[!UICONTROL Maximum number of SMS per message]**

  Den här inställningen fungerar bara om inställningen för meddelandenyttolast är inaktiverad (mer information finns i inställningarna för det externa kontot). Om meddelandet kräver mer SMS än det här värdet utlöses ett fel.

  SMS-protokollet begränsar SMS till 255 delar, men vissa mobiltelefoner har problem med att sätta ihop långa meddelanden med mer än 10 delar eller så (gränsen beror på exakt modell). Om du vill vara säker, gå inte över 5 delar per meddelande.

  På grund av hur personaliserade meddelanden fungerar i Adobe Campaign kan meddelandena variera i storlek, så om du har många mycket långa meddelanden kan det medföra att sändningskostnaderna ökar avsevärt: om du anger det här till ett rimligt värde kan det hjälpa till att kontrollera dessa kostnader.

  Om du anger 0 inaktiveras gränsen.

* **[!UICONTROL Optional SMPP parameters (TLV)]**
Du kan ange extra fält som ska skickas som valfria SMPP-parametrar (TLV). Dessa extra fält skickas med varje MT och anpassade fält kan ha olika värden för varje MT.
I tabellen visas valfria parametrar som kan skickas med varje meddelande. Kolumner innehåller följande information:
   * **Etikett**: Det här är en valfri etikett med valfri form. Den överförs inte till providern. Du kan ange en textbeskrivning av parametern.
   * **Tagg**: taggvärdet, antingen i decimalformat (t.ex. 12345) eller hexadecimalt med 0x-prefix (t.ex. 0x12ab). Taggar kan ligga mellan 0 och 65535. Fråga SMPP-tjänstleverantören om vilka taggar de stöder.
   * **Värde**: värde som ska skickas i den valfria parametern. Det här är ett personaliserat fält.
   * **Format**: Kodning används för parametern. Du kan välja valfri textkodning som stöds eller de vanligaste binära formaten. Fråga SMPP-tjänstleverantören om vilket format som krävs.
   * **Maximal längd**: Maximalt antal byte för den här parametern. Detta ignoreras för binära fält eftersom binära fält har en fast storlek.

* **[!UICONTROL Using binary formats for TLV]**

  Campaign stöder sändning av TLV i binärt format. Binary är begränsad till sändande nummer.

  Eftersom personliga fält alltid matar ut text måste det anpassade fältet innehålla en decimalrepresentation av talet (alla strängar är bra så länge de bara innehåller siffror). Värdena kan vara både signerade och osignerade, personaliseringsmotorn konverterar det bara till rätt binär representation.

  När du använder binära format kan specialvärdena &#39;&#39; (tom sträng), &#39;null&#39; och &#39;undefined&#39; helt inaktivera fältet utan att något fel genereras. I dessa tre specialfall skickas inte taggen alls. Detta gör att du bara kan skicka en specifik TLV-fil för vissa meddelanden när du använder noggrant framtagen Javascript i personaliseringsfältet.

  >[!NOTE]
  >
  >Binära format kodas alltid till bigendian-format.

