---
description: Creeer een PlaybackManager die de de stroomopstelling en playbackverrichting van HLS behandelt. Geen andere configuratie wordt vereist.
title: Afspelen van video inschakelen
exl-id: b53f602b-5752-4471-9905-2e4351dfc8d3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Afspelen van video inschakelen {#enable-video-playback}

Creeer een PlaybackManager die de de stroomopstelling en playbackverrichting van HLS behandelt. Geen andere configuratie wordt vereist.

1. Maak het mediaafspeelobject door ervoor te zorgen dat de volgende code aanwezig is in [!DNL PlayerFragment.java]:

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. De afspeelmanager maken via de `ManagerFactory`:

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. Implementeer de `PlaybackManagerEventListener` in de `PlayerFragment` om de afspeelgebeurtenissen af te handelen:

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. De gebeurtenislistener registreren in het dialoogvenster `PlayerFragment`:

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. De videobron instellen:

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. Stel de besturingsbalkbewerkingen in het dialoogvenster `PlayerFragment`:

   ```
   controlBar.pressPlay() { 
       playbackManager.play();  
   }
   ```

## Gerelateerde API-documentatie {#related-api-documentation}

* [Class PlaybackManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.html)
* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)
* [mediacore.utils.TimeRange](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/utils/TimeRange.html)
* [mediacore.BufferControlParameters](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/BufferControlParameters.html)
* [mediacore.MediaPlayer.PlayerState](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/MediaPlayer.PlayerState.html)
