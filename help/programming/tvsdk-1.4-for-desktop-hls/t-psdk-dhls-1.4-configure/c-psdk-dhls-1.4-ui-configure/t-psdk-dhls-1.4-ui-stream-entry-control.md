---
description: Bij het starten van het afspelen begint VOD-media standaard op 0 en wordt de live media gestart op het live punt van de client (DefaultMediaPlayer.LIVE_POINT).
seo-description: Bij het starten van het afspelen begint VOD-media standaard op 0 en wordt de live media gestart op het live punt van de client (DefaultMediaPlayer.LIVE_POINT).
seo-title: Een stream invoeren op een bepaald tijdstip
title: Een stream invoeren op een bepaald tijdstip
uuid: f58d908a-77b9-465f-b3a9-8fe63a249d39
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 1%

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
