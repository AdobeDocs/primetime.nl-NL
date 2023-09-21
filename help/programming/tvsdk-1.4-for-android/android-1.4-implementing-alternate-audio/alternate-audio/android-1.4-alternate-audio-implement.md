---
description: Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
title: Alternatieve audiotracks openen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Alternatieve audiotracks openen{#access-alternate-audio-tracks}

Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht op MediaPlayer om in minstens de VOORBEREIDDE staat te zijn.
1. Luister naar deze gebeurtenis:

   `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: De eerste lijst met audiotracks is beschikbaar.

1. Beschikbare audiotracks ophalen via de `MediaPlayerItem` -instantie.

   `mediaPlayerItem.getAudioTracks()` 1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. De geselecteerde audiotrack instellen op de `MediaPlayerItem` -instantie.

   `mediaPlayerItem.selectAudioTrack(audioTrack)`
