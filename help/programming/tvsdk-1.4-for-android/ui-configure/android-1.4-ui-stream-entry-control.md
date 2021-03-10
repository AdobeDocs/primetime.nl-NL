---
description: Bij het starten van het afspelen begint VOD-media standaard op 0 (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
title: Een stream invoeren op een bepaald tijdstip
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%

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

