---
description: Gebruik Adobe Primetime DRM API's om de handtekening te verifiëren als u lokaal gegenereerde certificaatintrekkingslijsten (CRL's) en beleidsupdate-lijsten wilt gebruiken.
title: Lokaal gegenereerde CRL's gebruiken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Lokaal gegenereerde CRL&#39;s gebruiken {#consuming-locally-generated-crls}

Gebruik Adobe Primetime DRM API&#39;s om de handtekening te verifiëren als u lokaal gegenereerde certificaatintrekkingslijsten (CRL&#39;s) en beleidsupdate-lijsten wilt gebruiken.

Met de volgende API&#39;s wordt gecontroleerd of er niet met de lijsten is geknoeid en of de lijsten zijn ondertekend door de juiste licentieserver:

* Roep [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) aan om de handtekening te controleren voordat u [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) aan om het even welke APIs verstrekt.

   Zie [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html) voor meer informatie.

* Roep [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) aan om de handtekening te controleren alvorens `PolicyUpdateList` aan om het even welke APIs te verstrekken.

   Voor meer informatie, zie [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

