---
description: Voor langbindende audio wordt PTMediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
title: Alternatieve audiotracks openen
exl-id: f3ab9573-c189-4132-820d-0ce98ee170d1
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Alternatieve audiotracks openen{#access-alternate-audio-tracks}

Voor langbindende audio wordt PTMediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht tot de MediaPlayer zich in minstens `PTMediaPlayerStatusReady` status.
1. Luister naar deze gebeurtenis:

   melding `PTMediaPlayerItemMediaSelectionOptionsAvailable`: De eerste lijst met audiotracks is beschikbaar.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. Beschikbare audiotracks ophalen via de `PTMediaPlayerItem` -instantie.

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. De geselecteerde audiotrack instellen op de `PTMediaPlayerItem` -instantie.
