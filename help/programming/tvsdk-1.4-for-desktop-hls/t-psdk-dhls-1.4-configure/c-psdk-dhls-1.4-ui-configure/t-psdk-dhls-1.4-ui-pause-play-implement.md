---
description: U kunt gedrag van TVSDK toevoegen om knopen te pauzeren en te spelen.
seo-description: U kunt gedrag van TVSDK toevoegen om knopen te pauzeren en te spelen.
seo-title: Een video afspelen en pauzeren
title: Een video afspelen en pauzeren
uuid: 04b3b23f-5ef1-4cc4-a22f-f6ffa9cefce5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Een video afspelen en pauzeren{#play-and-pause-a-video}

U kunt gedrag van TVSDK toevoegen om knopen te pauzeren en te spelen.

1. Maak een pauze-/afspeelknop die het volgende doet.
   1. Wacht tot de speler ten minste de status PREPARED heeft.
   1. Als u het afspelen wilt starten, roept u de afspeelmethode voor TVSDK op:

      ```
      function play():void;
      ```

   1. Roep de pauzemethode voor TVSDK op om het afspelen te pauzeren:

      ```
      function pause():void;
      ```

1. Gebruik de callback voor de `MediaPlayerStatusChangeEvent.STATUS_CHANGED` gebeurtenis om te controleren op fouten of om andere geschikte acties uit te voeren.

   TVSDK roept deze callback wanneer de pauze of playmethode wordt geroepen. TVSDK geeft informatie door over de statuswijziging in de callback, inclusief de nieuwe status, zoals PAUSED of PLAYING.
