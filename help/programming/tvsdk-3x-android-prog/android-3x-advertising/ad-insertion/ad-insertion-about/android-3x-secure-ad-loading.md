---
description: 'null'
seo-description: 'null'
seo-title: Beveiligde advertentie laden via HTTPS
title: Beveiligde advertentie laden via HTTPS
uuid: 18be77cc-c59b-4982-b8c1-e4451495edd2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Beveiligde advertentie laden via HTTPS {#secure-ad-loading-over-https}

Adobe Primetime biedt een optie om eerst een oproep te doen naar de Primetime-server en aan CRS gerelateerde aanroepen via HTTPS.

De functie is niet standaard ingeschakeld. Gebruik het volgende om veilig en ladend toe te laten.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
