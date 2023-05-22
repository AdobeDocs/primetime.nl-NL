---
description: Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.
title: Een mediabron laden met MediaPlayerItemLoader
exl-id: 9d129497-8a71-433a-a542-f49be519893b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Een mediabron laden met MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.

Via de `MediaPlayerItemLoader` klasse, kunt u een media middel voor het overeenkomstige ruilen `MediaPlayerItem` zonder een weergave te koppelen aan een `MediaPlayer` -instantie, die zou leiden tot de toewijzing van de hardwarebronnen voor videodecodering. Het proces om het `MediaPlayerItem` -instantie asynchroon is.

1. Implementeer de `MediaPlayerItemLoader.LoaderListener` callback-interface.

       Deze interface definieert twee methoden:
   
   * `LoaderListener.onError` callback, functie

      TVSDK gebruikt dit om uw toepassing te laten weten dat er een fout is opgetreden. TVSDK biedt een foutcode als parameters en een beschrijvende tekenreeks die diagnostische informatie bevat.

   * `LoaderListener.onError` callback, functie

      TVSDK gebruikt dit om uw toepassing te laten weten dat de gevraagde informatie beschikbaar is in de vorm van een `MediaPlayerItem` instantie die als parameter aan callback wordt overgegaan.

1. Registreer deze instantie bij TVSDK door deze als parameter door te geven aan de constructor van de component `MediaPlayerItemLoader`.
1. Bellen `MediaPlayerItemLoader.load`, door een instantie van een `MediaResource` object.

   De URL van de `MediaResource` -object moet verwijzen naar de stream waarvoor u informatie wilt ophalen. Bijvoorbeeld:

   ```java
   // instantiate the listener interface 
   MediaPlayerItemLoader.LoaderListener _itemLoaderListener = 
     new MediaPlayerItemLoader.LoaderListener() { 
       @Override 
       public void onError(MediaErrorCode mediaErrorCode, String description) { 
           // something went wrong - look at the error code and description 
       } 
       @Override 
           public void onLoadComplete(MediaPlayerItem playerItem) { 
           // information is available - look at the data in the "playerItem" object 
       } 
   } 
   
   // instantiate the MediaPlayerItemLoader object (pass the listener as parameter) 
   MediaPlayerItemLoader itemLoader = new MediaPlayerItemLoader(_itemLoaderListener); 
   
   // create the MediaResource instance and set the URL to point to the actual media stream 
   MediaResource mediaResource =  
     MediaResource.createFromUrl("https://test.com/test_media.m3u8", null); 
   
   // load the media resource 
   itemLoader.load(mediaResource); 
   ```
