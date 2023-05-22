---
description: Wanneer een gebruiker op een advertentie klikt, moet de toepassing het afspelen van de hoofdvideo-inhoud pauzeren.
title: Afspelen onderbreken en hervatten
exl-id: 06922c80-b5c1-4e0c-872b-9400e07cf613
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Afspelen onderbreken en hervatten {#pause-and-resume-playback}

Wanneer een gebruiker op een advertentie klikt, moet de toepassing het afspelen van de hoofdvideo-inhoud pauzeren.

De `onPause` en `onResume` uit de Android-activiteit.

```java
@Override 
public void onResume() { 
    super.onResume(); 
    requestAudioFocus(); 
    if (_lastKnownStatus == MediaPlayer.PlayerState.PAUSED) { 
        _mediaPlayer.play(); 
    } 
} 
... 
 
@Override 
public void onPause() { 
    super.onPause(); 
    if (_mediaPlayer != null) { 
        if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PLAYING || 
          _mediaPlayer.getStatus() == MediaPlayer.PlayerState.PAUSED) { 
            _savedPlayerState = _mediaPlayer.getStatus(); 
            _lastKnownTime = _mediaPlayer.getCurrentTime(); 
        } 
        if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PLAYING) { 
            _mediaPlayer.pause(); 
            _lastKnownStatus = MediaPlayer.PlayerState.PAUSED; 
        } 
    } 
} 
 
abandonAudioFocus(); 
```
