---
description: Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
seo-description: Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
seo-title: Een stream invoeren op een bepaald tijdstip
title: Een stream invoeren op een bepaald tijdstip
uuid: b315a967-77ad-4352-8a32-f228704d4b20
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 1%

---


# Een stream invoeren op een bepaald tijdstip {#enter-a-stream-at-a-specific-time}

Wanneer u het afspelen start, begint VOD-media standaard op 0 en wordt live media gestart op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.

1. Geef een positie door aan `MediaPlayer.prepareToPlay`.

   TVSDK beschouwt de gegeven positie als het uitgangspunt voor het actief en er is geen zoekbewerking vereist. Als de positie zich niet binnen het doorzoekbare bereik bevindt, gebruikt TVSDK de standaardpositie. Zie [Een mediabron in de mediaspeler laden](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md) voor meer informatie.

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
