---
description: Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
title: Een stream invoeren op een bepaald tijdstip
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Een stream invoeren op een bepaald tijdstip {#enter-a-stream-at-a-specific-time}

Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.

1. Een positie doorgeven aan `MediaPlayer.prepareToPlay`.

   TVSDK beschouwt de gegeven positie als het uitgangspunt voor het actief en er is geen zoekbewerking vereist. Als de positie zich niet binnen het doorzoekbare bereik bevindt, gebruikt TVSDK de standaardpositie. Zie voor meer informatie [Een mediabron laden in de mediaspeler](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md).

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
