---
description: Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
title: Een stream invoeren op een bepaald tijdstip
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 1%

---


# Een stream invoeren op een bepaald tijdstip {#enter-a-stream-at-a-specific-time}

Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.

1. Geef een positie door aan `MediaPlayer.prepareToPlay`.

   TVSDK beschouwt de gegeven positie als het uitgangspunt voor het actief en er is geen zoekbewerking vereist. Als de positie zich niet binnen het doorzoekbare bereik bevindt, gebruikt TVSDK de standaardpositie. Zie [Een mediabron in de mediaspeler laden](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md) voor meer informatie.

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

