---
description: De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset's availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.
title: Ondertiteling weergeven
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Ondertiteling weergeven {#expose-subtitles}

De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset&#39;s availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.

U hebt toegang tot de beschikbare ondertitels via het dialoogvenster `PTMediaPlayerItem` eigendom `subtitlesOptions`.

Ondertiteling toegankelijk maken:

1. De client registreren als een listener voor de `PTMediaPlayerMediaSelectionOptionsAvailableNotification` kennisgeving.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Wanneer uw klant deze melding ontvangt, zijn de ondertitels gereed in het dialoogvenster `PTMediaPlayerItem`.
1. Implementeer de `onMediaPlayerItemMediaSelectionOptionsAvailable` methode vergelijkbaar met het volgende voorbeeld:

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Zie voor informatie over alternatieve audiotracks  [Alternatieve audio](../../alternate-audio/ios-3x-alternate-audio.md).
