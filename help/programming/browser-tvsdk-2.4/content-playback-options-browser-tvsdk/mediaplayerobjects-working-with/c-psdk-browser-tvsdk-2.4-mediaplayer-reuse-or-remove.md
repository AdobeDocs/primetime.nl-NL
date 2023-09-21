---
description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Een MediaPlayer-instantie opnieuw gebruiken of verwijderen{#reuse-or-remove-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

## Een MediaPlayer-instantie opnieuw instellen of gebruiken {#section_C183E6164C184C3CBC5321FC6A2528EA}

U kunt een `MediaPlayer` instantie om de niet-geïnitialiseerde status van de ILLE te herstellen, zoals gedefinieerd in `MediaPlayerStatus`. U kunt het huidige media-item ook vervangen of een nieuw item instellen met behulp van een eerder geladen media-bron.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` -instantie maar moet een nieuwe instantie laden `MediaResource` (video-inhoud) en vervangt u de vorige instantie.

  Met opnieuw instellen kunt u de opdracht `MediaPlayer` instantie zonder de overhead van het vrijgeven van bronnen, opnieuw maken van de `MediaPlayer`en herallocatie van middelen. De `replaceCurrentItem` Deze stappen worden automatisch voor u uitgevoerd.

* Wanneer de `MediaPlayer` bevindt zich in een FOUT-status en moet worden gewist.

  >[!IMPORTANT]
  >
  >Dit is de enige manier om van de staat van de FOUT terug te krijgen.

1. Bellen `MediaPlayer.reset()` om de `MediaPlayer` instantie in de niet-geïnitialiseerde status:

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. Bellen `MediaPlayer.replaceCurrentItem()` om een andere `MediaResource`

   >[!TIP]
   >
   >Als u een fout wilt wissen, laadt u dezelfde `MediaResource`.

1. Roep de `prepareToPlay()` methode.

   >[!NOTE]
   >
   >Wanneer u de `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` Met de status PREPARED kunt u het afspelen starten.

## Een MediaPlayer-instantie en -bronnen opheffen {#section_2D159975C82245098E7078FE0B1578CE}

U moet een `MediaPlayer` instantie en bronnen wanneer u de MediaResource niet meer nodig hebt.

Hier volgen enkele redenen om een `MediaPlayer`:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Een onnodige `MediaPlayer` -object kan leiden tot een continu batterijverbruik voor mobiele apparaten.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

* Laat de `MediaPlayer`.

  ```js
  void release()
  ```

  >[!NOTE]
  >
  >Na de `MediaPlayer` -instantie wordt vrijgegeven, kunt u deze niet meer gebruiken. Indien een methode van de `MediaPlayer` de interface wordt geroepen nadat het wordt vrijgegeven, en `IllegalStateException` wordt gegenereerd.
