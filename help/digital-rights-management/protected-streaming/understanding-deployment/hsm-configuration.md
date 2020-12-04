---
description: Als u een HSM selecteert om uw servergeloofsbrieven op te slaan, moet u de privé sleutels en de certificaten op HSM laden en een pkcs11.cfg configuratiedossier creëren.
seo-description: Als u een HSM selecteert om uw servergeloofsbrieven op te slaan, moet u de privé sleutels en de certificaten op HSM laden en een pkcs11.cfg configuratiedossier creëren.
seo-title: HSM-configuratie
title: HSM-configuratie
uuid: 3610840b-082e-4a73-8aa5-5065f9232e0b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# HSM-configuratie{#hsm-configuration}

Als u een HSM selecteert om uw servergeloofsbrieven op te slaan, moet u de privé sleutels en de certificaten op HSM laden en een pkcs11.cfg configuratiedossier creëren.

U moet het configuratiebestand vinden in de map *LicenseServer.ConfigRoot*.

Zie de map [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] op de Adobe Primetime DRM DVD voor een voorbeeld-PKCS11-configuratiebestand.

Raadpleeg de documentatie bij de Sun PKCS11-provider met betrekking tot de indeling van [!DNL pkcs11.cfg]-bestand.

U kunt het volgende bevel van de folder gebruiken waar het [!DNL pkcs11.cfg] dossier wordt gevestigd ( [!DNL keytool] geïnstalleerd met Java JRE en JDK) om te verifiëren dat het HSM en PKCS11 configuratiedossier van de Zon correct is gevormd:

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Als u uw geloofsbrieven in de lijst kunt bekijken, dan wordt HSM correct gevormd en de vergunningsserver kan tot de geloofsbrieven nu toegang hebben.
