---
title: Beveiligde advertentie laden via HTTPS
description: Beveiligde advertentie laden via HTTPS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---


# Beveiligd laden van advertentie via HTTPS {#secure-ad-loading-over-https}

Adobe Primetime biedt een optie voor het aanvragen van een eerste aanroep naar de Primetime-server en aan CRS gerelateerde aanroepen via HTTPS.

De functie is niet standaard ingeschakeld. Gebruik het volgende om veilig en ladend toe te laten.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
