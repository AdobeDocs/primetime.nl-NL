---
description: De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset's availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.
title: Ondertiteling weergeven
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Ondertiteling {#expose-subtitles} weergeven

De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset&#39;s availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.

U kunt tot de beschikbare ondertitels door `PTMediaPlayerItem` bezit `subtitlesOptions` toegang hebben.

Ondertiteling toegankelijk maken:

1. Registreer de client als listener voor het `PTMediaPlayerMediaSelectionOptionsAvailableNotification`-bericht.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Wanneer uw klant deze melding ontvangt, zijn de ondertitels gereed in `PTMediaPlayerItem`.
1. Voer de methode `onMediaPlayerItemMediaSelectionOptionsAvailable` gelijkend op het volgende voorbeeld uit:

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Zie [Alternate Audio](../../alternate-audio/ios-3x-alternate-audio.md) voor informatie over alternatieve audiotracks.