---
description: Als u lokaal gegenereerde lijsten met certificaatintrekking (CRL's) en beleidsupdate wilt gebruiken, gebruikt u Adobe Primetime DRM API's om de handtekening te verifiëren.
seo-description: Als u lokaal gegenereerde lijsten met certificaatintrekking (CRL's) en beleidsupdate wilt gebruiken, gebruikt u Adobe Primetime DRM API's om de handtekening te verifiëren.
seo-title: Lokaal gegenereerde CRL's gebruiken
title: Lokaal gegenereerde CRL's gebruiken
uuid: 2e20b8ca-8606-4c27-b585-2f020b93be32
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Lokaal gegenereerde CRL&#39;s gebruiken {#consuming-locally-generated-crls}

Als u lokaal gegenereerde lijsten met certificaatintrekking (CRL&#39;s) en beleidsupdate wilt gebruiken, gebruikt u Adobe Primetime DRM API&#39;s om de handtekening te verifiëren.

Met de volgende API&#39;s wordt gecontroleerd of er niet met de lijsten is geknoeid en of de lijsten zijn ondertekend door de juiste licentieserver:

* Roep [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) aan om de handtekening te controleren voordat u de [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) aan om het even welke APIs verstrekt.

   Zie [RevocationListFactory voor meer informatie](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Roep [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) aan om de handtekening te controleren voordat u de handtekening aanbiedt `PolicyUpdateList` aan API&#39;s.

   Voor meer informatie, zie [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

