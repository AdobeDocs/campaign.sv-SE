---
product: campaign
title: Technical Note - Credential Rotation Guide
description: Adobe Campaign Technical Note - Credential Rotation Guide
hide: true
hidefromtoc: true
source-git-commit: 9d280a5c9d428a2795f2c893aad2d31ae2f122b9
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Teknisk kommentar: Roteringshandbok för autentiseringsuppgifter {#ac-customer-credentials}

Som kund ansvarar du för att regelbundet ersätta dina autentiseringsuppgifter med en ny uppsättning för att minska risken för kompromisser.

## Adobe Campaign Options - autentiseringsuppgifter {#ac-options-credentials}

I Adobe Campaign Explorer kan du ändra Adobe Campaign-alternativen med noden **Administration > Plattform > Alternativ** . Om du har sparat vissa inloggningsuppgifter här måste du rotera dem.

![](assets/technote-2.png)

## Autentiseringsuppgifter för externt konto {#ac-accounts-credentials}

Med noden **Administration > Plattform > Externa konton** kan du göra ändringar i Adobe Campaign externa konton.

Rotera alla autentiseringsuppgifter som har sparats i de externa kontona.

>[!CAUTION]
>
>**Ändra inte** de referenser som hanteras i Adobe. Externa konton med `adobe`-relaterad server ska inte ändras.

![](assets/technote-1.png)

För de specifika tekniska operatorerna `mc*` (t.ex. mc1, mc2 osv.) och `Interaction*` (t.ex. interaction1, interaction2 osv. ) kan någon av de två metoderna nedan följas:

1. Adobe kan ändra autentiseringsuppgifterna för sådana operatorer och dela dem med dig. Observera att alla integreringar som använder dessa operatorer slutar fungera tills autentiseringsuppgifterna för dessa operatorer uppdateras på din sida.

1. Adobe kan skapa **nya** -operatorer som motsvarar alla befintliga operatorer och dela dem med dig. Adobe tar bort alla förekomster av gamla operatorer när du har växlat till dessa nya operatorer.


## Privat nyckel/certifikat för mobila tjänster  {#ac-key-credentials}

Om du vill rotera de mobila tjänsterna relaterade till privata nycklar och certifikat ska du läsa länkarna nedan.

* Information om Android finns i [den här dokumentationen](https://experienceleague.adobe.com/en/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application-android){target="_blank"}.
Bläddra till avsnittet **Skapa Android mobilprogram > Konfigurera API-version**.

* Information om iOS finns i [den här dokumentationen](https://experienceleague.adobe.com/en/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application){target="_blank"}.
Bläddra till avsnittet **Skapa iOS-mobilapp->Autentiseringsläge**.

## GPG-nycklar {#ac-gpg-credentials}

Följande steg måste följas för att GPG-tangenterna ska kunna roteras:

1. Dekryptera befintliga data med den befintliga nyckeln. [Läs mer](https://experienceleague.adobe.com/en/docs/control-panel/using/instances-settings/gpg-keys-management#decrypting-data){target="_blank"}.

1. Skapa ett nytt GPG-nyckelpar. Läs mer om GPG-nyckelhantering i [den här dokumentationen](https://experienceleague.adobe.com/en/docs/control-panel/using/instances-settings/gpg-keys-management#decrypting-data){target="_blank"}.

1. Ersätt befintlig GPG-nyckelanvändning i alla arbetsflöden med den nya nyckeln.

1. Ta bort den befintliga GPG-nyckeln.