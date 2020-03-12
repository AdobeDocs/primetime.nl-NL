---
seo-title: Anonieme domeinregistratie implementeren
title: Anonieme domeinregistratie implementeren
uuid: 330d32fd-8c23-40f9-949b-635e5a9acc86
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Anonieme domeinregistratie implementeren{#implement-anonymous-domain-registration}

1. Maak een DRM-beleid dat aangeeft dat domeinregistratie is vereist.
1. Geef de URL van de domeinserver op als:

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. Anonieme verificatie verplicht maken.

   Stel in uw [!DNL .properties] bestand de volgende opties in:

   ```
   policy.domain.anonymous=true 
   ```
