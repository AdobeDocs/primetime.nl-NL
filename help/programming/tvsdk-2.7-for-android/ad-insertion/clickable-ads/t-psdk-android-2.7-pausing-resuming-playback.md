---
description: Wanneer een gebruiker op een advertentie klikt, moet de toepassing het afspelen van de hoofdvideo-inhoud pauzeren.
seo-description: Wanneer een gebruiker op een advertentie klikt, moet de toepassing het afspelen van de hoofdvideo-inhoud pauzeren.
seo-title: Afspelen onderbreken en hervatten
title: Afspelen onderbreken en hervatten
uuid: 229e2499-e30e-458c-bd6d-d035588c21cf
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Afspelen onderbreken en hervatten {#pause-and-resume-playback}

Wanneer een gebruiker op een advertentie klikt, moet de toepassing het afspelen van de hoofdvideo-inhoud pauzeren.

1. Overschrijf de `onPause` Android-activiteit en `onResume` de Android-activiteit.

   ```java
   @Override 
   public void onResume() { 
       super.onResume(); 
       requestAudioFocus(); 
       if (_lastKnownStatus == MediaPlayerStatus.PAUSED) { 
           _mediaPlayer.play(); 
       } 
   } 
   ... 
   
   @Override 
   public void onPause() { 
       super.onPause(); 
       if (_mediaPlayer != null) { 
           if (_mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING || 
             _mediaPlayer.getStatus() == MediaPlayerStatus.PAUSED) { 
               _savedPlayerStatus = _mediaPlayer.getStatus(); 
               _lastKnownTime = _mediaPlayer.getCurrentTime(); 
           } 
           if (_mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING) { 
               _mediaPlayer.pause(); 
               _lastKnownStatus = MediaPlayerStatus.PAUSED; 
           } 
       } 
   } 
   abandonAudioFocus(); 
   ```

