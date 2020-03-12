---
description: De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset's availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.
seo-description: De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset's availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.
seo-title: Ondertiteling weergeven
title: Ondertiteling weergeven
uuid: 1cd8761f-6e6f-4017-9852-fa61f36197c5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Ondertiteling weergeven {#expose-subtitles}

De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset&#39;s availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.

U hebt toegang tot de beschikbare ondertitels via de `PTMediaPlayerItem` eigenschap `subtitlesOptions`.

Ondertiteling toegankelijk maken:

1. Registreer de client als listener voor het `PTMediaPlayerMediaSelectionOptionsAvailableNotification` bericht.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Wanneer uw klant dit bericht ontvangt, zijn de ondertitels klaar in het `PTMediaPlayerItem`.
1. Voer de `onMediaPlayerItemMediaSelectionOptionsAvailable` methode uit gelijkend op het volgende voorbeeld:

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Zie [Alternatieve audio](../../alternate-audio/ios-3x-alternate-audio.md)voor informatie over alternatieve audiotracks.