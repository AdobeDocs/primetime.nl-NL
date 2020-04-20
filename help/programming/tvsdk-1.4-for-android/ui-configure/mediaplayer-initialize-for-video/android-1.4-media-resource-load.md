---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
seo-description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
seo-title: Een mediabron laden in de MediaPlayer
title: Een mediabron laden in de MediaPlayer
uuid: 6ee8032f-0728-423f-a1d2-5030aa7db14f
translation-type: tm+mt
source-git-commit: 4ef05be045334a2e723da4c7c6a7ee22fb0f776c

---


# Een mediabron laden in de MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.

1. Plaats het playable punt van uw MediaPlayer met de nieuwe te spelen bron.

   Vervang het momenteel afspeelbare item van uw bestaande MediaPlayer door een bestaande `MediaPlayer.replaceCurrentItem` instantie aan te roepen `MediaResource` en door te geven.

1. Registreer een implementatie van de `MediaPlayer.PlaybackEventListener` interface met de `MediaPlayer` instantie.

   * `onPrepared`
   * `onStateChanged`en controleer op INITIALIZED en ERROR.

1. Wanneer de status van de mediaspeler verandert in INITIALIZED, kunt u `MediaPlayer.prepareToPlay`

   De geINITIALISEERDE status geeft aan dat het medium is geladen. Het aanroepen `prepareToPlay` begint het proces van het oplossen en plaatsen van reclame, als om het even welk.

1. Wanneer TVSDK de `onPrepared` callback aanroept, is de mediastream geladen en voorbereid voor afspelen.

   Wanneer de mediastream wordt geladen, `MediaPlayerItem` wordt er een gemaakt.

>Als er een fout optreedt, gaat u naar de status FOUT. `MediaPlayer` Het brengt ook uw toepassing op de hoogte door uw `PlaybackEventListener.onStateChanged`callback te roepen.
>
>Hiermee worden verschillende parameters doorgegeven:
>* Een `state` parameter van type `MediaPlayer.PlayerState` met de waarde van `MediaPlayer.PlayerState.ERROR`.
   >
   >
* Een `notification` parameter van type `MediaPlayerNotification` die kenmerkende informatie over de foutengebeurtenis bevat.


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
