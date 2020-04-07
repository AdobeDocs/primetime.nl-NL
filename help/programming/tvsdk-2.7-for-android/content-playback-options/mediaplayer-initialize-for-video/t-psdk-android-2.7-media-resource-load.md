---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
seo-description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
seo-title: Een mediabron laden in de mediaspeler
title: Een mediabron laden in de mediaspeler
uuid: 0334fa69-1d92-44d8-8891-2bc90a1ea498
translation-type: tm+mt
source-git-commit: 67975894814fbed8cfc49764a54b80d123032a49

---


# Een mediabron laden in de mediaspeler {#load-a-media-resource-in-the-media-player}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.

1. Stel de mediaspeler in om de nieuwe bron af te spelen.

   Vervang het momenteel afspeelbare item door een bestaande `MediaPlayer.replaceCurrentResource()` instantie aan te roepen `MediaResource` en door te geven.

   Hierdoor wordt het proces voor het laden van bronnen gestart.

1. Registreer de `MediaPlayerEvent.STATUS_CHANGED` gebeurtenis bij de `MediaPlayer` instantie. In callback, controleer minstens de volgende statuswaarden:

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`
   Via deze gebeurtenissen wordt de toepassing door het `MediaPlayer` object op de hoogte gebracht wanneer de mediabron is geladen.
1. Wanneer de status van de mediaspeler verandert in `INITIALIZED`, kunt u bellen `MediaPlayer.prepareToPlay()`.

   Deze status geeft aan dat het medium is geladen. Het nieuwe bestand `MediaPlayerItem` kan worden afgespeeld. Het aanroepen `prepareToPlay()` begint het proces van het oplossen en plaatsen van reclame, als om het even welk.

Als een fout optreedt, schakelt de mediaspeler over naar de `ERROR` status.

De volgende vereenvoudigde voorbeeldcode illustreert het proces om een media middel te laden:

```java
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register a PlaybackEventListener implementation with the MediaPlayer instance 
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatus status) { 
        if(event.getStatus() == MediaPlayerStatus.PREPARED) { 
            // The resource is successfully loaded and available. The  
            // MediaPlayer is ready to start the playback and can 
            // provide a reference to the current playable item 
            MediaPlayerItem playerItem = mediaPlayer.getCurrentItem(); 
            if (playerItem != null) { 
                // We can look at the properties of the loaded stream 
            } 
        } 
        else if (event.getStatus() == MediaPlayerStatus.ERROR) { 
            //Something bad happened - the resource cannot be loaded. 
            // The Metadata object in the event provides details. 
        } 
        else if (status == MediaPlayerStatus.INITIALIZED) { 
            mediaPlayer.prepareToPlay(); 
        } 
    } 
} 
```
