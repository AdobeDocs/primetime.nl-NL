---
description: Wanneer een gebruiker op een advertentie klikt, moet de toepassing het afspelen van de hoofdvideo-inhoud pauzeren.
seo-description: Wanneer een gebruiker op een advertentie klikt, moet de toepassing het afspelen van de hoofdvideo-inhoud pauzeren.
seo-title: Afspelen onderbreken en hervatten
title: Afspelen onderbreken en hervatten
uuid: a8fec392-3a71-4086-abf1-23522d023680
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---


# Afspelen pauzeren en hervatten {#pause-and-resume-playback}

Wanneer een gebruiker op een advertentie klikt, moet de toepassing het afspelen van de hoofdvideo-inhoud pauzeren.

Overschrijf `onPause` en `onResume` van de Android-activiteit.

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

