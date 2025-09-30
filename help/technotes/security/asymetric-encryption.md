---
product: campaign
title: Technote - Asymetric Encryption and Decryption in Adobe Campaign
description: Teknisk anmärkning - asymmetrisk kryptering och dekryptering i Adobe Campaign
hide: true
hidefromtoc: true
source-git-commit: 1d9d4111cde1e230220a04c8fd10a126116339ad
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# TechNote: Asymmetrisk kryptering och dekryptering i Adobe Campaign {#asymetric-encryption}

Kryptografi med offentlig nyckel, eller asymmetrisk kryptografi, är det område i kryptografiska system som använder par av relaterade nycklar. Varje nyckelpar består av en **offentlig nyckel** och en motsvarande **privat nyckel**.

* Den **publika nyckeln** delas öppet och används för att kryptera data.

* Den **privata nyckeln** hålls hemlig och används för att dekryptera data.

Detta garanterar att även om någon har den offentliga nyckeln kan de inte dekryptera meddelandet utan den privata nyckeln. Det innehåller viktiga säkerhetsfunktioner som sekretess, autentisering och integritet.

Från och med Adobe Campaign v8.8.3 har två nya JavaScript-funktioner lagts till för kryptering och dekryptering:

* Kryptering med offentlig nyckel: `rsaPublicEncrypt(data, base64EncodedPublicKey, useOAEPpadding)`

* Dekryptering med privat nyckel: `rsaPrivateDecrypt(encryptedData, base64EncodedPrivateKey, useOAEPpadding)`


Exempel:

```Java
// Encryption with PKCS#1 v1.5 padding (default)
var encrypted = rsaPublicEncrypt(
    "Secret message",
    "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0t..." // Base64 encoded public key
);
 
// Encryption with OAEP padding
var encryptedOAEP = rsaPublicEncrypt(
    "Secret message",
    "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0t...", // Base64 encoded public key
    true
);
 
// Decryption
var decrypted = rsaPrivateDecrypt(
    encrypted,
    "LS0tLS1CRUdJTiBSU0EgUFJJVkFURSBLRVkt..." // Base64 encoded private key
);
```

**Ytterligare resurser**

* [Kom igång med [!DNL Campaign] API:er](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/api){target="_blank"}
* [Kampanj-JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/p-1.html){target="_blank"}
