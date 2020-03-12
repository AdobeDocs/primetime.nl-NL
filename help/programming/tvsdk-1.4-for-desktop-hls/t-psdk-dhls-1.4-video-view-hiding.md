---
description: Nadat een MediaPlayer-weergave is gebruikt om video af te spelen, kunt u deze verbergen en opnieuw weergeven met een TVSDK-methode of handmatig.
seo-description: Nadat een MediaPlayer-weergave is gebruikt om video af te spelen, kunt u deze verbergen en opnieuw weergeven met een TVSDK-methode of handmatig.
seo-title: Een videoweergave verbergen
title: Een videoweergave verbergen
uuid: 7cc02bf4-41ee-4af0-98ba-df070b50b88d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Een videoweergave verbergen{#hide-a-video-view}

Nadat een MediaPlayer-weergave is gebruikt om video af te spelen, kunt u deze verbergen en opnieuw weergeven met een TVSDK-methode of handmatig.

U moet een video pauzeren voordat u deze wist of van het scherm verplaatst.
* Optie 1: Wis het videoframe met `MediaPlayer.clearVideo`&#x200B; en vervang het frame later.
   * Pauzeer de video die u wilt verbergen.
   * Verwijder het weergegeven videoframe door het aan te roepen `MediaPlayer.clearVideo`.
   * Om het terug te stellen `MediaPlayer` zodat het opnieuw kan worden gespeeld, roep `replaceCurrentResource` of `replaceCurrentItem`.
* Optie 2: Verplaats de `MediaPlayer` weergave van het scherm en verplaats deze later terug zonder deze te vervangen.
   * Pauzeer de video die u wilt verbergen.
   * De weergave uit het werkgebied verplaatsen. Bijvoorbeeld:

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * Als u de video opnieuw wilt weergeven, verplaatst u de weergave terug naar het werkgebied.
