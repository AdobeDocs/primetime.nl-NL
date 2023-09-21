---
description: TVSDK introduceert veilige levering via HTTPS.
title: Beveiligde aflevering via HTTPS
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Beveiligde aflevering via HTTPS {#secure-delivery-https}

Adobe Primetime TVSDK biedt ondersteuning voor HTTPS-levering voor alle aanroepen die afkomstig zijn van TVSDK, waaronder

* Auditude en serveraanroepen
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
