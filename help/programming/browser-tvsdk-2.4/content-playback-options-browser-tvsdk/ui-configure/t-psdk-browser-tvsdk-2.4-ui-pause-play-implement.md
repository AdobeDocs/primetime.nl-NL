---
description: U kunt gedrag voor Browser-TVSDK toevoegen om knoppen te pauzeren en af te spelen.
title: Een video afspelen en pauzeren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

1. Luister naar de gebeurtenis `AdobePSDK.MediaPlayerStatusChangeEvent` om te controleren op fouten of om andere geschikte acties uit te voeren.

   Browser TVSDK activeert deze gebeurtenis wanneer pauze- of afspeelmethoden worden aangeroepen en geeft informatie over het gebeurtenisobject door, inclusief de nieuwe status, zoals `MediaPlayerStatus.PLAYING` of `MediaPlayerStatus.PAUSED`.

