---
description: Nadat een MediaPlayer-weergave is gebruikt om video af te spelen, kunt u deze verbergen en opnieuw weergeven met een TVSDK-methode of handmatig.
title: Een videoweergave verbergen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 1%

---


# Een videoweergave verbergen{#hide-a-video-view}

Nadat een MediaPlayer-weergave is gebruikt om video af te spelen, kunt u deze verbergen en opnieuw weergeven met een TVSDK-methode of handmatig.

U moet een video pauzeren voordat u deze wist of van het scherm verplaatst.
* Optie 1: Wis het videoframe met `MediaPlayer.clearVideo` &#x200B; en vervang het kader later.
   * Pauzeer de video die u wilt verbergen.
   * Verwijder het weergegeven videoframe door `MediaPlayer.clearVideo` aan te roepen.
   * Om `MediaPlayer` terug te stellen zodat het opnieuw kan worden gespeeld, roep `replaceCurrentResource` of `replaceCurrentItem`.
* Optie 2: Verplaats de `MediaPlayer` weergave van het scherm en verplaats deze later terug zonder deze te vervangen.
   * Pauzeer de video die u wilt verbergen.
   * De weergave uit het werkgebied verplaatsen. Bijvoorbeeld:

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * Als u de video opnieuw wilt weergeven, verplaatst u de weergave terug naar het werkgebied.
