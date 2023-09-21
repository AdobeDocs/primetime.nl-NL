---
description: Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.
title: Een mediabron laden met MediaPlayerItemLoader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Een mediabron laden met MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}

Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.

Via de `MediaPlayerItemLoader` klasse, kunt u een media middel voor het overeenkomstige `MediaPlayerItem` zonder een weergave te koppelen aan een `MediaPlayer` -instantie, die zou leiden tot de toewijzing van de hardwarebronnen voor videodecodering. Het proces om het `MediaPlayerItem` -instantie asynchroon is.

1. Implementeer gebeurtenislisteners voor deze `MediaPlayerItemLoader` gebeurtenissen:

   * `MediaPlayerItemLoaderEvent.ERROR` event

     TVSDK gebruikt dit om uw toepassing te laten weten dat er een fout is opgetreden. TVSDK biedt een fouteigenschap die diagnostische informatie bevat.

1. Deze instantie registreren voor de `MediaPlayerItemLoader`.
1. Bellen `DefaultMediaPlayerItemLoader.load`, door een instantie van een `MediaResource` object.

   De URL van de `MediaResource` -object moet verwijzen naar de stream waarvoor u informatie wilt ophalen. Bijvoorbeeld:

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
