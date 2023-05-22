---
title: Beveiligde advertentie laden via HTTPS
description: Beveiligde advertentie laden via HTTPS
copied-description: true
exl-id: f9de1a2b-4eea-4028-83db-1b4021d1fbb7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Beveiligde advertentie laden via HTTPS {#secure-ad-loading-over-https}

Adobe Primetime biedt een optie voor het aanvragen van een eerste aanroep naar de Primetime-server en aan CRS gerelateerde aanroepen via HTTPS.

De functie is niet standaard ingeschakeld. Gebruik het volgende om veilig en ladend toe te laten.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
