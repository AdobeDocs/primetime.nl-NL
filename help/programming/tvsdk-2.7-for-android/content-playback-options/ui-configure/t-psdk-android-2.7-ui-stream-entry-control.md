---
description: Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
seo-description: Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
seo-title: Een stream invoeren op een bepaald tijdstip
title: Een stream invoeren op een bepaald tijdstip
uuid: 65a19192-b890-4d69-9cb1-582a22988d2b
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Een stream invoeren op een bepaald tijdstip {#enter-a-stream-at-a-specific-time}

Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.

1. Geef een positie door aan `MediaPlayer.prepareToPlay`.

   TVSDK beschouwt de gegeven positie als het uitgangspunt voor het actief en er is geen zoekbewerking vereist. Als de positie zich niet binnen het doorzoekbare bereik bevindt, gebruikt TVSDK de standaardpositie. Zie Een mediabron [laden in de mediaspeler](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md)voor meer informatie.

   Bijvoorbeeld:

   ```java
   long desiredPostion = // TODO : choose a value; 
   @Override 
   public void onStatusChanged(MediaPlayerStatusChangedEvent statusChangedEvent) {   
       switch (statusChangedEvent.getStatus()) { 
           case INITIALIZED: 
               _mediaPlayer.prepareToPlay(desiredPosition); 
               break; 
           case PREPARING: 
               showBufferingSpinner(); 
               break; 
       } 
   }
   ```

