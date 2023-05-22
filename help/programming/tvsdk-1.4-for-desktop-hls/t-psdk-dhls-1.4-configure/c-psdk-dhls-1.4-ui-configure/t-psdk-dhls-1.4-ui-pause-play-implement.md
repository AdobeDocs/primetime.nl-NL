---
description: U kunt gedrag van TVSDK toevoegen om knopen te pauzeren en te spelen.
title: Een video afspelen en pauzeren
exl-id: c1c259a4-edb8-475b-96a2-7fa0903804c3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

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

1. Gebruik callback voor `MediaPlayerStatusChangeEvent.STATUS_CHANGED` om op fouten te controleren of om andere passende acties te ondernemen.

   TVSDK roept deze callback wanneer de pauze of playmethode wordt geroepen. TVSDK geeft informatie door over de statuswijziging in de callback, inclusief de nieuwe status, zoals PAUSED of PLAYING.
