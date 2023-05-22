---
title: SSL configureren op uw BES-server
description: SSL configureren op uw BES-server
copied-description: true
exl-id: 6823a71c-3be6-4c07-a3e6-e16bd931deaf
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# SSL configureren op uw BES-server {#configure-ssl-on-your-bees-server}

1. Geef het SSL-certificaat van de server op aan uw Adobe-contactpersoon die deze software heeft geleverd.

   Het certificaat wordt als vertrouwd certificaat toegevoegd aan de Primetime Cloud DRM-vertrouwde opslag.
1. Client authentication for the SSL connection (disabled in this version):
   1. Voeg de `[!DNL clouddrm-transport.cer]` en `[!DNL AdobeFlashAccessIntermediateCA.cer]` certificaten aan de vertrouwde opslag die voor cliëntauthentificatie wordt gebruikt.
   1. Schakel clientverificatie in uw SSL-configuratie in.
