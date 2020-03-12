---
description: U kunt gedrag voor Browser-TVSDK toevoegen om knoppen te pauzeren en af te spelen.
seo-description: U kunt gedrag voor Browser-TVSDK toevoegen om knoppen te pauzeren en af te spelen.
seo-title: Een video afspelen en pauzeren
title: Een video afspelen en pauzeren
uuid: 4053ea9e-6b74-41e9-ad04-087ad13e3698
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

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

1. Luister naar de `AdobePSDK.MediaPlayerStatusChangeEvent` gebeurtenis om te controleren op fouten of om andere relevante acties uit te voeren.

   Browser-TVSDK activeert deze gebeurtenis wanneer pauze- of afspeelmethoden worden aangeroepen en geeft informatie over het gebeurtenisobject, inclusief de nieuwe status, zoals `MediaPlayerStatus.PLAYING` of `MediaPlayerStatus.PAUSED`.

