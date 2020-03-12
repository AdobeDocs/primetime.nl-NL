---
description: Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerStatus wordt bepaald.
seo-description: Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerStatus wordt bepaald.
seo-title: Een MediaPlayer-instantie opnieuw instellen of gebruiken
title: Een MediaPlayer-instantie opnieuw instellen of gebruiken
uuid: b376096b-0aed-4ac2-96e5-e30a4eaf742e
translation-type: tm+mt
source-git-commit: c547002eb8946f8ccc5a79d0836f3f814e823b97

---


# Een MediaPlayer-instantie opnieuw instellen of gebruiken{#reset-or-reuse-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerStatus wordt bepaald.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` instantie opnieuw gebruiken, maar u moet een nieuwe `MediaResource` (video-inhoud) laden en de vorige instantie vervangen.

   Met resetting kunt u de `MediaPlayer` instantie opnieuw gebruiken zonder de overhead van het vrijgeven van bronnen, het opnieuw maken van de bronnen `MediaPlayer`en het opnieuw toewijzen van bronnen. De `replaceCurrentItem` en `replaceCurrentResource` methodes doen automatisch deze stappen voor u, zonder het moeten de terugstellingsmethode roepen.

* Wanneer de status FOUT `MediaPlayer` heeft en moet worden gewist.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de status van de FOUT terug te krijgen.

1. Vraag `reset` om de `MediaPlayer` instantie aan zijn uninitialized staat terug te keren:

   ```
   function reset():void; 
   ```

1. Gebruik `MediaPlayer.replaceCurrentItem` of `MediaPlayer.replaceCurrentResource` om een andere toepassing te laden `MediaResource`.

   >[!TIP]
   >
   >Als u een fout wilt wissen, laadt u dezelfde fout `MediaResource`.

1. Start het afspelen wanneer u de video ontvangt `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` met de `PREPARED` status.
