---
description: TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals het bufferen en zoeken van gebeurtenissen.
seo-description: TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals het bufferen en zoeken van gebeurtenissen.
seo-title: QoS-gebeurtenissen
title: QoS-gebeurtenissen
uuid: e6ba1e9b-435b-480d-bea9-bff41b4e0b21
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# QoS-gebeurtenissen{#qos-events}

TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals het bufferen en zoeken van gebeurtenissen.

In het volgende voorbeeld wordt een typische progressie van deze gebeurtenissen getoond:

```
// For buffering 
mediaPlayer.addEventListener(BufferEvent.BUFFERING_BEGIN, onBufferingBegin); 
private function onBufferingBegin(event:BufferEvent):void { ... } 
 
mediaPlayer.addEventListener(BufferEvent.BUFFERING_END, onBufferingCompleted); 
private function onBufferingCompleted(event:BufferEvent):void { ... } 
 
// For seeking 
mediaPlayer.addEventListener(SeekEvent.SEEK_BEGIN, onSeekBegin); 
private function onSeekBegin(event:SeekEvent):void { ... } 
 
mediaPlayer.addEventListener(SeekEvent.SEEK_COMPLETED, onSeekCompleted); 
private function onSeekCompleted(event:SeekEvent):void { ... } 
 
...  SeekEvent.SEEK_POSITION_ADJUSTED...  //if the desired 
// seek position is modified by the current advertising policies 
```

