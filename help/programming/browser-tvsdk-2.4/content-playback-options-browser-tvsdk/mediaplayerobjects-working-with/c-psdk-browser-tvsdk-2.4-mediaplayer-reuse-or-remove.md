---
description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
seo-description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
seo-title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
uuid: 0b9a06b0-ece7-4e18-9221-a4528bcbc141
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Een MediaPlayer-instantie opnieuw gebruiken of verwijderen{#reuse-or-remove-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

## Een MediaPlayer-instantie opnieuw instellen of gebruiken {#section_C183E6164C184C3CBC5321FC6A2528EA}

U kunt een `MediaPlayer` instantie opnieuw instellen om de niet-geïnitialiseerde status van het item te herstellen, zoals gedefinieerd in `MediaPlayerStatus`. U kunt het huidige media-item ook vervangen of een nieuw item instellen met behulp van een eerder geladen media-bron.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` instantie opnieuw gebruiken, maar u moet een nieuwe `MediaResource` (video-inhoud) laden en de vorige instantie vervangen.

   Met resetting kunt u de `MediaPlayer` instantie opnieuw gebruiken zonder de overhead van het vrijgeven van bronnen, het opnieuw maken van de bronnen `MediaPlayer`en het opnieuw toewijzen van bronnen. Deze stappen worden automatisch door de `replaceCurrentItem` methode uitgevoerd.

* Wanneer de status `MediaPlayer` FOUT is en moet worden gewist.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de staat van de FOUT terug te krijgen.

1. Vraag `MediaPlayer.reset()` om de `MediaPlayer` instantie aan zijn uninitialized staat terug te keren:

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. Vraag `MediaPlayer.replaceCurrentItem()` om een andere te laden `MediaResource`

   >[!TIP]
   >
   >Als u een fout wilt wissen, laadt u dezelfde fout `MediaResource`.

1. Roep de `prepareToPlay()` methode aan.

   >[!NOTE]
   >
   >Wanneer u de `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` gebeurtenis ontvangt met de status PREPARED, kunt u het afspelen starten.

## Een MediaPlayer-instantie en -bronnen opheffen {#section_2D159975C82245098E7078FE0B1578CE}

U zou een `MediaPlayer` instantie en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.

Hier volgen enkele redenen om een `MediaPlayer`:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Het achterlaten van een onnodig `MediaPlayer` object kan leiden tot een continu batterijverbruik voor mobiele apparaten.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

* Laat de muisknop los `MediaPlayer`.

   ```js
   void release()
   ```

   >[!NOTE]
   >
   >Nadat de `MediaPlayer` instantie is losgelaten, kunt u deze niet meer gebruiken. Als om het even welke methode van de `MediaPlayer` interface wordt geroepen nadat het wordt vrijgegeven, `IllegalStateException` wordt geworpen.

