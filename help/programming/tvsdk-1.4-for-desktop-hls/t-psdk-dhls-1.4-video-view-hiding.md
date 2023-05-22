---
description: Nadat een MediaPlayer-weergave is gebruikt om video af te spelen, kunt u deze verbergen en opnieuw weergeven met een TVSDK-methode of handmatig.
title: Een videoweergave verbergen
exl-id: 92354cd3-f0ed-4434-a7af-a3545e0e2460
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Een videoweergave verbergen{#hide-a-video-view}

Nadat een MediaPlayer-weergave is gebruikt om video af te spelen, kunt u deze verbergen en opnieuw weergeven met een TVSDK-methode of handmatig.

U moet een video pauzeren voordat u deze wist of van het scherm verplaatst.
* Optie 1: Het videoframe wissen met `MediaPlayer.clearVideo`&#x200B; en vervang het frame later.
   * Pauzeer de video die u wilt verbergen.
   * Verwijder het weergegeven videoframe door `MediaPlayer.clearVideo`.
   * Als u het dialoogvenster `MediaPlayer` zodat het opnieuw kan worden gespeeld, roep `replaceCurrentResource` of `replaceCurrentItem`.
* Optie 2: Verplaats de `MediaPlayer` van het scherm bekijken en het later terugbewegen zonder het moeten het vervangen.
   * Pauzeer de video die u wilt verbergen.
   * De weergave uit het werkgebied verplaatsen. Bijvoorbeeld:

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * Als u de video opnieuw wilt weergeven, verplaatst u de weergave terug naar het werkgebied.
