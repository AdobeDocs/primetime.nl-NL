---
description: Alternatieve audio gebruikt MediaPlayer om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
title: Alternatieve audiotracks openen
exl-id: 88fa8f42-59d7-4a57-90c6-4c23b2ea7e00
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Alternatieve audiotracks openen{#access-alternate-audio-tracks}

Alternatieve audio gebruikt MediaPlayer om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht op de `MediaPlayer` in ten minste `MediaPlayerStatus.PREPARED` status.
1. Luister naar de `MediaPlayerEvent.STATUS_CHANGED` gebeurtenis met status `MediaPlayerStatus.PREPARED`.

   Deze stap betekent dat de eerste lijst met audiotracks beschikbaar is.

1. Beschikbare audiotracks ophalen via de `MediaPlayerItem` -instantie.

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. De geselecteerde audiotrack instellen op de `MediaPlayerItem` -instantie.

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```
