---
description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
seo-description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
seo-title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
uuid: da7b3468-3f0f-4025-927b-d47764a053af
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Een MediaPlayer-instantie opnieuw gebruiken of verwijderen {#reuse-or-remove-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

## Een MediaPlayer-instantie opnieuw instellen of gebruiken {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

Wanneer u een `MediaPlayer` instantie opnieuw instelt, wordt het teruggegeven aan zijn uninitialized status IDLE zoals bepaald in `MediaPlayerStatus`

* U wilt een `MediaPlayer` instantie opnieuw gebruiken, maar u moet een nieuwe `MediaResource` (video-inhoud) laden en de vorige instantie vervangen.

   Met resetting kunt u de `MediaPlayer` instantie opnieuw gebruiken zonder de overhead van het vrijgeven van bronnen, het opnieuw maken van de bronnen `MediaPlayer`en het opnieuw toewijzen van bronnen.

* Wanneer de status FOUT `MediaPlayer` is en moet worden gewist.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de status van de FOUT terug te krijgen.

   1. Vraag `reset` om de `MediaPlayer` instantie aan zijn uninitialized status terug te keren:

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Gebruik deze optie `MediaPlayer.replaceCurrentResource()` om een andere `MediaResource`te laden.

      >[!NOTE]
      >
      >Als u een fout wilt wissen, laadt u dezelfde fout `MediaResource`.

   1. Wanneer u de `STATUS_CHANGED` gebeurteniscallback met `PREPARED` status ontvangt, begin de playback.

## Een MediaPlayer-instantie en -bronnen opheffen {#section_13A0914AFF784943ABC343F7EB249C4E}

U zou een `MediaPlayer` geval en middelen moeten vrijgeven wanneer u niet meer nodig hebt `MediaResource`.

Wanneer u een `MediaPlayer` object loslaat, worden de onderliggende hardwarebronnen die aan dit `MediaPlayer` object zijn gekoppeld, gedeallocatie.

Hier volgen enkele redenen om een `MediaPlayer`:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Als u een onnodig `MediaPlayer` object instantieert, kan dit leiden tot een continu batterijverbruik voor mobiele apparaten.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

* Laat de muisknop los `MediaPlayer`.

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >Nadat de `MediaPlayer` instantie is losgelaten, kunt u deze niet meer gebruiken. Als om het even welke methode van de `MediaPlayer` interface wordt geroepen nadat het wordt vrijgegeven, `MediaPlayerException` wordt geworpen.