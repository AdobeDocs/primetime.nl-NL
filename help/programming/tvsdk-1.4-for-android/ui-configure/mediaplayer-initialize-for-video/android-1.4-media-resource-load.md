---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de te spelen video-inhoud te laden. Dit is een manier om een mediabrondel te laden.
title: Een mediabron laden in de MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Een mediabron laden in de MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de te spelen video-inhoud te laden. Dit is een manier om een mediabrondel te laden.

1. Plaats het playable punt van uw MediaPlayer met de nieuwe te spelen bron.

   Vervang het momenteel afspeelbare item van uw bestaande MediaPlayer door het aanroepen van `MediaPlayer.replaceCurrentItem` en het doorgeven van bestaande `MediaResource` -instantie.

1. Een implementatie van de `MediaPlayer.PlaybackEventListener` interface met de `MediaPlayer` -instantie.

   * `onPrepared`
   * `onStateChanged`en controleer op INITIALIZED en ERROR.

1. Wanneer de status van de mediaspeler verandert in INITIALIZED, kunt u `MediaPlayer.prepareToPlay`

   De geINITIALISEERDE status geeft aan dat het medium is geladen. Aanroepen `prepareToPlay` start het proces voor het oplossen en plaatsen van reclame, indien van toepassing.

1. Wanneer TVSDK de `onPrepared` callback, de mediastream is geladen en is voorbereid voor afspelen.

   Wanneer de mediastream is geladen, wordt een `MediaPlayerItem` wordt gemaakt.

>Als er een fout optreedt, wordt de `MediaPlayer` schakelt over naar de status ERROR. Het brengt ook uw toepassing op de hoogte door uw `PlaybackEventListener.onStateChanged`callback.
>
>Hiermee worden verschillende parameters doorgegeven:
>* A `state` parameter of type `MediaPlayer.PlayerState` met de waarde van `MediaPlayer.PlayerState.ERROR`.
>
>* A `notification` parameter of type `MediaPlayerNotification` die diagnostische informatie over de foutgebeurtenis bevat.

De volgende vereenvoudigde voorbeeldcode illustreert het proces om een media middel te laden:

```java
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register a PlaybackEventListener implementation with the MediaPlayer  
instancemediaPlayer.addEventListener( 
  MediaPlayer.Event.PLAYBACK, 
  new MediaPlayer.PlaybackEventListener()) { 
    @Overridepublic void onPrepared() { 
        // at this point, the resource is successfully loaded and available 
        // and the MediaPlayer is ready to start the playback 
        // once the resource is loaded, the MediaPlayer is able to 
        // provide a reference to the current "playable item" 
 
        MediaPlayerItem playerItem = mediaPlayer.CurrentItem(); 
 
        if (playerItem != null) {     
            // here we can take a look at the properties of the     
            // loaded stream 
        } 
    } @Overridepublic void onStateChanged( 
        MediaPlayer.PlayerState state,  
        MediaPlayerNotification notification) { 
        if (state == MediaPlayer.PlayerState.ERROR) { 
            // something bad happened - the resource cannot be loaded    
            // details about the problem are provided via the  
            // MediaPlayerNotification instance 
        }  
        elseif (state == MediaPlayer.PlayerState.INITIALIZED) {     
            mediaPlayer.prepareToPlay(); 
        } 
    } 
    // implementation of the other methods in the PlaybackEventListener interface... 
} 
```
