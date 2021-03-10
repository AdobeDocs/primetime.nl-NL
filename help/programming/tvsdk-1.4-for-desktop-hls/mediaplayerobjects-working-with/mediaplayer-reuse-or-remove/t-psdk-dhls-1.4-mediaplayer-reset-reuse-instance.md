---
description: Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerStatus wordt bepaald.
title: Een MediaPlayer-instantie opnieuw instellen of gebruiken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---


# Een MediaPlayer-instantie opnieuw instellen of opnieuw gebruiken{#reset-or-reuse-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerStatus wordt bepaald.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` instantie opnieuw gebruiken maar moet een nieuwe `MediaResource` (video-inhoud) laden en de vorige instantie vervangen.

   Met resetting kunt u de `MediaPlayer`-instantie opnieuw gebruiken zonder de overhead van het vrijgeven van bronnen, het opnieuw maken van de `MediaPlayer` en het opnieuw toewijzen van bronnen. De `replaceCurrentItem` en `replaceCurrentResource` methodes doen automatisch deze stappen voor u, zonder het moeten de terugstellingsmethode roepen.

* Wanneer `MediaPlayer` een status van de FOUT heeft en moet worden ontruimd.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de status van de FOUT terug te krijgen.

1. Roep `reset` aan om de `MediaPlayer` instantie aan zijn niet-geïnitialiseerde staat terug te keren:

   ```
   function reset():void; 
   ```

1. Gebruik `MediaPlayer.replaceCurrentItem` of `MediaPlayer.replaceCurrentResource` om een andere `MediaResource` te laden.

   >[!TIP]
   >
   >Als u een fout wilt wissen, laadt u dezelfde `MediaResource`.

1. Wanneer u `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` met de status `PREPARED` ontvangt, begin de playback.
