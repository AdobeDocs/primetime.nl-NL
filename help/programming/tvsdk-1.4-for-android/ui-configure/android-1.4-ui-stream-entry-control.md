---
description: Bij het starten van het afspelen begint VOD-media standaard op 0 (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
title: Een stream invoeren op een bepaald tijdstip
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Een stream invoeren op een bepaald tijdstip {#enter-a-stream-at-a-specific-time}

Bij het starten van het afspelen begint VOD-media standaard op 0 (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.

1. Een positie doorgeven aan `MediaPlayer.prepareToPlay`.

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
