---
title: HSM-configuratie
description: HSM-configuratie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# HSM-configuratie {#hsm-configuration}

Als u ervoor kiest een HSM te gebruiken om uw serverreferenties op te slaan, moet u de persoonlijke sleutels en certificaten op de HSM laden en een [!DNL pkcs11.cfg] configuratiebestand. Dit bestand moet zich bevinden in het dialoogvenster *LicenseServer.ConfigRoot* directory. Zie de [!DNL Adobe Access Server for Protected Streaming/configs] directory op de Toegang DVD van de Adobe voor een PKCS11 configuratiedossier. Voor informatie over het formaat van [!DNL pkcs11.cfg], zie de PKCS11 van de Zon leveranciersdocumentatie.

Om te verifiëren dat uw HSM en PKCS11 configuratiedossier van de Zon behoorlijk wordt gevormd, kunt u het volgende bevel van de folder gebruiken waar [!DNL pkcs11.cfg] bestand bevindt zich ( [!DNL keytool] wordt geïnstalleerd met de Java JRE en JDK):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Als u uw geloofsbrieven in de lijst ziet, wordt HSM gevormd behoorlijk en de vergunningsserver zal tot de geloofsbrieven kunnen toegang hebben.

>[!NOTE]
>
>De Server van de Toegang van de Adobe voor beschermde Streaming steunt momenteel geen HSMs op OS met 64 bits van Vensters.
