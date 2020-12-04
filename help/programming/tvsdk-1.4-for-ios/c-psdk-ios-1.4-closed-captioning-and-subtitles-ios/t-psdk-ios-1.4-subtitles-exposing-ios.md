---
description: De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset's availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.
seo-description: De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset's availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.
seo-title: Ondertiteling weergeven
title: Ondertiteling weergeven
uuid: 657ab9c7-b205-4d13-81a7-51bc8e7d5ee2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '110'
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

   Zie [Alternate Audio](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md) voor informatie over alternatieve audiotracks.