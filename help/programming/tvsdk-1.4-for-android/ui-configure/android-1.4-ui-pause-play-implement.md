---
description: U kunt gedrag van TVSDK toevoegen om knopen te pauzeren en te spelen.
seo-description: U kunt gedrag van TVSDK toevoegen om knopen te pauzeren en te spelen.
seo-title: Een video afspelen en pauzeren
title: Een video afspelen en pauzeren
uuid: 24b26364-5cb8-4a95-9574-cc52ddfa876b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# Een video afspelen en pauzeren{#play-and-pause-a-video}

U kunt gedrag van TVSDK toevoegen om knopen te pauzeren en te spelen.

1. Maak een pauze-/afspeelknop die het volgende doet.
   1. Wacht tot de speler zich ten minste in de staat PREPARED bevindt.
   1. Als u het afspelen wilt starten, roept u de afspeelmethode voor TVSDK op:

      ```java
      void play() throws IllegalStateException;
      ```

   1. Roep de pauzemethode voor TVSDK op om het afspelen te pauzeren:

      ```java
      void pause() throws IllegalStateException;
      ```

1. Gebruik `MediaPlayer.PlaybackEventListener.onStateChanged` callback om fouten te controleren of andere aangewezen acties te nemen.

   TVSDK roept deze callback wanneer de pauze of playmethode wordt geroepen. TVSDK geeft informatie door over de statuswijziging in de callback, inclusief de nieuwe status, zoals PAUSED of PLAYING.

