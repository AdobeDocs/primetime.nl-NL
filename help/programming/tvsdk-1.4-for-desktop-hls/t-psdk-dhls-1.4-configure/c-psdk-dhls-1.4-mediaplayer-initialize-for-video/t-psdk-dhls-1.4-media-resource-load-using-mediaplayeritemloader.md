---
description: Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.
seo-description: Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.
seo-title: Een mediabron laden met MediaPlayerItemLoader
title: Een mediabron laden met MediaPlayerItemLoader
uuid: a7ec8f58-7357-4757-a402-e879dd6caec8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Een mediabron laden met MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}

Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.

Via de `MediaPlayerItemLoader` klasse kunt u een mediabronis voor de corresponderende bron uitwisselen `MediaPlayerItem` zonder een weergave aan een `MediaPlayer` instantie te koppelen. Dit zou leiden tot de toewijzing van de hardwarebronnen voor videodecodering. Het verkrijgen van de `MediaPlayerItem` instantie verloopt asynchroon.

1. Implementeer gebeurtenislisteners voor deze `MediaPlayerItemLoader` gebeurtenissen:

   * `MediaPlayerItemLoaderEvent.ERROR` event

      TVSDK gebruikt dit om uw toepassing te laten weten dat er een fout is opgetreden. TVSDK biedt een eigenschap error die diagnostische informatie bevat.

1. Registreer deze instantie bij de `MediaPlayerItemLoader`.
1. Roep aan `DefaultMediaPlayerItemLoader.load`en geef een instantie van een `MediaResource` object door.

   De URL van het `MediaResource` object moet verwijzen naar de stream waarvoor u informatie wilt ophalen. Bijvoorbeeld:

   ```
   private function onLoadError(event:MediaPlayerItemLoaderEvent):void { 
       // something went wrong - look at the error code and description 
       // contained within the event.error 
   } 
   private function onLoadCompleted(event:MediaPlayerItemLoaderEvent):void { 
       // information is available - look at the data in the "event.item" object 
   } 
   // instantiate the MediaPlayerItemLoader object and register event listeners 
   var itemLoader:MediaPlayerItemLoader = new DefaultMediaPlayerItemLoader(); 
   itemLoader.addEventListener(MediaPlayerItemLoaderEvent.ERROR, onLoadError); 
   itemLoader.addEventListener(MediaPlayerItemLoaderEvent.COMPLETED, onLoadCompleted); 
   // create the MediaResource instance and set the URL to point to the actual media stream 
   var mediaResource:MediaResource = 
     MediaResource.createFromURL("https://example.com/media/test_media.m3u8", null); 
   // load the media resource 
   itemLoader.load(mediaResource); 
   ```

