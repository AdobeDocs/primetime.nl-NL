---
seo-title: HSM-configuratie
title: HSM-configuratie
uuid: da4d7118-65a8-460d-a796-b7bf5c28b208
translation-type: tm+mt
source-git-commit: ac75f63f98060e1937570476362bb5d4458d1f85
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# HSM-configuratie {#hsm-configuration}

Als u ervoor kiest om een HSM te gebruiken om uw serverreferenties op te slaan, moet u de persoonlijke sleutels en certificaten op HSM laden en een configuratiebestand [!DNL pkcs11.cfg] maken. Dit bestand moet zich in de map *LicenseServer.ConfigRoot* bevinden. Zie de [!DNL Adobe Access Server for Protected Streaming/configs] folder op de Toegang DVD van de Adobe voor een voorbeeldPKCS11 configuratiedossier. Raadpleeg de documentatie bij de Sun PKCS11-provider voor informatie over de indeling van [!DNL pkcs11.cfg].

Om te verifiëren dat uw HSM en PKCS11 configuratiedossier van de Zon behoorlijk wordt gevormd, kunt u het volgende bevel van de folder gebruiken waar het [!DNL pkcs11.cfg] dossier wordt gevestigd ( [!DNL keytool] wordt geïnstalleerd met Java JRE en JDK):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Als u uw geloofsbrieven in de lijst ziet, wordt HSM gevormd behoorlijk en de vergunningsserver zal tot de geloofsbrieven kunnen toegang hebben.

>[!NOTE]
>
>Adobe Access Server for protected Streaming biedt momenteel geen ondersteuning voor HSM&#39;s op 64-bits Windows-besturingssystemen.
