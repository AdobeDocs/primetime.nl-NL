---
description: Gebruik Adobe Primetime DRM API's om de handtekening te verifiëren als u lokaal gegenereerde certificaatintrekkingslijsten (CRL's) en beleidsupdate-lijsten wilt gebruiken.
title: Lokaal gegenereerde CRL's gebruiken
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Lokaal gegenereerde CRL&#39;s gebruiken {#consuming-locally-generated-crls}

Gebruik Adobe Primetime DRM API&#39;s om de handtekening te verifiëren als u lokaal gegenereerde certificaatintrekkingslijsten (CRL&#39;s) en beleidsupdate-lijsten wilt gebruiken.

Met de volgende API&#39;s wordt gecontroleerd of er niet met de lijsten is geknoeid en of de lijsten zijn ondertekend door de juiste licentieserver:

* Bellen [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) om de handtekening te controleren voordat u de [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) naar API&#39;s.

   Zie voor meer informatie [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Bellen [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) om de handtekening te controleren voordat u de `PolicyUpdateList` naar API&#39;s.

   Zie voor meer informatie [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

