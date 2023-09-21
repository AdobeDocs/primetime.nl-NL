---
description: Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
title: Alternatieve audiotracks openen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Alternatieve audiotracks openen{#access-alternate-audio-tracks}

Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht op de `MediaPlayer` ten minste de status PREPARED hebben.
1. Luister naar deze gebeurtenissen:

   * `MediaPlayerItemEvent.ITEM_CREATED`: De eerste lijst met audiotracks is beschikbaar.
   * `MediaPlayerItemEvent.AUDIO_UPDATED`: audiotracks gewijzigd tijdens afspelen

1. Beschikbare audiotracks ophalen via de `MediaPlayerItem` -instantie.
1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. De geselecteerde audiotrack instellen op de `MediaPlayerItem` -instantie.
