---
description: U kunt gedrag van TVSDK toevoegen om knopen te pauzeren en te spelen.
title: Een video afspelen en pauzeren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
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

1. Gebruik de `MediaPlayer.PlaybackEventListener.onStateChanged` terugbellen om te controleren op fouten of om andere passende acties te ondernemen.

   TVSDK roept deze callback wanneer de pauze of playmethode wordt geroepen. TVSDK geeft informatie door over de statuswijziging in de callback, inclusief de nieuwe status, zoals PAUSED of PLAYING.
