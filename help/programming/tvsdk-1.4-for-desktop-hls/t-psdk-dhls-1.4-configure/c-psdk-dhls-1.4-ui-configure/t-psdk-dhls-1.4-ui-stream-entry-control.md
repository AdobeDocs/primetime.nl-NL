---
description: Bij het starten van het afspelen begint VOD-media standaard op 0 en wordt de live media gestart op het live punt van de client (DefaultMediaPlayer.LIVE_POINT).
title: Een stream invoeren op een bepaald tijdstip
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
