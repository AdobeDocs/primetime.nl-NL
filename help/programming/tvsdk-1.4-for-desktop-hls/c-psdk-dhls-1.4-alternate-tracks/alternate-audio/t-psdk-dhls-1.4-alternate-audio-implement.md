---
description: Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.
title: Alternatieve audiotracks openen
exl-id: 08158b3b-1ed2-4f86-a710-2b128bb28ed0
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Alternatieve audiotracks openen{#access-alternate-audio-tracks}

Voor langbindende audio wordt MediaPlayer gebruikt om een video af te spelen die is opgegeven in een M3U8 HLS-afspeellijst en die verschillende alternatieve audiostreams kan bevatten.

1. Wacht op de `MediaPlayer` ten minste de status PREPARED hebben.
1. Luister naar deze gebeurtenissen:

   * `MediaPlayerItemEvent.ITEM_CREATED`: De eerste lijst met audiotracks is beschikbaar.
   * `MediaPlayerItemEvent.AUDIO_UPDATED`: Audiotracks gewijzigd tijdens afspelen

1. Beschikbare audiotracks ophalen via de `MediaPlayerItem` -instantie.
1. (Optioneel) Stel de beschikbare tracks voor aan de gebruiker.
1. De geselecteerde audiotrack instellen op de `MediaPlayerItem` -instantie.
