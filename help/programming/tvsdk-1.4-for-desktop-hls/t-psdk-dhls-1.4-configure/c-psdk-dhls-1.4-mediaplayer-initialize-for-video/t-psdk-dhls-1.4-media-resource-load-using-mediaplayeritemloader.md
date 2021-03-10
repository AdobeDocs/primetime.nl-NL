---
description: Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.
title: Een mediabron laden met MediaPlayerItemLoader
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---


# Een mediabron laden met MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}

Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.

Via de klasse `MediaPlayerItemLoader` kunt u een mediabron voor de bijbehorende `MediaPlayerItem` uitwisselen zonder een weergave aan een `MediaPlayer`-instantie te koppelen, wat zou leiden tot de toewijzing van de hardwarebronnen voor videodecodering. Het proces voor het verkrijgen van de instantie `MediaPlayerItem` is asynchroon.

1. Implementeer gebeurtenislisteners voor deze `MediaPlayerItemLoader`-gebeurtenissen:

   * `MediaPlayerItemLoaderEvent.ERROR` event

      TVSDK gebruikt dit om uw toepassing te laten weten dat er een fout is opgetreden. TVSDK biedt een eigenschap error die diagnostische informatie bevat.

1. Registreer deze instantie aan `MediaPlayerItemLoader`.
1. Roep `DefaultMediaPlayerItemLoader.load` aan en geef een instantie van een `MediaResource`-object door.

   De URL van het object `MediaResource` moet verwijzen naar de stream waarvoor u informatie wilt ophalen. Bijvoorbeeld:

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

