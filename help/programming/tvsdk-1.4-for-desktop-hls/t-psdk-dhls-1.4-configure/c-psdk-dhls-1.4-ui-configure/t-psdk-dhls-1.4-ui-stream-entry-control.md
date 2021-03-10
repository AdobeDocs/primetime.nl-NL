---
description: Bij het starten van het afspelen begint VOD-media standaard op 0 en wordt de live media gestart op het live punt van de client (DefaultMediaPlayer.LIVE_POINT).
title: Een stream invoeren op een bepaald tijdstip
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

---


# Een stream invoeren op een bepaald tijdstip{#enter-a-stream-at-a-specific-time}

Bij het starten van het afspelen begint VOD-media standaard op 0 en wordt de live media gestart op het live punt van de client (DefaultMediaPlayer.LIVE_POINT).

Geef een positie door aan `MediaPlayer.prepareToPlay`.

TVSDK beschouwt de gegeven positie als het uitgangspunt voor het actief. Er is geen zoekbewerking vereist. Als de positie zich niet binnen het zoekbare bereik bevindt, wordt de standaardpositie gebruikt.

Bijvoorbeeld:

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
