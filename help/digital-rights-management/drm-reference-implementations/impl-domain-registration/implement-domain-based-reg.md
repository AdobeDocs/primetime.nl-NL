---
title: Domeinregistratie op basis van identiteit implementeren
description: Domeinregistratie op basis van identiteit implementeren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Domeinregistratie op basis van identiteit implementeren{#implement-identity-based-domain-registration}

1. Maak een DRM-beleid met een verplichte domeinregistratie.
1. Geef de host en poort van de server op voor de URL van de domeinserver.

   In uw [!DNL .properties] bestand, instellen:

   ```
   policy.domain.url=https://[server:port] 
   ```

1. Verificatie met een gebruikersnaam en wachtwoord verplicht maken.

   In uw [!DNL .properties] bestand, instellen:

   ```
   policy.domain.anonymous=false 
   ```
