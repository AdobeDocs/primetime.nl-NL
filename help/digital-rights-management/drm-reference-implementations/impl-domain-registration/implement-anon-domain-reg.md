---
title: Anonieme domeinregistratie implementeren
description: Anonieme domeinregistratie implementeren
copied-description: true
exl-id: 304cfe6f-0917-42ef-a49a-e6c4bc9c10d0
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
