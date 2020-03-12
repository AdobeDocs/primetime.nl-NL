---
description: Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
seo-description: Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
seo-title: Alternatieve audiotracks openen
title: Alternatieve audiotracks openen
uuid: 136b4f1b-e56f-4a8a-a961-05193434558c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Alternatieve audiotracks openen{#access-alternate-audio-tracks}

Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht tot de status `MediaPlayer` is VOORBEREID.
1. Luister naar deze gebeurtenissen:

   * `MediaPlayerItemEvent.ITEM_CREATED`: De eerste lijst met audiotracks is beschikbaar.
   * `MediaPlayerItemEvent.AUDIO_UPDATED`: Audiotracks gewijzigd tijdens afspelen

1. Haal de beschikbare audiotracks op uit de `MediaPlayerItem` instantie.
1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. Stel de geselecteerde audiotrack in op de `MediaPlayerItem` instantie.
