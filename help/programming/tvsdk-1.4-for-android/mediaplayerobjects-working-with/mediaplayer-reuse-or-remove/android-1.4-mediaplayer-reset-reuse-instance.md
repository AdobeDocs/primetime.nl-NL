---
description: Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerState wordt bepaald.
seo-description: Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerState wordt bepaald.
seo-title: Een MediaPlayer-instantie opnieuw instellen of gebruiken
title: Een MediaPlayer-instantie opnieuw instellen of gebruiken
uuid: 72cc4511-8ab0-44e5-b93c-b36f0321bba8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Een MediaPlayer-instantie opnieuw instellen, opnieuw gebruiken of verwijderen {#reset-or-reuse-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerState wordt bepaald.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` instantie opnieuw gebruiken, maar u moet een nieuwe `MediaResource` (video-inhoud) laden en de vorige instantie vervangen.

   Met resetting kunt u de `MediaPlayer` instantie opnieuw gebruiken zonder de overhead van het vrijgeven van bronnen, het opnieuw maken van de bronnen `MediaPlayer`en het opnieuw toewijzen van bronnen.

* Wanneer de status `MediaPlayer` FOUT is en moet worden gewist.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de staat van de FOUT terug te krijgen.

1. Vraag `reset` om de `MediaPlayer` instantie aan zijn uninitialized staat terug te keren:

   ```java
   void reset() throws IllegalStateException; 
   ```

1. Gebruik deze optie `MediaPlayer.replaceCurrentResource` om een andere `MediaResource`te laden.

   >[!TIP]
   >
   >Als u een fout wilt wissen, laadt u dezelfde fout `MediaResource`.

1. Start het afspelen wanneer u de `STATUS_CHANGED` gebeurteniscallback met de status PREPARED ontvangt.

## Een MediaPlayer-instantie en -bronnen opheffen{#release-a-mediaplayer-instance-and-resources}

U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.

Wanneer u een `MediaPlayer` object loslaat, worden de onderliggende hardwarebronnen die aan dit `MediaPlayer` object zijn gekoppeld, gedeallocatie.

Hier volgen enkele redenen om een MediaPlayer vrij te geven:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Het achterlaten van een onnodig `MediaPlayer` object kan leiden tot een continu batterijverbruik voor mobiele apparaten.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

1. Laat de muisknop los `MediaPlayer`.

   ```java
   void release() throws IllegalStateException;
   ```

Nadat de `MediaPlayer` instantie is losgelaten, kunt u deze niet meer gebruiken. Als om het even welke methode van de `MediaPlayer` interface wordt geroepen nadat het wordt vrijgegeven, `IllegalStateException` wordt geworpen.