---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
title: Een mediabron laden in de mediaspeler
exl-id: ee11876b-c752-46cc-8e65-8c1608a41362
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Een mediabron laden in de mediaspeler {#load-a-media-resource-in-the-media-player}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.

1. Stel de mediaspeler in om de nieuwe bron af te spelen.

   Vervang het momenteel afspeelbare item door het aanroepen van `MediaPlayer.replaceCurrentResource()` en bestaande `MediaResource` -instantie.

   Hierdoor wordt het proces voor het laden van bronnen gestart.

1. Registreer de `MediaPlayerEvent.STATUS_CHANGED` gebeurtenis met de `MediaPlayer` -instantie. In callback, controleer minstens de volgende statuswaarden:

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`

   Via deze gebeurtenissen `MediaPlayer` -object meldt de toepassing wanneer deze de mediabron heeft geladen.
1. Wanneer de status van de mediaspeler verandert in `INITIALIZED`, kunt u `MediaPlayer.prepareToPlay()`.

   Deze status geeft aan dat het medium is geladen. De nieuwe `MediaPlayerItem` is gereed voor afspelen. Aanroepen `prepareToPlay()` start het proces voor het oplossen en plaatsen van reclame, indien van toepassing.

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
