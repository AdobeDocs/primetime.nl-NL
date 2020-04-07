---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
seo-description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
seo-title: Een mediabron laden in de MediaPlayer
title: Een mediabron laden in de MediaPlayer
uuid: 8af3e8d1-359d-483c-b394-b95054f7265a
translation-type: tm+mt
source-git-commit: 84924d84bfa436a8807c2e8d74d1dc268d457051

---


# Een mediabron laden in de MediaPlayer{#load-a-media-resource-in-the-mediaplayer}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.

1. Stel het afspeelbare item van het `MediaPlayer` object in met de nieuwe bron die moet worden afgespeeld.

   Vervang het momenteel afspeelbare item van uw bestaande MediaPlayer door een bestaande `MediaPlayer.replaceCurrentResource` instantie aan te roepen `MediaResource` en door te geven.

1. Controleer op zijn minst op de volgende wijzigingen:

   * GEÏNITIALISEERD
   * BEREID
   * FOUT

      Via deze gebeurtenissen kan het `MediaPlayer` object een melding sturen naar de toepassing wanneer de mediabron is geladen.

1. Wanneer de status van de mediaspeler verandert in INITIALIZED, kunt u `MediaPlayer.prepareToPlay`

   De geINITIALISEERDE status geeft aan dat het medium is geladen. Het aanroepen `prepareToPlay` begint het proces van het oplossen en plaatsen van reclame, als om het even welk.

1. Wanneer de status van de mediaspeler verandert in PREPARED, is de mediastream geladen en voorbereid voor afspelen.

   Wanneer de mediastream wordt geladen, `MediaPlayerItem` wordt er een gemaakt.

Als er een fout optreedt, schakelt MediaPlayer over naar de status ERROR. Het brengt ook uw toepassing op de hoogte door de `STATUS_CHANGED` gebeurtenis naar uw `MediaPlayerStatusChangeEvent` callback te verzenden.

Hiermee worden verschillende parameters doorgegeven:
* Een `type` parameter van het type tekenreeks met de waarde `ERROR`.

* Een `MediaError` parameter die u kunt gebruiken om een bericht te krijgen dat kenmerkende informatie over de foutengebeurtenis bevat.


<!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

De volgende vereenvoudigde voorbeeldcode illustreert het proces om een media middel te laden:

```
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register an event listener with the MediaPlayer instance 
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
private function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
   switch(event.status) { 
      case MediaPlayerStatus.INITIALIZED: 
          // at this point, the resource is successfully loaded 
          // the media player will provide a reference to the current 
          // "playable item" ( is guarantee to be valid and not-null). 
          var playerItem: MediaPlayerItem = mediaPlayer.currentItem; 
          // we can take a look at the media item characteristics like 
          // alternate audio tracks, profile information, if is a live stream 
          // if is drm protected 
          mediaPlayer.prepareToPlay(); 
          break; 
    case MediaPlayerStatus.PREPARED: 
         // at this point, the resource is successfully processed all  
         // advertisement placements have been executed and the the  
         // MediaPlayer is ready to start the playback 
        if (autoPlay) { 
            mediaPlayer.play(); 
        } 
        break; 
    case MediaPlayerStatus.ERROR: 
        // something bad happened - the resource cannot be loaded 
        // details about the problem are provided via the event.error property 
        break; 
        // implementation of the other methods in the PlaybackEventListener interface 
        ... 
    } 
}
```
