---
description: U kunt gedrag voor Browser-TVSDK toevoegen om knoppen te pauzeren en af te spelen.
title: Een video afspelen en pauzeren
exl-id: ce3f8b0c-9765-4e77-b096-6b9789608fa8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Een video afspelen en pauzeren{#play-and-pause-a-video}

U kunt gedrag voor Browser-TVSDK toevoegen om knoppen te pauzeren en af te spelen.

1. Maak een pauze-/afspeelknop die het volgende doet.
   1. Wacht tot de speler zich ten minste in de staat PREPARED bevindt.
   1. Als u het afspelen wilt starten, roept u de afspeelmethode van de Browser-TVSDK op:

      ```js
      play() → {AdobePSDK.PSDKErrorCode.SUCCESS}
      ```

   1. Als u het afspelen wilt pauzeren, roept u de pauzemethode voor TVSDK van Browser aan:

      ```java
      void pause() throws IllegalStateException;
      ```

1. Luister naar de `AdobePSDK.MediaPlayerStatusChangeEvent` om op fouten te controleren of om andere passende acties te ondernemen.

   Browser TVSDK activeert deze gebeurtenis wanneer pauze- of afspeelmethoden worden aangeroepen en informatie over het gebeurtenisobject wordt doorgegeven, inclusief de nieuwe status, zoals `MediaPlayerStatus.PLAYING` of `MediaPlayerStatus.PAUSED`.
