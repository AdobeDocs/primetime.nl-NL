---
description: Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
seo-description: Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
seo-title: Alternatieve audiotracks openen
title: Alternatieve audiotracks openen
uuid: c7060022-29ec-43c1-811b-41cca5f5356c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Alternatieve audiotracks openen{#access-alternate-audio-tracks}

Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht op MediaPlayer om in minstens de VOORBEREIDDE staat te zijn.
1. Luister naar deze gebeurtenis:

   `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: De eerste lijst met audiotracks is beschikbaar.

1. Haal de beschikbare audiotracks op uit de instantie `MediaPlayerItem`.

   `mediaPlayerItem.getAudioTracks()` 1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. Stel de geselecteerde audiotrack in op de instantie `MediaPlayerItem`.

   `mediaPlayerItem.selectAudioTrack(audioTrack)`