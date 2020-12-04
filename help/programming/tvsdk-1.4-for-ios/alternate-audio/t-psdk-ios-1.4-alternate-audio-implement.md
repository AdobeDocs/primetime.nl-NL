---
description: Voor langbindende audio wordt PTMediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
seo-description: Voor langbindende audio wordt PTMediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
seo-title: Alternatieve audiotracks openen
title: Alternatieve audiotracks openen
uuid: 77e39633-bf17-4a06-a2a1-93fdaadedd17
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Alternatieve audiotracks openen{#access-alternate-audio-tracks}

Voor langbindende audio wordt PTMediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht op MediaPlayer om in minstens de `PTMediaPlayerStatusReady` status te zijn.
1. Luister naar deze gebeurtenis:

   kennisgeving `PTMediaPlayerItemMediaSelectionOptionsAvailable`: De eerste lijst met audiotracks is beschikbaar.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. Haal de beschikbare audiotracks op uit de instantie `PTMediaPlayerItem`.

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. Stel de geselecteerde audiotrack in op de instantie `PTMediaPlayerItem`.
