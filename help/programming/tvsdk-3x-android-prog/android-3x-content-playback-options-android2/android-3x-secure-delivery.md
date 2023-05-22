---
description: TVSDK introduceert veilige levering via HTTPS.
title: Beveiligde aflevering via HTTPS
exl-id: 41e2c925-2145-4dfd-909a-aec57dbae9cd
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

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
