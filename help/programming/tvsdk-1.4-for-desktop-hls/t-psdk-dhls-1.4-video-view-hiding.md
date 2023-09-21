---
description: Nadat een MediaPlayer-weergave is gebruikt om video af te spelen, kunt u deze verbergen en opnieuw weergeven met een TVSDK-methode of handmatig.
title: Een videoweergave verbergen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
* Optie 2: het gereedschap Verplaatsen `MediaPlayer` van het scherm bekijken en het later terugbewegen zonder het moeten het vervangen.
   * Pauzeer de video die u wilt verbergen.
   * De weergave uit het werkgebied verplaatsen. Bijvoorbeeld:

     ```
     view.x = -300; 
     view.y = -300;
     ```

   * Als u de video opnieuw wilt weergeven, verplaatst u de weergave terug naar het werkgebied.
