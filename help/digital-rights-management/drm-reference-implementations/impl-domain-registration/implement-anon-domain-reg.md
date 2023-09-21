---
title: Anonieme domeinregistratie implementeren
description: Anonieme domeinregistratie implementeren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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

   In uw [!DNL .properties] bestand, instellen:

   ```
   policy.domain.anonymous=true 
   ```
