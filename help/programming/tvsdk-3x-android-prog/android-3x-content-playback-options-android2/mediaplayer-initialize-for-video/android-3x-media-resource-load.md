---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
seo-description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.
seo-title: Een mediabron laden in de mediaspeler
title: Een mediabron laden in de mediaspeler
uuid: 1a27b83b-afa6-48c7-a701-e11b2d280810
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Een mediabron in de mediaspeler {#load-a-media-resource-in-the-media-player} laden

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld. Dit is een manier om een mediabrondel te laden.

1. Stel de mediaspeler in om de nieuwe bron af te spelen.

   Vervang het momenteel afspeelbare item door `MediaPlayer.replaceCurrentResource()` aan te roepen en een bestaande `MediaResource`-instantie door te geven.

   Hierdoor wordt het proces voor het laden van bronnen gestart.

1. Registreer de `MediaPlayerEvent.STATUS_CHANGED` gebeurtenis met de `MediaPlayer` instantie. In callback, controleer minstens de volgende statuswaarden:

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`

   Door deze gebeurtenissen, meldt het `MediaPlayer` voorwerp uw toepassing wanneer het met succes de media middel heeft geladen.
1. Wanneer de status van de mediaspeler verandert in `INITIALIZED`, kunt u `MediaPlayer.prepareToPlay()` aanroepen.

   Deze status geeft aan dat het medium is geladen. De nieuwe `MediaPlayerItem` is klaar om te worden afgespeeld. Als u `prepareToPlay()` aanroept, wordt het proces voor het oplossen en plaatsen van advertenties gestart, indien van toepassing.

Als een fout optreedt, schakelt de mediaspeler over naar de status `ERROR`.

De volgende vereenvoudigde voorbeeldcode illustreert het proces om een media middel te laden:

```java>
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
