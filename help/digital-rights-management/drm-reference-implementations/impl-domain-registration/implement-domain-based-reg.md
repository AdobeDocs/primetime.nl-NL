---
title: Domeinregistratie op basis van identiteit implementeren
description: Domeinregistratie op basis van identiteit implementeren
copied-description: true
exl-id: e2f826a8-eea5-4d5f-ac4d-401d7a6c5373
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
