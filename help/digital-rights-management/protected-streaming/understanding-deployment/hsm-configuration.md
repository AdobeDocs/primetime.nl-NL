---
description: Als u een HSM selecteert om uw servergeloofsbrieven op te slaan, moet u de privé sleutels en de certificaten op HSM laden en een pkcs11.cfg configuratiedossier creëren.
title: HSM-configuratie
exl-id: 4c4423ea-b7af-4a30-99ac-f5b74a1e1168
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# HSM-configuratie{#hsm-configuration}

Als u een HSM selecteert om uw servergeloofsbrieven op te slaan, moet u de privé sleutels en de certificaten op HSM laden en een pkcs11.cfg configuratiedossier creëren.

U moet het configuratiebestand zoeken in het dialoogvenster *LicenseServer.ConfigRoot* directory.

Zie de [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] op de Adobe Primetime DRM-dvd voor een voorbeeld-PKCS11-configuratiebestand.

Zie de de leveranciersdocumentatie van Zon PKCS11 betreffende het formaat van [!DNL pkcs11.cfg] bestand.

U kunt de volgende opdracht gebruiken vanuit de map waar de [!DNL pkcs11.cfg] bestand bevindt zich ( [!DNL keytool] wordt geïnstalleerd met Java JRE en JDK) om te verifiëren dat het de configuratiedossier van HSM en van de Zon PKCS11 correct is gevormd:

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Als u uw geloofsbrieven in de lijst kunt bekijken, dan wordt HSM correct gevormd en de vergunningsserver kan tot de geloofsbrieven nu toegang hebben.
