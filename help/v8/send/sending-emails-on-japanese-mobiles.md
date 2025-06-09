---
product: campaign
title: Skicka e-post till japanska mobiler med Adobe Campaign
description: Lär dig hur du konfigurerar, utformar och skickar e-postmeddelanden som ska läsas på japanska mobiler
feature: Email, Email Design
role: User
version: Campaign v8, Campaign Classic v7
exl-id: 02cca21f-b1ac-4ac2-9761-015f6c7f5567
source-git-commit: 3d562aab2f19b84aad8b484768bf19648145feb3
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# Skicka e-post till japanska mobiler {#sending-emails-on-japanese-mobiles}

## E-postformat för japanska mobiler {#email-formats-for-japanese-mobiles}

Adobe Campaign hanterar tre specifika japanska format för e-post på mobiler: **Deco-mail** (DoCoMo-mobiler), **Decore Mail** (Softbank-mobiler) och **Decoration Mail** (KDDI AU-mobiler). Dessa format medför särskilda begränsningar för kodning, struktur och storlek. Läs mer om begränsningar och rekommendationer i [det här avsnittet](#limitations-and-recommendations).

För att mottagaren ska kunna ta emot meddelanden i något av dessa format rekommenderar vi att du väljer **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** eller **[!UICONTROL Decoration Mail (KDDI AU)]** i motsvarande profil:

![](assets/deco-mail_03.png)

Om du låter alternativet **[!UICONTROL Email format]** vara **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** eller **[!UICONTROL Text]** identifierar Adobe Campaign automatiskt (när du skickar e-postmeddelandet) vilket japanskt format som ska användas så att meddelandet visas korrekt.

Det här automatiska identifieringssystemet baseras på listan med fördefinierade domäner som definierats i postregeluppsättningen **[!UICONTROL Management of Email Formats]**. Mer information om hur du hanterar e-postformat finns i [Campaign Classic-dokumentationen](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#managing-email-formats).

## Begränsningar och rekommendationer {#limitations-and-recommendations}

Ett visst antal begränsningar gäller för att skicka e-postmeddelanden som ska läsas på en mobil som drivs av en japansk leverantör (Softbank, DoCoMo, KDDI AU).

Därför måste du:

* Använd endast bilder i JPEG- eller GIF-format
* Skapa en leverans med text och HTML-avsnitt som är strikt mindre än 10 000 byte (för KDDI AU och DoCoMo)
* Använd bilder med en total storlek (före kodning) som är mindre än 100 kB
* Använd inte fler än 20 bilder per meddelande
* Använd ett HTML-format med reducerad storlek (ett begränsat antal taggar finns för varje operator)

>[!NOTE]
>
>Begränsningar som är specifika för varje operator måste beaktas när du skapar meddelandet. Läs produktdokumentationen för dem.


## Testa e-postinnehållet {#testing-the-email-content}

### Förhandsgranska meddelandet {#previewing-the-message}

Med Adobe Campaign kan du kontrollera att meddelandeformatet är anpassat för att skickas till en japansk mobiltelefon.

När du har definierat innehållet och angett ämnet för e-postmeddelandet kan du kontrollera visningen och formateringen när meddelandet skapas.

På fliken **[!UICONTROL Preview]** i fönstret för innehållsredigering kan du klicka på **[!UICONTROL More... > Deco-mail diagnostic]** för att:

* Kontrollera att HTML innehållstaggar följer de japanska formatbegränsningarna
* Kontrollera att antalet bilder i meddelandet inte överstiger gränsen för formatet (20 bilder)
* Kontrollera den totala meddelandestorleken (mindre än 100 kB)

  ![](assets/deco-mail_06.png)

### Kör typologiregel {#running-typology-rule}

Förutom förhandsgranskningsdiagnosen utförs en andra kontroll när du skickar ett bevis eller en leverans: en specifik typologiregel, **[!UICONTROL Deco-mail check]**, startas under analysen.

>[!IMPORTANT]
>
>Den här typologiregeln körs bara om minst en av mottagarna har konfigurerats att ta emot e-post i formatet **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** eller **[!UICONTROL Decoration Mail (KDDI AU)]**.

Med den här typologiregeln kan du se till att leveransen respekterar de [formatbegränsningar](#limitations-and-recommendations) som definieras av de japanska operatorerna, särskilt i förhållande till den totala storleken på e-postmeddelandet, storleken på HTML- och textavsnitten, antalet bilder i meddelandena samt taggarna i HTML-innehållet.

### Skicka korrektur {#sending-proofs}

Du kan skicka korrektur för att testa leveransen. När du skickar korrekturet anger du adresser som motsvarar e-postformatet för den profil som används, om du använder ersättningsadresser.

Du kan till exempel ersätta en profils adress med test@softbank.ne.jp om e-postformatet för den här profilen har definierats i förväg på **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## Skicka meddelanden {#sending-messages}

Om du vill skicka ett e-postmeddelande till mottagare med japanska e-postformat med Campaign kan du välja mellan två alternativ:

* Skapa två leveranser: en endast för japanska mottagare och en annan för andra mottagare - se [det här avsnittet](#designing-a-specific-delivery-for-japanese-formats).
* Skapa en enskild leverans så identifierar Adobe Campaign automatiskt vilket format som ska användas - se [det här avsnittet](#designing-a-delivery-for-all-formats).

### Designa en specifik leverans för japanska format {#designing-a-specific-delivery-for-japanese-formats}

Du kan skapa ett arbetsflöde som innehåller två leveranser: en som ska läsas på en japansk mobil och en annan för mottagare med ett standardformat för e-post.

Det gör du genom att använda aktiviteten **[!UICONTROL Split]** i arbetsflödet och definiera de japanska e-postformaten (Deco-mail, Decoration Mail och Decore Mail) som filtreringsvillkor.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### Designa för alla format {#designing-a-delivery-for-all-formats}

När Adobe Campaign dynamiskt hanterar formaten enligt domänen (profiler med e-postformat som definieras som **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** eller **[!UICONTROL Text]** ), kan du skicka samma leverans till alla dina mottagare.

Meddelandekontakten visas korrekt för användare på japanska mobiler, precis som för standardmottagare.

>[!IMPORTANT]
>
>Se till att du respekterar de specialfunktioner som är associerade med alla japanska e-postformat (Deco-mail, Decoration Mail och Decore Mail). Mer information om begränsningar finns i [det här avsnittet](#limitations-and-recommendations).
