---
description: Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerStatus wordt bepaald.
title: Een MediaPlayer-instantie opnieuw instellen of gebruiken
exl-id: e06a0052-ce0a-4a6c-8ebc-0666b109cf07
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Een MediaPlayer-instantie opnieuw instellen of gebruiken{#reset-or-reuse-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerStatus wordt bepaald.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` -instantie maar moet een nieuwe instantie laden `MediaResource` (video-inhoud) en vervangt u de vorige instantie.

   Met opnieuw instellen kunt u de opdracht `MediaPlayer` instantie zonder de overhead van het vrijgeven van bronnen, opnieuw maken van de `MediaPlayer`en herallocatie van middelen. De `replaceCurrentItem` en `replaceCurrentResource` de methodes doen automatisch deze stappen voor u, zonder het moeten de terugstellingsmethode roepen.

* Wanneer de `MediaPlayer` heeft een FOUT-status en moet worden gewist.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de status van de FOUT terug te krijgen.

1. Bellen `reset` om de `MediaPlayer` instantie in de niet-geïnitialiseerde status:

   ```
   function reset():void; 
   ```

1. Gebruiken `MediaPlayer.replaceCurrentItem` of `MediaPlayer.replaceCurrentResource` om een andere te laden `MediaResource`.

   >[!TIP]
   >
   >Als u een fout wilt wissen, laadt u dezelfde `MediaResource`.

1. Wanneer u de `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` met de `PREPARED` status, start het afspelen.
