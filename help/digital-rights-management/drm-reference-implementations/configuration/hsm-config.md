---
description: U kunt de verwijzingsimplementatie met de leverancier vormen van Zon PKCS#11 die HSM steunt. Hoewel het gebruik van een HSM niet vereist is, wordt het aanbevolen.
title: HSM-configuratie
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# HSM-configuratie{#hsm-configuration}

U kunt de verwijzingsimplementatie met de leverancier vormen van Zon PKCS#11 die HSM steunt. Hoewel het gebruik van een HSM niet vereist is, wordt het aanbevolen.

Om referentie op HSM te gebruiken, moet u een configuratiedossier voor de leverancier van de Zon PKCS#11 tot stand brengen. Zie de klasse [Java PCKS#11 Referentiehandleiding](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html).

Om te verifiëren dat uw HSM en PKCS#11 configuratiedossier van de Zon worden gevormd, typ het volgende bevel door keytool te gebruiken die met Java JDK werd geïnstalleerd:

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

U hebt HSM correct gevormd als u uw geloofsbrieven in de lijst kunt bekijken.

>[!NOTE]
>
>Vanaf Java 1.7 biedt 64-bits Sun Java voor Windows geen ondersteuning meer voor de PKCS#11-interfaces die Adobe Primetime DRM nodig heeft om te communiceren met HSM-apparaten. Als u van plan bent om HSM te gebruiken, zorg ervoor dat u een versie met 32 bits van Java gebruikt of JDK gebruikt die de volledige interfaces PKCS#11 steunt.
