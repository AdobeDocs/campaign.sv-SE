---
title: SMS-kanalsegenskaper
description: Lär dig SMS-kanalens egenskaper
feature: SMS
role: User
level: Intermediate
exl-id: abab6f15-43ea-42fc-817b-8dbd88df82f7
source-git-commit: 6f29a7f157c167cae6d304f5d972e2e958a56ec8
workflow-type: tm+mt
source-wordcount: '1378'
ht-degree: 0%

---

# SMS-kanalsegenskaper {#sms-channel}

>[!IMPORTANT]
>
>Denna dokumentation gäller Adobe Campaign v8.7.2 och senare. Om du vill växla från den gamla till den nya SMS-anslutningen läser du i den här [technote](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/sms-migration){target="_blank"}
>
>Om du har äldre versioner kan du läsa [Campaign Classic v7-dokumentationen](https://experienceleague.adobe.com/sv/docs/campaign-classic/using/sending-messages/sending-messages-on-mobiles/sms-set-up/sms-set-up){target="_blank"}.

## SMS-typer {#sms-types}

När du skickar SMS via en SMS-leverantör kommer du att stöta på tre olika typer av SMS:

* **SMS MT (Mobile Terminated)**: Detta är ett SMS som Adobe Campaign skickar till mobiltelefoner via SMPP-leverantören.
* **SMS MO (Mobile Originated)**: Detta är ett SMS som skickas av en mobiltelefon till Adobe Campaign via SMPP-providern.
* **SMS SR (statusrapport), DR eller DLR (leveranskvitto)**: Det här är ett returkvitto som skickas av mobilen till Adobe Campaign via SMPP-providern och som anger att SMS:et har tagits emot. Adobe Campaign kan också få ett SR-meddelande som anger att meddelandet inte kunde levereras, ofta med en beskrivning av felet.

Du måste skilja mellan bekräftelser (RESP PDU, en del av SMPP-protokollet) och SR. Ett SR är en typ av SMS som skickas via nätverket från början till slut, medan en bekräftelse bara är en bekräftelse på att en överföring har lyckats.

Både bekräftelser och SR kan utlösa fel, och om man skiljer mellan dem blir det enklare att felsöka.

### Information som medförs av ett sms  {#sms-info}

Ett SMS innehåller mer information än text. Här följer en lista över vad du kan förvänta dig i ett SMS:

* Texten, som är begränsad till 140 byte, vilket innebär mellan 70 och 160 tecken beroende på kodningen. Mer information och begränsningar finns i [SMS-textkodning](#sms-text-encoding) nedan.
* En mottagaradress, ibland kallad ADC eller MSISDN (det tekniska namnet för&quot;telefonnummer&quot;). Det är numret på den mobil som kommer att ta emot SMS:et.
* En avsändaradress som kan kallas oADC eller ibland avsändar-ID. Det kan vara ett telefonnummer (för daglig användning), en kort kod (när den skickas via en leverantör) eller ett namn (detta är en valfri funktion, i så fall kan du inte svara på SMS:et).
* En flagga som anger om meddelandet är ett flash-meddelande (ett flash-meddelande är ett popup-fönster som inte är sparat i minnet)
* En flagga som anger om ett SR förväntas eller inte.
* Ett giltighetsdatum efter vilket ingen nätverksutrustning får göra ett nytt försök (inte alltid närvarande eller respekterad).
* Ett data_coding-fält som anger textens kodning.

## SMS-textkodning {#sms-text-encoding}

>[!IMPORTANT]
>
>Kodning av SMS är ett omfattande och komplext ämne med många svällningar och implementeringar som inte uppfyller kraven.

Den första regeln är **att alltid kontakta SMPP-providern vid kodningsproblem**. Det är bara de som har exakta kunskaper om den kodning de stöder och särskilda regler som kan gälla på grund av begränsningar i deras tekniska plattform. Få dem att kontrollera vad du skickar och vad de skickar tillbaka till dig, det är den enda vägen till en lyckad och stabil sammankoppling.

SMS-meddelanden använder en speciell 7-bitars kodning, som ofta kallas GSM7-kodning.  Wikipedia har [en bra artikel om det (GSM 03.38 på engelska)](https://en.wikipedia.org/wiki/GSM_03.38).

I SMPP-protokollet kommer GSM7-text att utökas till 8 bitar per tecken för enklare felsökning. SMSC paketerar det i 7 bitar per tecken innan det skickas till mobilen. Det innebär att SMS-meddelandefältet short_message kan vara upp till 160 byte långt i SMPP-bildrutan, medan det är begränsat till 140 byte när det skickas via mobilnätet (den viktigaste biten ignoreras helt enkelt).

I händelse av kodningsproblem finns det några viktiga saker att kontrollera:
* Kontrollera först att du vet vilka tecken som tillhör vilken kodning. GSM7 är känt för sitt partiella stöd för diakritiska tecken (accenter). Särskilt på franska, där é och è är en del av GSM7, men ê, â eller ï inte är det. Detsamma gäller spanska.
* C med cedilla (ç) förekommer endast i versaler i GSM7-alfabetet, men vissa telefoner återger det i gemener eller i&quot;smart&quot; fall: den allmänna rekommendationen är att helt undvika det och ta bort cedillan (den är fortfarande mycket läsbar på franska) eller växla till UCS-2.
* **Använd inte ASCII i SMS!** om inte SMPP-providern uttryckligen har begärt det: Den här kodningen tar bort utrymme eftersom den har 8-bitars tecken och mindre täckning än GSM7. Denna kodning kan krävas för CDMA-nätverk (används i Nordamerika).
* Latin-1 stöds inte alltid. Kontrollera kompatibiliteten med SMPP-leverantören innan du försöker använda Latin-1.
* Tabeller för nationella språkskift stöds inte av Adobe Campaign-kopplingen. Du måste använda UCS-2 eller annan data_coding i stället.
* UCS-2 och UTF-16 blandas ofta med telefoner. Detta är ett problem för personer som skickar känslolägesikoner och andra sällan använda tecken som inte finns i UCS-2.
* Endast äldre telefoner har inte teckensnittstecken för alla UCS-2-tecken. De senaste smarttelefonerna kan oftast visa ovanliga tecken på ett relativt enkelt sätt, äldre smarttelefoner saknar ofta många känslolägesikoner, och mycket gamla funktionstelefoner har vanligtvis stöd för det som är användbart på det inhemska språket i det land de köptes i. Om du vill använda känslolägesikoner eller ASCII-bilder av något slag bör du testa dem i en mängd olika telefoner innan du skickar iväg dem. Förhandsgranskningen av kampanjen simulerar inte saknade specialtecken och visar de symboler som finns i webbläsaren som visar förhandsgranskningen.

Fältet *data_coding* anger vilken kodning som används. Ett stort problem är att värdet 0 betyder *standard-SMSC-kodning* i specifikationen, vanligtvis betyder det GSM7, men så är inte alltid fallet. Kontrollera med SMPP-providern vilken kodning som är associerad med data_coding = 0. Andra data_coding-värden följer ofta specifikationen, men det enda sättet att vara säker är att kontrollera med SMPP-providern.

Den största tillåtna storleken för ett meddelande beror på dess kodning. I denna tabell sammanfattas all relevant information:

| Kodning | Vanlig data_coding | Meddelandestorlek (tecken) | Delstorlek för multipart-SMS | Tillgängliga tecken |
|:-:|:-:|:-:|:-:|:-:|  
| GSM7 | 0 | 160 | 152 | Grundläggande GSM7-teckenuppsättning + tillägg (utökade tecken tar 2 tecken) |
| Latin-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 UTF-16 | 8 | 70 | 67 | Unicode (varierar från telefon till telefon) |

## Multipart SMS (long SMS) {#multipart-sms}

Multipart SMS (kallas ofta långt SMS) är SMS som skickas i flera delar. På grund av tekniska begränsningar i mobilnätverksprotokollet kan ett SMS inte vara större än 140 byte (se avsnittet SMS-textkodning nedan för antalet tecken som får plats i ett SMS) så längre meddelanden måste delas upp.

Varje del av ett långt meddelande är ett individuellt SMS. Dessa delar är oberoende av varandra på nätet och har monterats av den mottagande mobiltelefonen. För att hantera återförsök och anslutningsproblem på ett smidigt sätt skickar Campaign reservdelar i omvänd ordning och begär endast ett SR på den första delen av meddelandet (den som skickas sist). Eftersom mobiltelefonen endast visar ett meddelande när den tog emot den första delen, kommer återförsök på ytterligare delar inte att skapa dubbletter på mobiltelefonen.

Det maximala antalet SMS per meddelande kan anges per leverans med inställningen för maximalt antal SMS per meddelande i leveransmallen. Meddelanden som överskrider den här gränsen misslyckas när ett SMS skickas med en för lång felorsak.

Det finns två sätt att skicka långt SMS:

* UDH
* message_payload

UDH är standardmetoden och rekommenderas för att skicka långa meddelanden. I det här läget delar anslutningsprogrammet upp meddelandet i flera PDU:er av typen SUBMIT_SM med UDH-information. Det här protokollet används av mobiltelefoner själva, vilket innebär att Campaign har störst kontroll över meddelandegenereringen, vilket gör det möjligt att beräkna exakt hur många delar som skickades och hur de delades.

*message_payload* är ett sätt att skicka hela det långa meddelandet i en enda PDU för SUBMIT_SM. Leverantören måste dela upp den, vilket betyder att det är omöjligt för Campaign att veta exakt hur många delar som har skickats. Vissa leverantörer kräver det här läget, använd det bara om de inte har stöd för UDH.

Se beskrivningen av fälten esm_class, short_message och message_payload i PDU:n SUBMIT_SM ovan för mer information om protokoll och format.

>[!NOTE]
>
>Även om Adobe Campaign har stöd för både UDH och message_payload för sändning stöds endast message_payload för inkommande SMS (MO).
