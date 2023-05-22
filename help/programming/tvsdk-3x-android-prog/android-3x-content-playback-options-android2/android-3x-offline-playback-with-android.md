---
description: Er zijn nieuwe API's geïntroduceerd die TVSDK de instructie geven de status van de netwerkconnectiviteit te negeren tijdens het downloaden van manifests.
title: Offline afspelen met Android
exl-id: 9ac50d3e-5839-4eb9-8811-efde56cfe375
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Offline afspelen met Android {#offline-playback-with-android}

De volgende APIs is geïntroduceerd die TVSDK zal instrueren om de staat van de netwerkconnectiviteit te negeren wanneer het downloaden van manifests. De verbindingsstaat van het netwerk wordt over het algemeen gebruikt tijdens het Adaptief Bitrate stromen (ABR), om te bepalen of om een reserve te proberen of op het netwerk te wachten om te hervatten.

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

U kunt deze instelling inschakelen en de netwerkconnectiviteit negeren.

Set `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` naar waar. De standaardwaarde voor een Booleaanse waarde is false.

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
