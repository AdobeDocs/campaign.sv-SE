---
title: Förstå händelsebeskrivning
description: Läs om hur transaktionshändelser hanteras i Adobe Campaign Classic med SOAP metoder
feature: Transactional Messaging
role: User
level: Intermediate
exl-id: 2f679d1c-4eb6-4b3c-bdc5-02d3dea6b7d3
source-git-commit: 69ff08567f3a0ab827a118a089495fc75bb550c5
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Förstå händelsebeskrivning {#about-event-desc}

## Datamodell för transaktionsmeddelanden {#about-mc-datamodel}

Transactional messaging förlitar sig på Adobe Campaign datamodell och använder ytterligare två separata tabeller. Dessa tabeller, **NmsRtEvent** och **NmsBatchEvent**, innehåller samma fält och gör att du kan hantera realtidshändelser å ena sidan och batchhändelser å andra sidan.

## SOAP-metoder {#soap-methods}

I det här avsnittet beskrivs de SOAP-metoder som är associerade med scheman för modulen för transaktionsmeddelanden.

Två **PushEvent** - eller **PushEvents** SOAP-metoder är länkade till de två **nms:rtEvent** - och **nms:BatchEvent** -datascheman. Det är informationssystemet som avgör om en händelse är av typen&quot;batch&quot; eller&quot;realtid&quot;.

* Med **PushEvent** kan du infoga en händelse i meddelandet,
* Med **PushEvents** kan du infoga en serie händelser i meddelandet.

WSDL-sökvägen för åtkomst till båda metoderna är:

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** för att komma åt typschemat i realtid.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** för att komma åt batchtypsschemat.

Båda metoderna innehåller ett **`<urn:sessiontoken>`**-element för inloggning i transaktionsmeddelandemodulen. Vi rekommenderar att du använder en identifieringsmetod via betrodda IP-adresser. Om du vill hämta sessionstoken gör du ett SOAP-inloggningsanrop och sedan en get-token följt av en utloggning. Använd samma token för flera RT-anrop. Exemplen i det här avsnittet använder sessionstokenmetoden som rekommenderas.

Om du använder en server för belastningsutjämning kan du använda autentisering av användare/lösenord (på nivån för RT-meddelandet). Exempel:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

Metoden **PushEvent** består av en **`<urn:domevent>`**-parameter som innehåller händelsen.

Metoden **PushEvents** består av en **`<urn:domeventcollection>`**-parameter som innehåller händelser.

Exempel med PushEvent:

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>Om metoden **PushEvents** anropas måste ett överordnat XML-element läggas till för att uppfylla standard-XML. Det här XML-elementet kommer att rama in de olika **`<rtevent>`** elementen i händelsen.

Exempel med PushEvents:

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

Elementen **`<rtevent>`** och **`<batchevent>`** har en uppsättning attribut samt ett obligatoriskt underordnat element: **`<ctx>`** för att integrera meddelandedata.

>[!NOTE]
>
>Med elementet **`<batchevent>`** kan du lägga till händelsen i batchkön. **`<rtevent>`** lägger till händelsen i realtidskön.

De obligatoriska attributen för elementen **`<rtevent>`** och **`<batchevent>`** är @type och @email. Värdet för @type måste vara samma som det specificerade listvärdet som definieras när körningsinstansen konfigureras. Med det här värdet kan du definiera mallen som ska länkas till innehållet i händelsen under leveransen.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

I det här exemplet finns det två kanaler: e-postadressen och mobiltelefonnumret. Med **önskadKanal** kan du välja den kanal som du vill använda när du omvandlar händelsen till ett meddelande. Värdet &quot;0&quot; motsvarar e-postkanalen, värdet &quot;1&quot; till mobilkanalen osv.

Om du vill skjuta upp en händelseleverans lägger du till fältet **[!UICONTROL scheduled]** följt av önskat datum. Händelsen omvandlas till ett meddelande det här datumet.

Vi rekommenderar att du fyller i attributen @önskadKanal och @emailFormat med numeriska värden. Funktionstabellen som länkar numeriska värden och etiketter finns i dataschemabeskrivningen.

>[!NOTE]
>
>En detaljerad beskrivning av alla godkända attribut samt deras värden finns i beskrivningen av dataschemat **nms:rtEvent** och **nms:BatchEvent**.

Elementet **`<ctx>`** innehåller meddelandedata. Dess XML-innehåll är öppet, vilket betyder att det kan konfigureras beroende på vilket innehåll som ska levereras.

>[!NOTE]
>
>Det är viktigt att optimera antalet och storleken på XML-noder i meddelandet för att undvika att överbelasta servrarna under leveransen.

Exempel på data:

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
```

## Information som returnerats av SOAP {#information-returned-by-the-soap-call}

När Adobe Campaign tar emot en händelse genereras ett unikt retur-ID. Detta är ID:t för den arkiverade versionen av händelsen.

>[!IMPORTANT]
>
>När Adobe Campaign tar emot SOAP-samtal verifieras e-postadressformatet. Om en e-postadress är felaktigt formaterad returneras ett fel.

* Exempel på en identifierare som returneras av metoden när händelsebearbetningen lyckas:

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
           <plId xsi:type="xsd:long">72057594037935966</plId>
        </urn:PushEventResponse>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

Om värdet för returidentifieraren är strikt större än noll betyder det att händelsen har arkiverats i Adobe Campaign.

Om händelsen inte kan bearbetas returnerar metoden ett felmeddelande eller ett värde som är lika med noll.

* Bearbetningsexempel på en händelse som misslyckades när frågan inte innehåller någon inloggning eller när den angivna operatorn inte har de nödvändiga rättigheterna:

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <SOAP-ENV:Fault>
           <faultcode>SOAP-ENV:Client</faultcode>
           <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
           <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
        </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Exempel på en händelse som misslyckades på grund av ett fel i frågan (XML-klassificeringen uppfylls inte):

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <SOAP-ENV:Fault>
           <faultcode>SOAP-ENV:Client</faultcode>
           <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
           <detail xsi:type="xsd:string"><![CDATA[(16:8): Expected end of tag 'rtevent'
  Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
     <soapenv:Header/>
     <soapenv:Body>
        <urn:PushEvent>
           <urn:sessiontoken>mc/</urn:sessiontoken>
           <urn:domEvent>
  <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
        externalId="1596" language="english" country="EN" emailFormat="2"
        mobilePhone="+447700123123">
    <ctx>
     <website name="eCommerce" url="http://www.eCo']]></detail>
        </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Exempel på en händelse som misslyckades och returnerade en nollidentifierare (fel metodnamn):

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
           <plId xsi:type="xsd:long">0</plId>
        </urn:PushEventResponse>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```
