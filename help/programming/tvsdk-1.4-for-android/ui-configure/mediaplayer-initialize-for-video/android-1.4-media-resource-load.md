---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
title: Een mediabron laden in de MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Een mediabron laden in de MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.

1. Plaats het playable punt van uw MediaPlayer met de nieuwe te spelen bron.

   Vervang het momenteel afspeelbare item van uw bestaande MediaPlayer door `MediaPlayer.replaceCurrentItem` aan te roepen en een bestaande `MediaResource`-instantie door te geven.

1. Registreer een implementatie van de `MediaPlayer.PlaybackEventListener` interface met `MediaPlayer` instantie.

   * `onPrepared`
   * `onStateChanged`en controleer op INITIALIZED en ERROR.

1. Wanneer de status van de mediaspeler verandert in INITIALIZED, kunt u `MediaPlayer.prepareToPlay`

   De geINITIALISEERDE status geeft aan dat het medium is geladen. Als u `prepareToPlay` aanroept, wordt het proces voor het oplossen en plaatsen van advertenties gestart, indien van toepassing.

1. Wanneer TVSDK de callback `onPrepared` aanroept, is de mediastream geladen en voorbereid voor afspelen.

   Wanneer de mediastream wordt geladen, wordt een `MediaPlayerItem` gemaakt.

>Als er een fout optreedt, schakelt `MediaPlayer` over naar de status ERROR. Het brengt ook uw toepassing op de hoogte door uw `PlaybackEventListener.onStateChanged`callback te roepen.
>
>Hiermee worden verschillende parameters doorgegeven:
>* Een `state`-parameter van het type `MediaPlayer.PlayerState` met de waarde `MediaPlayer.PlayerState.ERROR`.
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
