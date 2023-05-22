---
title: HSM-configuratie
description: HSM-configuratie
copied-description: true
exl-id: a3e5759e-1419-4519-bcd7-de83364a48f8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# HSM-configuratie {#hsm-configuration}

Als u ervoor kiest een HSM te gebruiken om uw serverreferenties op te slaan, moet u de persoonlijke sleutels en certificaten op de HSM laden en een [!DNL pkcs11.cfg] configuratiebestand. Dit bestand moet zich bevinden in het dialoogvenster *LicenseServer.ConfigRoot* directory. Zie de [!DNL Adobe Access Server for Protected Streaming/configs] op de Adobe Access DVD voor een voorbeeld-PKCS11-configuratiebestand. Voor informatie over het formaat van [!DNL pkcs11.cfg], zie de PKCS11 van de Zon leveranciersdocumentatie.

Om te verifiëren dat uw HSM en PKCS11 configuratiedossier van de Zon behoorlijk wordt gevormd, kunt u het volgende bevel van de folder gebruiken waar [!DNL pkcs11.cfg] bestand bevindt zich ( [!DNL keytool] wordt geïnstalleerd met de Java JRE en JDK):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Als u uw geloofsbrieven in de lijst ziet, wordt HSM gevormd behoorlijk en de vergunningsserver zal tot de geloofsbrieven kunnen toegang hebben.

>[!NOTE]
>
>Adobe Access Server for protected Streaming biedt momenteel geen ondersteuning voor HSM&#39;s op 64-bits Windows-besturingssystemen.
