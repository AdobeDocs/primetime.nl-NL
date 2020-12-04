---
description: Creeer een PlaybackManager die de de stroomopstelling en playbackverrichting van HLS behandelt. Geen andere configuratie wordt vereist.
seo-description: Creeer een PlaybackManager die de de stroomopstelling en playbackverrichting van HLS behandelt. Geen andere configuratie wordt vereist.
seo-title: Afspelen van video inschakelen
title: Afspelen van video inschakelen
uuid: ddc0defa-c40f-4ee6-a69f-d5eeca6c2fce
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---


# Afspelen van video {#enable-video-playback} inschakelen

Creeer een PlaybackManager die de de stroomopstelling en playbackverrichting van HLS behandelt. Geen andere configuratie wordt vereist.

1. Maak het mediaspelerobject door ervoor te zorgen dat de volgende code voorkomt in [!DNL PlayerFragment.java]:

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. Creeer playbackmanager door `ManagerFactory`:

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. Voer `PlaybackManagerEventListener` in `PlayerFragment` uit om de playbackgebeurtenissen te behandelen:

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. Registreer de gebeurtenislistener in `PlayerFragment`:

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. De videobron instellen:

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. Opstelling de verrichtingen van de controlebar in `PlayerFragment`:

   ```
   controlBar.pressPlay() { 
       playbackManager.play();  
   }
   ```

## Verwante API-documentatie {#related-api-documentation}

* [Class PlaybackManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.html)
* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)
* [mediacore.utils.TimeRange](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/utils/TimeRange.html)
* [mediacore.BufferControlParameters](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/BufferControlParameters.html)
* [mediacore.MediaPlayer.PlayerState](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/MediaPlayer.PlayerState.html)