---
title: SSL configureren op uw BES-server
description: SSL configureren op uw BES-server
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# SSL configureren op uw BES-server {#configure-ssl-on-your-bees-server}

1. Geef uw SSL-servercertificaat door aan de contactpersoon van de Adobe die deze software heeft geleverd.

   Het certificaat wordt als vertrouwd certificaat toegevoegd aan de Primetime Cloud DRM-vertrouwde opslag.
1. Client authentication for the SSL connection (disabled in this version):
   1. Voeg de `[!DNL clouddrm-transport.cer]` en `[!DNL AdobeFlashAccessIntermediateCA.cer]` certificaten aan de vertrouwde opslag die voor cliëntauthentificatie wordt gebruikt.
   1. Schakel clientverificatie in uw SSL-configuratie in.
