---
description: 'null'
seo-description: 'null'
seo-title: Beveiligde advertentie laden via HTTPS
title: Beveiligde advertentie laden via HTTPS
uuid: 0d680fef-a372-4157-a89b-d9f10003c768
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Beveiligd laden van advertentie via HTTPS{#secure-ad-loading-over-https}

Adobe Primetime biedt een optie voor het aanvragen van een eerste aanroep naar de Primetime-server en aan CRS gerelateerde aanroepen via HTTPS.

De functie is niet standaard ingeschakeld. Gebruik het volgende om veilig en ladend toe te laten.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

