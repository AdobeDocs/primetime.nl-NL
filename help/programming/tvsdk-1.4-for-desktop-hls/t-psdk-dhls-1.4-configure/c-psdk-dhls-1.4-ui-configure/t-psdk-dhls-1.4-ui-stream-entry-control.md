---
description: Bij het starten van het afspelen begint VOD-media standaard op 0 en wordt de live media gestart op het live punt van de client (DefaultMediaPlayer.LIVE_POINT).
title: Een stream invoeren op een bepaald tijdstip
exl-id: b97dbabf-e2ab-4669-a9f3-9129af938a40
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Een stream invoeren op een bepaald tijdstip{#enter-a-stream-at-a-specific-time}

Bij het starten van het afspelen begint VOD-media standaard op 0 en wordt de live media gestart op het live punt van de client (DefaultMediaPlayer.LIVE_POINT).

Een positie doorgeven aan `MediaPlayer.prepareToPlay`.

TVSDK beschouwt de gegeven positie als het uitgangspunt voor het actief. Er is geen zoekbewerking vereist. Als de positie zich niet binnen het zoekbare bereik bevindt, wordt de standaardpositie gebruikt.

Bijvoorbeeld:

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
