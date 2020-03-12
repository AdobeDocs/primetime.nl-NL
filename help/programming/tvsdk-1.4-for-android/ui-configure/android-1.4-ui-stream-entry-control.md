---
description: Bij het starten van het afspelen begint VOD-media standaard op 0 (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
seo-description: Bij het starten van het afspelen begint VOD-media standaard op 0 (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
seo-title: Een stream invoeren op een bepaald tijdstip
title: Een stream invoeren op een bepaald tijdstip
uuid: ac3479e2-46a1-4ac8-a9e8-68a23f5dd74d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Een stream invoeren op een bepaald tijdstip {#enter-a-stream-at-a-specific-time}

Bij het starten van het afspelen begint VOD-media standaard op 0 (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.

1. Geef een positie door aan `MediaPlayer.prepareToPlay`.

   TVSDK beschouwt de gegeven positie als het uitgangspunt voor het actief. Er is geen zoekbewerking vereist. Als de positie zich niet binnen het doorzoekbare bereik bevindt, gebruikt TVSDK de standaardpositie.

   Bijvoorbeeld:

   ```java
   long desiredPostion = //TODO : choose a value; 
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state, MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               _mediaPlayer.prepareToPlay(desiredPosition); 
               break; 
               case PREPARING: 
               showBufferingSpinner(); 
               break; 
           ... 
       } 
   } 
   ```

