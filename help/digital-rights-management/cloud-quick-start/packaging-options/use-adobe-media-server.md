---
title: Adobe Media-server gebruiken
description: Adobe Media-server gebruiken
copied-description: true
exl-id: bb0b12f0-cd33-4a8a-8466-ae0e35cb1641
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---

# Adobe Media-server gebruiken {#use-adobe-media-server}

Sommige klanten kunnen reeds de Server van Adobe Media gebruiken en willen dat model van de inhoudslevering handhaven. Als dit het geval is, kunnen de vereiste DRM-specifieke gegevens worden verzameld van één van beide configuratiedossiers inbegrepen in deze uitrusting om de configuratie van XML van JIT (enkel in Tijd) voor AMS te bevolken.

Bijvoorbeeld:

```xml
<?xml version="1.0"?>
<Application>
  <HDS>
    <HLS>
      <Encryption enabled="true" protection-scheme="AdobeAccessV4">
        <AdobeAccessV4>
          <ContentID>SampleVideo</ContentID>
          <CommonKeyPath>common-key.bin</CommonKeyPath>
          <LicenseServerURL>
            https://access.adobeprimetime.com/flashaccessserver/axs_prod
          </LicenseServerURL>
          <KeyServerURL>
            https://access.adobeprimetime.com:443/faxsks/axs_prod/key
          </KeyServerURL>
          <TransportCertPath>cert/Cloud DRM-transport.cer</TransportCertPath>
          <LicenseServerCertPath>cert/Cloud DRM-license.cer</LicenseServerCertPath>
          <PackagerCredentialPath>cert-from-adobe.pfx</PackagerCredentialPath>
          <PackagerCredentialPwd>pass-for-cert-from-adobe</PackagerCredentialPwd>
          <PolicyPath>policy_ios_localkeyserver.pol</PolicyPath>
        </AdobeAccessV4>
      </Encryption>
    </HLS>
  </HDS>
</Application>
```
