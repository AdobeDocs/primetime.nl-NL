---
description: Voor langbindende audio wordt PTMediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
title: Alternatieve audiotracks openen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Alternatieve audiotracks openen {#access-alternate-audio-tracks}

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
