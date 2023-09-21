---
title: Beveiligde advertentie laden via HTTPS
description: Beveiligde advertentie laden via HTTPS
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Beveiligde advertentie laden via HTTPS{#secure-ad-loading-over-https}

Adobe Primetime biedt een optie voor het aanvragen van een eerste aanroep naar de Primetime-server en aan CRS gerelateerde aanroepen via HTTPS.

De functie is niet standaard ingeschakeld. Gebruik het volgende om veilig en ladend toe te laten.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
