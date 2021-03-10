---
title: Domeinregistratie op basis van identiteit implementeren
description: Domeinregistratie op basis van identiteit implementeren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
