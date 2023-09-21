---
title: HSM-configuratie
description: HSM-configuratie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# HSM-configuratie {#hsm-configuration}

Het gebruik van een HSM is niet verplicht, maar wordt wel aanbevolen. De verwijzingsimplementatie kan worden gevormd om de leverancier van Zon te gebruiken PKCS11 voor steun HSM. Als u een referentie op een HSM wilt gebruiken, moet u een configuratiebestand voor de Sun PKCS11-provider maken. Raadpleeg de documentatie bij Sun voor meer informatie. Om te verifiëren dat uw HSM en PKCS11 configuratiedossier van de Zon behoorlijk worden gevormd, kunt u het volgende bevel gebruiken (keytool is geïnstalleerd met Java JDK):

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

Als u uw geloofsbrieven in de lijst ziet, wordt HSM gevormd behoorlijk.

>[!NOTE]
>
>Vanaf Java 1.7 biedt 64-bits Sun Java voor Windows geen ondersteuning voor de PKCS11-interfaces die Adobe Access DRM vereist om te communiceren met HSM-apparaten. Als u een HSM wilt gebruiken, moet u een 32-bits versie van Java gebruiken of een JDK gebruiken die de volledige PKCS11-interfaces ondersteunt.
