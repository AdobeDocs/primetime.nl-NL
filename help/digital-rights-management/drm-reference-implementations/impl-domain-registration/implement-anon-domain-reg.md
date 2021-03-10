---
title: Anonieme domeinregistratie implementeren
description: Anonieme domeinregistratie implementeren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---


# Anonieme domeinregistratie implementeren{#implement-anonymous-domain-registration}

1. Maak een DRM-beleid dat aangeeft dat domeinregistratie is vereist.
1. Geef de URL van de domeinserver op als:

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. Anonieme verificatie verplicht maken.

   Stel in uw [!DNL .properties]-bestand het volgende in:

   ```
   policy.domain.anonymous=true 
   ```
