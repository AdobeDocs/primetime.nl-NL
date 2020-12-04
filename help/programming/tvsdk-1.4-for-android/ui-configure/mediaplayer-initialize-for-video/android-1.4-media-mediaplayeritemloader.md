---
description: Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.
seo-description: Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.
seo-title: Een mediabron laden met MediaPlayerItemLoader
title: Een mediabron laden met MediaPlayerItemLoader
uuid: b2311ddc-f059-4775-8553-fc354ec2636b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Een mediabron laden met MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

Een andere manier om een mediabron op te lossen is met MediaPlayerItemLoader. Dit is nuttig wanneer u informatie over een bepaalde media stroom wilt verkrijgen zonder een instantie te concretiseren MediaPlayer.

Via de klasse `MediaPlayerItemLoader` kunt u een mediabron voor de bijbehorende `MediaPlayerItem` uitwisselen zonder een weergave aan een `MediaPlayer`-instantie te koppelen, wat zou leiden tot de toewijzing van de hardwarebronnen voor videodecodering. Het proces voor het verkrijgen van de instantie `MediaPlayerItem` is asynchroon.

1. Voer de `MediaPlayerItemLoader.LoaderListener` callback interface uit.

       Deze interface definieert twee methoden:
   
   * `LoaderListener.onError` callback, functie

      TVSDK gebruikt dit om uw toepassing te laten weten dat er een fout is opgetreden. TVSDK biedt een foutcode als parameters en een beschrijvende tekenreeks die diagnostische informatie bevat.

   * `LoaderListener.onError` callback, functie

      TVSDK gebruikt dit om uw toepassing mee te delen dat de gevraagde informatie in de vorm van een `MediaPlayerItem` instantie beschikbaar is die als parameter aan callback wordt overgegaan.

1. Registreer deze instantie aan TVSDK door het als parameter tot de aannemer van `MediaPlayerItemLoader` over te gaan.
1. Roep `MediaPlayerItemLoader.load` aan en geef een instantie van een `MediaResource`-object door.

   De URL van het object `MediaResource` moet verwijzen naar de stream waarvoor u informatie wilt ophalen. Bijvoorbeeld:

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

