---
description: Alternatieve audio gebruikt MediaPlayer om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
seo-description: Alternatieve audio gebruikt MediaPlayer om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
seo-title: Alternatieve audiotracks openen
title: Alternatieve audiotracks openen
uuid: 9cec3a00-1416-497d-8d16-0ee429c8b575
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Alternatieve audiotracks openen {#access-alternate-audio-tracks}

Alternatieve audio gebruikt MediaPlayer om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht tot de `MediaPlayer` status ten minste `MediaPlayerStatus.PREPARED` is ingesteld.
1. Luister naar de `MediaPlayerEvent.STATUS_CHANGED` gebeurtenis met status `MediaPlayerStatus.PREPARED`.

   Deze stap betekent dat de eerste lijst met audiotracks beschikbaar is.

1. Haal de beschikbare audiotracks op uit de `MediaPlayerItem` instantie.

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. Stel de geselecteerde audiotrack in op de `MediaPlayerItem` instantie.

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```

