---
seo-title: SSL configureren op uw BES-server
title: SSL configureren op uw BES-server
uuid: 041a106e-8b21-4018-815d-b7ea48c3de03
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# SSL configureren op uw BES-server {#configure-ssl-on-your-bees-server}

1. Geef het SSL-certificaat van de server op aan uw Adobe-contactpersoon die deze software heeft geleverd.

   Het certificaat wordt als vertrouwd certificaat toegevoegd aan de Primetime Cloud DRM-vertrouwde opslag.
1. Client authentication for the SSL connection (disabled in this version):
   1. Voeg de `[!DNL clouddrm-transport.cer]`- en `[!DNL AdobeFlashAccessIntermediateCA.cer]`-certificaten toe aan de vertrouwde opslag die wordt gebruikt voor clientverificatie.
   1. Schakel clientverificatie in uw SSL-configuratie in.
