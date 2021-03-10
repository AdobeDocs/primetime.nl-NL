---
description: 'Er zijn nieuwe API''s geïntroduceerd die TVSDK de instructie geven de status van de netwerkconnectiviteit te negeren tijdens het downloaden van manifests. '
title: Offline afspelen met Android
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

Stel `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` in op true. De standaardwaarde voor een Booleaanse waarde is false.

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
