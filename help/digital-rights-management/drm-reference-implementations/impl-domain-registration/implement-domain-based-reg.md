---
seo-title: Domeinregistratie op basis van identiteit implementeren
title: Domeinregistratie op basis van identiteit implementeren
uuid: 4a71b2e0-d1a2-4d63-9cbd-980a292774ab
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# Implementeer domeinregistratie op basis van identiteit{#implement-identity-based-domain-registration}

1. Maak een DRM-beleid met een verplichte domeinregistratie.
1. Geef de host en poort van de server op voor de URL van de domeinserver.

   Stel in uw [!DNL .properties]-bestand het volgende in:

   ```
   policy.domain.url=https://[server:port] 
   ```

1. Verificatie met een gebruikersnaam en wachtwoord verplicht maken.

   Stel in uw [!DNL .properties]-bestand het volgende in:

   ```
   policy.domain.anonymous=false 
   ```
