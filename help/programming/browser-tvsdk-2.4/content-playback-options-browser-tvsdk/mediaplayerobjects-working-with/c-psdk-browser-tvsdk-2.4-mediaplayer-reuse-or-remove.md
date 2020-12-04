---
description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
seo-description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
seo-title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
uuid: 0b9a06b0-ece7-4e18-9221-a4528bcbc141
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Een MediaPlayer-instantie opnieuw gebruiken of verwijderen{#reuse-or-remove-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

## Een MediaPlayer-instantie {#section_C183E6164C184C3CBC5321FC6A2528EA} opnieuw instellen of gebruiken

U kunt een `MediaPlayer` instantie terugstellen om het aan zijn niet geïnitialiseerde staat terug te keren IDLE zoals die in `MediaPlayerStatus` wordt bepaald. U kunt het huidige media-item ook vervangen of een nieuw item instellen met behulp van een eerder geladen media-bron.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` instantie opnieuw gebruiken maar moet een nieuwe `MediaResource` (video-inhoud) laden en de vorige instantie vervangen.

   Met resetting kunt u de `MediaPlayer`-instantie opnieuw gebruiken zonder de overhead van het vrijgeven van bronnen, het opnieuw maken van de `MediaPlayer` en het opnieuw toewijzen van bronnen. De `replaceCurrentItem` methode doet automatisch deze stappen voor u.

* Wanneer `MediaPlayer` in een FOUTstatus is en moet worden ontruimd.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de staat van de FOUT terug te krijgen.

1. Roep `MediaPlayer.reset()` aan om de `MediaPlayer` instantie aan zijn uninitialized staat terug te keren:

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. Roep `MediaPlayer.replaceCurrentItem()` aan om een andere `MediaResource` te laden

   >[!TIP]
   >
   >Als u een fout wilt wissen, laadt u dezelfde `MediaResource`.

1. Roep de methode `prepareToPlay()` aan.

   >[!NOTE]
   >
   >Wanneer u de gebeurtenis `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` met de status PREPARED ontvangt, kunt u het afspelen starten.

## Een MediaPlayer-instantie en -bronnen opheffen {#section_2D159975C82245098E7078FE0B1578CE}

U zou een `MediaPlayer` instantie en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.

Hier zijn enkele redenen om een `MediaPlayer` vrij te geven:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Als u een overbodig `MediaPlayer`-object overlaat, kan dit leiden tot een continu batterijverbruik voor mobiele apparaten.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

* Geef `MediaPlayer` vrij.

   ```js
   void release()
   ```

   >[!NOTE]
   >
   >Nadat de `MediaPlayer` instantie wordt vrijgegeven, kunt u het niet meer gebruiken. Als om het even welke methode van de `MediaPlayer` interface wordt geroepen nadat het wordt vrijgegeven, wordt `IllegalStateException` geworpen.

