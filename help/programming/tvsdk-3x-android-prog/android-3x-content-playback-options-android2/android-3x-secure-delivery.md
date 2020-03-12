---
description: TVSDK introduceert veilige levering via HTTPS.
seo-description: TVSDK introduceert veilige levering via HTTPS.
seo-title: Beveiligde aflevering via HTTPS
title: Beveiligde aflevering via HTTPS
translation-type: tm+mt
source-git-commit: 4a2271fc481b37bb0a437091de6efe98fcb348d9

---


# Beveiligde aflevering via HTTPS {#secure-delivery-https}

Adobe Primetime TVSDK biedt ondersteuning voor HTTPS-levering voor alle aanroepen die afkomstig zijn van TVSDK, waaronder

* Server-aanroepen van Auditude en
* CRS-verzoeken
* DRM-licentieaanroepen
* Video Analytics Pings
* Facturerings

Als u deze functie wilt gebruiken, moet u ervoor zorgen dat de servers die zijn geconfigureerd voor het aanbieden van de bovenstaande aanvragen, HTTPS ondersteunen.

Dit nieuwe gedrag is niet standaard ingeschakeld. Gebruik het volgende om veilige levering vóór vraag toe te laten om `MediaPlayer.replaceCurrentResource()`

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
